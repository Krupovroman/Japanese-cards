<script>
import MnemCard from './components/MnemCard.vue'
import Exam from './components/ExamComponent.vue'
import FAQComponent from './components/FAQComponent.vue'
import { NTabs, NTabPane } from 'naive-ui'
import * as XLSX from 'xlsx/xlsx.mjs';







export default {
  components: { MnemCard, Exam, NTabPane, NTabs, FAQComponent },
  data() {
   return {
    wordList: [
    {
        "wordWithKanji": "会う",
        "word": "あう",
        "translate": "встречаться, видеться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "吹く",
        "word": "ふく",
        "translate": "подуть, веять, играть, хвастаться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "挨拶",
        "word": "あいさつ",
        "translate": "Вежливые слова приветствия и прощания",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "おはようございます",
        "word": "おはよう ございます",
        "translate": "Доброе утро",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "こんにちは ",
        "word": "こんにちは ",
        "translate": "Здравствуйте,\r\nдобрый день",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "こんばんは",
        "word": "こんばんは",
        "translate": "Добрый вечер",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "お休みなさい",
        "word": "おやすみなさい",
        "translate": "Спокойной ночи",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "さようなら",
        "word": "さようなら",
        "translate": "До свидания, прощайте",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "またあした",
        "word": "またあした",
        "translate": "До завтра",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "ありがとう",
        "word": "ありがとう",
        "translate": "Спасибо (неформально)",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "ありがとう ございます",
        "word": "ありがとう ございます",
        "translate": "Большое спасибо",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "どうも",
        "word": "どうも",
        "translate": "Спасибо (неформально)",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "どうも ありがとう ございます",
        "word": "どうも ありがとう ございます",
        "translate": "Большое спасибо",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "どういたしまして",
        "word": "どういたしまして",
        "translate": "Не за что",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "すみません",
        "word": "すみません",
        "translate": "Извините",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "失礼します",
        "word": "しつれいします",
        "translate": "Простите, пожалуйста",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "お疲れ様です",
        "word": "おつかれさまです",
        "translate": "Вы хорошо поработали",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "おめでとう ございます",
        "word": "おめでとう ございます",
        "translate": "Поздравляю",
        "groupName": "Вежливые слова для приветствия и прощания"
    },
    {
        "wordWithKanji": "日本語",
        "word": "にほんご",
        "translate": "Японский язык",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "国語",
        "word": "こくご",
        "translate": "Родной язык",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ローマ字 ",
        "word": "ローマじ",
        "translate": "Латиница",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "平仮名",
        "word": "ひらがな",
        "translate": "Хирагана",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "片仮名",
        "word": "カタカナ",
        "translate": "Катакана",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "漢字仮名交じり文",
        "word": "かんじかな まじりぶん",
        "translate": "Смешанное письмо (в японском языке)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "漢字",
        "word": "かんじ",
        "translate": "Иероглифы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "仮名",
        "word": "かな",
        "translate": "Канна (азбуки)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "てん",
        "word": "点",
        "translate": "Запятая",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "丸",
        "word": "まる",
        "translate": "Точка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "はてなマーク",
        "word": "はてなマーク",
        "translate": "Вопросительный знак",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "びっくりマーク",
        "word": "びっくりマーク",
        "translate": "Восклицательный знак",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "叔母さん",
        "word": "おばさん",
        "translate": "Тётя",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "お婆さんは",
        "word": "おばあさん",
        "translate": "Бабушка",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "叔父さん",
        "word": "おじさん",
        "translate": "Дядя",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "お爺さん",
        "word": "おじいさん",
        "translate": "Дедушка",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "母",
        "word": "はは",
        "translate": "Мама",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "父",
        "word": "ちち",
        "translate": "Папа",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "息子",
        "word": "むすこ",
        "translate": "Сын",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "娘",
        "word": "むすめ",
        "translate": "Дочь",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "兄",
        "word": "あに",
        "translate": "Старший брат",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "弟",
        "word": "おとうと",
        "translate": "Младший брат",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "姉",
        "word": "あね",
        "translate": "Старшая сестра",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "妹",
        "word": "いもうと",
        "translate": "Младшая сестра",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "両親",
        "word": "りょうしん",
        "translate": "Родители",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "家",
        "word": "うち",
        "translate": "Дом",
        "groupName": "Семья"
    },
    {
        "wordWithKanji": "はい",
        "word": "はい",
        "translate": "Да",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "いいえ",
        "word": "いいえ",
        "translate": "Нет",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "名前",
        "word": "なまえ",
        "translate": "Имя",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "会話",
        "word": "かいわ",
        "translate": "Диалог",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "私",
        "word": "わたし",
        "translate": "Я",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "塩",
        "word": "しお",
        "translate": "Соль",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "お菓子",
        "word": "おかし",
        "translate": "Сладости",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "鳥",
        "word": "とり",
        "translate": "Птица",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "夢",
        "word": "ゆめ",
        "translate": "Мечта, сон",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "初めまして",
        "word": "はじめまして",
        "translate": "Позвольте представиться",
        "groupName": "Полезные фразы для знакомства"
    },
    {
        "wordWithKanji": "よろしく お願いします",
        "word": "よろしく おねがいします",
        "translate": "Прошу любить и жаловать",
        "groupName": "Полезные фразы для знакомства"
    },
    {
        "wordWithKanji": "私はミハイルです",
        "word": "わたしは ミハイルです",
        "translate": "Я - Михаил",
        "groupName": "Полезные фразы для знакомства"
    },
    {
        "wordWithKanji": "私の名前はミハイル です",
        "word": "わたしのなまえはミハ イルです",
        "translate": "Моё имя - Михаил",
        "groupName": "Полезные фразы для знакомства"
    },
    {
        "wordWithKanji": "あなたのお名前は何 ですか",
        "word": "あなたの おなまえは （なんですか）",
        "translate": "Как Ваше имя? / Как Вас зовут?",
        "groupName": "Полезные фразы для знакомства"
    },
    {
        "wordWithKanji": "私",
        "word": "わたし",
        "translate": "я",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "私たち",
        "word": "わたしたち",
        "translate": "мы",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "あなた",
        "word": "あなた",
        "translate": "вы",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "あなたたち",
        "word": "あなたたち",
        "translate": "вы (мн.ч.)",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "彼",
        "word": "かれ",
        "translate": "он",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "彼ら",
        "word": "かれら",
        "translate": "они",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "彼女",
        "word": "かのじょ",
        "translate": "она",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "彼女たち",
        "word": "かのじょたち",
        "translate": "они (ж.р., мн.ч.)",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "あの人",
        "word": "あのひと",
        "translate": "тотчеловек, он,она",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "あの人たち",
        "word": "あのひとたち",
        "translate": "телюди,они",
        "groupName": "Местоимения"
    },
    {
        "wordWithKanji": "学生",
        "word": "がくせい",
        "translate": "студент",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "生徒",
        "word": "せいと",
        "translate": "ученик школы",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "先生",
        "word": "せんせい",
        "translate": "учитель",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "医者",
        "word": "いしゃ",
        "translate": "врач",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "エンジニア",
        "word": "エンジニア",
        "translate": "инженер",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "技師",
        "word": "ぎし",
        "translate": "инженер",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "店員",
        "word": "てんいん",
        "translate": "продавец",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "プログラマー",
        "word": "プログラマー",
        "translate": "программист",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "デザイナー",
        "word": "デザイナー",
        "translate": "дизайнер",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "調理師",
        "word": "ちょうりし",
        "translate": "повар",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "弁護士",
        "word": "べんごし",
        "translate": "адвокат",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "主婦",
        "word": "しゅふ",
        "translate": "домохозяйка",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "画家",
        "word": "がか",
        "translate": "художник",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "作家",
        "word": "さっか",
        "translate": "писатель",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "警察官",
        "word": "けいさつかん",
        "translate": "полицейский",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "看護婦",
        "word": "かんごふ",
        "translate": "медсестра",
        "groupName": "Существительные на тему \"Профессии\""
    },
    {
        "wordWithKanji": "ロシア",
        "word": "ロシア",
        "translate": "Россия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "日本",
        "word": "にほん",
        "translate": "Япония",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "アメリカ",
        "word": "アメリカ",
        "translate": "Америка",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "イギリス",
        "word": "イギリス",
        "translate": "Англия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "ドイツ",
        "word": "ドイツ",
        "translate": "Германия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "フランス",
        "word": "フランス",
        "translate": "Франция",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "イタリア",
        "word": "イタリア",
        "translate": "Италия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "インド",
        "word": "インド",
        "translate": "Индия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "スペイン",
        "word": "スペイン",
        "translate": "Испания",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "ウクライナ",
        "word": "ウクライナ",
        "translate": "Украина",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "ギリシャ",
        "word": "ギリシャ",
        "translate": "Греция",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "メキシコ",
        "word": "メキシコ",
        "translate": "Мексика",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "モンゴル",
        "word": "モンゴル",
        "translate": "Монголия",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "韓国",
        "word": "かんこく",
        "translate": "Южная Корея",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "中国",
        "word": "ちゅうごく",
        "translate": "Китай",
        "groupName": "Существительные на тему \"Страны\""
    },
    {
        "wordWithKanji": "ロシア人",
        "word": "ロシアじん",
        "translate": "русский, русская",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "日本人",
        "word": "にほんじん",
        "translate": "японец, японка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "アメリカ人",
        "word": "アメリカじん",
        "translate": "американец,\r\nамериканка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "イギリス人",
        "word": "イギリスじん",
        "translate": "англичанин,\r\nангличанка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "ドイツ人",
        "word": "ドイツじん",
        "translate": "немец, немка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "フランス人",
        "word": "フランスじん",
        "translate": "француз,\r\nфранцуженка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "イタリア人",
        "word": "イタリアじん",
        "translate": "итальянец,\r\nитальянка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "インド人",
        "word": "インドじん",
        "translate": "индиец, индианка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "スペイン人",
        "word": "スペインじん",
        "translate": "испанец, испанка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "ウクライナ人",
        "word": "ウクライナじん",
        "translate": "украинец, украинка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "ギリシャ人",
        "word": "ギリシャじん",
        "translate": "грек, гречанка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "メキシコ人",
        "word": "メキシコじん",
        "translate": "мексиканец,\r\nмексиканка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "モンゴル人",
        "word": "モンゴルじん",
        "translate": "монгол, монголка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "韓国人",
        "word": "かんこくじん",
        "translate": "кореец, кореянка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "中国人",
        "word": "ちゅうごくじん",
        "translate": "китаец, китаянка",
        "groupName": "Существительные на тему \"Жители разных стран\""
    },
    {
        "wordWithKanji": "仕事",
        "word": "しごと",
        "translate": "работа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "国",
        "word": "くに",
        "translate": "страна",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "何",
        "word": "なに（なん）",
        "translate": "что",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "友達",
        "word": "ともだち",
        "translate": "друг, подруга",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ホテル",
        "word": "ホテル",
        "translate": "отель",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "レストラン",
        "word": "レストラン",
        "translate": "ресторан",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "病院",
        "word": "びょういん",
        "translate": "больница",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "医者",
        "word": "いしゃ",
        "translate": "врач",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "スーパー",
        "word": "スーパー",
        "translate": "супермаркет",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "店員",
        "word": "てんいん",
        "translate": "продавец",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "トイレ",
        "word": "トイレ",
        "translate": "туалет",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "保育園",
        "word": "ほいくえん",
        "translate": "детский сад",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "空港",
        "word": "くうこう",
        "translate": "аэропорт",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "飛行機",
        "word": "ひこうき",
        "translate": "самолёт",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "駅",
        "word": "えき",
        "translate": "станция",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "電車",
        "word": "でんしゃ",
        "translate": "электричка",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "地下鉄",
        "word": "ちかてつ",
        "translate": "метро",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "銀行",
        "word": "ぎんこう",
        "translate": "банк",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "銀行員",
        "word": "ぎんこういん",
        "translate": "банкир",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "会社",
        "word": "かいしゃ",
        "translate": "фирма",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "会社員",
        "word": "かいしゃいん",
        "translate": "сотрудник фирмы",
        "groupName": "Существительные: Город"
    },
    {
        "wordWithKanji": "椅子",
        "word": "いす",
        "translate": "стул",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "机",
        "word": "つくえ",
        "translate": "стол",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "棚",
        "word": "たな",
        "translate": "полка",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "本",
        "word": "ほん",
        "translate": "книга",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "教科書",
        "word": "きょうかしょ",
        "translate": "учебник",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "写真",
        "word": "しゃしん",
        "translate": "фотография",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "雑誌",
        "word": "ざっし",
        "translate": "журнал",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "新聞",
        "word": "しんぶん",
        "translate": "газета",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "ノート",
        "word": "ノート",
        "translate": "тетрадь",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "ペン",
        "word": "ペン",
        "translate": "ручка",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "鉛筆",
        "word": "えんぴつ",
        "translate": "карандаш",
        "groupName": "Существительные:рабочий стол"
    },
    {
        "wordWithKanji": "猫",
        "word": "ねこ",
        "translate": "кошка",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "犬",
        "word": "いぬ",
        "translate": "собака",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "キリン",
        "word": "キリン",
        "translate": "жираф",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "象",
        "word": "ぞう",
        "translate": "слон",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "虎",
        "word": "とら",
        "translate": "тигр",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "亀",
        "word": "かめ",
        "translate": "черепаха",
        "groupName": "Существительные: животные"
    },
    {
        "wordWithKanji": "鞄",
        "word": "かばん",
        "translate": "сумка, портфель",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "電話",
        "word": "でんわ",
        "translate": "телефон\r\n(стационарный)",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "携帯電話",
        "word": "けいたいでんわ",
        "translate": "мобильный\r\nтелефон",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "名刺",
        "word": "めいし",
        "translate": "визитная карточка",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "眼鏡",
        "word": "めがね",
        "translate": "очки",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "財布",
        "word": "さいふ",
        "translate": "кошелёк",
        "groupName": "Существительные:в сумке"
    },
    {
        "wordWithKanji": "一",
        "word": "いち",
        "translate": "один",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "二",
        "word": "に",
        "translate": "два",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "三人",
        "word": "さん",
        "translate": "три",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "四",
        "word": "よん、し",
        "translate": "четыре",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "五",
        "word": "ご",
        "translate": "пять",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "六",
        "word": "ろく",
        "translate": "шесть",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "七",
        "word": "なな、しち",
        "translate": "семь",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "八",
        "word": "はち",
        "translate": "восемь",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "九",
        "word": "きゅう、く",
        "translate": "девять",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "十",
        "word": "じゅう",
        "translate": "десять",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "百",
        "word": "ひゃく",
        "translate": "сто",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "千",
        "word": "せん",
        "translate": "тысяча",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "万",
        "word": "まん",
        "translate": "десять тысяч",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "億",
        "word": "おく",
        "translate": "сто миллионов",
        "groupName": "Числительные"
    },
    {
        "wordWithKanji": "ジュース",
        "word": "ジュース",
        "translate": "сок",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "お酒",
        "word": "おさけ",
        "translate": "алкоголь",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "日本酒",
        "word": "にほんしゅ",
        "translate": "японское саке",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ビール",
        "word": "ビール",
        "translate": "пиво",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "飴",
        "word": "あめ",
        "translate": "леденец",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "蜜柑",
        "word": "みかん",
        "translate": "мандарин",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "林檎",
        "word": "りんご",
        "translate": "яблоко",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "梨",
        "word": "なし",
        "translate": "груша",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "葡萄",
        "word": "ぶどう",
        "translate": "виноград",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "オレンジ",
        "word": "オレンジ",
        "translate": "апельсин",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "バナナ",
        "word": "バナナ",
        "translate": "банан",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "苺",
        "word": "いちご",
        "translate": "клубника",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "メロン",
        "word": "メロン",
        "translate": "дыня",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "西瓜",
        "word": "すいか",
        "translate": "арбуз",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "トマト",
        "word": "トマト",
        "translate": "помидор",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "胡瓜",
        "word": "きゅうり",
        "translate": "огурец",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "キャベツ",
        "word": "キャベツ",
        "translate": "капуста",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "人参",
        "word": "にんじん",
        "translate": "морковь",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "大蒜",
        "word": "にんにく",
        "translate": "чеснок",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "玉葱",
        "word": "たまねぎ",
        "translate": "лук",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "茄子",
        "word": "なす",
        "translate": "баклажан",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "これ",
        "word": "これ",
        "translate": "это",
        "groupName": "Предметно-указательные местоимения"
    },
    {
        "wordWithKanji": "それ",
        "word": "それ",
        "translate": "это,то",
        "groupName": "Предметно-указательные местоимения"
    },
    {
        "wordWithKanji": "あれ",
        "word": "あれ",
        "translate": "то",
        "groupName": "Предметно-указательные местоимения"
    },
    {
        "wordWithKanji": "どれ",
        "word": "どれ",
        "translate": "которое?",
        "groupName": "Предметно-указательные местоимения"
    },
    {
        "wordWithKanji": "この",
        "word": "この",
        "translate": "этот",
        "groupName": "Указательные местоимения"
    },
    {
        "wordWithKanji": "その",
        "word": "その",
        "translate": "этот, тот",
        "groupName": "Указательные местоимения"
    },
    {
        "wordWithKanji": "あの",
        "word": "あの",
        "translate": "тот",
        "groupName": "Указательные местоимения"
    },
    {
        "wordWithKanji": "どの",
        "word": "どの",
        "translate": "который?",
        "groupName": "Указательные местоимения"
    },
    {
        "wordWithKanji": "ここ",
        "word": "ここ",
        "translate": "здесь",
        "groupName": "Местоимения, указывающие на место"
    },
    {
        "wordWithKanji": "そこ",
        "word": "そこ",
        "translate": "здесь, там",
        "groupName": "Местоимения, указывающие на место"
    },
    {
        "wordWithKanji": "あそこ",
        "word": "あそこ",
        "translate": "там",
        "groupName": "Местоимения, указывающие на место"
    },
    {
        "wordWithKanji": "どこ",
        "word": "どこ",
        "translate": "где?",
        "groupName": "Местоимения, указывающие на место"
    },
    {
        "wordWithKanji": "歴史",
        "word": "れきし",
        "translate": "история",
        "groupName": "Существительные: обучение, учёба"
    },
    {
        "wordWithKanji": "文学",
        "word": "ぶんがく",
        "translate": "литература",
        "groupName": "Существительные: обучение, учёба"
    },
    {
        "wordWithKanji": "数学",
        "word": "すうがく",
        "translate": "математика",
        "groupName": "Существительные: обучение, учёба"
    },
    {
        "wordWithKanji": "時計",
        "word": "とけい",
        "translate": "часы",
        "groupName": "Существительные: обучение, учёба"
    },
    {
        "wordWithKanji": "消しゴム",
        "word": "けしごむ",
        "translate": "ластик",
        "groupName": "Существительные: обучение, учёба"
    },
    {
        "wordWithKanji": "お肉",
        "word": "おにく",
        "translate": "мясо",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "卵",
        "word": "たまご",
        "translate": "яйцо",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "魚",
        "word": "さかな",
        "translate": "рыба",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "刺身",
        "word": "さしみ",
        "translate": "сашими",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "山葵",
        "word": "わさび",
        "translate": "васаби",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "果物",
        "word": "くだもの",
        "translate": "фрукты",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "野菜",
        "word": "やさい",
        "translate": "овощи",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "バター",
        "word": "バター",
        "translate": "сливочное масло",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "パン",
        "word": "パン",
        "translate": "хлеб",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "トースト",
        "word": "トースト",
        "translate": "тосты",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ケーキ",
        "word": "ケーキ",
        "translate": "пирожное, торт",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "お茶",
        "word": "おちゃ",
        "translate": "зеленый чай",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "紅茶",
        "word": "こうちゃ",
        "translate": "чёрный чай",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ナイフ",
        "word": "ナイフ",
        "translate": "нож",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "フォーク",
        "word": "フォーク",
        "translate": "вилка",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "スプーン",
        "word": "スプーン",
        "translate": "ложка",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "お誕生日",
        "word": "おたんじょうび",
        "translate": "день рождения",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "男性",
        "word": "だんせい",
        "translate": "мужчина, парень",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "女性",
        "word": "じょせい",
        "translate": "женщина,\r\nдевушка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "買い物",
        "word": "かいもの",
        "translate": "покупки",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "昼",
        "word": "ひる",
        "translate": "дневное время",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "彼",
        "word": "かれ",
        "translate": "он, парень",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "彼女",
        "word": "かのじょ",
        "translate": "она, девушка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "デパート",
        "word": "デパート",
        "translate": "универмаг",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "聞いて\r\nください",
        "word": "きいて\r\nください。",
        "translate": "Послушайте,\r\nпожалуйста",
        "groupName": "Фразы для аудирования"
    },
    {
        "wordWithKanji": "繰り返して\r\nください。",
        "word": "くりかえして\r\nください。",
        "translate": "Повторите,\r\nпожалуйста",
        "groupName": "Фразы для аудирования"
    },
    {
        "wordWithKanji": "質問します。\r\n答えてください。",
        "word": "しつもんします。\r\nこたえてください。",
        "translate": "Задаю вопрос.\r\nОтветьте,\r\nпожалуйста",
        "groupName": "Фразы для аудирования"
    },
    {
        "wordWithKanji": "読んでください。",
        "word": "よんでください。",
        "translate": "Прочитайте,\r\nпожалуйста",
        "groupName": "Фразы для аудирования"
    },
    {
        "wordWithKanji": "みてください。",
        "word": "見てください。",
        "translate": "Посмотрите,\r\nпожалуйста",
        "groupName": "Фразы для аудирования"
    },
    {
        "wordWithKanji": "朝",
        "word": "あさ",
        "translate": "утро",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "昼",
        "word": "ひる",
        "translate": "день, обеденное время",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "夜",
        "word": "よる",
        "translate": "вечер",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "晩",
        "word": "ばん",
        "translate": "вечер",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "今夜",
        "word": "こんや",
        "translate": "сегодняшний вечер",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "昨夜",
        "word": "ゆうべ",
        "translate": "вчерашний вечер",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "一昨日",
        "word": "おととい",
        "translate": "позавчера",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "昨日",
        "word": "きのう",
        "translate": "вчера",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "今日",
        "word": "きょう",
        "translate": "сегодня",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "明日",
        "word": "あした",
        "translate": "завтра",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "明後日",
        "word": "あさって",
        "translate": "послезавтра",
        "groupName": "Существительные: время"
    },
    {
        "wordWithKanji": "天気",
        "word": "てんき",
        "translate": "погода",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "勉強",
        "word": "べんきょう",
        "translate": "занятие, учёба",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "文学",
        "word": "ぶんがく",
        "translate": "литература",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "専門",
        "word": "せんもん",
        "translate": "специальность",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "経済",
        "word": "けいざい",
        "translate": "экономика",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "写真",
        "word": "しゃしん",
        "translate": "фотография",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "面白い",
        "word": "おもしろい",
        "translate": "интересный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "つまらない",
        "word": "つまらない",
        "translate": "скучный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "やさしい",
        "word": "やさしい",
        "translate": "легкий, простой;\r\nдобрый (о человеке)",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "難しい",
        "word": "むずかしい",
        "translate": "сложный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "大きい",
        "word": "おおきい",
        "translate": "большой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "小さい",
        "word": "ちいさい",
        "translate": "маленький",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "広い",
        "word": "ひろい",
        "translate": "широкий, просторный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "狭い",
        "word": "せまい",
        "translate": "тесный, маленький (о\r\nпомещении)",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "高い",
        "word": "たかい",
        "translate": "1) высокий\r\n2) дорогой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "低い",
        "word": "ひくい",
        "translate": "низкий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "安い",
        "word": "やすい",
        "translate": "дешевый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "近い",
        "word": "ちかい",
        "translate": "близкий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "いい、よい",
        "word": "いい или よい",
        "translate": "хороший",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "悪い",
        "word": "わるい",
        "translate": "плохой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "明るい",
        "word": "あかるい",
        "translate": "светлый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "黒い",
        "word": "くろい",
        "translate": "чёрный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "短い",
        "word": "みじかい",
        "translate": "короткий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "長い",
        "word": "ながい",
        "translate": "длинный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "少し",
        "word": "すこし",
        "translate": "немного",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "ちょっと",
        "word": "ちょっと",
        "translate": "немного, немножко,\r\nчуть-чуть",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "とても",
        "word": "とても",
        "translate": "очень",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "大変",
        "word": "たいへん",
        "translate": "ужасно (очень)",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "あまり",
        "word": "あまり+ отрицание",
        "translate": "не совсем",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "少しも",
        "word": "すこしも +\r\nотрицание",
        "translate": "нисколько, ничуть",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "日曜日",
        "word": "にちようび",
        "translate": "воскресенье",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "月曜日",
        "word": "げつようび",
        "translate": "понедельник",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "火曜日",
        "word": "かようび",
        "translate": "вторник",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "水曜日",
        "word": "すいようび",
        "translate": "среда",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "木曜日",
        "word": "もくようび",
        "translate": "четверг",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "金曜日",
        "word": "きんようび",
        "translate": "пятница",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "土曜日",
        "word": "どようび",
        "translate": "суббота",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "何曜日",
        "word": "なんようび",
        "translate": "какой день недели?",
        "groupName": "Дни недели"
    },
    {
        "wordWithKanji": "一昨日",
        "word": "おととい",
        "translate": "позавчера",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "昨日",
        "word": "きのう",
        "translate": "вчера",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "今日",
        "word": "きょう",
        "translate": "сегодня",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "明日",
        "word": "あした",
        "translate": "завтра",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "明後日",
        "word": "あさって",
        "translate": "послезавтра",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "今朝",
        "word": "けさ",
        "translate": "сегодняшнее утро",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "今晩",
        "word": "こんばん",
        "translate": "сегодняшний вечер",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "毎朝",
        "word": "まいあさ",
        "translate": "каждое утро",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "毎晩",
        "word": "まいばん",
        "translate": "каждый вечер",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "毎日",
        "word": "まいにち",
        "translate": "каждый день",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "週",
        "word": "しゅう",
        "translate": "неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "毎週",
        "word": "まいしゅう",
        "translate": "каждая неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "先々週",
        "word": "せんせんしゅう",
        "translate": "позапрошлая неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "先週",
        "word": "せんしゅう",
        "translate": "прошлая неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "今週",
        "word": "こんしゅう",
        "translate": "эта неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "来週",
        "word": "らいしゅう",
        "translate": "следующая неделя",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "再来週",
        "word": "さらいしゅう",
        "translate": "неделя после\r\nследующей",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "四季",
        "word": "しき",
        "translate": "времена года",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "冬",
        "word": "ふゆ",
        "translate": "зима",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "春",
        "word": "はる",
        "translate": "весна",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "夏",
        "word": "なつ",
        "translate": "лето",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "秋",
        "word": "あき",
        "translate": "осень",
        "groupName": "Существительные о времени"
    },
    {
        "wordWithKanji": "休み",
        "word": "やすみ",
        "translate": "выходной, отдых",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "昼休み",
        "word": "ひるやすみ",
        "translate": "обеденный перерыв",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "冬休み",
        "word": "ふゆやすみ",
        "translate": "зимние каникулы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "春休み",
        "word": "はるやすみ",
        "translate": "весенние каникулы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "夏休み",
        "word": "なつやすみ",
        "translate": "летние каникулы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "秋休み",
        "word": "あきやすみ",
        "translate": "осенние каникулы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "パーティー",
        "word": "パーティー",
        "translate": "вечеринка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "道",
        "word": "みち",
        "translate": "путь, дорога",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "しけん",
        "word": "試験",
        "translate": "экзамен",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テスト",
        "word": "テスト",
        "translate": "тест",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "結婚",
        "word": "けっこん",
        "translate": "свадьба",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "結婚式",
        "word": "けっこんしき",
        "translate": "свадебная церемония",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "誕生日",
        "word": "たんじょうび",
        "translate": "день рождения",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "プレゼント",
        "word": "プレゼント",
        "translate": "подарок",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "会議",
        "word": "かいぎ",
        "translate": "совещание",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "仕事",
        "word": "しごと",
        "translate": "работа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "親戚",
        "word": "しんせき",
        "translate": "родственники (свои)",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "祖父",
        "word": "そふ",
        "translate": "дедушка",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "祖母",
        "word": "そぼ",
        "translate": "бабушка",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "両親",
        "word": "りょうしん",
        "translate": "родители",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "父",
        "word": "ちち",
        "translate": "отец",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "母",
        "word": "はは",
        "translate": "мать",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "叔父",
        "word": "おじ",
        "translate": "дядя",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "叔母",
        "word": "おば",
        "translate": "тётя",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "兄妹",
        "word": "きょうだい",
        "translate": "братья и сёстры",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "姉",
        "word": "あね",
        "translate": "сестра",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "兄",
        "word": "あに",
        "translate": "брат",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "弟",
        "word": "おとうと",
        "translate": "младший брат",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "妹",
        "word": "いもうと",
        "translate": "младшая сестра",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "夫",
        "word": "おっと",
        "translate": "муж",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "妻",
        "word": "つま",
        "translate": "жена",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "息子",
        "word": "むすこ",
        "translate": "сын",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "娘",
        "word": "むすめ",
        "translate": "дочь",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "ご親戚",
        "word": "ごしんせき",
        "translate": "родственники (чужие\r\nили обращение)",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お爺さん",
        "word": "おじいさん",
        "translate": "дедушка",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お婆さん",
        "word": "おばあさん",
        "translate": "бабушка",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "ご両親",
        "word": "ごりょうしん",
        "translate": "родители",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お父さん",
        "word": "おとうさん",
        "translate": "отец",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お母さん",
        "word": "おかあさん",
        "translate": "мать",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "叔父さん",
        "word": "おじさん",
        "translate": "дядя",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "叔母さん",
        "word": "おばさん",
        "translate": "тётя",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "ご兄妹",
        "word": "ごきょうだい",
        "translate": "братья и сёстры",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お姉さん",
        "word": "おねえさん",
        "translate": "сестра",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "お兄さん",
        "word": "おにいさん",
        "translate": "брат",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "弟さん",
        "word": "おとうとさん",
        "translate": "младший брат",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "妹さん",
        "word": "いもうとさん",
        "translate": "младшая сестра",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "ご主人",
        "word": "ごしゅじん",
        "translate": "муж",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "奥さん",
        "word": "おくさん",
        "translate": "жена",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "息子さん",
        "word": "むすこさん",
        "translate": "сын",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "娘さん",
        "word": "むすめさん",
        "translate": "дочь",
        "groupName": "Названия родственников"
    },
    {
        "wordWithKanji": "赤い",
        "word": "あかい",
        "translate": "красный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "白い",
        "word": "しろい",
        "translate": "белый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "黒い",
        "word": "くろい",
        "translate": "чёрный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "茶色い",
        "word": "ちゃいろい",
        "translate": "коричневый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "黄色い",
        "word": "きいろい",
        "translate": "жёлтый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "青い",
        "word": "あおい",
        "translate": "синий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "熱い/暑い/厚い",
        "word": "あつい",
        "translate": "горячий/жаркий/толстый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "暖かい",
        "word": "あたたかい",
        "translate": "тёплый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "冷たい",
        "word": "つめたい",
        "translate": "прохладный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "寒い",
        "word": "さむい",
        "translate": "холодный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "優しい",
        "word": "やさしい",
        "translate": "добрый, лёгкий(простой)",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "厳しい",
        "word": "きびしい",
        "translate": "суровый,строгий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "面白い",
        "word": "おもしろい",
        "translate": "интересный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "つまらない",
        "word": "つまらない",
        "translate": "скучный,бесполезный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "辛い",
        "word": "からい",
        "translate": "острый(о пище)",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "甘い",
        "word": "あまい",
        "translate": "сладкий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "酸っぱい",
        "word": "すっぱい",
        "translate": "кислый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "大きい",
        "word": "おおきい",
        "translate": "большой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "小さい",
        "word": "ちいさい",
        "translate": "маленький",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "少ない",
        "word": "すくない",
        "translate": "малочисленный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "おかしい",
        "word": "おかしい",
        "translate": "смешной, странный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "すごい",
        "word": "すごい",
        "translate": "классный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "広い",
        "word": "ひろい",
        "translate": "широкий,просторный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "狭い",
        "word": "せまい",
        "translate": "маленький, тесный (про\r\nпомещение)",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "明るい",
        "word": "あかるい",
        "translate": "светлый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "遅い",
        "word": "おそい",
        "translate": "поздний, медленный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "涼しい",
        "word": "すずしい",
        "translate": "прохладный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "軽い",
        "word": "かるい",
        "translate": "теплый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "重い",
        "word": "おもい",
        "translate": "тяжелый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "古い",
        "word": "ふるい",
        "translate": "старый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "新しい",
        "word": "あたらしい",
        "translate": "новый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "安全な",
        "word": "あんぜんな",
        "translate": "безопасный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "色々な",
        "word": "いろいろな",
        "translate": "разнообразный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "簡単な",
        "word": "かんたんな",
        "translate": "простой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "急な",
        "word": "きゅうな",
        "translate": "срочный,неотложный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "嫌いな",
        "word": "きらいな",
        "translate": "нелюбимый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "綺麗な",
        "word": "きれいな",
        "translate": "красивый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "元気な",
        "word": "げんきな",
        "translate": "бодрый,здоровый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "静かな",
        "word": "しずかな",
        "translate": "тихий",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "にぎやかな",
        "word": "にぎやかな",
        "translate": "шумный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "上手な",
        "word": "じょうずな",
        "translate": "умелый,искусный",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "下手な",
        "word": "へたな",
        "translate": "неумелый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "親切な",
        "word": "しんせつな",
        "translate": "добрый",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "しんぷるな",
        "word": "シンプルな",
        "translate": "простой",
        "groupName": "Прилагательные"
    },
    {
        "wordWithKanji": "番号",
        "word": "ばんごう",
        "translate": "номер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "電話番号",
        "word": "でんわばんごう",
        "translate": "номер телефона",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "何番",
        "word": "なんばん",
        "translate": "какой номер?",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "明日",
        "word": "あした",
        "translate": "завтра",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "またね",
        "word": "またね",
        "translate": "пока!",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "またあした",
        "word": "またあした",
        "translate": "до завтра!",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "会う",
        "word": "あう",
        "translate": "встретить",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "上がる",
        "word": "あがる",
        "translate": "подниматься",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "上げる",
        "word": "あげる",
        "translate": "поднимать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "洗う",
        "word": "あらう",
        "translate": "мыть",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "行く",
        "word": "いく",
        "translate": "идти",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "動く",
        "word": "うごく",
        "translate": "двигаться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "起きる",
        "word": "おきる",
        "translate": "встать, проснуться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "教える",
        "word": "おしえる",
        "translate": "обучать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "覚える",
        "word": "おぼえる",
        "translate": "помнить, запоминать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "終わる",
        "word": "おわる",
        "translate": "закончиться, кончиться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "買う",
        "word": "かう",
        "translate": "покупать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "書く",
        "word": "かく",
        "translate": "писать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "貸す",
        "word": "かす",
        "translate": "давать в долг",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "借りる",
        "word": "かりる",
        "translate": "брать в долг",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "考える",
        "word": "かんがえる",
        "translate": "думать, размышлять",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "聞く",
        "word": "きく",
        "translate": "слушать, спрашивать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "決める",
        "word": "きめる",
        "translate": "решать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "切る",
        "word": "きる",
        "translate": "резать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "比べる",
        "word": "くらべる",
        "translate": "сравнивать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "来る",
        "word": "くる",
        "translate": "приходить",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "調べる",
        "word": "しらべる",
        "translate": "проверять, узнавать, изучать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "する",
        "word": "する",
        "translate": "делать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "食べる",
        "word": "たべる",
        "translate": "есть",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "手伝う",
        "word": "てつだう",
        "translate": "помогать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "取る",
        "word": "とる",
        "translate": "брать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "習う",
        "word": "ならう",
        "translate": "изучать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "飲む",
        "word": "のむ",
        "translate": "пить",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "寝る",
        "word": "ねる",
        "translate": "спать,лечьспать, уснуть",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "走る",
        "word": "はしる",
        "translate": "бежать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "始まる",
        "word": "はじまる",
        "translate": "начинаться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "始める",
        "word": "はじめる",
        "translate": "начинать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "話す",
        "word": "はなす",
        "translate": "говорить, разговаривать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "働く",
        "word": "はたらく",
        "translate": "работать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "もらう",
        "word": "もらう",
        "translate": "получать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "見る",
        "word": "みる",
        "translate": "смотреть",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "休む",
        "word": "やすむ",
        "translate": "отдыхать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "読む",
        "word": "よむ",
        "translate": "читать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "分かる",
        "word": "わかる",
        "translate": "понимать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "安心する",
        "word": "あんしんする",
        "translate": "успокоиться",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "悪化する",
        "word": "あっかする",
        "translate": "ухудшаться",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "研究する",
        "word": "けんきゅうする",
        "translate": "исследовать",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "散歩する",
        "word": "さんぽする",
        "translate": "гулять, прогуливаться",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "写真を撮る",
        "word": "しゃしんをとる",
        "translate": "фотографировать",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "修理する",
        "word": "しゅうりする",
        "translate": "чинить, ремонтировать",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "卒業する",
        "word": "そつぎょうする",
        "translate": "оканчивать(школу,\r\nинститут)",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "電話をかける",
        "word": "でんわをかける",
        "translate": "звонить по телефону",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "電話をする",
        "word": "でんわをする",
        "translate": "звонить по телефону",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "出る",
        "word": "でる",
        "translate": "выходить",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "ピンポンをする",
        "word": "ピンポンをする",
        "translate": "играть в пинг-понг",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "勉強する",
        "word": "べんきょうする",
        "translate": "учиться",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "放送する",
        "word": "ほうそうする",
        "translate": "вещать, транслировать",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "旅行する",
        "word": "りょこうする",
        "translate": "путешествовать",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "練習する",
        "word": "れんしゅうする",
        "translate": "повторять, тренироваться",
        "groupName": "Составные глаголы"
    },
    {
        "wordWithKanji": "教室",
        "word": "きょうしつ",
        "translate": "аудитория",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "部屋",
        "word": "へや",
        "translate": "комната",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "アパート",
        "word": "アパート",
        "translate": "квартира",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "マンション",
        "word": "マンション",
        "translate": "многоквартирный дом",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "机",
        "word": "つくえ",
        "translate": "стол",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "椅子",
        "word": "いす",
        "translate": "стул",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "エアコン",
        "word": "エアコン",
        "translate": "кондиционер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "図書館",
        "word": "としょかん",
        "translate": "библиотека",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "博物館",
        "word": "はくぶつかん",
        "translate": "музей",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "美術館",
        "word": "びじゅつかん",
        "translate": "музей искусств, художественный музей",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "郵便局",
        "word": "ゆうびんきょく",
        "translate": "почтовое отделение",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "病院",
        "word": "びょういん",
        "translate": "больница",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "美容院",
        "word": "びよういん",
        "translate": "салон красоты",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "公園",
        "word": "こうえん",
        "translate": "парк",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "動物園",
        "word": "どうぶつえん",
        "translate": "зоопарк",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "麒麟",
        "word": "キリン",
        "translate": "жираф",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "象",
        "word": "ぞう",
        "translate": "слон",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "猿",
        "word": "さる",
        "translate": "обезьяна",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "会社",
        "word": "かいしゃ",
        "translate": "фирма",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "学校",
        "word": "がっこう",
        "translate": "школа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "大学",
        "word": "だいがく",
        "translate": "университет",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "試験",
        "word": "しけん",
        "translate": "экзамен",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テスト",
        "word": "テスト",
        "translate": "тест",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "問題",
        "word": "もんだい",
        "translate": "задание",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "宿題",
        "word": "しゅくだい",
        "translate": "домашнее задание",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "パーティー",
        "word": "パーティー",
        "translate": "вечеринка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "映画",
        "word": "えいが",
        "translate": "фильм, кино",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "映画館",
        "word": "えいがかん",
        "translate": "кинотеатр",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "手紙",
        "word": "てがみ",
        "translate": "письмо",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "授業",
        "word": "じゅぎょう",
        "translate": "занятия",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "食堂",
        "word": "しょくどう",
        "translate": "столовая",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "朝ご飯",
        "word": "あさごはん",
        "translate": "завтрак",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "昼ごはん",
        "word": "ひるごはん",
        "translate": "обед",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "晩ごはん",
        "word": "ばんごはん",
        "translate": "ужин",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "スポーツをする",
        "word": "スポーツをする",
        "translate": "заниматься спортом",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テニスをする",
        "word": "テニスをする",
        "translate": "играть в теннис",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ゲームをする",
        "word": "ゲームをする",
        "translate": "играть в игры",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "蜂蜜",
        "word": "はちみつ",
        "translate": "мёд",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "木",
        "word": "き",
        "translate": "дерево",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "白樺",
        "word": "しらかば",
        "translate": "берёза",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "松",
        "word": "まつ",
        "translate": "сосна",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ポプラ",
        "word": "ポプラ",
        "translate": "тополь",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "どこ",
        "word": "どこ",
        "translate": "где",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "どう",
        "word": "どう",
        "translate": "как",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "いつ",
        "word": "いつ",
        "translate": "когда",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "いくつ",
        "word": "いくつ",
        "translate": "сколько",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "いくら",
        "word": "いくら",
        "translate": "сколько стоит",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "コーヒー",
        "word": "コーヒー",
        "translate": "кофе",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "紅茶",
        "word": "こうちゃ",
        "translate": "черный чай",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "お茶",
        "word": "おちゃ",
        "translate": "зеленый чай",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "日本茶",
        "word": "にほんちゃ",
        "translate": "японский (зеленый)\r\nчай",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "天気",
        "word": "てんき",
        "translate": "погода",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "仕事",
        "word": "しごと",
        "translate": "работа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "赤の広場",
        "word": "あかのひろば",
        "translate": "Красная площадь",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "エッフェル塔",
        "word": "エッフェル とう",
        "translate": "Эйфелева башня",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "パリ",
        "word": "パリ",
        "translate": "Париж",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "マクドナルド",
        "word": "マクドナルド",
        "translate": "Макдональдс",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "スターバックス",
        "word": "スターバックス",
        "translate": "Старбакс",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "カフェ",
        "word": "カフェ",
        "translate": "кафе",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "喫茶店",
        "word": "きっさてん",
        "translate": "кафе",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "～の上に",
        "word": "～のうえに",
        "translate": "сверху",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の下に",
        "word": "～のしたに",
        "translate": "снизу",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の前に",
        "word": "～のまえに",
        "translate": "перед",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の後に",
        "word": "～のうしろに",
        "translate": "позади",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の中に",
        "word": "～のなかに",
        "translate": "внутри",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の側に",
        "word": "～のそばに",
        "translate": "возле,рядом,сбоку",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の外に",
        "word": "～のそとに",
        "translate": "снаружи",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の間に",
        "word": "～のあいだに",
        "translate": "между",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "～の隣に",
        "word": "～のとなりに",
        "translate": "рядом",
        "groupName": "Пространственные послелоги места"
    },
    {
        "wordWithKanji": "出来る",
        "word": "できる",
        "translate": "мочь, уметь",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "分かる",
        "word": "わかる",
        "translate": "понимать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "飛ぶ",
        "word": "とぶ",
        "translate": "летать, прыгать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "働く",
        "word": "はたらく",
        "translate": "работать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "休む",
        "word": "やすむ",
        "translate": "отдыхать\r\n(+пропускать)",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "壊す",
        "word": "こわす",
        "translate": "ломать",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "壊れる",
        "word": "こわれる",
        "translate": "ломаться",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "受ける",
        "word": "うける",
        "translate": "получать \\ сдавать экзамен",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "繰り返す",
        "word": "くりかえす",
        "translate": "повторять",
        "groupName": "Глаголы"
    },
    {
        "wordWithKanji": "鶴",
        "word": "つる",
        "translate": "журавль",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "大雨",
        "word": "おおあめ",
        "translate": "ливень",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "湖",
        "word": "みずうみ",
        "translate": "озеро",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "橋",
        "word": "はし",
        "translate": "мост",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "お箸",
        "word": "おはし",
        "translate": "палочкидля еды",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "コーヒー",
        "word": "コーヒー",
        "translate": "кофе",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "喫茶店",
        "word": "きっさてん",
        "translate": "кафе",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "駅",
        "word": "えき",
        "translate": "станция",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "お寺",
        "word": "おてら",
        "translate": "храм",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "スタジアム",
        "word": "スタジアム",
        "translate": "стадион",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "図書館",
        "word": "としょかん",
        "translate": "библиотека",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "本屋",
        "word": "ほんや",
        "translate": "книжный магазин",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "売り場",
        "word": "うりば",
        "translate": "отдел (в магазине)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "新聞",
        "word": "しんぶん",
        "translate": "газета",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "雑誌",
        "word": "ざっし",
        "translate": "журнал",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "本",
        "word": "ほん",
        "translate": "книга",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "手帳",
        "word": "てちょう",
        "translate": "блокнот",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ノート",
        "word": "ノート",
        "translate": "тетрадь",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "切符",
        "word": "きっぷ",
        "translate": "билет",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "プレゼント",
        "word": "プレゼント",
        "translate": "подарок",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "読書",
        "word": "どくしょ",
        "translate": "чтение",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "話",
        "word": "はなし",
        "translate": "разговор",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ニュース",
        "word": "ニュース",
        "translate": "новости",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "仕事",
        "word": "しごと",
        "translate": "работа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "お仕事",
        "word": "おしごと",
        "translate": "Ваша работа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "会話",
        "word": "かいわ",
        "translate": "диалог",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "質問",
        "word": "しつもん",
        "translate": "вопрос",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テスト",
        "word": "テスト",
        "translate": "тест",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "試験",
        "word": "しけん",
        "translate": "экзамен",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "よく",
        "word": "よく",
        "translate": "часто",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "時々",
        "word": "ときどき",
        "translate": "иногда",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "いつも",
        "word": "いつも",
        "translate": "всегда",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "あまり",
        "word": "あまり",
        "translate": "неочень, почтине",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "全然",
        "word": "ぜんぜん",
        "translate": "совсемне",
        "groupName": "Наречия"
    },
    {
        "wordWithKanji": "蟻",
        "word": "あり",
        "translate": "муравей",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "エジプト",
        "word": "エジプト",
        "translate": "Египет",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "エジプトのピラミッド",
        "word": "エジプトのピラミッド",
        "translate": "Египетские пирамиды",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "砂漠",
        "word": "さばく",
        "translate": "пустыня",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "砂",
        "word": "すな",
        "translate": "песок",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "棘",
        "word": "とげ",
        "translate": "шип, колючка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "駱駝",
        "word": "らくだ",
        "translate": "верблюд",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "蠍",
        "word": "さそり",
        "translate": "скорпион",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "水族館",
        "word": "すいぞくかん",
        "translate": "океанариум",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "海",
        "word": "うみ",
        "translate": "море",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "サボテン",
        "word": "サボテン",
        "translate": "кактус",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "草",
        "word": "くさ",
        "translate": "трава",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "空港",
        "word": "くうこう",
        "translate": "аэропорт",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "飛行機",
        "word": "ひこうき",
        "translate": "самолёт",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "バス",
        "word": "バス",
        "translate": "автобус",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "バス乗り場",
        "word": "バスのりば",
        "translate": "автобусная остановка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "駅",
        "word": "えき",
        "translate": "станция",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "電車",
        "word": "でんしゃ",
        "translate": "поезд",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "新幹線",
        "word": "しんかんせん",
        "translate": "синкансэн",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "地下鉄",
        "word": "ちかてつ",
        "translate": "метро",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "キロ（メートル）",
        "word": "キロ（メートル）",
        "translate": "километр",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "キロ（グラム）",
        "word": "キロ（グラム）",
        "translate": "килограмм",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "返事",
        "word": "へんじ",
        "translate": "ответ",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "結婚",
        "word": "けっこん",
        "translate": "свадьба (+する =\r\nжениться/выходить\r\nзамуж)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "離婚",
        "word": "りこん",
        "translate": "развод (+する =разводиться)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "南極",
        "word": "なんきょく",
        "translate": "Южный полюс",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "北極",
        "word": "ほっきょく",
        "translate": "Северный полюс",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "雪",
        "word": "ゆき",
        "translate": "снег",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "雪山",
        "word": "ゆきやま",
        "translate": "снежные горы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "雪だるま",
        "word": "ゆきだるま",
        "translate": "снеговик",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "氷",
        "word": "こおり",
        "translate": "лёд",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "マンモス",
        "word": "マンモス",
        "translate": "мамонт",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "風",
        "word": "かぜ",
        "translate": "ветер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "デパート",
        "word": "デパート",
        "translate": "универмаг",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "銀行",
        "word": "ぎんこう",
        "translate": "банк",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "わさび",
        "word": "わさび",
        "translate": "васаби",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "お肉",
        "word": "（お）にく",
        "translate": "мясо",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "お魚",
        "word": "（お）さかな",
        "translate": "рыба",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "刺身",
        "word": "さしみ",
        "translate": "сасими (сашими)",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "竹輪",
        "word": "ちくわ",
        "translate": "рыбные палочки",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ナイフ",
        "word": "ナイフ",
        "translate": "нож",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "フォーク",
        "word": "フォーク",
        "translate": "вилка",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "スプーン",
        "word": "スプーン",
        "translate": "ложка",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "トースト",
        "word": "トースト",
        "translate": "тост",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "バター",
        "word": "バター",
        "translate": "масло",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ジュース",
        "word": "ジュース",
        "translate": "сок",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "オレンジジュース",
        "word": "オレンジジュース",
        "translate": "апельсиновый сок",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "紅茶",
        "word": "こうちゃ",
        "translate": "чёрный чай",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "パン",
        "word": "パン",
        "translate": "хлеб",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "ケーキ",
        "word": "ケーキ",
        "translate": "пирожное",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "卵",
        "word": "たまご",
        "translate": "яйцо",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "野菜",
        "word": "やさい",
        "translate": "овощи",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "果物",
        "word": "くだもの",
        "translate": "фрукты",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "人参",
        "word": "にんじん",
        "translate": "морковь",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "キャベツ",
        "word": "キャベツ",
        "translate": "капуста",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "トマト",
        "word": "トマト",
        "translate": "помидор",
        "groupName": "Существительные: еда и напитки"
    },
    {
        "wordWithKanji": "れい、ゼロ",
        "word": "れい、ゼロ",
        "translate": "ноль",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "一つ",
        "word": "ひとつ",
        "translate": "один",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "二つ",
        "word": "ふたつ",
        "translate": "два",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "三つ",
        "word": "みっつ",
        "translate": "три",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "四つ",
        "word": "よっつ",
        "translate": "четыре",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "五つ",
        "word": "いつつ",
        "translate": "пять",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "六つ",
        "word": "むっつ",
        "translate": "шесть",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "七つ",
        "word": "ななつ",
        "translate": "семь",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "八つ",
        "word": "やっつ",
        "translate": "восемь",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "九つ",
        "word": "ここのつ",
        "translate": "девять",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "十",
        "word": "とお",
        "translate": "десять",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "いくつ",
        "word": "いくつ",
        "translate": "сколько",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "いくら",
        "word": "いくら",
        "translate": "сколько стоит",
        "groupName": "Японские числительные для предметов"
    },
    {
        "wordWithKanji": "お寺",
        "word": "おてら",
        "translate": "буддийский храм",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "神社",
        "word": "じんじゃ",
        "translate": "синтоистский храм",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "庭",
        "word": "にわ",
        "translate": "двор, сад",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "部屋",
        "word": "へや",
        "translate": "комната",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "教室",
        "word": "きょうしつ",
        "translate": "аудитория",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "天井",
        "word": "てんじょう",
        "translate": "потолок",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "壁",
        "word": "かべ",
        "translate": "стена",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テーブル",
        "word": "テーブル",
        "translate": "стол (европейский)",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "机",
        "word": "つくえ",
        "translate": "стол",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "椅子",
        "word": "いす",
        "translate": "стул",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "コンピューター",
        "word": "コンピューター",
        "translate": "компьютер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "テレビ",
        "word": "テレビ",
        "translate": "телевизор",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "手",
        "word": "て",
        "translate": "рука",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "足",
        "word": "あし",
        "translate": "нога",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "頭",
        "word": "あたま",
        "translate": "голова",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "耳",
        "word": "みみ",
        "translate": "ухо",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "口",
        "word": "くち",
        "translate": "рот",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "鼻",
        "word": "はな",
        "translate": "нос",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "目",
        "word": "め",
        "translate": "глаз",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "首",
        "word": "くび",
        "translate": "шея",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "背",
        "word": "せ",
        "translate": "спина,рост",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "髪",
        "word": "かみ",
        "translate": "волосы",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "象",
        "word": "ぞう",
        "translate": "слон",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "猫",
        "word": "ねこ",
        "translate": "кошка",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "犬",
        "word": "いぬ",
        "translate": "собака",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "キリン",
        "word": "キリン",
        "translate": "жираф",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "猿",
        "word": "さる",
        "translate": "обезьяна",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "クジラ",
        "word": "クジラ",
        "translate": "кит",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "自然",
        "word": "しぜん",
        "translate": "природа",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "性格",
        "word": "せいかく",
        "translate": "характер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "人口",
        "word": "じんこう",
        "translate": "население",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "物価",
        "word": "ぶっか",
        "translate": "цена",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "値段",
        "word": "ねだん",
        "translate": "цена, стоимость",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "食べ物",
        "word": "たべもの",
        "translate": "еда, пища",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "飲物",
        "word": "のみもの",
        "translate": "напитки",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "アイスクリーム",
        "word": "アイスクリーム",
        "translate": "мороженое",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ハンバーガー",
        "word": "ハンバーガー",
        "translate": "гамбургер",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "桃",
        "word": "もも",
        "translate": "персик",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "みかん",
        "word": "みかん",
        "translate": "мандарин",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "オレンジ",
        "word": "オレンジ",
        "translate": "апельсин",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "梨",
        "word": "なし",
        "translate": "груша",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "りんご",
        "word": "りんご",
        "translate": "яблоко",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "すいか",
        "word": "すいか",
        "translate": "арбуз",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "きゅうり",
        "word": "きゅうり",
        "translate": "огурец",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "たまねぎ",
        "word": "たまねぎ",
        "translate": "репчатый лук",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "ピーマン",
        "word": "ピーマン",
        "translate": "перец",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "サラダ",
        "word": "サラダ",
        "translate": "салат",
        "groupName": "Существительные"
    },
    {
        "wordWithKanji": "一月",
        "word": "いちがつ",
        "translate": "январь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "二月",
        "word": "にがつ",
        "translate": "февраль",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "三月",
        "word": "さんがつ",
        "translate": "март",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "四月",
        "word": "しがつ",
        "translate": "апрель",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "五月",
        "word": "ごがつ",
        "translate": "май",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "六月",
        "word": "ろくがつ",
        "translate": "июнь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "七月",
        "word": "しちがつ",
        "translate": "июль",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "八月",
        "word": "はちがつ",
        "translate": "август",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "九月",
        "word": "くがつ",
        "translate": "сентябрь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "十月",
        "word": "じゅうがつ",
        "translate": "октябрь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "十一月",
        "word": "じゅういちがつ",
        "translate": "ноябрь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "十二月",
        "word": "じゅうにがつ",
        "translate": "декабрь",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "何月",
        "word": "なんがつ",
        "translate": "какой, который месяц?",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "今は何月ですか。",
        "word": "いまはなんがつですか。",
        "translate": "Какой сейчас месяц?",
        "groupName": "Название месяцев"
    },
    {
        "wordWithKanji": "一日",
        "word": "ついたち",
        "translate": "1-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二日",
        "word": "ふつか",
        "translate": "2-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "三日",
        "word": "みっか",
        "translate": "3-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "四日",
        "word": "よっか",
        "translate": "4-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "五日",
        "word": "いつか",
        "translate": "5-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "六日",
        "word": "むいか",
        "translate": "6-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "七日",
        "word": "なのか",
        "translate": "7-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "八日",
        "word": "ようか",
        "translate": "8-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "九日",
        "word": "ここのか",
        "translate": "9-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十日",
        "word": "とおか",
        "translate": "10-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十一日",
        "word": "じゅういちにち",
        "translate": "11-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十二日",
        "word": "じゅうににち",
        "translate": "12-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十三日",
        "word": "じゅうさんにち",
        "translate": "13-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十四日",
        "word": "じゅうよっか",
        "translate": "14-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十五日",
        "word": "じゅうごにち",
        "translate": "15-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十六日",
        "word": "じゅうろくにち",
        "translate": "16-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十七日",
        "word": "じゅうしちにち\r\nじゅうななにち",
        "translate": "17-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十八日",
        "word": "じゅうはちにち",
        "translate": "18-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "十九日",
        "word": "じゅうくにち",
        "translate": "19-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十日",
        "word": "はつか",
        "translate": "20-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十一日",
        "word": "にじゅういちにち",
        "translate": "21-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十二日",
        "word": "にじゅうににち",
        "translate": "22-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十三日",
        "word": "にじゅうさんにち",
        "translate": "23-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十四日",
        "word": "にじゅうよっか",
        "translate": "24-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十五日",
        "word": "にじゅうごにち",
        "translate": "25-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十六日",
        "word": "にじゅうろくにち",
        "translate": "26-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十七日",
        "word": "にじゅうしちにち\r\nにじゅうななにち",
        "translate": "27-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十八日",
        "word": "にじゅうはちにち",
        "translate": "28-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "二十九日",
        "word": "にじゅうくにち",
        "translate": "29-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "三十日",
        "word": "さんじゅうにち",
        "translate": "30-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "三十一日",
        "word": "さんじゅういちにち",
        "translate": "31-ечисло",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "何日",
        "word": "なんにち",
        "translate": "какое число?",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "今日は何日ですか。",
        "word": "きょうはなんにちですか。",
        "translate": "Которое сегодня число?",
        "groupName": "Числа месяца"
    },
    {
        "wordWithKanji": "時",
        "word": "じ",
        "translate": "час",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "半",
        "word": "はん",
        "translate": "половина, 30 минут",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "分",
        "word": "ぷん",
        "translate": "минута",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "何時",
        "word": "なんじ",
        "translate": "сколько часов?",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "何分",
        "word": "なんぷん",
        "translate": "сколько минут?",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "午前",
        "word": "ごぜん",
        "translate": "утро, первая половина дня(до 12 часов)",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "午後",
        "word": "ごご",
        "translate": "вторая половина дня (после 12 часов)",
        "groupName": "Время"
    },
    {
        "wordWithKanji": "～の近くに",
        "word": "～のちかくに",
        "translate": "рядом,поблизости",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の側に",
        "word": "～のそばに",
        "translate": "рядом, сбоку",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の上に",
        "word": "～のうえに",
        "translate": "сверху",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の下に",
        "word": "～のしたに",
        "translate": "снизу, под",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の前に",
        "word": "～のまえに",
        "translate": "перед,впереди",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の後ろに",
        "word": "～のうしろに",
        "translate": "сзади, позади",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の間に",
        "word": "～のあいだに",
        "translate": "между",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の真ん中に",
        "word": "～のまんなかに",
        "translate": "вцентре,посередине",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の右に",
        "word": "～のみぎに",
        "translate": "справа",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "～の左に",
        "word": "～のひだりに",
        "translate": "слева",
        "groupName": "Послелоги места"
    },
    {
        "wordWithKanji": "動物",
        "word": "どうぶつ",
        "translate": "животное",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "犬",
        "word": "いぬ",
        "translate": "собака",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "猫",
        "word": "ねこ",
        "translate": "кошка",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "鼠",
        "word": "ネズミ",
        "translate": "мышь",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "針鼠",
        "word": "ハリネズミ",
        "translate": "ёж",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "狐",
        "word": "きつね",
        "translate": "лиса",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "狼",
        "word": "おおかみ",
        "translate": "волк",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "熊",
        "word": "くま",
        "translate": "медведь",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "馬",
        "word": "うま",
        "translate": "лошадь",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "牛",
        "word": "うし",
        "translate": "корова",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "豚",
        "word": "ぶた",
        "translate": "свинья",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "羊",
        "word": "ひつじ",
        "translate": "овца",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "兎",
        "word": "うさぎ",
        "translate": "заяц",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "鳥",
        "word": "とり",
        "translate": "птица",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "鶏",
        "word": "にわとり",
        "translate": "курица",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "家鴨",
        "word": "あひる",
        "translate": "домашняя утка",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "虎",
        "word": "とら",
        "translate": "тигр",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "ライオン",
        "word": "ライオン",
        "translate": "лев",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "豹",
        "word": "ひょう",
        "translate": "леопард",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "河馬",
        "word": "かば",
        "translate": "бегемот",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "縞馬",
        "word": "しまうま",
        "translate": "зебра",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "麒麟",
        "word": "きりん",
        "translate": "жираф",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "サイ",
        "word": "さい",
        "translate": "носорог",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "鰐",
        "word": "わに",
        "translate": "крокодил",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "動物園",
        "word": "どうぶつえん",
        "translate": "зоопарк",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "公園",
        "word": "こうえん",
        "translate": "парк",
        "groupName": "Названия животных"
    },
    {
        "wordWithKanji": "行く",
        "word": "いく",
        "translate": "идти",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "来る",
        "word": "くる",
        "translate": "приходить",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "帰る",
        "word": "かえる",
        "translate": "возвращаться домой",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "戻る",
        "word": "もどる",
        "translate": "возвращаться",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "乗る",
        "word": "のる",
        "translate": "ехать,садиться на транспорт",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "登る",
        "word": "のぼる",
        "translate": "взбираться",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "会う",
        "word": "あう",
        "translate": "встречаться",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "疲れる",
        "word": "つかれる",
        "translate": "устать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "忘れる",
        "word": "わすれる",
        "translate": "забывать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "仕事",
        "word": "しごと",
        "translate": "работа",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "仕事（を）する",
        "word": "しごと（を）する",
        "translate": "работать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "質問",
        "word": "しつもん",
        "translate": "вопрос",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "質問（を）する",
        "word": "しつもん（を）する",
        "translate": "спрашивать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "勉強",
        "word": "べんひょう",
        "translate": "учеба,занятие",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "勉強（を）する",
        "word": "べんきょう（を）する",
        "translate": "учиться",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "買い物",
        "word": "かいもの",
        "translate": "покупки",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "買い物（を）する",
        "word": "かいもの（を）する",
        "translate": "делатьпокупки",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "食事",
        "word": "しょくじ",
        "translate": "еда,пища",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "食事（ を）する",
        "word": "しょくじ（を）する",
        "translate": "есть,принимать пищу",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "散歩",
        "word": "さんぽ",
        "translate": "прогулка",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "散歩（を）する",
        "word": "さんぽ（を）する",
        "translate": "гулять,прогуливаться",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "遅刻",
        "word": "ちこく",
        "translate": "опоздание",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "遅刻（を）する",
        "word": "ちこく（を）する",
        "translate": "опаздывать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "旅行",
        "word": "りょこう",
        "translate": "путешествие",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "旅行（を）する",
        "word": "りょこう（を）する",
        "translate": "путешествовать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "旅行に行く",
        "word": "りょこうにいく",
        "translate": "отправиться в путешествие",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "出張",
        "word": "しゅっちょう",
        "translate": "командировка",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "出張に行く",
        "word": "しゅっちょうにいく",
        "translate": "поехать в командировку",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "写真",
        "word": "しゃしん",
        "translate": "фотография",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "写真を撮る",
        "word": "しゃしんをとる",
        "translate": "фотографировать",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "チケット",
        "word": "チケット",
        "translate": "билет",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "友達",
        "word": "ともだち",
        "translate": "друг",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "図書館",
        "word": "としょかん",
        "translate": "библиотека",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "デパート",
        "word": "デパート",
        "translate": "магазин,универмаг",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "コンビニ",
        "word": "コンビニ",
        "translate": "круглосуточный магазин",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "モール",
        "word": "モール",
        "translate": "молл,магазин",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "郵便局",
        "word": "ゆうびんきょく",
        "translate": "почта",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "食堂",
        "word": "しょくどう",
        "translate": "столовая",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "美容室",
        "word": "びようしつ",
        "translate": "салон красоты",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "美容院",
        "word": "びよういん",
        "translate": "салон красоты",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "病院",
        "word": "びょういん",
        "translate": "больница",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "会う",
        "word": "あう",
        "translate": "встретить,встречаться",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "書く",
        "word": "かく",
        "translate": "писать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "行く",
        "word": "いく",
        "translate": "идти",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "話す",
        "word": "はなす",
        "translate": "разговаривать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "立つ",
        "word": "たつ",
        "translate": "вставать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "死ぬ",
        "word": "しぬ",
        "translate": "умирать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "読む",
        "word": "よむ",
        "translate": "читать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "運ぶ",
        "word": "はこぶ",
        "translate": "носить,переносить\r\n(предметы)",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "入る",
        "word": "はいる",
        "translate": "входить",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "食べる",
        "word": "たべる",
        "translate": "есть",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "見る",
        "word": "みる",
        "translate": "смотреть",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "開ける",
        "word": "あける",
        "translate": "открывать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "来る",
        "word": "くる",
        "translate": "приходить",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "する",
        "word": "する",
        "translate": "делать",
        "groupName": "Глаголы ( 16 раздел )"
    },
    {
        "wordWithKanji": "ヒーロー",
        "word": "ヒーロー",
        "translate": "герой",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "主人公",
        "word": "しゅじんこう",
        "translate": "герой(произведения)",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "始めに",
        "word": "はじめに",
        "translate": "сначала",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "最初に",
        "word": "さいしょに",
        "translate": "сначала,вначале",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "初めに",
        "word": "はじめに",
        "translate": "сначала,вначале",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "それから",
        "word": "それから",
        "translate": "затем,послеэтого",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "そして",
        "word": "そして",
        "translate": "и,затем",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "しかし",
        "word": "しかし",
        "translate": "но,однако",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "普通",
        "word": "ふつう",
        "translate": "обычно",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "たいてい",
        "word": "たいてい",
        "translate": "побольшейчасти",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "だいたい",
        "word": "だいたい",
        "translate": "приблизительно",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "一杯",
        "word": "いっぱい",
        "translate": "1. одинстакан; 2. весь,полный,  полностью",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "ご飯",
        "word": "ごはん",
        "translate": "еда,пища,рис",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "骨",
        "word": "ほね",
        "translate": "кость",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "星",
        "word": "ほし",
        "translate": "звезда",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "幸せ",
        "word": "しあわせ",
        "translate": "счастье,удача",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "不幸",
        "word": "ふこう",
        "translate": "несчастье,бедствие",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "よかった（です）",
        "word": "よかった（です）",
        "translate": "Здорово!Отлично!",
        "groupName": "Другая лексика"
    },
    {
        "wordWithKanji": "集まる",
        "word": "あつまる",
        "translate": "собирать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "教える",
        "word": "おしえる",
        "translate": "обучать,объяснять,\r\nпоказывать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "助ける",
        "word": "たすける",
        "translate": "спасать,выручать,помогать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "立つ",
        "word": "たつ",
        "translate": "стоять",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "座る",
        "word": "すわる",
        "translate": "сидеть",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "居る",
        "word": "いる",
        "translate": "быть,находиться(одуш.)",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "入る",
        "word": "はいる",
        "translate": "входить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "乗る",
        "word": "のる",
        "translate": "садиться,ехать на транспорте",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "地下鉄に乗る",
        "word": "ちかてつにのる",
        "translate": "ехать на метро",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "バスに乗る",
        "word": "バスにのる",
        "translate": "ехать на автобусе",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "出る",
        "word": "でる",
        "translate": "выходить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "降りる",
        "word": "おりる",
        "translate": "спускаться,выходить из транспорта",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "家を出る",
        "word": "いえをでる",
        "translate": "выходить из дома",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "外へ出る",
        "word": "そとへでる",
        "translate": "выходить на улицу",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "地下鉄を出る",
        "word": "ちかてつをでる",
        "translate": "выходить из метро",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "バスを降りる",
        "word": "バスをおりる",
        "translate": "выходить из автобуса",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "病気",
        "word": "びょうき",
        "translate": "болезнь",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "病気になる",
        "word": "びょうきになる",
        "translate": "заболеть",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "治る",
        "word": "なおる",
        "translate": "выздоравливать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "病気から治る",
        "word": "びょうきからなおる",
        "translate": "выздороветь от болезни,\r\nпоправиться",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "疲れ",
        "word": "つかれ",
        "translate": "усталость",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "疲れる",
        "word": "つかれる",
        "translate": "уставать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "休み",
        "word": "やすみ",
        "translate": "отдых",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "休む",
        "word": "やすむ",
        "translate": "отдыхать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "壊す",
        "word": "こわす",
        "translate": "разрушать,ломать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "直す",
        "word": "なおす",
        "translate": "чинить,исправлять",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "心配",
        "word": "しんぱい",
        "translate": "волнение,беспокойство",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "心配（を）する",
        "word": "しんぱい（を）する",
        "translate": "переживать,беспокоиться",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "安心",
        "word": "あんしん",
        "translate": "спокойствие,успокоение",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "安心（を）する",
        "word": "あんしん（を）する",
        "translate": "успокоиться",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "持ってくる",
        "word": "もってくる",
        "translate": "приносить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "持っていく",
        "word": "もっていく",
        "translate": "забирать,уносить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "呼ぶ",
        "word": "よぶ",
        "translate": "звать,вызывать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "起きる",
        "word": "おきる",
        "translate": "просыпаться,вставать",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "顔を洗う",
        "word": "かおをあらう",
        "translate": "умываться",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "ニュースを聞く",
        "word": "ニュースをきく",
        "translate": "слушать новости",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "買い物をする",
        "word": "かいものをする",
        "translate": "делать покупки",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "電話をする",
        "word": "でんわをする",
        "translate": "звонить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "エアコンを付ける",
        "word": "エアコンをつける",
        "translate": "включать кондиционер",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "エアコンを消す",
        "word": "エアコンをけす",
        "translate": "выключать кондиционер",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "開ける",
        "word": "あける",
        "translate": "открыть",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "閉める",
        "word": "しめる",
        "translate": "закрыть",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "急ぐ",
        "word": "いそぐ",
        "translate": "спешить",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "住所",
        "word": "じゅうしょ",
        "translate": "адрес",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "電話番号",
        "word": "でんわばんごう",
        "translate": "номертелефона",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "何も",
        "word": "なにも",
        "translate": "ничего (сотрицанием)",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "どこも",
        "word": "どこも",
        "translate": "везде\r\nнигде(сотрицанием)",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "どこへも",
        "word": "どこへも",
        "translate": "никуда(сотрицанием)",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "どれぐらい",
        "word": "どれぐらい",
        "translate": "сколько примерно?",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "薬",
        "word": "くすり",
        "translate": "лекарство",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "早く",
        "word": "はやく",
        "translate": "пораньше,скорее",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "すぐ",
        "word": "すぐ",
        "translate": "сразу",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "食前",
        "word": "しょくぜん",
        "translate": "передедой",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "食後",
        "word": "しょくご",
        "translate": "послееды",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "大声で",
        "word": "おおごえで",
        "translate": "громким голосом",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "静かに",
        "word": "しずかに",
        "translate": "тихо",
        "groupName": "Словарь 17 раздел"
    },
    {
        "wordWithKanji": "ささやき声で",
        "word": "ささやきごえで",
        "translate": "шепотом",
        "groupName": "Словарь 17 раздел"
    }
],
    filteredItems: [],
    search: '',
    activePage: 'mnemoticCardsPage',
    selectThemeOverrides: {
        barColor: '#C08916'
      }
   }
  },
  created() {
    console.log(JSON.parse(localStorage.getItem("wordList")), 'words list')
    this.wordList = JSON.parse(localStorage.getItem("wordList")) || this.wordList;
    this.filteredItems = JSON.parse(localStorage.getItem("wordList")) || this.wordList;
  },

  mounted() {
    document.querySelector('input').addEventListener('change', (event) => {
            var reader = new FileReader();
            reader.onload = (event) => {
                var arrayBuffer = event.target.result,
                    array = new Uint8Array(arrayBuffer),
                    binaryString = String.fromCharCode.apply(null, array);

                var workbook = XLSX.read(binaryString, {
                    type: "binary"
                });

                var first_sheet_name = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[first_sheet_name];
                const data = XLSX.utils.sheet_to_json(worksheet, { raw: true });
                console.log(data, 'Import data')
                this.wordList = data.map(item => {
                  return {
                    wordWithKanji: item.kanji ,
                    word: item.kana ,
                    translate: item.translate ,
                    groupName: item.group 
                  }
                });
                this.filteredItems = this.wordList;
                localStorage.setItem("wordList", JSON.stringify(this.wordList));
            }
            reader.readAsArrayBuffer(event.target.files[0]);
        });

  },

  methods: {
    onChangeSearch (val) {
      const value = val.target.value.toLowerCase();
      this.filteredItems = this.wordList.filter(item => item.wordWithKanji.includes(value) || item.word.includes(value) || item.translate.toLowerCase().includes(value) || item.groupName.toLowerCase().includes(value));
    }
  }
}

