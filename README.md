<html lang="pl">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>🍜 Bar Sajgon</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
.quickButtons{

display:grid;

grid-template-columns:repeat(5,1fr);

gap:15px;

margin-top:35px;

}

.quickButtons button{

padding:18px;

border:none;

border-radius:18px;

background:#b91c1c;

color:white;

font-size:18px;

cursor:pointer;

transition:.3s;

}

.quickButtons button:hover{

transform:translateY(-5px);

background:#ef4444;

box-shadow:0 0 20px red;

}

.summary{

margin-top:35px;

display:grid;

gap:15px;

}

.summaryItem{

display:flex;

justify-content:space-between;

padding:18px;

border-radius:16px;

background:rgba(255,255,255,.05);

}

.totalBox{

margin-top:25px;

padding:25px;

text-align:center;

border-radius:20px;

background:rgba(255,255,255,.08);

border:1px solid rgba(255,255,255,.08);

}

.totalBox h1{

font-size:52px;

color:#FFD54A;

text-shadow:

0 0 20px gold,

0 0 35px red;

}

.actions{

margin-top:30px;

display:grid;

grid-template-columns:repeat(2,1fr);

gap:18px;

}

.actions button{

padding:20px;

border:none;

border-radius:18px;

cursor:pointer;

font-size:18px;

color:white;

background:#991b1b;

transition:.3s;

}

.actions button:hover{

background:#dc2626;

transform:scale(1.05);

box-shadow:0 0 25px red;

}

.history{

margin-top:35px;

}

.historyItem{

padding:15px;

margin-top:10px;

border-radius:15px;

background:rgba(255,255,255,.05);

}

.notification{

position:fixed;

right:30px;

bottom:30px;

padding:18px 30px;

border-radius:16px;

background:#d62828;

opacity:0;

transition:.4s;

}

.notification.show{

opacity:1;

}

@media(max-width:1000px){

.grid{

grid-template-columns:1fr;

}

.quickButtons{

grid-template-columns:repeat(2,1fr);

}

.actions{

grid-template-columns:1fr;

}

.logo{

font-size:38px;

}

.counter{

flex-direction:column;

}

.counter input{

width:100%;

}

}

</style>

</head>

<body>

<div class="container">

<div class="header">

<div>

<div class="logo">

🍜 BAR SAJGON

</div>

<div class="subtitle">

Kalkulator zestawów

</div>

</div>

<div class="clock" id="clock">

00:00:00

</div>

</div>

<div class="grid">

<div class="panel">

<h2>Wybierz ilość zestawów</h2>
*{
<div class="counter">

    <button id="minus">−</button>

    <input
        id="amount"
        type="number"
        value="0"
        min="0">

    <button id="plus">+</button>

</div>

<div class="quickButtons">

    <button class="quick" data-value="1">
        +1
    </button>

    <button class="quick" data-value="10">
        +10
    </button>

    <button class="quick" data-value="25">
        +25
    </button>

    <button class="quick" data-value="50">
        +50
    </button>

    <button class="quick" data-value="100">
        +100
    </button>

</div>

<div class="summary">

    <div class="summaryItem">

        <span>Ilość zestawów</span>

        <strong id="summaryAmount">

            0

        </strong>

    </div>

    <div class="summaryItem">

        <span>Cena za zestaw</span>

        <strong>

            15 000$

        </strong>

    </div>

    <div class="summaryItem">

        <span>Rabat</span>

        <strong id="discountText">

            0%

        </strong>

    </div>

</div>

<div class="totalBox">

    <h3>

        Do zapłaty

    </h3>

    <h1 id="totalPrice">

        0$

    </h1>

</div>

<div class="actions">

    <button id="discountButton">

        🔥 50% OFF

    </button>

    <button id="themeButton">

        🎨 Motyw

    </button>

    <button id="copyButton">

        📋 Kopiuj

    </button>

    <button id="resetButton">

        🗑 Reset

    </button>

</div>

</div>

<div class="panel">

<h2>

Historia

</h2>

<div id="history">

<p>

Brak zapisanych obliczeń.

</p>

</div>

</div>

</div>

<div

class="notification"

id="notification">

Skopiowano ✔

</div>

<script>
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{

background:url("assets/background.png");

background-size:cover;

background-position:center;

background-attachment:fixed;

min-height:100vh;

overflow-x:hidden;

color:white;

}

body::before{

content:"";

position:fixed;

inset:0;

background:rgba(0,0,0,.55);

backdrop-filter:blur(4px);

z-index:-1;

}

.container{

width:92%;

max-width:1500px;

margin:auto;

padding:40px;

}

.header{

display:flex;

justify-content:space-between;

align-items:center;

margin-bottom:35px;

}

.logo{

font-size:55px;

font-weight:700;

color:#FFD966;

text-shadow:
0 0 15px red,
0 0 30px red;

}

.subtitle{

opacity:.8;

margin-top:5px;

}

.clock{

font-size:22px;

padding:18px 30px;

border-radius:18px;

background:rgba(255,255,255,.08);

backdrop-filter:blur(15px);

border:1px solid rgba(255,255,255,.08);

}

.grid{

display:grid;

grid-template-columns:2fr 1fr;

gap:35px;

}

.panel{

background:rgba(255,255,255,.08);

border:1px solid rgba(255,255,255,.12);

backdrop-filter:blur(18px);

border-radius:25px;

padding:30px;

box-shadow:

0 0 25px rgba(255,0,0,.18);

}

.panel h2{

margin-bottom:25px;

font-size:28px;

}

.counter{

display:flex;

justify-content:center;

align-items:center;

gap:25px;

margin-top:20px;

}

.counter button{

width:75px;

height:75px;

border:none;

border-radius:20px;

font-size:36px;

cursor:pointer;

background:#d62828;

color:white;

transition:.3s;

}

.counter button:hover{

transform:scale(1.08);

background:#ff4040;

box-shadow:0 0 25px red;

}

.counter input{

width:180px;

height:75px;

text-align:center;

font-size:34px;

border:none;

border-radius:20px;

background:rgba(255,255,255,.08);

color:white;

outline:none;

}
