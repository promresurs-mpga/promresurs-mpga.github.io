<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Ubuntu+Condensed&display=swap" rel="stylesheet">
<style>
:root{
--white:#fff;
--light-gray:#e0e0e0;
--gray:#c0c0c0;
--bg-light:#004080;
--bg-dark:#002040;

--fs-1:60px;
--fs-2:45px;
--fs-3:30px;
--fs-4:22.5px;
--fs-5:15px;
}

*{box-sizing:border-box}
body{margin:0;font-family:'Ubuntu Condensed',sans-serif}

.clickable,.lang-box div,.item,img{transition:all .25s ease}

.header{
background:var(--bg-light);
color:var(--white);
display:flex;
justify-content:space-between;
align-items:center;
padding:calc(var(--fs-1)/8);
}

.title{font-size:var(--fs-1);font-weight:bold}
.subtitle{font-size:var(--fs-3);color:var(--gray);margin-top:calc(var(--fs-3)/8)}

.header-right{display:flex;align-items:center;gap:calc(var(--fs-3)/2);font-size:var(--fs-3)}

.clickable{cursor:pointer}
.clickable:hover{color:var(--bg-dark)}

.icon{width:30px;height:30px}
.icon:hover{filter:brightness(0.7)}

.lang{position:relative}

.lang-box{
display:none;
position:absolute;
right:0;
background:var(--bg-dark);
min-width:120px;
border:1px solid var(--white);
}

.lang-item{
display:flex;
align-items:center;
gap:8px;
padding:10px;
cursor:pointer;
}

.lang-item:hover{background:var(--bg-light)}

.active-lang{
color:var(--gray);
pointer-events:none;
}

.section{
max-width:1200px;
margin:0 auto;
padding:calc(var(--fs-1)/2) calc(var(--fs-3)/2);
}

.light{background:var(--white);color:var(--bg-light)}
.dark{background:var(--bg-light);color:var(--white)}
.dark-alt{background:var(--bg-dark);color:var(--white)}

.title-big{font-size:var(--fs-1);font-weight:bold;text-align:center}

.text{
font-size:var(--fs-3);
margin:calc(var(--fs-3)/4) 0;
line-height:1.5;
}

.table{
width:100%;
margin:calc(var(--fs-3)/2) 0;
border-collapse:collapse;
}

.table th,.table td{
padding:calc(var(--fs-5));
text-align:center;
background:white;
border:2px solid;
}

.table th{font-size:var(--fs-3)}
.table td{font-size:var(--fs-4)}

.light-table th{background:var(--bg-dark);color:white;border-color:var(--bg-light)}
.light-table td{color:var(--bg-dark);border-color:var(--bg-light)}

.dark-table th{background:var(--bg-light);color:white;border-color:var(--bg-dark)}
.dark-table td{color:var(--bg-light);border-color:var(--bg-dark)}

.row{display:flex;gap:calc(var(--fs-3));flex-wrap:wrap;margin-top:calc(var(--fs-3))}
.item{font-size:var(--fs-3)}
.img{width:150px;height:150px;background:var(--gray);margin-bottom:calc(var(--fs-5))}

.contacts{
background:var(--bg-light);
color:white;
display:flex;
justify-content:space-between;
gap:40px;
padding:calc(var(--fs-1)/2);
}

.contacts-left{max-width:500px}
.contacts-title{font-size:var(--fs-1);color:white;font-weight:bold}
.contacts-name{color:var(--light-gray);font-size:var(--fs-3);font-weight:bold;margin-top:10px}
.contacts-text{color:var(--gray);font-size:var(--fs-3);margin-top:10px}

.footer{
background:var(--bg-dark);
color:white;
display:flex;
justify-content:space-between;
padding:calc(var(--fs-3)/2);
}

.footer-title{font-size:var(--fs-2);font-weight:bold}
.footer-right{display:flex;flex-direction:column;gap:10px;font-size:var(--fs-3)}

.footer-icons{display:flex;gap:10px}

.footer .icon:hover{filter:brightness(1.4)}
</style>
</head>
<body>

<div class="header">
<div>
<div class="title" id="title"></div>
<div class="subtitle" id="subtitle"></div>
</div>

<div class="header-right">
<div id="phone"></div>
<div id="email"></div>

<a href="https://wa.me/77753316444" target="_blank">
<img class="icon clickable" src="https://cdn-icons-png.flaticon.com/512/733/733585.png">
</a>

<div class="lang clickable" onclick="toggleLang()">
<span id="currentLang">РУС</span> <span id="arrow">▼</span>
<div class="lang-box" id="langBox"></div>
</div>
</div>
</div>

<div id="content"></div>

<div class="contacts">
<div class="contacts-left" id="contacts"></div>
<iframe src="https://maps.google.com/maps?q=Aktobe&t=&z=13&output=embed" width="50%" height="300"></iframe>
</div>

<div class="footer">
<div class="footer-title" id="footerTitle"></div>
<div class="footer-right" id="footerRight"></div>
</div>