</script>

<template>
    <div>
      <n-tabs default-value="Cards" justify-content="center" type="line" animated tab-style="color: #C08916" :theme-overrides="selectThemeOverrides">
        <n-tab-pane name="Cards" tab="Карточки">
          <div style="display: flex; justify-content: flex-end;">
            <label class="custom-file-upload">
              <span>Импорт набора слов (xlsx)</span>
              <input id="file" type="file" accept=".xlsx" />
            </label>
          </div>
          <div style="display: flex; justify-content: center;">
            <div class="form__group field">
              <input type="input" class="form__field" placeholder="Name" name="name" id='name' required v-model="search" v-on:change="onChangeSearch" autocomplete="off" />
              <label for="name" class="form__label">Поиск</label>
            </div>
          </div>
          <div class="wrapper">
            <MnemCard v-bind:key="wordItem.translate + key" v-for="wordItem, key in filteredItems" :wordWithKanji="wordItem.wordWithKanji" :word="wordItem.word" :translate="wordItem.translate" :groupName="wordItem.groupName" />
          </div>
        </n-tab-pane>
        <n-tab-pane name="Exam" tab="Тестирование" style="height: 100%;">
          <Exam :wordList="wordList" />
        </n-tab-pane>
        <n-tab-pane name="FAQ" tab="FAQ" style="height: 100%;">
          <FAQComponent :wordList="wordList" />
        </n-tab-pane>
      </n-tabs>

    </div>
