<script>
    import { NSelect, NButton, NCheckbox, NCard, NAlert, NTable } from 'naive-ui'
    import _ from 'lodash'
    export default {
        components: { NSelect, NButton, NCheckbox, NCard, NAlert, NTable },
        computed: {
            groups() {
                return _.uniq(this.wordList.map(item => item.groupName));
            }
        },
        props: {
            wordList: {
              type: Array,
              required: true
            }
        },
        data() {
            return {
                groupOptions: [],
                onlyKanji: false,
                onlyTranslate: false,
                selectedWords: [],
                isStarted: false,
                selectedGroup: [],
                questionNumber: 0,
                error: null,
                isEnd: false,
                statistic: {}
            }
            
        },
        methods: {
            checkboxKanjiChanged(val) {
                this.onlyKanji = val;
            },
            checkboxOnlyTranslateChanged(val) {
                this.onlyTranslate = val;
            },
            startExam() {
                this.selectedWords = this.selectedGroup.length > 0 && !this.selectedGroup.includes(null) ? this.wordList.filter(item => this.selectedGroup.some(group => group === item.groupName)) : this.wordList;
                this.selectedWords = _.uniqBy(this.selectedWords, 'word');

                if(this.selectedWords.length < 4) {
                    this.error = {title: 'Ошибка', text: 'В выборке содержится менее 4 слов, выберите больше групп'};
                    setTimeout(() => { this.error = null }, 5000);
                    return;
                }

                this.shuffleArray(this.selectedWords);

                this.selectedWords = this.selectedWords.map((item, key) => {
                    let arr = [key];
                    while(arr.length < 4){
                        let r = _.random(0, this.selectedWords.length - 1);
                        if(arr.indexOf(r) === -1) arr.push(r);
                    }
                    this.shuffleArray(arr);
                    return {...item, answer: null, answerOptions: arr, selectedButton: null}
                });

                this.isStarted = true;
            },
            groupSelect(val) {
                this.selectedGroup = val;
            },
            reinit() {
                this.onlyKanji = false;
                this.onlyTranslate = false;
                this.selectedWords = [];
                this.isStarted = false;
                this.selectedGroup = [];
                this.questionNumber = 0;
                this.isEnd = false;
                this.statistic = {};
            },
            shuffleArray(array) {
                for (var i = array.length - 1; i > 0; i--) {
                    var j = Math.floor(Math.random() * (i + 1));
                    var temp = array[i];
                    array[i] = array[j];
                    array[j] = temp;
                }
            },
            changeQuestion(val) {
                val === 'minus' ? this.questionNumber-- : this.questionNumber++;
            },
            setAnswer(id, answerId, key) {
                this.selectedWords[id].answer = answerId;
                this.selectedWords[id].selectedButton = key;
            },
            endExam() {
                this.statistic = {
                    answersCount: this.selectedWords.filter(item => item.answer !== null).length,
                    correctAnswersCount: this.selectedWords.filter((item, key) => item.answer === key).length,
                    wordsWithError: this.selectedWords.filter((item, key) => item.answer !== key),
                }
                this.isEnd = true;

            }
        },
        created() {
            this.groupOptions = this.groups.map(item => { return { label: item, value: item } });
            this.groupOptions.unshift({value: null, label: 'Все'});
        }
    }
</script>

