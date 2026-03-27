<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Ubuntu+Condensed&display=swap" rel="stylesheet">

<style>
:root {
    --white: rgb(255,255,255);
    --light-gray: rgb(224,224,224);
    --gray: rgb(192,192,192);
    --dark-gray: rgb(128,128,128);
    --bg-light: #004080;
    --bg-dark: #002040;

    --fs-1: 60px;
    --fs-2: 45px;
    --fs-3: 30px;
    --fs-4: 22.5px;
    --fs-5: 15px;
}

body {
    margin: 0;
    font-family: 'Ubuntu Condensed', sans-serif;
}

.header {
    background: var(--bg-light);
    color: var(--white);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: calc(var(--fs-3)/4) calc(var(--fs-3)/2);
}

.header-left {
    display: flex;
    flex-direction: column;
    gap: calc(var(--fs-3)/4);
}

.title {
    font-size: var(--fs-1);
    font-weight: bold;
}

.subtitle {
    font-size: var(--fs-3);
    color: var(--gray);
}

.header-right {
    display: flex;
    align-items: center;
    gap: calc(var(--fs-3)/2);
}

.clickable {
    cursor: pointer;
    font-size: var(--fs-3);
    color: var(--white);
}

.clickable:hover {
    color: var(--bg-dark);
}

.lang {
    position: relative;
}

.lang-box {
    display: none;
    position: absolute;
    top: calc(var(--fs-3));
    right: 0;
    background: var(--bg-dark);
    padding: calc(var(--fs-5));
}

.section {
    text-align: center;
    padding: calc(var(--fs-1)/2);
}

.light {
    background: var(--white);
    color: var(--bg-light);
}

.dark {
    background: var(--bg-light);
    color: var(--white);
}

.dark-alt {
    background: var(--bg-dark);
    color: var(--white);
}

.title-big {
    font-size: var(--fs-1);
}

.text {
    font-size: var(--fs-3);
    max-width: 900px;
    margin: calc(var(--fs-3)/4) auto;
    line-height: 1.5;
}

.table {
    margin: calc(var(--fs-3)/2) auto;
    border-collapse: collapse;
}

.table th, .table td {
    padding: calc(var(--fs-5));
}

.table th {
    background: var(--bg-dark);
    color: var(--white);
    font-size: var(--fs-3);
}

.table td {
    font-size: var(--fs-4);
}

.light-table th, .light-table td {
    border: 2px solid var(--bg-light);
    color: var(--bg-dark);
}

.dark-table th, .dark-table td {
    border: 2px solid var(--bg-dark);
}

.dark-table td {
    color: var(--white);
}

.row {
    display: flex;
    justify-content: center;
    gap: calc(var(--fs-3));
    flex-wrap: wrap;
    margin-top: calc(var(--fs-3));
}

.item {
    text-align: center;
    font-size: var(--fs-3);
}

.img {
    width: 150px;
    height: 150px;
    background: var(--gray);
    margin-bottom: calc(var(--fs-5));
}
</style>
</head>

<body>

<div class="header">
    <div class="header-left">
        <div class="title" id="title"></div>
        <div class="subtitle" id="subtitle"></div>
    </div>

    <div class="header-right">
        <div class="clickable">1</div>
        <div class="clickable">2</div>
        <div class="clickable">3</div>
        <div class="clickable">+7 (775) 331-64-44</div>

        <div class="lang clickable" onclick="toggleLang()">
            <span id="currentLang">РУС</span> ▼
            <div class="lang-box" id="langBox">
                <div onclick="setLang('ru')">РУС</div>
                <div onclick="setLang('en')">ENG</div>
            </div>
        </div>
    </div>
</div>

<div id="content"></div>

