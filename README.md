<!doctype html>
<html lang="pl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Kalkulator Benny's — Cyan Edition</title>

<style>
:root{
  --bg:#041014;
  --card:#071b20;
  --muted:#8fbfc7;

  --accent:#00e5ff;
  --accent-2:#00bcd4;
  --accent-glow: rgba(0,229,255,0.18);

  --success:#22c55e;
  --danger:#ff4d4f;

  --glass: rgba(255,255,255,0.02);
  --radius:12px;
  --gap:14px;
  --shadow: 0 10px 40px rgba(0,0,0,0.7);

  --mono: 'Inter', system-ui, sans-serif;

  --tab-active: rgba(0,229,255,0.10);
  --tab-border: rgba(255,255,255,0.03);

  --small: 0.86rem;
}

*{
  box-sizing:border-box;
}

body{
  margin:0;
  background:linear-gradient(180deg,var(--bg),#02090c);
  color:white;
  font-family:var(--mono);
  overflow:hidden;
}

.app{
  width:min(980px,96vw);
  margin:auto;
  margin-top:20px;
  padding:18px;
  border-radius:18px;
  background:rgba(255,255,255,0.03);
  backdrop-filter:blur(12px);
  box-shadow:var(--shadow);
}

header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:20px;
}

.logo{
  width:50px;
  height:50px;
  border-radius:12px;
  background:linear-gradient(135deg,rgba(0,229,255,0.18),rgba(0,188,212,0.08));
  display:flex;
  align-items:center;
  justify-content:center;
  color:var(--accent);
  font-weight:900;
  font-size:22px;
}

h1{
  margin:0;
  color:var(--accent);
}

.lead{
  color:var(--muted);
  margin-top:4px;
}

.tabs{
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-bottom:18px;
}

.tab{
  padding:10px 14px;
  border-radius:10px;
  border:1px solid rgba(255,255,255,0.05);
  background:rgba(255,255,255,0.03);
  cursor:pointer;
  transition:0.2s;
}

.tab:hover{
  transform:translateY(-3px);
}

.tab.active{
  background:var(--tab-active);
  color:var(--accent);
  box-shadow:0 0 20px rgba(0,229,255,0.2);
}

.grid{
  display:grid;
  grid-template-columns:1fr 320px;
  gap:18px;
}

.list{
  display:flex;
  flex-direction:column;
  gap:12px;
}

.service{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:14px;
  border-radius:14px;
  background:rgba(255,255,255,0.03);
  border:1px solid rgba(255,255,255,0.04);
  transition:0.2s;
}

.service:hover{
  transform:translateY(-3px);
  box-shadow:0 10px 25px rgba(0,229,255,0.12);
}

.title{
  font-weight:700;
}

.price{
  color:var(--muted);
  margin-top:4px;
}

.controls{
  display:flex;
  align-items:center;
  gap:10px;
}

.btn{
  width:38px;
  height:38px;
  border:none;
  border-radius:10px;
  cursor:pointer;
  font-weight:900;
  transition:0.15s;
}

.btn:hover{
  transform:scale(1.05);
}

.add{
  background:linear-gradient(180deg,var(--accent),var(--accent-2));
  color:black;
  box-shadow:0 0 18px rgba(0,229,255,0.3);
}

.remove{
  background:rgba(255,255,255,0.05);
  color:#ff5d5d;
}

.count{
  min-width:40px;
  text-align:center;
  font-weight:700;
}

.summary{
  background:rgba(255,255,255,0.03);
  border-radius:14px;
  padding:18px;
  border:1px solid rgba(255,255,255,0.04);
  height:fit-content;
  position:sticky;
  top:20px;
}

.totalLabel{
  color:var(--muted);
}

.totalValue{
  font-size:2rem;
  font-weight:900;
  color:var(--accent);
  margin-top:10px;
  text-shadow:0 0 20px rgba(0,229,255,0.4);
}

.actionBtn{
  width:100%;
  margin-top:12px;
  padding:14px;
  border:none;
  border-radius:12px;
  cursor:pointer;
  font-weight:700;
  transition:0.2s;
}

.checkout{
  background:linear-gradient(90deg,var(--accent),var(--accent-2));
  color:black;
}

.checkout:hover{
  transform:translateY(-2px);
  box-shadow:0 0 25px rgba(0,229,255,0.35);
}

