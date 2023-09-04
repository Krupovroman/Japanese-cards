<script>
    import { NButton, NCard } from 'naive-ui'
    import _ from 'lodash'
    import * as XLSX from 'xlsx/xlsx.mjs';
    export default {
        components: { NButton, NCard },
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
            exportTemplate() {
                const data = this.wordList.map(item => { 
                    return {
                        group: item.groupName ,
                        kana: item.word ,
                        kanji: item.wordWithKanji ,
                        translate: item.translate ,
                    }
                 });
                const filename='Шаблон.xlsx';
                var ws = XLSX.utils.json_to_sheet(data);
                var wb = XLSX.utils.book_new();
                XLSX.utils.book_append_sheet(wb, ws);
                XLSX.writeFile(wb,filename);
            }
        },
        created() {
        }
    }
</script>

<template>
    <div class="exam-wrapper">
        <n-card title="FAQ" size="large">
            <n-button :on-click="exportTemplate" type="warning">
                Экспорт файла шаблона
            </n-button>            
        </n-card>
    </div>
</template>

<style scoped>
.exam-wrapper {
    height: 100%;
}

.question-text {
    font-size: 60px;
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
    font-size: 30px;
    font-family: "Tsunagi Gothic Black";
}
</style>
