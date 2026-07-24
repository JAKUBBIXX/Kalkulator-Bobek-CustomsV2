<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bar Sajgon | Kalkulator</title>

    <link rel="stylesheet" href="style.css">

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

    <script src="https://kit.fontawesome.com/6c4f7d8d3b.js" crossorigin="anonymous"></script>
</head>

<body>

<div class="background"></div>

<div class="overlay"></div>

<div class="container">

<header>

<div class="logo">

<h1>🍜 BAR SAJGON</h1>

<p>Kalkulator Zestawów</p>

</div>

</header>

<div class="calculator">

<div class="left">

<h2>Ilość zestawów</h2>

<div class="counter">

<button id="minus">-</button>

<input type="number" id="count" value="0" min="0">

<button id="plus">+</button>

</div>

<div class="quick">

<button class="quickBtn" data-add="10">+10</button>

<button class="quickBtn" data-add="25">+25</button>

<button class="quickBtn" data-add="50">+50</button>

<button class="quickBtn" data-add="100">+100</button>

</div>

</div>

<div class="right">

<div class="priceBox">

<span>Cena za zestaw</span>

<h2>15 000$</h2>

</div>

<div class="summary">

<h3>Podsumowanie</h3>

<p>Zestawy:
<span id="summaryCount">
0
</span>
</p>

<p>Rabat:
<span id="discountText">
Brak
</span>
</p>

<p>Do zapłaty</p>

<h1 id="total">

0 $

</h1>

</div>

<div class="buttons">

<button id="discount">

50% OFF

</button>

<button id="copy">

Kopiuj

</button>

<button id="clear">

Wyczyść

</button>

<button id="theme">

Motyw

</button>

</div>

</div>

</div>

<footer>

Bar Sajgon © 2026

</footer>

</div>

<script src="script.js"></script>

</body>
</html>
 <section class="history">

            <div class="glass">

                <h2>Historia</h2>

                <div id="historyList">

                    <p>Brak zapisanych obliczeń.</p>

                </div>

            </div>

        </section>

    </main>

    <footer>

        <span>Bar Sajgon © 2026</span>

    </footer>

</div>

<div id="notification" class="notification">
    Skopiowano do schowka ✔
</div>

</body>

</html>
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bar Sajgon | Kalkulator</title>

    <link rel="stylesheet" href="style.css">

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

    <script src="script.js" defer></script>
</head>

<body>

<div class="background"></div>

<div class="overlay"></div>

<div class="container">

    <header>

        <div class="logoBox">

            <h1>🍜 BAR SAJGON</h1>

            <p>Kalkulator Zestawów</p>

        </div>

    </header>

    <main>

        <section class="calculator">

            <div class="glass">

                <h2>Ilość zestawów</h2>

                <div class="counter">

                    <button id="minus">
                        −
                    </button>

                    <input
                        type="number"
                        id="amount"
                        value="0"
                        min="0">

                    <button id="plus">
                        +
                    </button>

                </div>

                <div class="quickButtons">

                    <button class="quick" data-add="1">
                        +1
                    </button>

                    <button class="quick" data-add="10">
                        +10
                    </button>

                    <button class="quick" data-add="25">
                        +25
                    </button>

                    <button class="quick" data-add="50">
                        +50
                    </button>

                    <button class="quick" data-add="100">
                        +100
                    </button>

                </div>

            </div>

            <div class="glass summary">

                <h2>Podsumowanie</h2>

                <div class="line">

                    <span>Zestawy</span>

                    <strong id="summaryAmount">
                        0
                    </strong>

                </div>

                <div class="line">

                    <span>Cena za zestaw</span>

                    <strong>
                        15 000$
                    </strong>

                </div>

                <div class="line">

                    <span>Rabat</span>

                    <strong id="discountValue">
                        0%
                    </strong>

                </div>

                <div class="total">

                    <h3>Do zapłaty</h3>

                    <h1 id="price">
                        0$
                    </h1>

                </div>

            </div>

            <div class="glass actions">

                <button id="discount">
                    🔥 50% OFF
                </button>

                <button id="theme">
                    🎨 Zmień motyw
                </button>

                <button id="copy">
                    📋 Kopiuj
                </button>

                <button id="reset">
                    🗑 Wyczyść
                </button>

            </div>

        </section>
        /* ===========================
   RESET
=========================== */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{

    font-family:'Poppins',sans-serif;

    background:#111;

    overflow-x:hidden;

    min-height:100vh;

    color:white;

}

/* ===========================
   TŁO
=========================== */

.background{

    position:fixed;

    inset:0;

    background:url("assets/background.png");

    background-size:cover;

    background-position:center;

    z-index:-3;

}

.overlay{

    position:fixed;

    inset:0;

    background:linear-gradient(
        rgba(0,0,0,.45),
        rgba(0,0,0,.75)
    );

    backdrop-filter:blur(3px);

    z-index:-2;

}

/* ===========================
   GŁÓWNY UKŁAD
=========================== */

.container{

    width:100%;

    max-width:1450px;

    margin:auto;

    padding:40px;

}

header{

    text-align:center;

    margin-bottom:45px;

}

.logoBox{

    display:inline-block;

    padding:25px 55px;

    border-radius:25px;

    background:rgba(15,15,15,.45);

    backdrop-filter:blur(18px);

    border:1px solid rgba(255,255,255,.08);

    box-shadow:
    0 0 35px rgba(255,0,0,.18);

}