.clear{
  background:rgba(255,255,255,0.05);
  color:white;
}

#wybrane-czesci{
  margin-top:22px;
  padding:18px;
  border-radius:12px;
  background:#03151a;
  border:2px solid var(--accent);
}

#wybrane-czesci h3{
  text-align:center;
  color:var(--accent);
}

#lista-wybranych{
  background:#081d24;
  padding:12px;
  border-radius:10px;
  border:1px solid rgba(0,229,255,0.25);
  color:white;
  min-height:120px;
  white-space:pre-wrap;
}

#kopiuj-liste-btn{
  width:100%;
  margin-top:14px;
  padding:14px;
  border:none;
  border-radius:10px;
  background:linear-gradient(90deg,var(--accent),var(--accent-2));
  color:black;
  font-weight:900;
  cursor:pointer;
  transition:0.2s;
}

#kopiuj-liste-btn:hover{
  transform:translateY(-2px);
  box-shadow:0 0 20px rgba(0,229,255,0.35);
}

canvas{
  position:fixed;
  inset:0;
  z-index:-1;
}
</style>
</head>

<body>

<canvas id="bgCanvas"></canvas>

<div class="app">

<header>
  <div>
    <h1>Kalkulator Benny's</h1>
    <div class="lead">CYAN EDITION</div>
  </div>

  <div class="logo">
    B
  </div>
</header>

<div class="tabs">
  <div class="tab active">Wszystkie</div>
  <div class="tab">Naprawy</div>
  <div class="tab">Lakierowanie</div>
  <div class="tab">Neony</div>
  <div class="tab">Karoseria</div>
</div>

<div class="grid">

<div class="list">

<div class="service">
  <div>
    <div class="title">Naprawa silnika</div>
    <div class="price">15 000 $</div>
  </div>

  <div class="controls">
    <button class="btn remove">−</button>
    <div class="count">0</div>
    <button class="btn add">+</button>
  </div>
</div>

<div class="service">
  <div>
    <div class="title">Pełna naprawa</div>
    <div class="price">20 000 $</div>
  </div>

  <div class="controls">
    <button class="btn remove">−</button>
    <div class="count">0</div>
    <button class="btn add">+</button>
  </div>
</div>

<div class="service">
  <div>
    <div class="title">Kolor główny</div>
    <div class="price">25 000 $</div>
  </div>

  <div class="controls">
    <button class="btn remove">−</button>
    <div class="count">0</div>
    <button class="btn add">+</button>
  </div>
</div>

</div>

<aside class="summary">

<div class="totalLabel">
Kwota całkowita
</div>

<div class="totalValue">
0 $
</div>

<button class="actionBtn checkout">
Kopiuj podsumowanie
</button>

<button class="actionBtn clear">
Wyczyść
</button>

<div id="wybrane-czesci">

<h3>Twoje podsumowanie</h3>

<pre id="lista-wybranych">
Nic nie wybrano jeszcze.
</pre>

<button id="kopiuj-liste-btn">
Kopiuj podsumowanie
</button>

</div>

</aside>

</div>

</div>

<script>
const canvas = document.getElementById('bgCanvas');
const ctx = canvas.getContext('2d');

let w = canvas.width = innerWidth;
let h = canvas.height = innerHeight;

window.addEventListener('resize',()=>{
  w = canvas.width = innerWidth;
  h = canvas.height = innerHeight;
});

const particles = [];

for(let i=0;i<70;i++){
  particles.push({
    x:Math.random()*w,
    y:Math.random()*h,
    r:Math.random()*2+1,
    vx:(Math.random()-0.5)*0.5,
    vy:(Math.random()-0.5)*0.5,
    hue:180+Math.random()*30
  });
}

function animate(){

  ctx.clearRect(0,0,w,h);

  particles.forEach(p=>{

    p.x += p.vx;
    p.y += p.vy;

    if(p.x<0||p.x>w) p.vx*=-1;
    if(p.y<0||p.y>h) p.vy*=-1;

    ctx.beginPath();
    ctx.fillStyle = `hsla(${p.hue},100%,60%,0.7)`;
    ctx.shadowBlur = 20;
    ctx.shadowColor = `hsla(${p.hue},100%,60%,0.7)`;
    ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
    ctx.fill();

  });

  requestAnimationFrame(animate);
}

animate();
</script>

</body>
</html>
