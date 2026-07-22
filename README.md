
<html lang="pl"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Bar Sajgon - Kalkulator Zestawów</title>
<style>
body{margin:0;font-family:Arial;background:#111;color:#fff;display:flex;justify-content:center;align-items:center;height:100vh}
.box{background:#1b1b1b;padding:30px;border-radius:16px;box-shadow:0 0 20px #000;width:360px;text-align:center}
button{font-size:24px;width:50px;height:50px}
.count{display:inline-block;width:80px;font-size:32px}
.total{font-size:36px;color:#00d4ff;margin:20px 0}
.actions button{width:auto;padding:10px 20px;font-size:16px;margin:5px}
</style></head><body>
<div class="box">
<h1>🍜 Bar Sajgon</h1>
<p>Cena za zestaw: <b>15 000$</b></p>
<div><button onclick="chg(-1)">-</button><span class="count" id="c">0</span><button onclick="chg(1)">+</button></div>
<p>Lub wpisz liczbę zestawów:</p>
<input id="inp" type="number" min="0" value="0" style="width:120px;padding:8px;font-size:18px;text-align:center" oninput="setCount()">
<div class="total" id="t">0 $</div>
<div id="s">Wybrano: 0 zestawów</div>
<div class="actions">
<button onclick="reset()">Wyczyść</button>
<button onclick="copySum()">Kopiuj</button>
</div>
</div>
<script>
let n=0;
function upd(){inp.value=n;c.textContent=n;t.textContent=(n*15000).toLocaleString('pl-PL')+' $';s.textContent='Wybrano: '+n+' zestawów';}
function chg(x){n=Math.max(0,n+x);upd();}
function setCount(){n=Math.max(0,parseInt(inp.value)||0);upd();}
function reset(){n=0;inp.value=0;upd();}
function copySum(){navigator.clipboard.writeText('Bar Sajgon\nZestawy: '+n+'\nSuma: '+(n*15000).toLocaleString('pl-PL')+' $');alert('Skopiowano!');}
upd();
</script></body></html>