.logoBox h1{

    font-size:55px;

    color:#ffd86b;

    text-shadow:
    0 0 15px #ff2f2f,
    0 0 30px #ff0000;

}

.logoBox p{

    margin-top:10px;

    color:#fff;

    opacity:.9;

    font-size:20px;

}

.calculator{

    display:grid;

    grid-template-columns:

    1fr

    420px;

    gap:35px;

}

/* ===========================
   GLASS
=========================== */

.glass{

    background:rgba(255,255,255,.08);

    border:1px solid rgba(255,255,255,.15);

    backdrop-filter:blur(22px);

    border-radius:28px;

    padding:35px;

    box-shadow:

    0 10px 40px rgba(0,0,0,.45),

    0 0 20px rgba(255,40,40,.25);

}
/* ===========================
   LICZNIK
=========================== */

.counter{

    margin-top:30px;

    display:flex;

    justify-content:center;

    align-items:center;

    gap:20px;

}

.counter button{

    width:70px;

    height:70px;

    border:none;

    border-radius:18px;

    background:#d62828;

    color:white;

    font-size:34px;

    cursor:pointer;

    transition:.3s;

    box-shadow:
    0 0 15px rgba(255,0,0,.5);

}

.counter button:hover{

    transform:scale(1.08);

    background:#ff3b3b;

    box-shadow:
    0 0 30px red;

}

.counter input{

    width:170px;

    height:70px;

    border:none;

    border-radius:18px;

    text-align:center;

    font-size:32px;

    color:white;

    background:rgba(255,255,255,.08);

    outline:none;

}

/* ===========================
   SZYBKIE PRZYCISKI
=========================== */

.quickButtons{

    margin-top:35px;

    display:grid;

    grid-template-columns:repeat(5,1fr);

    gap:15px;

}

.quick{

    border:none;

    border-radius:15px;

    padding:16px;

    font-size:18px;

    cursor:pointer;

    color:white;

    background:#b91c1c;

    transition:.25s;

}

.quick:hover{

    transform:translateY(-4px);

    background:#ef4444;

    box-shadow:0 0 20px red;

}

/* ===========================
   PODSUMOWANIE
=========================== */

.summary h2{

    margin-bottom:25px;

}

.line{

    display:flex;

    justify-content:space-between;

    margin:18px 0;

    font-size:20px;

}

.total{

    margin-top:30px;

    padding:25px;

    border-radius:20px;

    background:rgba(255,255,255,.05);

    text-align:center;

}

.total h1{

    margin-top:15px;

    font-size:48px;

    color:#ffd54a;

    text-shadow:
    0 0 15px gold,
    0 0 30px red;

}

/* ===========================
   AKCJE
=========================== */

.actions{

    display:grid;

    grid-template-columns:repeat(2,1fr);

    gap:20px;

    margin-top:35px;

}

.actions button{

    border:none;

    border-radius:18px;

    padding:20px;

    font-size:18px;

    cursor:pointer;

    background:#991b1b;

    color:white;

    transition:.3s;

}

.actions button:hover{

    transform:scale(1.05);

    background:#dc2626;

    box-shadow:
    0 0 25px red;

}
/* ========================================
   HISTORIA
======================================== */

.history{

    margin-top:35px;

}

.history .glass{

    min-height:180px;

}

#historyList{

    display:flex;

    flex-direction:column;

    gap:12px;

    margin-top:20px;

}

#historyList p{

    padding:15px;

    border-radius:14px;

    background:rgba(255,255,255,.05);

    border-left:4px solid #ff4040;

}

/* ========================================
   NOTYFIKACJA
======================================== */

.notification{

    position:fixed;

    right:35px;

    bottom:35px;

    padding:18px 28px;

    border-radius:15px;

    background:#c62828;

    color:white;

    font-weight:600;

    opacity:0;

    transform:translateY(40px);

    transition:.35s;

    box-shadow:
    0 0 25px rgba(255,0,0,.5);

}

.notification.show{

    opacity:1;

    transform:translateY(0);

}

/* ========================================
   ANIMACJE
======================================== */

@keyframes glow{

    0%{

        box-shadow:
        0 0 10px rgba(255,0,0,.25);

    }

    50%{

        box-shadow:
        0 0 35px rgba(255,80,80,.8);

    }

    100%{

        box-shadow:
        0 0 10px rgba(255,0,0,.25);

    }

}

.glass{

    animation:glow 3s infinite;

}

@keyframes floating{

    0%{

        transform:translateY(0px);

    }

    50%{

        transform:translateY(-6px);

    }

    100%{

        transform:translateY(0px);

    }

}

.logoBox{

    animation:floating 5s ease-in-out infinite;

}

/* ========================================
   RESPONSYWNOŚĆ
======================================== */

@media(max-width:1100px){

    .calculator{

        grid-template-columns:1fr;

    }

}

@media(max-width:700px){

    .container{

        padding:20px;

    }

    .logoBox h1{

        font-size:36px;

    }

    .counter{

        flex-direction:column;

    }

    .counter input{

        width:100%;

    }

    .quickButtons{

        grid-template-columns:repeat(2,1fr);

    }

    .actions{

        grid-template-columns:1fr;

    }

    .total h1{

        font-size:36px;

    }

}
