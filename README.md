# songam
sóng truyền trong âm thanh 
from pathlib import Path

html = r'''<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NTT | Sóng truyền trong âm thanh</title>
<style>
:root{--bg:#08111f;--panel:#101e32;--panel2:#14243b;--text:#edf5ff;--muted:#a8bad0;--cyan:#58d7e8;--blue:#648bff;--line:rgba(160,190,225,.16)}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;background:radial-gradient(circle at 80% 5%,#18375b 0,transparent 32%),linear-gradient(180deg,#08111f,#0b1627 55%,#08111f);color:var(--text);font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",sans-serif;line-height:1.65}
header{position:sticky;top:0;z-index:10;background:rgba(8,17,31,.78);backdrop-filter:blur(16px);border-bottom:1px solid var(--line)}
.nav{max-width:1120px;margin:auto;padding:14px 22px;display:flex;align-items:center;justify-content:space-between}.brand{font-weight:850;letter-spacing:.14em;font-size:1.2rem}.brand span{color:var(--cyan)}nav{display:flex;gap:22px}nav a{color:var(--muted);text-decoration:none;font-size:.92rem}nav a:hover{color:white}
main{max-width:1120px;margin:auto;padding:0 22px}.hero{padding:78px 0 48px;display:grid;grid-template-columns:1.05fr .95fr;gap:34px;align-items:center}.eyebrow{color:var(--cyan);font-size:.78rem;font-weight:800;letter-spacing:.18em;text-transform:uppercase}.hero h1{font-size:clamp(2.4rem,5vw,4.7rem);line-height:1.06;letter-spacing:-.045em;margin:14px 0 20px}.hero h1 em{font-style:normal;background:linear-gradient(90deg,var(--cyan),#91aaff);-webkit-background-clip:text;background-clip:text;color:transparent}.lead{color:var(--muted);font-size:1.08rem;max-width:600px}.actions{display:flex;gap:12px;margin-top:28px;flex-wrap:wrap}.btn{border:1px solid var(--line);border-radius:12px;padding:11px 17px;color:var(--text);text-decoration:none;font-weight:700;background:var(--panel2);transition:.25s}.btn.primary{background:linear-gradient(100deg,#1aaec4,#526fe5);border:0}.btn:hover{transform:translateY(-3px);box-shadow:0 12px 30px #0005}
.visual{background:linear-gradient(145deg,rgba(31,65,100,.8),rgba(13,27,46,.9));border:1px solid var(--line);border-radius:24px;padding:20px;box-shadow:0 25px 70px #0005;overflow:hidden}.visual-top{display:flex;justify-content:space-between;color:var(--muted);font-size:.82rem}.live{color:#80edc2}.wave{width:100%;height:230px;display:block;margin-top:12px}.wave path{fill:none;stroke:url(#grad);stroke-width:3;stroke-linecap:round;filter:drop-shadow(0 0 7px #58d7e8)}.wave .axis{stroke:#8196b4;stroke-width:1;opacity:.35;filter:none}.wave .wave2{stroke:#829bff;opacity:.45;stroke-width:1.6;filter:none}.pulse{animation:pulse 2.8s ease-in-out infinite}@keyframes pulse{50%{opacity:.45}}.visual-foot{display:flex;gap:18px;color:var(--muted);font-size:.8rem}.dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:var(--cyan);margin-right:7px}
section{padding:44px 0}.section-head{margin-bottom:22px}.section-head h2{font-size:clamp(1.7rem,3vw,2.4rem);margin:5px 0}.section-head p{color:var(--muted);margin:0}.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}.card{background:linear-gradient(145deg,rgba(20,36,59,.95),rgba(12,25,43,.95));border:1px solid var(--line);border-radius:18px;padding:22px;transition:transform .25s,border-color .25s}.card:hover{transform:translateY(-5px);border-color:#58d7e866}.icon{width:42px;height:42px;border-radius:12px;background:#58d7e81c;display:grid;place-items:center;color:var(--cyan);font-size:1.25rem;margin-bottom:14px}.card h3{margin:0 0 8px}.card p{color:var(--muted);margin:0;font-size:.95rem}
.simulator{display:grid;grid-template-columns:1fr 280px;gap:18px}.sim-box,.control-box{background:var(--panel);border:1px solid var(--line);border-radius:20px;padding:20px}.sim-box canvas{width:100%;height:250px;display:block}.control-box label{display:flex;justify-content:space-between;font-size:.9rem;margin:14px 0 7px}.control-box input{width:100%;accent-color:var(--cyan)}.value{color:var(--cyan);font-variant-numeric:tabular-nums}.note{font-size:.82rem;color:var(--muted);margin-top:15px}.equation{font-size:1.5rem;text-align:center;padding:18px;background:#071321;border:1px solid var(--line);border-radius:14px;margin-top:15px;color:#9eeaf2}.compare{display:grid;grid-template-columns:1fr 1fr;gap:16px}.compare .card{min-height:170px}.tag{display:inline-block;color:var(--cyan);background:#58d7e817;padding:3px 9px;border-radius:30px;font-size:.75rem;font-weight:800;margin-bottom:10px}
footer{border-top:1px solid var(--line);padding:28px 22px;text-align:center;color:var(--muted);font-size:.85rem}.reveal{opacity:0;transform:translateY(18px);transition:opacity .7s ease,transform .7s ease}.reveal.show{opacity:1;transform:none}
@media(max-width:800px){.hero{grid-template-columns:1fr;padding-top:52px}.grid{grid-template-columns:1fr}.simulator{grid-template-columns:1fr}nav{gap:12px}nav a{font-size:.8rem}.compare{grid-template-columns:1fr}}
@media(max-width:480px){.nav{padding:12px 16px}nav a:nth-child(2){display:none}main{padding:0 16px}.hero{padding-top:42px}.visual{padding:14px}.wave{height:190px}}
</style>
</head>
<body>
<header><div class="nav"><div class="brand">N<span>TT</span>.</div><nav><a href="#kienthuc">Kiến thức</a><a href="#mophong">Mô phỏng</a><a href="#ungdung">Ứng dụng</a></nav></div></header>
<main>
<section class="hero">
 <div><div class="eyebrow">Vật lý · Sóng cơ · Âm học</div><h1>Sóng truyền trong <em>âm thanh</em></h1><p class="lead">Âm thanh không tự di chuyển như một vật thể. Nó lan truyền nhờ dao động của các phần tử môi trường, mang năng lượng từ nguồn âm đến tai người nghe.</p><div class="actions"><a class="btn primary" href="#mophong">Khám phá mô phỏng ↓</a><a class="btn" href="#kienthuc">Tìm hiểu lý thuyết</a></div></div>
 <div class="visual"><div class="visual-top"><span>MINH HỌA SÓNG ÂM</span><span class="live">● ĐANG LAN TRUYỀN</span></div><svg class="wave" viewBox="0 0 600 230" preserveAspectRatio="none" aria-label="Đường sóng âm minh họa"><defs><linearGradient id="grad"><stop stop-color="#58d7e8"/><stop offset="1" stop-color="#829bff"/></linearGradient></defs><path class="axis" d="M0 115H600"/><path class="wave2 pulse" d="M0 115 Q30 65 60 115 T120 115 T180 115 T240 115 T300 115 T360 115 T420 115 T480 115 T540 115 T600 115"/><path id="heroWave" d=""/></svg><div class="visual-foot"><span><i class="dot"></i>Dao động tuần hoàn</span><span>→ Hướng truyền sóng</span></div></div>
</section>
<section id="kienthuc" class="reveal"><div class="section-head"><div class="eyebrow">01 / Nền tảng</div><h2>Âm thanh được truyền như thế nào?</h2><p>Hiểu bản chất của sóng âm qua ba ý chính.</p></div><div class="grid">
 <article class="card"><div class="icon">〰</div><h3>1. Nguồn âm dao động</h3><p>Khi một vật dao động, nó làm các phần tử môi trường xung quanh dao động theo, tạo ra những vùng nén và giãn liên tiếp.</p></article>
 <article class="card"><div class="icon">⇢</div><h3>2. Sóng lan truyền</h3><p>Sự biến đổi áp suất và dao động được truyền từ phần tử này sang phần tử khác. Các phần tử chỉ dao động quanh vị trí cân bằng.</p></article>
 <article class="card"><div class="icon">耳</div><h3>3. Tai tiếp nhận âm</h3><p>Khi sóng âm đến tai, nó làm màng nhĩ dao động. Não bộ xử lý tín hiệu để ta cảm nhận được âm thanh.</p></article>
 </div></section>
<section id="mophong" class="reveal"><div class="section-head"><div class="eyebrow">02 / Tương tác</div><h2>Phòng thí nghiệm sóng âm</h2><p>Thay đổi tần số và biên độ để quan sát dạng sóng thay đổi.</p></div>
 <div class="simulator"><div class="sim-box"><canvas id="waveCanvas" width="900" height="300"></canvas><div class="equation">v = λ · f</div><p class="note">Trong cùng một môi trường, tốc độ truyền âm gần như không đổi; khi tần số tăng thì bước sóng giảm.</p></div>
 <div class="control-box"><h3>Điều chỉnh sóng</h3><label for="freq">Tần số <span class="value" id="freqVal">4 Hz</span></label><input id="freq" type="range" min="1" max="10" value="4"><label for="amp">Biên độ <span class="value" id="ampVal">60%</span></label><input id="amp" type="range" min="15" max="100" value="60"><label for="speed">Tốc độ hoạt ảnh <span class="value" id="speedVal">1×</span></label><input id="speed" type="range" min="1" max="5" value="1"><p class="note">Đây là mô phỏng trực quan dạng sóng, không phát ra âm thanh thật và không mô phỏng chính xác mọi đặc tính của không khí.</p></div></div>
</section>
<section class="reveal"><div class="section-head"><div class="eyebrow">03 / Ghi nhớ</div><h2>Đặc điểm quan trọng của sóng âm</h2></div><div class="compare">
 <article class="card"><span class="tag">BẢN CHẤT</span><h3>Sóng âm là sóng cơ</h3><p>Sóng âm cần môi trường vật chất để truyền, chẳng hạn chất khí, chất lỏng hoặc chất rắn. Âm không truyền được trong chân không.</p></article>
 <article class="card"><span class="tag">TRONG KHÔNG KHÍ</span><h3>Sóng dọc</h3><p>Các phần tử không khí dao động theo phương trùng với phương truyền sóng, tạo nên các vùng nén và vùng giãn.</p></article>
 </div></section>
<section id="ungdung" class="reveal"><div class="section-head"><div class="eyebrow">04 / Liên hệ thực tế</div><h2>Sóng âm quanh ta</h2></div><div class="grid">
 <article class="card"><div class="icon">🎧</div><h3>Tai nghe</h3><p>Màng loa rung tạo ra biến thiên áp suất trong không khí, truyền đến tai người nghe.</p></article>
 <article class="card"><div class="icon">🩺</div><h3>Siêu âm</h3><p>Sóng âm tần số cao được dùng trong y học để tạo ảnh bên trong cơ thể.</p></article>
 <article class="card"><div class="icon">🏛</div><h3>Cách âm</h3><p>Vật liệu cách âm giúp hấp thụ hoặc cản bớt năng lượng âm truyền qua không gian.</p></article>
 </div></section>
</main>
<footer>NTT · Góc học tập Vật lý <br>Khám phá thế giới dao động và sóng âm</footer>
<script>
const hero=document.getElementById('heroWave');let ht=0;
function drawHero(){let d='',w=600;for(let x=0;x<=w;x+=3){let y=115-34*Math.sin(x*.055-ht);d+=(x?'L':'M')+x+' '+y+' '}hero.setAttribute('d',d);ht+=.035;requestAnimationFrame(drawHero)}drawHero();
const canvas=document.getElementById('waveCanvas'),ctx=canvas.getContext('2d');
const freq=document.getElementById('freq'),amp=document.getElementById('amp'),speed=document.getElementById('speed');
let t=0;
function render(){const w=canvas.width,h=canvas.height;ctx.clearRect(0,0,w,h);ctx.strokeStyle='rgba(155,180,210,.16)';ctx.lineWidth=1;for(let x=0;x<w;x+=75){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,h);ctx.stroke()}for(let y=0;y<h;y+=50){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(w,y);ctx.stroke()}
ctx.beginPath();ctx.strokeStyle='#58d7e8';ctx.lineWidth=4;ctx.shadowColor='#58d7e8';ctx.shadowBlur=12;let f=Number(freq.value),a=Number(amp.value)*1.05;for(let x=0;x<=w;x+=2){let y=h/2-a*Math.sin((x/w)*f*Math.PI*2-t);if(x===0)ctx.moveTo(x,y);else ctx.lineTo(x,y)}ctx.stroke();ctx.shadowBlur=0;
ctx.fillStyle='#a8bad0';ctx.font='18px system-ui';ctx.fillText('Biên độ',14,24);ctx.fillText('Phương truyền sóng →',w-220,h-14);
t+=.035*Number(speed.value);requestAnimationFrame(render)}
[freq,amp,speed].forEach(el=>el.addEventListener('input',()=>{document.getElementById('freqVal').textContent=freq.value+' Hz';document.getElementById('ampVal').textContent=amp.value+'%';document.getElementById('speedVal').textContent=speed.value+'×'}));render();
const observer=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('show');observer.unobserve(e.target)}}),{threshold:.12});document.querySelectorAll('.reveal').forEach(el=>observer.observe(el));
</script>
</body></html>'''
path = Path("/mnt/data/ntt_song_am.html")
path.write_text(html, encoding="utf-8")
print(path, path.stat().st_size)
