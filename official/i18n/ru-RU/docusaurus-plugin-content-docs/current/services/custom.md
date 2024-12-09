# Пользовательский интерфейс перевода

## ImmersiveL

[Модель погруженного перевода](https://github.com/immersive-translate/ImmersiveL) теперь поддерживает настройку пользовательского интерфейса.

На странице 【Настройки】, в режиме разработчика, включите функцию 【Beta】, чтобы увидеть в сервисе перевода:

![](https://s.immersivetranslate.com/assets/20231026-125902.jpeg)

## Запрос

- method: POST
- content-type: application/json
- body
  - source_lang: исходный {код языка}
  - target_lang: целевой {код языка}
  - text_list: массив строк текста для перевода

## Ответ

- response
  - translations: массив
    - detected_source_lang: обнаруженный исходный язык {код языка}
    - text: переведенный текст

## Сохранение заполнителей

Цель состоит в том, чтобы оставить место для не текстового содержимого веб-страниц при переводе, сохраняя эти специальные символы. После завершения перевода мы восстановим соответствующее не текстовое содержимое.

### Формат

Массив строк

- 0: левая часть парного разделителя
- 1: правая часть парного разделителя
- 2: разделитель тегов

#### Пример

- Пример1: ['{', '}']

```
   Оригинал: 😁 привет 👏🏻 мир
Заполнитель оригинала: {0} привет {1} мир

Заполнитель перевода: {0} здравствуй {1} мир
   Перевод: 😁 здравствуй 👏🏻 мир
```

- Пример2: ['', '', 'b']

```
   Оригинал: 😁 привет 👏🏻 мир
Заполнитель оригинала: <b0></b0> привет <b1></b1> мир

Заполнитель перевода: <b0></b0> здравствуй <b1></b1> мир
   Перевод: 😁 здравствуй 👏🏻 мир
```

## Коды языков

```bash
auto: Автоматическое определение языка, Detect Language
af: Африкаанс, Afrikaans
am: Амхарский, Amharic
ar: Арабский, Arabic
az: Азербайджанский, Azerbaijani
be: Белорусский, Belarusian
bg: Болгарский, Bulgarian
tn: Язык Зана, Zana
bn: Бенгальский, Bengali
bs: Боснийский, Bosnian
ca: Каталонский, Catalan
ceb: Себуанский, Cebuano
co: Корсиканский, Corsican
cs: Чешский, Czech
cy: Валлийский, Welsh
da: Датский, Danish
de: Немецкий, German
el: Греческий, Greek
en: Английский, English
eo: Эсперанто, Esperanto
es: Испанский, Spanish
et: Эстонский, Estonian
eu: Баскский, Basque
fa: Персидский, Farsi
fi: Финский, Finnish
fil: Филиппинский, Filipino
fj: Фиджийский, Fijian
fr: Французский, French
fy: Фризский, Frisian
ga: Ирландский, Irish
gd: Шотландский гэльский, Scottish Gaelic
gl: Галисийский, Galician
gu: Гуджарати, Gujarati
ha: Хауса, Hausa
haw: Гавайский, Hawaiian
he: Иврит, Hebrew
hi: Хинди, Hindi
hmn: Хмонг, Hmong
hr: Хорватский, Croatian
ht: Гаитянский креольский, Haitian Creole
hu: Венгерский, Hungarian
hy: Армянский, Armenian
id: Индонезийский, Indonesian
ig: Игбо, Igbo
is: Исландский, Icelandic
it: Итальянский, Italian
ja: Японский, 日本語
jw: Яванский, Javanese
ka: Грузинский, Georgian
kk: Казахский, Kazakh
km: Кхмерский, Khmer
kn: Каннада, Kannada
ko: Корейский, Korean
ku: Курдский, Kurdish
ky: Киргизский, Kyrgyz
la: Латинский, Latin
lb: Люксембургский, Luxembourgish
lo: Лаосский, Lao
lt: Литовский, Lithuanian
lv: Латышский, Latvian
mg: Малагасийский, Malagash
mi: Маори, Maori
mk: Македонский, Macedonian
ml: Малаялам, Malayalam
mn: Монгольский, Mongolian
mr: Маратхи, Marathi
ms: Малайский, Malay
mt: Мальтийский, Maltese
mww: Белый мяо, Bai Miao
my: Бирманский, Burmese
ne: Непальский, Nepali
nl: Голландский, Dutch
no: Норвежский, Norwegian
ny: Чичева (Чичева), Nyanz(Chichewa)
otq: Отоми Керетаро, Querétaro Otomi
pa: Пенджабский, Punjabi
pl: Польский, Polish
ps: Пушту, Afghan/Pashto
pt: Португальский (Португалия, Бразилия), Portuguese(Portugal,Brazil)
ro: Румынский, Romanian
ru: Русский, Russian
sd: Синдхи, Sindhi
si: Сингальский, Sinhala
sk: Словацкий, Slovak
sl: Словенский, Slovenian
sm: Самоанский, Samoan
sn: Шона, Shona
so: Сомали, Somali
sq: Албанский, Albanian
sr: Сербский, Serbian
sr-Cyrl: Сербский (кириллица), Serbia(Cyrillic)
sr-Latn: Сербский (латиница), Serbia(Latin)
st: Сесото, Sesotho
su: Сунданский, Sundanese
sv: Шведский, Swedish
sw: Суахили, Swahili
ta: Тамильский, Tamil
te: Телугу, Telugu
tg: Таджикский, Tajik
th: Тайский, Thai
tlh: Клингонский, Klingon
tlh-Qaak: Клингонский (piqaD), Klingo(piqaD)
to: Тонганский, Tongan
tr: Турецкий, Turkish
ty: Таитянский, Tahiti
ug: Уйгурский, Uyghur
uk: Украинский, Ukrainian
ur: Урду, Urdu
uz: Узбекский, Uzbek
vi: Вьетнамский, Vietnamese
wyw: Классический китайский, 文言文
xh: Банту, Bantu
yi: Идиш, Yiddish
yo: Йоруба, Yoruba
yua: Юкатекский майя, Yucatan Mayan
yue: Кантонский (традиционный), Cantones(Traditional)
zh-CN: Упрощенный китайский, 简体中文
zh-TW: Традиционный китайский, 繁體中文
zu: Зулусский, Zulu
```