<script>
const DATA = {
ru: {
title: 'ТОО «ПРОМРЕСУРС MPGA»',
subtitle: 'Производственно-торговая компания',
blocks: [

{
type:'text',
title:'О НАС',
text:`ТОО «Промресурс MPGA» — производственно-торговая компания, основанная в 2017 году в городе Актобе, Республике Казахстан.

Компания специализируется на производстве лакокрасочной продукции и строительных материалов, а также на поставке химических компонентов для различных отраслей промышленности.

Предприятие располагает собственными производственными мощностями и современным оборудованием, что позволяет выпускать широкий ассортимент продукции и поддерживать стабильное качество.

Одним из ключевых принципов работы компании является строгое соблюдение технологических норм производства, использование сырья от проверенных и надежных поставщиков, а также постоянное совершенствование производственных процессов.

Благодаря развитию производственной базы и расширению технологических возможностей компания планирует увеличить ассортимент выпускаемой продукции до 500 наименований.`
},

{
type:'table',
dark:true,
title:'МЫ ПРОИЗВОДИМ',
text:`<b>ТОО «Промресурс MPGA»</b> производит широкий спектр лакокрасочной и строительной продукции, используемой в строительстве, ремонте и промышленности.

Ассортимент выпускаемой продукции включает несколько основных направлений.`,
headers:['Краски','Материалы','Покрытия'],
cols:[
['Дорожные','Интерьерные','Моющиеся','Потолочные','Универсальные'],
['Герметики','Шпатлевки','Наливные полы'],
['Бетоноконтакт','Грунтовки','Лаки']
]
},

{
type:'row',
title:'НАША ПРОДУКЦИЯ',
items:['Продукт 1','Продукт 2','Продукт 3','Продукт 4']
},

{
type:'table',
darkAlt:true,
title:'МЫ ПОСТАВЛЯЕМ',
text:`<b>ТОО «Промресурс MPGA»</b> также занимается поставкой химических компонентов для предприятий химической промышленности и производственных компаний.

Компания обеспечивает стабильные поставки продукции, высокое качество материалов и профессиональную техническую поддержку для своих клиентов.

Закупка химического сырья осуществляется напрямую у заводов-изготовителей или у официальных дистрибьюторов, что гарантирует надежность и соответствие продукции установленным стандартам.

В ассортименте поставляемой продукции представлены только проверенные химические компоненты, соответствующие международным требованиям качества.`,
headers:['Смолы','Растворители','Пигменты','Добавки','Отвердители и Катализаторы'],
cols:[
['Акриловые','Алкидные','Виниловые','Полиуретановые','Силиконовые','Эпоксидные'],
['Ароматические углеводороды','Вода','Жиры','Кетоны','Масла','Эфиры'],
['Антикоррозионные','Минеральные','Неорганические','Органические'],
['Адгезионные','Биологические','Диспергирующие','Пенообразующие','Реологические','Функциональные'],
['Амины','Изоцианаты','Металлические сиккативы','Пероксиды']
]
},

{
type:'row',
title:'НАШИ ПАРТНЁРЫ',
items:['','','','']
}

]
},

en:{
title:'PROMRESURS MPGA LLP',
subtitle:'Manufacturing and trading company',
blocks:[

{
type:'text',
title:'ABOUT US',
text:`PROMRESURS MPGA LLP is a manufacturing and trading company founded in 2017 in Aktobe, Republic of Kazakhstan.

The company specializes in the production of paints and coatings, construction materials, and the supply of chemical components for various industries.

The enterprise has its own production facilities and modern equipment, allowing it to produce a wide range of products while maintaining consistent quality.

One of the key principles of the company is strict compliance with production technologies, the use of raw materials from reliable suppliers, and continuous improvement of manufacturing processes.

Due to the development of its production base and expansion of technological capabilities, the company plans to increase its product range to 500 items.`
},

{
type:'table',
dark:true,
title:'WE PRODUCE',
text:`<b>PROMRESURS MPGA LLP</b> produces a wide range of paints, coatings, and construction materials used in construction, repair, and industry.

The product range includes several main categories.`,
headers:['Paints','Materials','Coatings'],
cols:[
['Road','Interior','Washable','Ceiling','Universal'],
['Sealants','Putty','Self-leveling floors'],
['Concrete contact','Primers','Varnishes']
]
},

{
type:'row',
title:'OUR PRODUCTS',
items:['Product 1','Product 2','Product 3','Product 4']
},

{
type:'table',
darkAlt:true,
title:'WE SUPPLY',
text:`<b>PROMRESURS MPGA LLP</b> also supplies chemical components for industrial enterprises and manufacturing companies.

The company ensures stable deliveries, high material quality, and professional technical support.

Raw materials are sourced directly from manufacturers or official distributors.

Only proven chemical components that meet international quality standards are supplied.`,
headers:['Resins','Solvents','Pigments','Additives','Hardeners and Catalysts'],
cols:[
['Acrylic','Alkyd','Vinyl','Polyurethane','Silicone','Epoxy'],
['Aromatic hydrocarbons','Water','Fats','Ketones','Oils','Esters'],
['Anti-corrosion','Mineral','Inorganic','Organic'],
['Adhesion','Biological','Dispersing','Foaming','Rheological','Functional'],
['Amines','Isocyanates','Metal driers','Peroxides']
]
},

{
type:'row',
title:'OUR PARTNERS',
items:['','','','']
}

]
}
};

let lang='ru';

function render(){
const d=DATA[lang];
document.getElementById('title').innerText=d.title;
document.getElementById('subtitle').innerText=d.subtitle;

const root=document.getElementById('content');
root.innerHTML='';

d.blocks.forEach(b=>{
let div=document.createElement('div');

if(b.dark) div.className='section dark';
else if(b.darkAlt) div.className='section dark-alt';
else div.className='section light';

let html=`<div class="title-big">${b.title}</div>`;

if(b.text) html+=`<div class="text">${b.text}</div>`;

if(b.type==='table'){
html+=`<table class="table ${b.dark?'light-table':'dark-table'}"><tr>`;
b.headers.forEach(h=>html+=`<th>${h}</th>`);
html+=`</tr>`;

let max=Math.max(...b.cols.map(c=>c.length));
for(let i=0;i<max;i++){
html+=`<tr>`;
b.cols.forEach(c=>{
html+=`<td>${c[i]||''}</td>`;
});
html+=`</tr>`;
}

html+=`</table>`;
}

if(b.type==='row'){
html+=`<div class="row">`;
b.items.forEach(i=>{
html+=`<div class="item"><div class="img"></div>${i}</div>`;
});
html+=`</div>`;
}

div.innerHTML=html;
root.appendChild(div);
});
}

function toggleLang(){
let b=document.getElementById('langBox');
b.style.display=b.style.display==='block'?'none':'block';
}

function setLang(l){
lang=l;
document.getElementById('currentLang').innerText=l==='ru'?'РУС':'ENG';
render();
document.getElementById('langBox').style.display='none';
}

render();
</script>

</body>
</html>
