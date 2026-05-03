
<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Space+Mono:wght@400;700&display=swap');
*{box-sizing:border-box;margin:0;padding:0;}

.wrap{background:#0d1117;color:#c9d1d9;font-family:'Fira Code',monospace;position:relative;overflow:hidden;}

/* ── Full-page particle canvas ── */
#bgcanvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;}

.content{position:relative;z-index:1;}

/* ── Header with its own particle canvas ── */
.header-wrap{position:relative;overflow:hidden;padding:36px 20px 44px;text-align:center;}
#hcanvas{position:absolute;top:0;left:0;width:100%;height:100%;z-index:0;}
.header-inner{position:relative;z-index:1;}
.header-wrap::after{content:'';position:absolute;bottom:-1px;left:0;right:0;height:30px;background:#0d1117;clip-path:ellipse(55% 100% at 50% 100%);z-index:2;}

.wave-top h1{font-size:30px;font-weight:700;color:#fff;letter-spacing:1px;animation:fsd .8s ease both;text-shadow:0 0 30px rgba(167,139,250,.6);}
.wave-top p{font-size:13px;color:#c4b5fd;margin-top:6px;animation:fsd .8s .2s ease both;opacity:0;}
@keyframes fsd{from{opacity:0;transform:translateY(-14px)}to{opacity:1;transform:translateY(0)}}

.typing-line{text-align:center;padding:14px 16px 4px;font-size:12px;color:#a78bfa;min-height:32px;}
.cursor{display:inline-block;width:2px;height:1em;background:#a78bfa;vertical-align:middle;margin-left:2px;animation:blink .8s step-end infinite;}
@keyframes blink{50%{opacity:0}}

.sec{padding:14px 16px 0;}
.sec-title{font-size:12px;font-weight:600;color:#e2e8f0;margin-bottom:10px;display:flex;align-items:center;gap:8px;}
.sec-title::after{content:'';flex:1;height:1px;background:linear-gradient(to right,#302b63,transparent);}

.code-block{background:rgba(22,27,34,.88);border:1px solid #30363d;border-radius:8px;padding:12px 14px;font-size:10px;line-height:1.85;animation:fi .6s .4s ease both;opacity:0;backdrop-filter:blur(6px);}
@keyframes fi{to{opacity:1}}
.kw{color:#ff7b72}.str{color:#a5d6ff}.key{color:#79c0ff}.em{color:#ffa657}

.stack-group{margin-bottom:14px;}
.stack-label{font-size:10px;color:#6e7681;text-transform:uppercase;letter-spacing:.6px;margin-bottom:8px;}
.icons-row{display:flex;flex-wrap:wrap;gap:10px;align-items:flex-start;}
.icon-item{display:flex;flex-direction:column;align-items:center;gap:4px;animation:popIn .35s ease both;cursor:default;width:48px;}
.icon-item:hover .icon-box{transform:translateY(-3px);box-shadow:0 6px 18px rgba(167,139,250,.4);border-color:#a78bfa;}
.icon-box{width:38px;height:38px;border-radius:8px;border:1px solid #30363d;background:rgba(22,27,34,.85);display:flex;align-items:center;justify-content:center;transition:transform .2s,box-shadow .2s,border-color .2s;backdrop-filter:blur(4px);}
.icon-box img{width:24px;height:24px;object-fit:contain;}
.icon-label{font-size:8.5px;color:#6e7681;text-align:center;line-height:1.2;word-break:break-word;}
@keyframes popIn{from{opacity:0;transform:scale(.8)}to{opacity:1;transform:scale(1)}}

.stats-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:8px;}
.stat-card{background:rgba(22,27,34,.85);border:1px solid #30363d;border-radius:8px;padding:12px;animation:fi .6s .5s ease both;opacity:0;backdrop-filter:blur(4px);}
.stat-label{font-size:9px;color:#8b949e;text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px;}
.stat-val{font-size:20px;font-weight:700;color:#a78bfa;font-family:'Space Mono',monospace;}
.stat-sub{font-size:9px;color:#6e7681;margin-top:2px;}

.streak-row{display:flex;gap:8px;margin-bottom:10px;}
.streak-box{flex:1;background:rgba(22,27,34,.85);border:1px solid #30363d;border-radius:8px;padding:10px;text-align:center;animation:fi .6s .6s ease both;opacity:0;backdrop-filter:blur(4px);}
.streak-num{font-size:18px;font-weight:700;font-family:'Space Mono',monospace;}
.streak-lbl{font-size:8px;color:#8b949e;text-transform:uppercase;letter-spacing:.5px;margin-top:2px;}

.bar-row{display:flex;align-items:center;gap:8px;margin-bottom:7px;font-size:10px;}
.bar-lang{width:68px;color:#8b949e;text-align:right;flex-shrink:0;}
.bar-track{flex:1;height:5px;background:#21262d;border-radius:3px;overflow:hidden;}
.bar-fill{height:100%;border-radius:3px;width:0;transition:width 1.4s cubic-bezier(.4,0,.2,1);}
.bar-pct{width:28px;color:#e2e8f0;font-size:9px;}

.act-grid{display:grid;grid-template-columns:repeat(26,1fr);gap:2px;margin:6px 0;}
.act-cell{aspect-ratio:1;border-radius:2px;}

.cert-table{width:100%;font-size:10.5px;border-collapse:collapse;}
.cert-table td{padding:6px 8px;border-bottom:1px solid #21262d;color:#c9d1d9;}
.cert-table td:first-child{color:#a78bfa;width:50%;}

.connect-row{display:flex;gap:8px;flex-wrap:wrap;padding:12px 16px 0;}
.cbtn{display:inline-flex;align-items:center;gap:6px;padding:7px 13px;border-radius:6px;font-size:11px;font-weight:500;cursor:pointer;transition:opacity .2s,transform .2s;border:none;font-family:inherit;}
.cbtn:hover{opacity:.85;transform:translateY(-1px);}
.btn-web{background:#302b63;color:#c4b5fd;}
.btn-li{background:#0077B5;color:#fff;}
.btn-gh{background:#21262d;color:#e2e8f0;border:1px solid #30363d;}

/* ── Footer with own particle canvas ── */
.footer-wrap{position:relative;overflow:hidden;height:60px;margin-top:16px;}
#fcanvas{position:absolute;top:0;left:0;width:100%;height:100%;}
.footer-clip{position:absolute;top:0;left:0;right:0;height:100%;clip-path:ellipse(55% 100% at 50% 100%);}
</style>

<canvas id="bgcanvas"></canvas>

<div class="wrap">
  <div class="content">

    <!-- HEADER -->
    <div class="header-wrap wave-top">
      <canvas id="hcanvas"></canvas>
      <div class="header-inner">
        <h1>Gauransh Singh</h1>
        <p>Data Analyst &nbsp;|&nbsp; AI/ML Engineer</p>
      </div>
    </div>

    <div class="typing-line"><span id="typed"></span><span class="cursor"></span></div>

    <div class="sec">
      <div class="sec-title">🧬 about me</div>
      <div class="code-block">
        <span class="kw">const</span> <span class="em">garv</span> = {<br>
        &nbsp;&nbsp;<span class="key">"name"</span>: <span class="str">"Gauransh Singh"</span>,<br>
        &nbsp;&nbsp;<span class="key">"edu"</span>: <span class="str">"BCA (AI/ML) @ Galgotias University"</span>,<br>
        &nbsp;&nbsp;<span class="key">"focus"</span>: [<span class="str">"Data Analytics"</span>, <span class="str">"ML"</span>, <span class="str">"Computer Vision"</span>, <span class="str">"BI"</span>],<br>
        &nbsp;&nbsp;<span class="key">"wins"</span>: [<span class="str">"🏆 SIH Top 11"</span>, <span class="str">"🥇 Code Astra IEEE 2025"</span>],<br>
        &nbsp;&nbsp;<span class="key">"goal"</span>: <span class="str">"Data & AI roles in Europe 🇩🇪🇳🇱"</span><br>
        }
      </div>
    </div>

    <div class="sec" style="margin-top:12px;">
      <div class="sec-title">🛠️ tech stack</div>
      <div id="stack-container"></div>
    </div>

    <div class="sec" style="margin-top:6px;">
      <div class="sec-title">📊 github stats</div>
      <div class="stats-row">
        <div class="stat-card"><div class="stat-label">Stars Earned</div><div class="stat-val" id="sc">0</div><div class="stat-sub">across repos</div></div>
        <div class="stat-card"><div class="stat-label">Contributions</div><div class="stat-val" id="cc">0</div><div class="stat-sub">this year</div></div>
      </div>
      <div class="streak-row">
        <div class="streak-box"><div class="streak-num" style="color:#ff6b6b" id="s1">0</div><div class="streak-lbl">Current Streak</div></div>
        <div class="streak-box"><div class="streak-num" style="color:#ffa657" id="s2">0</div><div class="streak-lbl">Longest Streak</div></div>
        <div class="streak-box"><div class="streak-num" style="color:#58a6ff" id="s3">0</div><div class="streak-lbl">Total Commits</div></div>
      </div>
    </div>

    <div class="sec" style="margin-top:4px;">
      <div class="sec-title">💻 top languages</div>
      <div id="bars"></div>
    </div>

    <div class="sec" style="margin-top:4px;">
      <div class="sec-title">📅 contribution activity</div>
      <div class="act-grid" id="agrid"></div>
    </div>

    <div class="sec" style="margin-top:12px;">
      <div class="sec-title">🏅 achievements & certs</div>
      <table class="cert-table">
        <tr><td>🏆 Top 11 — Smart India Hackathon</td><td>IBM Data Analyst Professional</td></tr>
        <tr><td>🥇 National Finalist — Code Astra IEEE 2025</td><td>AWS Cloud Practitioner</td></tr>
        <tr><td></td><td>Cisco Networking Essentials</td></tr>
        <tr><td></td><td>Deloitte Data Analytics (Forage)</td></tr>
      </table>
    </div>

    <div class="sec" style="margin-top:12px;"><div class="sec-title">🌐 connect</div></div>
    <div class="connect-row">
      <button class="cbtn btn-web" onclick="openLink('https://gauransh-singh.github.io')">🌐 Portfolio</button>
      <button class="cbtn btn-li" onclick="openLink('https://linkedin.com/in/gauransh-singh-211586294')">in LinkedIn</button>
      <button class="cbtn btn-gh" onclick="openLink('https://github.com/gauransh-singh')">⌥ GitHub</button>
    </div>

    <!-- FOOTER -->
    <div class="footer-wrap">
      <canvas id="fcanvas"></canvas>
    </div>

  </div>
</div>

<script>
/* ══════════════════════════════════
   PARTICLE ENGINE — reusable
══════════════════════════════════ */
function makeParticleSystem(canvas, opts){
  const ctx = canvas.getContext('2d');
  let W, H, particles = [];
  const count = opts.count || 60;
  const colors = opts.colors || ['167,139,250','88,166,255','255,107,107'];
  const connectDist = opts.connectDist || 80;
  const bgGradient = opts.bgGradient || null;

  function resize(){
    W = canvas.width = canvas.offsetWidth || canvas.parentElement?.offsetWidth || 680;
    H = canvas.height = canvas.offsetHeight || canvas.parentElement?.offsetHeight || 200;
    particles.forEach(p => { if(p.x>W) p.x=Math.random()*W; if(p.y>H) p.y=Math.random()*H; });
  }

  class P {
    constructor(){ this.reset(true); }
    reset(init){
      this.x = Math.random()*W; this.y = init ? Math.random()*H : (Math.random()<.5?-2:H+2);
      this.r = Math.random()*1.6+.4;
      this.vx = (Math.random()-.5)*(opts.speed||.4);
      this.vy = (Math.random()-.5)*(opts.speed||.4);
      this.alpha = Math.random()*.45+.15;
      this.color = colors[Math.floor(Math.random()*colors.length)];
    }
    update(){ this.x+=this.vx; this.y+=this.vy; if(this.x<0||this.x>W||this.y<0||this.y>H) this.reset(false); }
    draw(){
      ctx.beginPath(); ctx.arc(this.x,this.y,this.r,0,Math.PI*2);
      ctx.fillStyle=`rgba(${this.color},${this.alpha})`; ctx.fill();
    }
  }

  resize();
  for(let i=0;i<count;i++) particles.push(new P());

  function frame(){
    ctx.clearRect(0,0,W,H);
    if(bgGradient){
      const g = ctx.createLinearGradient(0,0,W,H);
      bgGradient.forEach(([stop,color]) => g.addColorStop(stop,color));
      ctx.fillStyle=g; ctx.fillRect(0,0,W,H);
    }
    for(let i=0;i<particles.length;i++){
      particles[i].update(); particles[i].draw();
      for(let j=i+1;j<particles.length;j++){
        const dx=particles[i].x-particles[j].x, dy=particles[i].y-particles[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<connectDist){
          ctx.beginPath(); ctx.moveTo(particles[i].x,particles[i].y); ctx.lineTo(particles[j].x,particles[j].y);
          ctx.strokeStyle=`rgba(167,139,250,${.14*(1-d/connectDist)})`; ctx.lineWidth=.5; ctx.stroke();
        }
      }
    }
    requestAnimationFrame(frame);
  }
  frame();
  window.addEventListener('resize', resize);
  return { resize };
}

/* ── HEADER particle canvas ── */
const hc = document.getElementById('hcanvas');
hc.style.cssText='position:absolute;top:0;left:0;width:100%;height:100%;';
makeParticleSystem(hc, {
  count: 55,
  speed: .45,
  connectDist: 70,
  bgGradient: [
    [0,'rgba(15,12,41,0.97)'],
    [0.5,'rgba(48,43,99,0.97)'],
    [1,'rgba(36,36,62,0.97)']
  ]
});

/* ── FOOTER particle canvas ── */
const fc = document.getElementById('fcanvas');
fc.style.cssText='position:absolute;top:0;left:0;width:100%;height:100%;';
makeParticleSystem(fc, {
  count: 40,
  speed: .4,
  connectDist: 65,
  bgGradient: [
    [0,'rgba(36,36,62,0.97)'],
    [0.5,'rgba(48,43,99,0.97)'],
    [1,'rgba(15,12,41,0.97)']
  ]
});

/* ── BODY background (subtle, sparse) ── */
const bgc = document.getElementById('bgcanvas');
bgc.style.cssText='position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;';
makeParticleSystem(bgc, { count:50, speed:.28, connectDist:72 });

/* ── Typing ── */
const lines=["Data Analyst | AI/ML Engineer","Python · SQL · Power BI · Tableau","TensorFlow · PyTorch · OpenCV · Git","Smart India Hackathon — Top 11 🏆","Turning raw data into real insights ✨"];
let li=0,ci=0,del=false;
const tel=document.getElementById('typed');
function type(){const c=lines[li];if(!del){tel.textContent=c.slice(0,++ci);if(ci===c.length){del=true;setTimeout(type,1900);return;}}else{tel.textContent=c.slice(0,--ci);if(ci===0){del=false;li=(li+1)%lines.length;}}setTimeout(type,del?38:68);}
type();

/* ── Stack icons ── */
const SI=s=>`https://skillicons.dev/icons?i=${s}`;
const DV=s=>`https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/${s}`;
const stack=[
  {label:'🐍 Languages',icons:[
    {src:SI('python'),name:'Python'},{src:SI('mysql'),name:'MySQL'},
    {src:SI('html'),name:'HTML'},{src:SI('css'),name:'CSS'},{src:SI('js'),name:'JavaScript'}
  ]},
  {label:'🤖 AI / ML / Deep Learning',icons:[
    {src:SI('tensorflow'),name:'TensorFlow'},{src:SI('pytorch'),name:'PyTorch'},
    {src:SI('opencv'),name:'OpenCV'},{src:SI('sklearn'),name:'Scikit-Learn'},
    {src:'https://upload.wikimedia.org/wikipedia/commons/a/ae/Keras_logo.svg',name:'Keras'}
  ]},
  {label:'📊 Data & Analytics',icons:[
    {src:DV('pandas/pandas-original.svg'),name:'Pandas'},
    {src:DV('numpy/numpy-original.svg'),name:'NumPy'},
    {src:DV('matplotlib/matplotlib-original.svg'),name:'Matplotlib'},
    {src:DV('plotly/plotly-original.svg'),name:'Plotly'},
    {src:'https://seaborn.pydata.org/_images/logo-mark-lightbg.svg',name:'Seaborn'}
  ]},
  {label:'📈 BI & Visualization',icons:[
    {src:'https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg',name:'Power BI'},
    {src:'https://cdn.worldvectorlogo.com/logos/tableau-software.svg',name:'Tableau'},
    {src:DV('microsoftexcel/microsoftexcel-original.svg'),name:'Excel'}
  ]},
  {label:'🔧 Tools & Platforms',icons:[
    {src:SI('git'),name:'Git'},{src:SI('github'),name:'GitHub'},
    {src:SI('vscode'),name:'VS Code'},
    {src:DV('jupyter/jupyter-original.svg'),name:'Jupyter'},
    {src:DV('googlecolab/googlecolab-original.svg'),name:'Colab'},
    {src:SI('aws'),name:'AWS'},{src:SI('linux'),name:'Linux'},{src:SI('docker'),name:'Docker'}
  ]}
];
const sc2=document.getElementById('stack-container');
stack.forEach((group,gi)=>{
  const gd=document.createElement('div');gd.className='stack-group';
  const lb=document.createElement('div');lb.className='stack-label';lb.textContent=group.label;
  const row=document.createElement('div');row.className='icons-row';
  group.icons.forEach((icon,ii)=>{
    const item=document.createElement('div');item.className='icon-item';
    item.style.animationDelay=(gi*.1+ii*.055)+'s';
    const box=document.createElement('div');box.className='icon-box';
    const img=document.createElement('img');img.src=icon.src;img.alt=icon.name;img.title=icon.name;
    img.style.cssText='width:24px;height:24px;object-fit:contain;';
    img.onerror=()=>{
      box.removeChild(img);
      box.style.fontSize='11px';box.style.fontWeight='600';box.style.color='#a78bfa';
      box.textContent=icon.name.slice(0,2).toUpperCase();
    };
    const lbl2=document.createElement('div');lbl2.className='icon-label';lbl2.textContent=icon.name;
    box.appendChild(img);item.appendChild(box);item.appendChild(lbl2);row.appendChild(item);
  });
  gd.appendChild(lb);gd.appendChild(row);sc2.appendChild(gd);
});

/* ── Counters ── */
function aCount(id,val,dur=1400){const el=document.getElementById(id);const s=Date.now();const t=()=>{const p=Math.min((Date.now()-s)/dur,1);el.textContent=Math.round(p*val);if(p<1)requestAnimationFrame(t);};requestAnimationFrame(t);}
setTimeout(()=>{aCount('sc',47);aCount('cc',312);aCount('s1',14);aCount('s2',31);aCount('s3',312);},600);

/* ── Lang bars ── */
const langs=[{name:'Python',pct:58,color:'#3776AB'},{name:'SQL',pct:24,color:'#4479A1'},{name:'HTML/CSS',pct:11,color:'#e34c26'},{name:'JS',pct:7,color:'#f7df1e'}];
const bc=document.getElementById('bars');
langs.forEach((l,i)=>{
  const row=document.createElement('div');row.className='bar-row';
  row.innerHTML=`<span class="bar-lang">${l.name}</span><div class="bar-track"><div class="bar-fill" id="bf${i}" style="background:${l.color}"></div></div><span class="bar-pct">${l.pct}%</span>`;
  bc.appendChild(row);
});
setTimeout(()=>langs.forEach((_,i)=>{document.getElementById('bf'+i).style.width=langs[i].pct+'%';}),400);

/* ── Activity grid ── */
const ag=document.getElementById('agrid');
const sh=['#161b22','#0e4429','#006d32','#26a641','#39d353'];
for(let i=0;i<104;i++){const c=document.createElement('div');c.className='act-cell';const r=Math.random();c.style.background=r<.55?sh[0]:r<.7?sh[1]:r<.82?sh[2]:r<.93?sh[3]:sh[4];ag.appendChild(c);}

/* resize footer canvas height after render */
setTimeout(()=>{
  const fw=document.querySelector('.footer-wrap');
  if(fw){ fc.width=fw.offsetWidth; fc.height=fw.offsetHeight; }
},500);
</script>