</template>

<style scss scoped>
.custom-file-upload {
  border-radius: 5px;
  display: inline-block;
  cursor: pointer;
  background-color: #ffcb5d;
  font-family: "Tsunagi Gothic Black";
  margin-right: 10px;
}

.custom-file-upload:hover {
  background-color: rgb(192, 137, 22);
}
input[type="file"] {
    display: none;
}
.form__group {
  position: relative;
  padding: 15px 0 0;
  margin-top: 10px;
  width: 50%;
}

.form__field {
  font-family: "Tsunagi Gothic Black";
  width: 100%;
  border: 0;
  border-bottom: 2px solid #FFE4AC;
  outline: 0;
  font-size: 1.3rem;
  color: #FFE4AC;
  padding: 7px 0;
  background: transparent;
  transition: border-color 0.2s;

  &::placeholder {
    color: transparent;
  }

  &:placeholder-shown ~ .form__label {
    font-size: 1.3rem;
    cursor: text;
    top: 20px;
  }
}

.form__label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 1rem;
  color: #FFE4AC;
}

.form__field:focus {
  ~ .form__label {
    position: absolute;
    top: 0;
    display: block;
    transition: 0.2s;
    font-size: 1rem;
    color: #FFD680;
    font-weight:700;    
  }
  padding-bottom: 6px;  
  font-weight: 700;
  border-width: 3px;
  border-image: linear-gradient(to right, #FFD680,#FFD680);
  color: #C08916;
  border-image-slice: 1;
}
.form__field{
  &:required,&:invalid { box-shadow:none; }
}















nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@font-face {
    font-family: "Tsunagi Gothic Black";
    src: url("../src/assets/TsunagiGothic.ttf") format("truetype");
    font-style: normal; 
    font-weight: normal;
  }

.wrapper {
    display: grid;
    width: 100%;
    padding: 2rem;
    gap: 10px;
  }

@media (min-width: 300px) {
  .wrapper {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 10px;
    width: 100%;
    padding: 2rem;
  }

  .custom-file-upload {
        padding: 6px 8px;
        font-size: 14px;
   }

   .form__group {
    width: 75%;
   }
}

@media (min-width: 1281px) {
  .wrapper {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    width: 100%;
    padding: 2rem;
  }
  .custom-file-upload {
        padding: 10px 14px;
   }
}
</style>