<template>
    <div class="exam-wrapper">
        <n-card title="Тестирование" size="large">
            <div v-if="!isStarted">
                <div v-if="error">
                    <n-alert :title="error.title" type="error">
                      {{ error.text }}
                    </n-alert>
                </div>
                <div style="padding-top: 20px; display: flex; justify-content: center; align-items: center; flex-direction: column;">
                    <n-select class="group-select" :options="groupOptions" placeholder="Выберите группу слов" multiple :on-update:value="groupSelect" filterable />
                    <div class="config-checkbox-wrapper" style="display: flex; padding-top: 20px; justify-content: start;">
                        <n-checkbox label="Только кандзи" :on-update-checked="checkboxKanjiChanged" />
                        <n-checkbox label="Режим перевода" :on-update-checked="checkboxOnlyTranslateChanged" style="padding-left: 20px;" />
                    </div>
                </div>
                <div style="padding-top: 20px; display: flex; justify-content: center;">
                    <n-button :on-click="startExam" type="success">Начать</n-button>
                </div>
            </div>
            <div v-else>
                <div v-if="!isEnd">
                    <div>
                        <div>
                            <span class="counter">{{ (questionNumber + 1) + ' / ' + (selectedWords.length)}}</span>
                        </div>
                        <div style="display: flex; flex-direction: column; justify-content: center;">
                            <span class="question-text">{{ onlyTranslate ? selectedWords[questionNumber].translate : selectedWords[questionNumber].wordWithKanji }}</span>
                            <span v-if="!onlyKanji && !onlyTranslate" class="question-text">{{ selectedWords[questionNumber].word }}</span>
                        </div>
                        <div style="width: 100%; display: grid; grid-template-columns: repeat(2, 1fr); padding-top: 20px;">
                            <n-button style="width: 100%; height: 100%; white-space: normal;" :type="(selectedWords[questionNumber].answer === null || selectedWords[questionNumber].selectedButton !== key) ? 'default' : selectedWords[questionNumber].answer === questionNumber ? 'success' : 'error'" 
                            :disabled="selectedWords[questionNumber].answer !== null" class="answer-text" v-bind:key="item + key + Math.random()" v-for="item, key in selectedWords[questionNumber].answerOptions" :on-click="() => {setAnswer(questionNumber, item, key)}">
                                {{ onlyTranslate ? selectedWords[item].wordWithKanji + (onlyKanji ? '' : ` (${selectedWords[item].word})`) : selectedWords[item].translate }}
                            </n-button>
                        </div>
                    </div>
                    <div style="display: flex; justify-content: space-around; padding-top: 20px;">
                        <n-button :disabled="questionNumber === 0" type="warning" :on-click="() => {changeQuestion('minus')}">
                            Предыдущий
                        </n-button>
                        <n-button :disabled="questionNumber === selectedWords.length - 1" type="warning" :on-click="() => {changeQuestion('plus')}">
                            Следующий
                        </n-button>
                    </div>
                    <div style="display: flex; justify-content: end; margin-top: 20px;">
                        <n-button type="error" :on-click="() => {endExam()}">
                            Завершить
                        </n-button>
                    </div>
                </div>
                <div v-else style="display: flex; flex-direction: column;" class="statistic">
                    <div style="display: flex; justify-content: flex-end;">
                        <n-button style="margin-bottom: 20px;" type="info" :on-click="() => {reinit()}">
                            Заново
                        </n-button>
                    </div>
                    <span>{{ 'Количество ответов: ' + this.statistic.answersCount + ' / ' + selectedWords.length}}</span>
                    <span>{{ 'Количество правильных ответов: ' + this.statistic.correctAnswersCount  + ' / ' + selectedWords.length }}</span>
                    <div v-if="this.statistic.wordsWithError.length">
                        <span>Слова для повторения:</span>
                        <n-table size="small" :bordered="false" :single-line="false">
                          <thead>
                            <tr>
                              <th>Слово</th>
                              <th>Хирагана <br/> Катакана</th>
                              <th>Перевод</th>
                              <th>Группа</th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr v-bind:key="key" v-for="word, key in this.statistic.wordsWithError">
                              <td>{{ word.wordWithKanji }}</td>
                              <td>{{ word.word }}</td>
                              <td>{{ word.translate }}</td>
                              <td>{{ word.groupName ? word.groupName : ' - ' }}</td>
                            </tr>
                          </tbody>
                        </n-table>
                    </div>
                </div>
            </div>
        </n-card>
    </div>
</template>

<style scoped>
.exam-wrapper {
    height: 100%;
}

.question-text {
    font-family: "Tsunagi Gothic Black";
    pointer-events: none;
    text-align: center;
}

.answer-text {
    font-size: 14px;
    padding: 10px;
    font-family: "Tsunagi Gothic Black";
}

.counter { 
    font-size: 20px;
    font-family: "Tsunagi Gothic Black";
    display: flex;
    justify-content: flex-end;
    padding-bottom: 30px;
}

.statistic {
    font-family: "Tsunagi Gothic Black";
}

@media (min-width: 300px) {
    .group-select {
        width: 90%;
    }

    .question-text {
        font-size: 20px;
    }

    .statistic {
        font-size: 15px;
    }
}

@media (min-width: 1281px) {
    .group-select {
        width: 50%;
    }

    .config-checkbox-wrapper {
        width: 50%;
    }

    .question-text {
        font-size: 60px;
    }

    .statistic {
        font-size: 30px;
    }
}
</style>
