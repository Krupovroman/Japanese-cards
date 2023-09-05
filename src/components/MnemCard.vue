<script setup>
    import { NButton, NIcon } from 'naive-ui'
    defineProps({
        wordWithKanji: {
          type: String,
          required: true
        },
        word: {
          type: String,
          required: false
        },
        translate: {
          type: String,
          required: true
        },
        groupName: {
          type: String,
          required: false
        },
        img: {
          type: String,
          required: false
        },
        playVoice: {
          type: Function,
          required: false
        },
        isChrome: {
          type: Boolean,
          required: false
        }
    })
</script>

<template>
    <div class="mnem-box">
        <div class="mnem-box-group-name"><span style="max-width: 80%; text-decoration: underline;">{{ groupName ? groupName : ' - ' }}</span>
          <n-button v-if="isChrome" circle tertiary :onclick="() => { playVoice(wordWithKanji) }">
            <template #icon>
              <n-icon>
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512"><path d="M133 440a35.37 35.37 0 0 1-17.5-4.67c-12-6.8-19.46-20-19.46-34.33V111c0-14.37 7.46-27.53 19.46-34.33a35.13 35.13 0 0 1 35.77.45l247.85 148.36a36 36 0 0 1 0 61l-247.89 148.4A35.5 35.5 0 0 1 133 440z" fill="currentColor"></path></svg>
              </n-icon>
            </template>
          </n-button>
        </div>
        <div class="mnem-box-text"><span>{{ wordWithKanji }}</span></div>
        <div class="mnem-box-text"><span>{{ word ? word : ' - ' }}</span></div>
        <div class="mnem-box-text"><span>{{ translate }}</span></div>
    </div>
</template>

<style scoped>
.mnem-box {
    min-height: 150px;
    background-color: #ffcb5d;
    transition: 0.2s;
    box-shadow: 0px -1px 16px 0px rgba(34, 60, 80, 0.1);
    border-radius: 0 10px 10px 0px;
    padding: 10px;
    display: flex;
    justify-content: space-evenly;
    flex-direction: column;
    transition: 0.3s;
}
.mnem-box:hover {
    background-color: #FFD680;
}
.mnem-box-text {
    width: 100%;
    border-bottom: 1px dotted black;
    font-size: 18px;
    font-family: "Tsunagi Gothic Black";
    pointer-events: none;
}

.mnem-box-group-name {
    width: 100%;
    display: flex;
    justify-content: space-between;
    font-family: "Tsunagi Gothic Black";
    font-size: 12px;
    
}
.dot {
    width: 20px;
    height: 20px;
    position: absolute;
    background-color: white;
    border-radius: 50%;
}
</style>
