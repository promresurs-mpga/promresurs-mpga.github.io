<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Ubuntu+Condensed&display=swap" rel="stylesheet">

<style>
:root {
    /* COLORS */
    --white: #fff;
    --light-gray: #e0e0e0;
    --gray: #c0c0c0;
    --dark-gray: #808080;
    --bg-light: #004080;
    --bg-dark: #002040;

    /* FONT SIZES */
    --fs-1: 60px;
    --fs-2: 45px;
    --fs-3: 30px;
    --fs-4: 22px;
    --fs-5: 15px;

    /* SPACING */
    --sp-1: 60px;
    --sp-2: 30px;
    --sp-3: 15px;
}

* { box-sizing: border-box; }

body {
    margin: 0;
    font-family: 'Ubuntu Condensed', sans-serif;
}

/* ANIMATION */
.clickable, .item, .lang-box div {
    transition: all 0.25s ease;
}

/* HEADER */
.header {
    background: var(--bg-light);
    color: var(--white);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: var(--sp-3) var(--sp-2);
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
    gap: var(--sp-2);
}

.clickable {
    cursor: pointer;
}

.clickable:hover {
    color: var(--bg-dark);
}

.icon {
    width: 30px;
    height: 30px;
}

/* LANGUAGE */
.lang { position: relative; }

.lang-box {
    display: none;
    position: absolute;
    right: 0;
    background: var(--bg-dark);
}

.lang-box div {
    padding: 10px;
    cursor: pointer;
}

.lang-box div:hover {
    background: var(--bg-light);
}

.active-lang {
    color: var(--gray);
    pointer-events: none;
}

/* SECTIONS */
.section {
    width: 100%;
    padding: var(--sp-1) var(--sp-2);
    text-align: center;
}

.light { background: var(--white); color: var(--bg-light); }
.dark { background: var(--bg-light); color: var(--white); }
.dark-alt { background: var(--bg-dark); color: var(--white); }

.title-big {
    font-size: var(--fs-1);
    font-weight: bold;
}

.text {
    font-size: var(--fs-3);
    max-width: 900px;
    margin: auto;
}

/* TABLE */
.table {
    margin: var(--sp-2) auto;
    border-collapse: collapse;
}

.table th, .table td {
    padding: 10px;
    text-align: center;
    background: white;
}

.light-table th {
    background: var(--bg-dark);
    color: var(--white);
}

.light-table td {
    color: var(--bg-dark);
    border: 2px solid var(--bg-light);
}

.dark-table th {
    background: var(--bg-light);
    color: var(--white);
}

.dark-table td {
    color: var(--bg-light);
    border: 2px solid var(--bg-dark);
}

/* ROW */
.row {
    display: flex;
    justify-content: center;
    gap: var(--sp-2);
    flex-wrap: wrap;
}

.img {
    width: 150px;
    height: 150px;
    background: var(--gray);
}

/* FOOTER */
.footer {
    background: var(--bg-dark);
    color: white;
    display: flex;
    justify-content: space-between;
    padding: var(--sp-2);
}
</style>
</head>

<body>

<div class="header">
    <div>
        <div class="title">ТОО «ПРОМРЕСУРС MPGA»</div>
        <div class="subtitle">Производственно-торговая компания</div>
    </div>

    <div class="header-right">
        <div>+7 (775) 331-64-44</div>
        <div>promresurs-mpga@outlook.com</div>

        <a href="https://wa.me/77753316444" target="_blank">
            <img class="icon clickable" src="https://cdn-icons-png.flaticon.com/512/733/733585.png">
        </a>

        <a href="https://t.me/oleg_kenroy" target="_blank">
            <img class="icon clickable" src="https://cdn-icons-png.flaticon.com/512/733/733579.png">
        </a>

        <div class="lang clickable" onclick="toggleLang()">
            РУС ▼
            <div class="lang-box" id="langBox">
                <div class="active-lang">РУС</div>
                <div>ENG</div>
            </div>
        </div>
    </div>
</div>

<div class="section dark">
    <div class="title-big">КОНТАКТЫ</div>
    <div class="text"><b>ТОО «ПРОМРЕСУРС MPGA»</b><br>
    promresurs-mpga@outlook.com<br>
    +7 (775) 331-64-44<br>
    Республика Казахстан, г. Актобе, ул. Карасай-Батыра 35</div>

    <iframe src="https://maps.google.com/maps?q=Aktobe&t=&z=13&ie=UTF8&iwloc=&output=embed" width="100%" height="300"></iframe>
</div>

<div class="footer">
    <div><b>ТОО «ПРОМРЕСУРС MPGA»</b></div>
    <div>
        +7 (775) 331-64-44<br>
        promresurs-mpga@outlook.com
    </div>
</div>

<script>
function toggleLang(){
    const b=document.getElementById('langBox');
    b.style.display=b.style.display==='block'?'none':'block';
}
</script>

</body>
</html>
