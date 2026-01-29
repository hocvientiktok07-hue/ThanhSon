<!DOCTYPE html>
<html lang="vi">
<head>
<!-- iOS App Icon -->
<head>
<meta charset="UTF-8">

<link rel="apple-touch-icon" sizes="180x180" href="apple-touch-icon.png">

<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Thanh Son iOS">

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Thanh Son iOS</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
*{box-sizing:border-box;font-family:Arial}
body{
  margin:0;height:100vh;
  background:radial-gradient(circle at top,#1b2a3a,#05080d);
  display:flex;justify-content:center;align-items:center
}
.container{width:360px}
.card{
  position:relative;background:#0f1722;color:#fff;
  border-radius:20px;padding:25px;
  box-shadow:0 0 25px rgba(0,255,255,.4);
  overflow:hidden
}

/* chú ý: canvas sẽ nằm trên nội dung (để tuyết rơi thấy rõ),
   nhưng pointer-events: none để không chặn tương tác */
#snow,#lightning{position:absolute;top:0;left:0;z-index:4;pointer-events:none}
.card>*:not(canvas):not(.crosshair){position:relative;z-index:2}

#title{text-align:center;font-size:32px;color:#00ffff;text-shadow:0 0 5px #0ff,0 0 20px #09f}
.status{text-align:center;font-weight:bold}
.status.inactive{color:orange}
.status.active{color:#00ff88}

.key-box{display:flex;gap:10px;margin:10px 0}
.key-box input{flex:1;padding:10px;border-radius:8px;border:none}
.key-box button{padding:10px;border:none;border-radius:8px;background:#00e676;font-weight:bold;cursor:pointer}

.expire{text-align:center;color:#00ff88;font-size:14px}
.notify{text-align:center;height:22px;font-weight:bold}

.game-select{display:flex;gap:10px;margin:10px 0}
.game-btn{flex:1;padding:10px;border-radius:10px;background:#222;color:#fff;border:none;cursor:pointer}
.game-btn.active{background:#ff5722;color:#000}

.feature .item{
  display:flex;justify-content:space-between;
  align-items:center;padding:12px;
  background:#151d29;border-radius:12px;margin-bottom:8px
}
.locked .item{opacity:.4}

.switch{position:relative;width:52px;height:28px}
.switch input{opacity:0}
.slider{position:absolute;inset:0;border-radius:28px;background:#555}
.slider:before{
  content:"";position:absolute;width:22px;height:22px;left:3px;top:3px;
  background:#ccc;border-radius:50%;transition:.3s
}
.switch input:checked+.slider{
  background:linear-gradient(135deg,#00ff88,#00c853);
  box-shadow:0 0 10px rgba(0,255,136,.8)
}
.switch input:checked+.slider:before{transform:translateX(24px);background:#fff}

/* crosshair phải nằm trên canvas nên z-index cao hơn */
.crosshair{
  position:absolute;top:50%;left:50%;
  width:36px;height:36px;border:2px solid #0ff;
  border-radius:50%;transform:translate(-50%,-50%);
  display:none;pointer-events:none;z-index:6;
  box-shadow:0 0 8px #0ff,inset 0 0 6px #0ff
}
.crosshair:before,.crosshair:after{content:"";position:absolute;background:#0ff}
.crosshair:before{width:2px;height:18px;left:50%;top:50%;transform:translate(-50%,-50%)}
.crosshair:after{height:2px;width:18px;left:50%;top:50%;transform:translate(-50%,-50%)}
</style>
</head>

<body>
<div class="container">
  <div class="card" id="card">
    <!-- canvas tuyết và sấm sét -->
    <canvas id="snow"></canvas>
    <canvas id="lightning"></canvas>

    <div id="crosshair" class="crosshair"></div>

    <h1 id="title">Thanh Son iOS</h1>
    <p id="status" class="status inactive">Chưa kích hoạt</p>

    <div class="key-box">
      <input id="keyInput" placeholder="Nhập key...">
      <button onclick="checkKey()">Xác nhận</button>
    </div>

    <p id="expireText" class="expire"></p>
    <p id="notify" class="notify"></p>

    <div class="game-select">
      <button class="game-btn active" id="btnNormal" onclick="selectGame('normal')">Free Fire Thường</button>
      <button class="game-btn" id="btnMax" onclick="selectGame('max')">Free Fire Max</button>
    </div>

    <div class="feature locked" id="features">
      <div class="item"><span>🔒 AIMLOCK</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'AIMLOCK')"><span class="slider"></span></label></div>
      <div class="item"><span>✔ EXACTLY++</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'EXACTLY++')"><span class="slider"></span></label></div>
      <div class="item"><span>⚡ OPTIMIZE</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'OPTIMIZE')"><span class="slider"></span></label></div>
      <div class="item"><span>➕ SENSITIVITY PRO</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'SENSITIVITY PRO')"><span class="slider"></span></label></div>
      <div class="item"><span>⚙ LEGIT PRO</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'LEGIT PRO')"><span class="slider"></span></label></div>
      <div class="item"><span>🎯 TÂM ẢO</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'TÂM ẢO')"><span class="slider"></span></label></div>
    </div>
  </div>
</div>

<script>
/* ===== giữ nguyên logic key + UI như bạn yêu cầu ===== */
const STORAGE="TSIOS_KEY_DATA";
const deviceId=btoa(navigator.userAgent+screen.width+screen.height);
let timer=null;

function notify(t,c="#0ff"){
  const n=document.getElementById("notify");
  n.textContent=t; n.style.color=c;
  setTimeout(()=>n.textContent="",2500)
}

function unlock(){
  document.getElementById("status").textContent="Đã kích hoạt";
  document.getElementById("status").className="status active";
  document.getElementById("features").classList.remove("locked");
  document.querySelectorAll("#features input").forEach(i=>i.disabled=false)
}

function lock(){
  localStorage.removeItem(STORAGE);
  clearInterval(timer);
  document.getElementById("status").textContent="Hết hạn";
  document.getElementById("status").className="status inactive";
  document.getElementById("features").classList.add("locked");
  document.querySelectorAll("#features input").forEach(i=>{ i.checked=false; i.disabled=true });
  document.getElementById("crosshair").style.display="none";
  notify("Key đã hết hạn","#f44336")
}

function startTimer(exp){
  clearInterval(timer);
  timer=setInterval(()=>{
    const left=exp-Date.now();
    if(left<=0) return lock();
    const h=Math.floor(left/3600000);
    const m=Math.floor(left%3600000/60000);
    const s=Math.floor(left%60000/1000);
    document.getElementById("expireText").textContent=`Còn lại: ${h}h ${m}m ${s}s`;
  },1000)
}

function checkKey(){
  const key=document.getElementById("keyInput").value.trim();
  if(!key.startsWith("THANHSONIOS-")) return notify("Key không hợp lệ","#ff9800");
  const days=parseInt(key.split("-")[1]);
  if(isNaN(days)) return notify("Sai định dạng key","#ff9800");
  const exp=Date.now()+days*86400000;
  localStorage.setItem(STORAGE,JSON.stringify({key,exp,deviceId}));
  unlock(); startTimer(exp);
  notify("Kích hoạt thành công","#00ff88")
}

function toggleFeature(cb,name){
  if(name==="TÂM ẢO") document.getElementById("crosshair").style.display=cb.checked?"block":"none";
  notify((cb.checked?"Bật ":"Tắt ")+name, cb.checked?"#00ff88":"#ff9800")
}

function selectGame(g){
  const btnNormal=document.getElementById("btnNormal");
  const btnMax=document.getElementById("btnMax");
  btnNormal.classList.remove("active");
  btnMax.classList.remove("active");
  (g==="normal"?btnNormal:btnMax).classList.add("active");
  notify("Đã chọn "+(g==="normal"?"Free Fire Thường":"Free Fire Max"),"#00ff88")
}

window.onload=()=>{
  const d=JSON.parse(localStorage.getItem(STORAGE)||"null");
  if(d && d.deviceId===deviceId && d.exp>Date.now()){
    unlock(); startTimer(d.exp)
  }
}

/* ===== TUYẾT RƠI (CẢI TIẾN) =====
   - canvas sẽ cover toàn bộ .card area (dynamic)
   - pointer-events:none nên vẫn click được bình thường
   - ResizeObserver để chiều cao/chiều rộng tự cập nhật khi layout thay đổi
*/

const card = document.getElementById('card');
const snow = document.getElementById('snow');
const lightning = document.getElementById('lightning');
const sx = snow.getContext('2d');
const lx = lightning.getContext('2d');

let flakes = [];
let FL_COUNT = 260; // tăng để dày đặc hơn
let snowW = 360, snowH = 520;

function resizeCanvases(){
  // lấy kích thước thực của .card
  const rect = card.getBoundingClientRect();
  const w = Math.max(200, Math.floor(rect.width)); // đảm bảo min width
  const h = Math.max(200, Math.floor(rect.height)); // đảm bảo min height
  // set kích thước canvas theo card
  snowW = w; snowH = h;
  snow.width = w; snow.height = h;
  lightning.width = w; lightning.height = h;
  // nếu flakes rỗng hoặc kích thước thay đổi lớn thì recreate
  initFlakes();
}

// tạo mảng flakes
function initFlakes(){
  flakes = [];
  for(let i=0;i<FL_COUNT;i++){
    flakes.push({
      x: Math.random()*snowW,
      y: Math.random()*snowH,
      r: Math.random()*3 + 1,
      v: Math.random()*1.8 + 0.6,
      sway: (Math.random()*0.6) + 0.2,
      phase: Math.random()*Math.PI*2
    });
  }
}

// vẽ tuyết
function drawSnow(){
  sx.clearRect(0,0,snowW,snowH);
  // tô nhẹ nền (không che nội dung vì pointer-events:none)
  for(let f of flakes){
    f.phase += 0.01 + f.sway*0.003;
    f.x += Math.sin(f.phase) * f.sway; // drift
    f.y += f.v;
    // khi vượt ra ngoài đáy thì cho rơi lại ở top (để full rơi xuyên suốt)
    if(f.y > snowH + 10){
      f.y = -10;
      f.x = Math.random()*snowW;
      f.v = Math.random()*1.8 + 0.6;
      f.r = Math.random()*3 + 1;
      f.sway = (Math.random()*0.6) + 0.2;
      f.phase = Math.random()*Math.PI*2;
    }
    // vẽ
    sx.beginPath();
    sx.arc(f.x, f.y, f.r, 0, Math.PI*2);
    // làm nhiều mức alpha để cảm giác gần/xa
    const alpha = 0.6 - (f.r-1)/6;
    sx.fillStyle = `rgba(255,255,255,${alpha})`;
    sx.fill();
  }
  requestAnimationFrame(drawSnow);
}

/* ===== SẤM SÉT (giữ như trước nhưng tính theo kích thước mới) ===== */
function lightningPulse(){
  if(Math.random() < 0.6) return; // tỉ lệ sấm
  lx.fillStyle = "rgba(255,255,255,0.12)";
  lx.fillRect(0,0,snowW,snowH);
  lx.beginPath();
  let x = snowW/2, y = 0;
  lx.moveTo(x,y);
  const seg = Math.max(6, Math.floor(snowH/60));
  for(let i=0;i<seg;i++){
    x += (Math.random()*40 - 20);
    y += (Math.random()*40 + Math.max(10, snowH/seg));
    lx.lineTo(x, Math.min(y, snowH));
  }
  lx.strokeStyle = "#9ff";
  lx.lineWidth = 2;
  lx.stroke();
  setTimeout(()=>lx.clearRect(0,0,snowW,snowH),120);
}

// ResizeObserver để cập nhật canvas khi card thay đổi (ví dụ thay đổi nội dung)
if (window.ResizeObserver) {
  const ro = new ResizeObserver(() => {
    resizeCanvases();
  });
  ro.observe(card);
} else {
  window.addEventListener('resize', resizeCanvases);
}

// khởi tạo
resizeCanvases();
drawSnow();
setInterval(lightningPulse, 2500);

</script>
</body>
</html>
