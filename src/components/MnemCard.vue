<script setup>
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
        }
    })
</script>

<template>
    <div class="mnem-box">
        <div class="mnem-box-group-name"><span>{{ groupName ? groupName : ' - ' }}</span></div>
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
    width: max-content;
    pointer-events: none;
    height: 20px;
    font-family: "Tsunagi Gothic Black";
    font-size: 12px;
    border-bottom: 1px solid black;
}
.dot {
    width: 20px;
    height: 20px;
    position: absolute;
    background-color: white;
    border-radius: 50%;
}
</style>