<script>
const DATA={
ru:{
title:'ТОО «ПРОМРЕСУРС MPGA»',
subtitle:'Производственно-торговая компания',
phone:'+7 (775) 331-64-44',
email:'promresurs-mpga@outlook.com',
contacts:{
name:'ТОО «ПРОМРЕСУРС MPGA»',
phone:'+7 (775) 331-64-44',
email:'promresurs-mpga@outlook.com',
address:'Республика Казахстан, г. Актобе, ул. Карасай-Батыра 35, н. п. 2'
},
blocks:[
{type:'text',title:'О НАС',text:`<b>ТОО «ПРОМРЕСУРС MPGA»</b> — производственно-торговая компания, основанная в 2017 году в городе Актобе, Республике Казахстан.

Компания специализируется на производстве лакокрасочной продукции и строительных материалов, а также на поставке химических компонентов для различных отраслей промышленности.

Предприятие располагает собственными производственными мощностями и современным оборудованием.

Компания планирует увеличить ассортимент до 500 наименований.`},

{type:'table',dark:true,title:'МЫ ПРОИЗВОДИМ',text:'',headers:['Краски','Материалы','Покрытия'],cols:[
['Дорожные','Интерьерные','Моющиеся','Потолочные','Универсальные'],
['Герметики','Шпатлевки','Наливные полы'],
['Бетоноконтакт','Грунтовки','Лаки']
]},

{type:'row',title:'НАША ПРОДУКЦИЯ',items:['Продукт 1','Продукт 2','Продукт 3','Продукт 4']},

{type:'table',darkAlt:true,title:'МЫ ПОСТАВЛЯЕМ',headers:['Смолы','Растворители','Пигменты','Добавки','Отвердители и Катализаторы'],cols:[
['Акриловые','Алкидные','Виниловые','Полиуретановые','Силиконовые','Эпоксидные'],
['Ароматические углеводороды','Вода','Жиры','Кетоны','Масла','Эфиры'],
['Антикоррозионные','Минеральные','Неорганические','Органические'],
['Адгезионные','Биологические','Диспергирующие','Пенообразующие','Реологические','Функциональные'],
['Амины','Изоцианаты','Металлические сиккативы','Пероксиды']
]},

{type:'row',title:'НАШИ ПАРТНЁРЫ',items:['','','','']}
]
},

en:{title:'PROMRESURS MPGA LLP',subtitle:'Manufacturing and trading company',phone:'+7 (775) 331-64-44',email:'promresurs-mpga@outlook.com',contacts:{name:'PROMRESURS MPGA LLP',phone:'+7 (775) 331-64-44',email:'promresurs-mpga@outlook.com',address:'Kazakhstan, Aktobe'} ,blocks:[]}
};

let lang='ru';

function render(){
const d=DATA[lang];

document.getElementById('title').innerHTML=d.title;
document.getElementById('subtitle').innerHTML=d.subtitle;
document.getElementById('phone').innerHTML=d.phone;
document.getElementById('email').innerHTML=d.email;

const root=document.getElementById('content');
root.innerHTML='';

d.blocks.forEach(b=>{
let div=document.createElement('div');
div.className='section '+(b.dark?'dark':b.darkAlt?'dark-alt':'light');

let html=`<div class="title-big">${b.title}</div>`;

if(b.text) html+=`<div class="text">${b.text}</div>`;

if(b.type==='table'){
html+=`<table class="table ${b.dark?'light-table':'dark-table'}"><tr>`;
b.headers.forEach(h=>html+=`<th>${h}</th>`);
html+='</tr>';
let max=Math.max(...b.cols.map(c=>c.length));
for(let i=0;i<max;i++){
html+='<tr>';
b.cols.forEach(c=>html+=`<td>${c[i]||''}</td>`);
html+='</tr>';
}
html+='</table>';
}

if(b.type==='row'){
html+='<div class="row">';
b.items.forEach(i=>html+=`<div class="item clickable"><div class="img"></div>${i}</div>`);
html+='</div>';
}

div.innerHTML=html;
root.appendChild(div);
});

const c=d.contacts;
document.getElementById('contacts').innerHTML=`
<div class="contacts-title">КОНТАКТЫ</div>
<div class="contacts-name">${c.name}</div>
<div class="contacts-text">${c.phone}</div>
<div class="contacts-text">${c.email}</div>
<div class="contacts-text">${c.address}</div>`;

const footerRight=document.getElementById('footerRight');
footerRight.innerHTML=`${d.phone}<br>${d.email}<div class='footer-icons'><a href='https://wa.me/77753316444'><img class='icon' src='https://cdn-icons-png.flaticon.com/512/733/733585.png'></a></div>`;

document.getElementById('footerTitle').innerHTML=d.title;

renderLang();
}

function renderLang(){
const box=document.getElementById('langBox');
box.innerHTML='';
['ru','en'].forEach(l=>{
let div=document.createElement('div');
div.className='lang-item'+(l===lang?' active-lang':'');
div.innerHTML=(l==='ru'?'🇷🇺 РУС':'🇬🇧 ENG');
if(l!==lang) div.onclick=()=>{lang=l;document.getElementById('currentLang').innerText=l==='ru'?'РУС':'ENG';toggleLang();render()};
box.appendChild(div);
});
}

function toggleLang(){
let b=document.getElementById('langBox');
let arrow=document.getElementById('arrow');
let open=b.style.display==='block';
b.style.display=open?'none':'block';
arrow.innerText=open?'▼':'▲';
}

render();
</script>

</body>
</html>
