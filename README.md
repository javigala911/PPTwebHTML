<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🏆 Torneo Interactivo de Competencias 🏆</title>
<style>
/* ============ BASE ============ */
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --gold:#ffd54a;
  --silver:#c8d6e5;
  --bronze:#e08b4a;
  --neon:#00e5ff;
  --pink:#ff3ea5;
  --green:#00ff9d;
  --violet:#a06bff;
}
html{scroll-behavior:smooth}
body{
  font-family:'Segoe UI',system-ui,-apple-system,"Helvetica Neue",sans-serif;
  background:#05081a;
  color:#eaf2ff;
  min-height:100vh;
  overflow-x:hidden;
  position:relative;
}
body::before{
  content:'';
  position:fixed;inset:-10%;
  background:
    radial-gradient(circle at 18% 12%, rgba(0,180,255,.22), transparent 45%),
    radial-gradient(circle at 82% 18%, rgba(180,0,255,.22), transparent 45%),
    radial-gradient(circle at 50% 92%, rgba(0,255,150,.16), transparent 50%),
    radial-gradient(circle at 12% 80%, rgba(255,62,165,.14), transparent 45%);
  animation:bgShift 20s ease-in-out infinite alternate;
  pointer-events:none;z-index:0;
}
@keyframes bgShift{
  0%{transform:scale(1) rotate(0deg)}
  100%{transform:scale(1.18) rotate(3deg)}
}
#confetti{
  position:fixed;inset:0;width:100%;height:100%;
  pointer-events:none;z-index:9999;
}
.wrap{position:relative;z-index:1;max-width:1500px;margin:0 auto;padding:clamp(12px,2vw,32px)}

/* ============ HERO ============ */
.hero{text-align:center;padding:clamp(16px,4vw,44px) 8px clamp(10px,2vw,22px)}
.hero h1{
  font-size:clamp(1.9rem,6vw,4.4rem);
  font-weight:900;
  letter-spacing:2px;
  line-height:1.1;
  background:linear-gradient(90deg,#00e5ff,#a06bff,#ff3ea5,#ffd54a,#00ff9d,#00e5ff);
  background-size:300% 100%;
  -webkit-background-clip:text;background-clip:text;
  -webkit-text-fill-color:transparent;color:transparent;
  animation:rainbow 8s linear infinite;
  text-shadow:0 0 40px rgba(0,229,255,.35);
  filter:drop-shadow(0 0 22px rgba(160,107,255,.45));
}
@keyframes rainbow{to{background-position:300% 0}}
.hero .sub{
  margin-top:12px;
  font-size:clamp(.95rem,2.2vw,1.5rem);
  color:#9fb4d8;font-weight:600;letter-spacing:1px;
}
.hero .spark{display:inline-block;animation:float 3s ease-in-out infinite}
.hero .spark:nth-child(2){animation-delay:.6s}
@keyframes float{0%,100%{transform:translateY(0) rotate(-6deg)}50%{transform:translateY(-14px) rotate(6deg)}}

/* ============ PANELES ============ */
.panel{
  background:linear-gradient(160deg, rgba(20,28,58,.88), rgba(10,14,34,.92));
  border:2px solid rgba(120,170,255,.22);
  border-radius:clamp(16px,2vw,28px);
  padding:clamp(16px,3vw,38px);
  margin:clamp(14px,2.4vw,32px) auto;
  box-shadow:0 0 0 1px rgba(255,255,255,.04) inset, 0 22px 60px rgba(0,0,0,.55), 0 0 70px rgba(0,120,255,.09);
  backdrop-filter:blur(9px);
  animation:panelIn .6s cubic-bezier(.2,1.1,.4,1) both;
}
@keyframes panelIn{from{opacity:0;transform:translateY(28px) scale(.97)}to{opacity:1;transform:none}}
.hidden{display:none !important}

.section-title{
  font-size:clamp(1.4rem,4vw,2.7rem);
  font-weight:900;text-align:center;letter-spacing:2px;
  margin-bottom:clamp(14px,2.5vw,30px);
  background:linear-gradient(90deg,var(--neon),var(--violet),var(--pink));
  -webkit-background-clip:text;background-clip:text;
  -webkit-text-fill-color:transparent;color:transparent;
  filter:drop-shadow(0 0 14px rgba(0,229,255,.35));
}
.sub-title{
  font-size:clamp(1.05rem,2.4vw,1.6rem);font-weight:800;text-align:center;
  margin:clamp(18px,3vw,32px) 0 16px;color:#c9dcff;letter-spacing:1.5px;
}

/* ============ CONTADOR ============ */
.counter-row{display:flex;align-items:center;justify-content:center;gap:clamp(12px,3vw,34px);margin-bottom:18px}
.round-btn{
  width:clamp(58px,9vw,86px);height:clamp(58px,9vw,86px);
  border-radius:50%;border:3px solid rgba(0,229,255,.55);
  background:radial-gradient(circle at 30% 25%, rgba(0,229,255,.28), rgba(10,20,50,.9));
  color:#eaf6ff;font-size:clamp(1.8rem,4.5vw,3rem);font-weight:900;
  cursor:pointer;transition:.2s;line-height:1;
  box-shadow:0 0 22px rgba(0,229,255,.3), inset 0 0 18px rgba(0,229,255,.12);
  user-select:none;
}
.round-btn:hover{transform:scale(1.12) rotate(4deg);box-shadow:0 0 40px rgba(0,229,255,.75);border-color:#00e5ff}
.round-btn:active{transform:scale(.95)}
.count-display{
  font-size:clamp(3.4rem,11vw,7rem);font-weight:900;line-height:1;
  min-width:clamp(110px,20vw,220px);text-align:center;
  background:linear-gradient(180deg,#fff,#00e5ff 60%,#a06bff);
  -webkit-background-clip:text;background-clip:text;
  -webkit-text-fill-color:transparent;color:transparent;
  filter:drop-shadow(0 0 26px rgba(0,229,255,.6));
  animation:pulseNum 2.2s ease-in-out infinite;
}
@keyframes pulseNum{0%,100%{transform:scale(1)}50%{transform:scale(1.07)}}
.presets{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:10px}
.presets button{
  padding:10px 22px;border-radius:999px;cursor:pointer;font-weight:900;
  font-size:clamp(.95rem,2vw,1.2rem);letter-spacing:1px;
  background:rgba(255,255,255,.06);color:#bcd4ff;
  border:2px solid rgba(140,180,255,.3);transition:.2s;
}
.presets button:hover{background:rgba(0,229,255,.2);color:#fff;transform:translateY(-3px);box-shadow:0 8px 26px rgba(0,229,255,.3)}

/* ============ NOMBRES ============ */
.name-grid{
  display:grid;gap:12px;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  margin-top:6px;
}
.name-field{
  display:flex;align-items:center;gap:10px;
  background:rgba(255,255,255,.045);
  border:2px solid rgba(140,180,255,.18);
  border-radius:14px;padding:8px 12px;transition:.2s;
}
.name-field:focus-within{border-color:var(--neon);box-shadow:0 0 22px rgba(0,229,255,.35);background:rgba(0,229,255,.08)}
.name-field .num{
  width:32px;height:32px;flex:none;display:grid;place-items:center;border-radius:9px;
  background:linear-gradient(135deg,var(--neon),var(--violet));
  color:#02101f;font-weight:900;font-size:1rem;
}
.name-field input{
  flex:1;background:transparent;border:none;outline:none;color:#fff;
  font-size:1.08rem;font-weight:700;font-family:inherit;min-width:0;
}
.name-field input::placeholder{color:#5f7199;font-weight:600}

/* ============ BOTONES ============ */
.actions{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;margin-top:clamp(18px,3vw,32px)}
.btn{
  padding:clamp(12px,1.6vw,18px) clamp(22px,3.4vw,44px);
  border-radius:999px;border:none;cursor:pointer;
  font-size:clamp(1rem,2.2vw,1.4rem);font-weight:900;letter-spacing:1.2px;
  font-family:inherit;transition:.22s;position:relative;overflow:hidden;
}
.btn.primary{
  background:linear-gradient(135deg,#00ff9d,#00e5ff 45%,#a06bff);
  color:#031024;box-shadow:0 10px 36px rgba(0,229,255,.42);
}
.btn.primary:hover{transform:translateY(-4px) scale(1.04);box-shadow:0 16px 50px rgba(0,229,255,.7)}
.btn.ghost{
  background:rgba(255,255,255,.06);color:#cfe0ff;border:2px solid rgba(140,180,255,.35);
}
.btn.ghost:hover{background:rgba(160,107,255,.24);transform:translateY(-3px);box-shadow:0 10px 30px rgba(160,107,255,.4)}
.btn.danger{
  background:linear-gradient(135deg,#ff3ea5,#ff7a3e);color:#fff;
  box-shadow:0 10px 34px rgba(255,62,165,.4);
}
.btn.danger:hover{transform:translateY(-3px) scale(1.03);box-shadow:0 16px 46px rgba(255,62,165,.65)}
.btn:active{transform:scale(.96)}

/* ============ LISTA CONCURSANTES ============ */
.competitors{
  display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-bottom:20px;
}
.chip{
  display:flex;align-items:center;gap:8px;
  padding:8px 16px;border-radius:999px;font-weight:800;
  font-size:clamp(.85rem,1.8vw,1.1rem);
  background:linear-gradient(135deg, rgba(0,229,255,.16), rgba(160,107,255,.16));
  border:2px solid rgba(0,229,255,.4);color:#e6f6ff;
  box-shadow:0 0 18px rgba(0,229,255,.18);
  transition:.3s;
}
.chip.out{
  background:rgba(255,60,90,.12);border-color:rgba(255,60,90,.5);
  color:#ff8fa3;text-decoration:line-through;opacity:.62;
  box-shadow:none;filter:grayscale(.7);
  animation:shakeOut .5s ease;
}
@keyframes shakeOut{0%,100%{transform:translateX(0)}25%{transform:translateX(-6px)}75%{transform:translateX(6px)}}

/* ============ BRACKET ============ */
.bracket-scroll{overflow-x:auto;padding:8px 4px 22px;scrollbar-color:var(--neon) transparent;scrollbar-width:thin}
.bracket-scroll::-webkit-scrollbar{height:10px}
.bracket-scroll::-webkit-scrollbar-thumb{background:linear-gradient(90deg,var(--neon),var(--violet));border-radius:999px}
#bracket{display:flex;gap:clamp(12px,2vw,32px);min-width:max-content;align-items:stretch}
.round{display:flex;flex-direction:column;min-width:clamp(210px,20vw,270px);animation:panelIn .5s cubic-bezier(.2,1.1,.4,1) both}
.round-title{
  text-align:center;font-size:clamp(.85rem,1.5vw,1.25rem);font-weight:900;letter-spacing:1.5px;
  padding:11px 8px;margin-bottom:14px;border-radius:14px;
  background:linear-gradient(90deg, rgba(0,229,255,.18), rgba(255,62,165,.18));
  border:2px solid rgba(255,255,255,.16);
  color:#dceaff;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;
  box-shadow:0 0 22px rgba(0,229,255,.14);
}
.matches{flex:1;display:flex;flex-direction:column;justify-content:space-around;gap:16px}

.match{
  background:linear-gradient(160deg, rgba(26,36,72,.92), rgba(12,18,42,.94));
  border:2px solid rgba(120,170,255,.22);
  border-radius:18px;padding:9px;
  display:flex;flex-direction:column;gap:6px;
  box-shadow:0 10px 26px rgba(0,0,0,.45);
  transition:.25s;position:relative;
}
.match:hover{border-color:rgba(0,229,255,.55);box-shadow:0 0 34px rgba(0,229,255,.28)}
.match.decided{border-color:rgba(0,255,157,.35)}
.match::after{
  content:'';position:absolute;inset:-2px;border-radius:18px;pointer-events:none;
  background:linear-gradient(120deg,transparent 35%,rgba(255,255,255,.18) 50%,transparent 65%);
  background-size:250% 100%;opacity:0;transition:.4s;
}
.match:hover::after{opacity:1;animation:shine 1.1s linear infinite}
@keyframes shine{to{background-position:-250% 0}}

.slot{
  display:flex;align-items:center;gap:10px;
  padding:clamp(8px,1.2vw,13px) clamp(10px,1.4vw,15px);
  border-radius:12px;font-weight:800;
  font-size:clamp(.9rem,1.7vw,1.18rem);
  background:rgba(255,255,255,.05);
  border:2px solid transparent;transition:.22s;
  min-height:clamp(40px,5vw,54px);
}
.slot .s-icon{font-size:1.25em;flex:none;line-height:1}
.slot .s-name{overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.slot.clickable{cursor:pointer}
.slot.clickable:hover{
  background:linear-gradient(90deg, rgba(0,229,255,.28), rgba(160,107,255,.28));
  border-color:var(--neon);transform:translateX(5px) scale(1.02);
  box-shadow:0 0 24px rgba(0,229,255,.45);
}
.slot.winner{
  background:linear-gradient(90deg,#00ff9d,#00e5ff);
  color:#02141f;border-color:#7dffd0;
  box-shadow:0 0 26px rgba(0,255,157,.7);
  animation:winnerPop .5s cubic-bezier(.2,1.6,.4,1);
}
@keyframes winnerPop{0%{transform:scale(.85)}60%{transform:scale(1.06)}100%{transform:scale(1)}}
.slot.loser{
  opacity:.42;text-decoration:line-through;color:#ff9db4;
  background:rgba(255,60,90,.1);filter:grayscale(.5);
}
.slot.empty{opacity:.4;font-style:italic;font-weight:600;color:#8fa4c9}

.vs{
  text-align:center;font-size:.8rem;font-weight:900;letter-spacing:3px;
  color:#6d84ad;line-height:1;
}
.match.decided .vs{color:var(--green);text-shadow:0 0 12px rgba(0,255,157,.8)}

/* ============ PODIO ============ */
#podiumPanel{
  background:linear-gradient(160deg, rgba(40,26,66,.9), rgba(12,14,34,.95));
  border-color:rgba(255,213,74,.35);
  box-shadow:0 0 90px rgba(255,213,74,.16), 0 22px 60px rgba(0,0,0,.6);
}
.podium-wrap{
  display:flex;align-items:flex-end;justify-content:center;
  gap:clamp(6px,1.6vw,28px);margin-top:clamp(14px,3vw,36px);
}
.podium-col{flex:1 1 0;max-width:280px;display:flex;flex-direction:column;align-items:center}
.podium-card{
  text-align:center;margin-bottom:14px;width:100%;
  animation:cardIn .7s cubic-bezier(.2,1.5,.4,1) both;
}
@keyframes cardIn{from{opacity:0;transform:translateY(-26px) scale(.8)}to{opacity:1;transform:none}}
.podium-card .medal{font-size:clamp(2rem,5.5vw,3.4rem);line-height:1;filter:drop-shadow(0 0 16px rgba(255,213,74,.8))}
.podium-card .avatar{
  font-size:clamp(2rem,6vw,3.6rem);line-height:1.1;margin:4px 0;
  filter:drop-shadow(0 0 16px rgba(0,229,255,.65));
  animation:float 3s ease-in-out infinite;
}
.podium-card .pname{
  font-size:clamp(.9rem,2.1vw,1.45rem);font-weight:900;letter-spacing:.5px;
  color:#fff;word-break:break-word;
}
.podium-card .place-label{
  font-size:clamp(.7rem,1.5vw,1rem);font-weight:800;letter-spacing:3px;color:#8fa4c9;margin-top:2px;
}
.podium-bar{
  width:100%;border-radius:20px 20px 0 0;
  display:flex;align-items:center;justify-content:center;
  font-size:clamp(2rem,7vw,4.6rem);font-weight:900;color:rgba(0,0,0,.42);
  transform-origin:bottom;animation:rise .95s cubic-bezier(.2,1.3,.4,1) both;
  box-shadow:0 -8px 40px rgba(0,0,0,.45), inset 0 6px 22px rgba(255,255,255,.25);
  border:2px solid rgba(255,255,255,.25);border-bottom:none;
}
@keyframes rise{from{transform:scaleY(0);opacity:0}to{transform:scaleY(1);opacity:1}}
.podium-col.first .podium-bar{height:clamp(120px,20vw,220px);background:linear-gradient(180deg,#fff3b0,#ffd54a 35%,#ff9d00)}
.podium-col.second .podium-bar{height:clamp(90px,15vw,168px);background:linear-gradient(180deg,#f4f9ff,#c8d6e5 40%,#8fa2bb);animation-delay:.18s}
.podium-col.third .podium-bar{height:clamp(66px,11vw,124px);background:linear-gradient(180deg,#f5c491,#e08b4a 40%,#a95c1f);animation-delay:.34s}
.podium-col.first .podium-card{animation-delay:.1s}
.podium-col.third .podium-card{animation-delay:.3s}

.champion-banner{
  margin-top:clamp(20px,4vw,44px);text-align:center;
  font-size:clamp(1.3rem,4.6vw,3rem);font-weight:900;letter-spacing:2px;
  padding:clamp(14px,2.6vw,28px);border-radius:22px;
  background:linear-gradient(90deg,rgba(255,213,74,.18),rgba(255,62,165,.18),rgba(0,229,255,.18));
  background-size:250% 100%;
  border:3px solid rgba(255,213,74,.55);
  color:#fff;text-shadow:0 0 26px rgba(255,213,74,.9);
  animation:rainbow 6s linear infinite, glowPulse 2.4s ease-in-out infinite;
}
@keyframes glowPulse{0%,100%{box-shadow:0 0 34px rgba(255,213,74,.35)}50%{box-shadow:0 0 80px rgba(255,213,74,.75)}}

/* ============ RESPONSIVE ============ */
@media(max-width:640px){
  .name-grid{grid-template-columns:1fr}
  .podium-card .pname{font-size:.85rem}
  .round{min-width:180px}
}
</style>
</head>
<body>

<canvas id="confetti"></canvas>

<div class="wrap">

  <header class="hero">
    <h1><span class="spark">🏆</span> TORNEO DE CAMPEONES <span class="spark">🏆</span></h1>
    <p class="sub">⚔️ Elige a los ganadores · 💀 Elimina rivales · 👑 Corona al campeón</p>
  </header>

  <!-- ============ CONFIGURACIÓN ============ -->
  <section class="panel" id="setupPanel">
    <h2 class="section-title">👥 NÚMERO DE COMPETIDORES</h2>

    <div class="counter-row">
      <button class="round-btn" id="btnMinus" aria-label="Menos">−</button>
      <div class="count-display" id="countDisplay">8</div>
      <button class="round-btn" id="btnPlus" aria-label="Más">+</button>
    </div>

    <div class="presets">
      <button data-n="2">2 👤</button>
      <button data-n="4">4 ⚔️</button>
      <button data-n="8">8 🔥</button>
      <button data-n="16">16 🌟</button>
    </div>

    <h3 class="sub-title">📝 LISTA DE CONCURSANTES</h3>
    <div class="name-grid" id="nameInputs"></div>

    <div class="actions">
      <button class="btn ghost" id="btnRandom">🎲 Nombres aleatorios</button>
      <button class="btn primary" id="btnStart">🚀 INICIAR TORNEO</button>
    </div>
  </section>

  <!-- ============ BRACKET ============ -->
  <section class="panel hidden" id="bracketPanel">
    <h2 class="section-title">⚔️ ENFRENTAMIENTOS</h2>
    <div class="competitors" id="competitorList"></div>
    <div class="bracket-scroll"><div id="bracket"></div></div>
    <div class="actions">
      <button class="btn ghost" id="btnSimulate">⚡ Simular todo</button>
      <button class="btn danger" id="btnReset">🔄 Nuevo torneo</button>
    </div>
  </section>

  <!-- ============ PODIO ============ -->
  <section class="panel hidden" id="podiumPanel">
    <h2 class="section-title">🎉 PODIO FINAL 🎉</h2>
    <div id="podiumContent"></div>
  </section>

</div>

<script>
/* =====================================================================
   DATOS
   ===================================================================== */
const EMOJIS = ['🦁','🐯','🦅','🐲','🐺','🦈','🐆','🐍','🦉','⚡','🦊','🐻',
                '🦂','🐋','🐉','🐙','🦏','🦬','🦌','🐊','🦇','🦚','🦜','🐘'];
const NAMES  = ['León','Tigre','Águila','Dragón','Lobo','Tiburón','Pantera','Cobra',
                'Búho','Rayo','Zorro','Oso','Escorpión','Ballena','Fénix','Pulpo',
                'Rinoceronte','Bisonte','Ciervo','Cocodrilo','Murciélago','Pavo Real','Loro','Elefante'];

const state = {
  count: 8,
  players: [],
  rounds: [],
  thirdPlace: null,
  eliminated: new Set(),
  podiumShown: false
};

/* =====================================================================
   UTILIDADES
   ===================================================================== */
const $ = s => document.querySelector(s);

function shuffle(arr){
  const a = arr.slice();
  for(let i=a.length-1;i>0;i--){
    const j = Math.floor(Math.random()*(i+1));
    [a[i],a[j]] = [a[j],a[i]];
  }
  return a;
}
function nextPow2(n){ let p=1; while(p<n) p*=2; return p; }

/* Orden de siembra estándar (1 vs último, etc.) */
function seedOrder(n){
  let rounds = Math.log2(n);
  let order = [1,2];
  for(let i=1;i<rounds;i++){
    const sum = order.length*2+1;
    const next = [];
    order.forEach(s=>{ next.push(s); next.push(sum-s); });
    order = next;
  }
  return order;
}

function escapeHtml(str){
  return String(str).replace(/[&<>"']/g, c => ({
    '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'
  }[c]));
}

function getRoundNames(total){
  const names = [];
  for(let i=0;i<total;i++){
    const fromEnd = total-1-i;
    if(fromEnd===0)      names.push('🏆 GRAN FINAL');
    else if(fromEnd===1) names.push('🥈 SEMIFINALES');
    else if(fromEnd===2) names.push('🎯 CUARTOS DE FINAL');
    else if(fromEnd===3) names.push('⚔️ OCTAVOS DE FINAL');
    else                 names.push('🔥 RONDA ' + (i+1));
  }
  return names;
}

/* =====================================================================
   MOTOR DEL TORNEO
   ===================================================================== */
function buildTournament(names){
  const players = names.map((n,i)=>({
    id: 'p'+i+'_'+Math.random().toString(36).slice(2,8),
    name: n,
    emoji: EMOJIS[i % EMOJIS.length]
  }));

  const shuffled = shuffle(players);
  const slots = nextPow2(Math.max(2, shuffled.length));
  const order = seedOrder(slots);

  // Los "seeds" mayores al número de jugadores son BYES (null)
  const seeded = order.map(seed => seed <= shuffled.length ? shuffled[seed-1] : null);

  const totalRounds = Math.log2(slots);
  const rounds = [];

  const first = [];
  for(let i=0;i<seeded.length;i+=2){
    first.push({ a: seeded[i], b: seeded[i+1], winner:null });
  }
  rounds.push(first);

  for(let r=1;r<totalRounds;r++){
    const prev = rounds[r-1];
    const cur = [];
    for(let i=0;i<prev.length;i+=2) cur.push({a:null,b:null,winner:null});
    rounds.push(cur);
  }

  state.players = shuffled;
  state.rounds = rounds;
  state.eliminated = new Set();
  state.podiumShown = false;
  state.thirdPlace = totalRounds >= 2 ? { a:null, b:null, winner:null, third:true } : null;

  autoResolve();
}

function setWinner(ri, mi, player){
  const m = state.rounds[ri][mi];
  if(m.winner) return;
  m.winner = player;

  const loser = (m.a === player) ? m.b : m.a;
  if(loser) state.eliminated.add(loser.id);

  // Avanzar a la siguiente ronda
  if(ri + 1 < state.rounds.length){
    const nm = state.rounds[ri+1][Math.floor(mi/2)];
    if(mi % 2 === 0) nm.a = player; else nm.b = player;
  }

  // Alimentar el partido por el 3er puesto con los perdedores de semifinales
  if(state.thirdPlace && state.rounds.length >= 2 && ri === state.rounds.length - 2){
    if(mi === 0) state.thirdPlace.a = loser;
    else         state.thirdPlace.b = loser;
  }
}

function autoResolve(){
  let guard = 0, changed = true;
  while(changed && guard++ < 300){
    changed = false;
    for(let ri=0; ri<state.rounds.length; ri++){
      const round = state.rounds[ri];
      for(let mi=0; mi<round.length; mi++){
        const m = round[mi];
        if(m.winner) continue;
        if(m.a && !m.b){ setWinner(ri, mi, m.a); changed = true; }
        else if(!m.a && m.b){ setWinner(ri, mi, m.b); changed = true; }
      }
    }
    if(state.thirdPlace && !state.thirdPlace.winner){
      const t = state.thirdPlace;
      if(t.a && !t.b){ t.winner = t.a; changed = true; }
      else if(!t.a && t.b){ t.winner = t.b; changed = true; }
    }
  }
}

function computePodium(){
  const final = state.rounds[state.rounds.length-1][0];
  if(!final || !final.winner) return null;
  const first = final.winner;
  const second = (final.a === first) ? final.b : final.a;
  let third = null;
  if(state.thirdPlace && state.thirdPlace.winner) third = state.thirdPlace.winner;
  return { first, second, third };
}

/* =====================================================================
   RENDER
   ===================================================================== */
function renderCompetitors(){
  const wrap = $('#competitorList');
  wrap.innerHTML = '';
  state.players.forEach(p=>{
    const out = state.eliminated.has(p.id);
    const el = document.createElement('div');
    el.className = 'chip' + (out ? ' out' : '');
    el.innerHTML = `<span>${out ? '💀' : p.emoji}</span><span>${escapeHtml(p.name)}</span>`;
    wrap.appendChild(el);
  });
}

function renderSlot(m, ri, mi, key){
  const p = m[key];
  const el = document.createElement('div');

  if(!p){
    el.className = 'slot empty';
    el.innerHTML = '<span class="s-icon">⏳</span><span class="s-name">Por definir</span>';
    return el;
  }

  const decided = !!m.winner;
  const isWin = decided && m.winner.id === p.id;
  el.className = 'slot' + (isWin ? ' winner' : (decided ? ' loser' : ''));
  el.innerHTML =
    `<span class="s-icon">${isWin ? '✅' : (decided ? '❌' : p.emoji)}</span>` +
    `<span class="s-name">${escapeHtml(p.name)}</span>`;

  if(!decided && m.a && m.b){
    el.classList.add('clickable');
    el.title = 'Clic para elegir como ganador';
    el.addEventListener('click', ()=> onPick(ri, mi, p));
  }
  return el;
}

function renderMatch(m, ri, mi){
  const el = document.createElement('div');
  el.className = 'match' + (m.winner ? ' decided' : '');

  el.appendChild(renderSlot(m, ri, mi, 'a'));

  const vs = document.createElement('div');
  vs.className = 'vs';
  vs.textContent = m.winner ? '✔ GANADOR' : 'VS';
  el.appendChild(vs);

  el.appendChild(renderSlot(m, ri, mi, 'b'));
  return el;
}

function renderBracket(){
  const wrap = $('#bracket');
  wrap.innerHTML = '';
  const names = getRoundNames(state.rounds.length);

  state.rounds.forEach((round, ri)=>{
    const col = document.createElement('div');
    col.className = 'round';

    const title = document.createElement('div');
    title.className = 'round-title';
    title.textContent = names[ri];
    col.appendChild(title);

    const list = document.createElement('div');
    list.className = 'matches';
    round.forEach((m, mi)=> list.appendChild(renderMatch(m, ri, mi)));
    col.appendChild(list);

    wrap.appendChild(col);
  });

  if(state.thirdPlace){
    const col = document.createElement('div');
    col.className = 'round';
    const title = document.createElement('div');
    title.className = 'round-title';
    title.textContent = '🥉 TERCER PUESTO';
    col.appendChild(title);
    const list = document.createElement('div');
    list.className = 'matches';
    list.appendChild(renderMatch(state.thirdPlace, -1, 0));
    col.appendChild(list);
    wrap.appendChild(col);
  }
}

/* =====================================================================
   INTERACCIÓN
   ===================================================================== */
function onPick(ri, mi, player){
  if(ri === -1){
    const m = state.thirdPlace;
    if(!m || m.winner || !m.a || !m.b) return;
    m.winner = player;
    const loser = (m.a === player) ? m.b : m.a;
    if(loser) state.eliminated.add(loser.id);
  } else {
    const m = state.rounds[ri][mi];
    if(m.winner || !m.a || !m.b) return;
    setWinner(ri, mi, player);
    autoResolve();
  }

  renderBracket();
  renderCompetitors();
  updatePodium();
}

/* =====================================================================
   PODIO
   ===================================================================== */
function updatePodium(){
  const p = computePodium();
  if(!p) return;

  const panel = $('#podiumPanel');
  const isNew = !state.podiumShown;

  if(isNew){
    state.podiumShown = true;
    panel.classList.remove('hidden');
    startConfetti(9000);
    setTimeout(()=> panel.scrollIntoView({behavior:'smooth', block:'center'}), 350);
  }
  renderPodium(p);
}

function renderPodium(p){
  const wrap = $('#podiumContent');

  const makeCol = (player, medal, cls, place) => `
    <div class="podium-col ${cls}">
      <div class="podium-card">
        <div class="medal">${medal}</div>
        <div class="avatar">${player ? player.emoji : '❔'}</div>
        <div class="pname">${player ? escapeHtml(player.name) : 'Pendiente'}</div>
        <div class="place-label">${place}º LUGAR</div>
      </div>
      <div class="podium-bar"><span>${place}</span></div>
    </div>`;

  wrap.innerHTML = `
    <div class="podium-wrap">
      ${makeCol(p.second, '🥈', 'second', '2')}
      ${makeCol(p.first,  '🥇', 'first',  '1')}
      ${makeCol(p.third,  '🥉', 'third',  '3')}
    </div>
    <div class="champion-banner">
      🎊 ¡${escapeHtml(p.first.name)} ES EL CAMPEÓN! 🎊
    </div>
  `;
}

/* =====================================================================
   CONFETI
   ===================================================================== */
const canvas = document.getElementById('confetti');
const ctx = canvas.getContext('2d');
let particles = [];
let confettiEnd = 0;
let rafId = null;

const COLORS = ['#ffd54a','#00e5ff','#ff3ea5','#00ff9d','#a06bff','#ff7a3e','#ffffff','#5ce1ff'];

function resizeCanvas(){
  canvas.width  = window.innerWidth;
  canvas.height = window.innerHeight;
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

function spawnConfetti(n){
  for(let i=0;i<n;i++){
    particles.push({
      x: Math.random()*canvas.width,
      y: -30 - Math.random()*canvas.height*0.6,
      vx: (Math.random()-0.5)*5,
      vy: Math.random()*4 + 2.5,
      size: Math.random()*12 + 6,
      color: COLORS[Math.floor(Math.random()*COLORS.length)],
      rot: Math.random()*Math.PI*2,
      vr: (Math.random()-0.5)*0.35,
      shape: Math.random() < 0.32 ? 'circle' : 'rect',
      alpha: 1
    });
  }
}

function drawParticle(p){
  ctx.save();
  ctx.translate(p.x, p.y);
  ctx.rotate(p.rot);
  ctx.globalAlpha = p.alpha;
  ctx.fillStyle = p.color;
  if(p.shape === 'circle'){
    ctx.beginPath();
    ctx.arc(0, 0, p.size/2, 0, Math.PI*2);
    ctx.fill();
  } else {
    ctx.fillRect(-p.size/2, -p.size/4, p.size, p.size/2);
  }
  ctx.restore();
}

function confettiLoop(){
  rafId = requestAnimationFrame(confettiLoop);
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  const now = performance.now();
  if(now < confettiEnd){
    spawnConfetti(7);
  }

  for(const p of particles){
    p.x += p.vx;
    p.y += p.vy;
    p.vy += 0.085;
    p.vx *= 0.995;
    p.rot += p.vr;
    if(p.y > canvas.height * 0.7) p.alpha -= 0.006;
  }
  particles = particles.filter(p => p.y < canvas.height + 60 && p.alpha > 0.02);

  for(const p of particles) drawParticle(p);

  if(particles.length === 0 && now >= confettiEnd){
    cancelAnimationFrame(rafId);
    rafId = null;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  }
}

function startConfetti(duration){
  confettiEnd = performance.now() + (duration || 8000);
  if(!rafId) confettiLoop();
}

function stopConfetti(){
  confettiEnd = 0;
  particles = [];
  if(rafId){ cancelAnimationFrame(rafId); rafId = null; }
  ctx.clearRect(0, 0, canvas.width, canvas.height);
}

/* =====================================================================
   UI SETUP
   ===================================================================== */
function renderNameInputs(){
  const wrap = $('#nameInputs');
  const prev = [...wrap.querySelectorAll('input')].map(i => i.value);
  wrap.innerHTML = '';

  for(let i=0;i<state.count;i++){
    const field = document.createElement('div');
    field.className = 'name-field';

    const num = document.createElement('span');
    num.className = 'num';
    num.textContent = i+1;

    const input = document.createElement('input');
    input.type = 'text';
    input.maxLength = 16;
    input.placeholder = 'Competidor ' + (i+1);
    input.value = prev[i] || '';

    field.appendChild(num);
    field.appendChild(input);
    wrap.appendChild(field);
  }
}

function setCount(n){
  state.count = Math.max(2, Math.min(16, n));
  $('#countDisplay').textContent = state.count;
  renderNameInputs();
}

function fillRandomNames(){
  const inputs = [...document.querySelectorAll('#nameInputs input')];
  const pool = shuffle(NAMES).slice(0, inputs.length);
  inputs.forEach((inp, i)=>{
    inp.value = pool[i] || ('Competidor ' + (i+1));
    inp.style.transform = 'scale(1.06)';
    setTimeout(()=> inp.style.transform = '', 180);
  });
}

function startTournament(){
  const inputs = [...document.querySelectorAll('#nameInputs input')];
  const names = inputs.map((inp, i) => (inp.value.trim() || ('Competidor ' + (i+1))));

  buildTournament(names);

  $('#setupPanel').classList.add('hidden');
  $('#podiumPanel').classList.add('hidden');
  $('#bracketPanel').classList.remove('hidden');
  state.podiumShown = false;

  renderCompetitors();
  renderBracket();

  setTimeout(()=> $('#bracketPanel').scrollIntoView({behavior:'smooth', block:'start'}), 120);
}

function simulateAll(){
  let guard = 0;
  while(guard++ < 800){
    const pending = [];
    state.rounds.forEach((round, ri)=>{
      round.forEach((m, mi)=>{
        if(!m.winner && m.a && m.b) pending.push([ri, mi]);
      });
    });
    if(state.thirdPlace && !state.thirdPlace.winner && state.thirdPlace.a && state.thirdPlace.b){
      pending.push([-1, 0]);
    }
    if(!pending.length) break;

    const [ri, mi] = pending[Math.floor(Math.random()*pending.length)];

    if(ri === -1){
      const m = state.thirdPlace;
      const pick = Math.random() < 0.5 ? m.a : m.b;
      m.winner = pick;
      const loser = (m.a === pick) ? m.b : m.a;
      if(loser) state.eliminated.add(loser.id);
    } else {
      const m = state.rounds[ri][mi];
      const pick = Math.random() < 0.5 ? m.a : m.b;
      setWinner(ri, mi, pick);
      autoResolve();
    }
  }
  renderBracket();
  renderCompetitors();
  updatePodium();
}

function resetTournament(){
  stopConfetti();
  state.players = [];
  state.rounds = [];
  state.thirdPlace = null;
  state.eliminated = new Set();
  state.podiumShown = false;

  $('#bracketPanel').classList.add('hidden');
  $('#podiumPanel').classList.add('hidden');
  $('#setupPanel').classList.remove('hidden');

  setTimeout(()=> $('#setupPanel').scrollIntoView({behavior:'smooth', block:'start'}), 100);
}

/* =====================================================================
   EVENTOS
   ===================================================================== */
$('#btnMinus').addEventListener('click', ()=> setCount(state.count - 1));
$('#btnPlus').addEventListener('click',  ()=> setCount(state.count + 1));

document.querySelectorAll('.presets button').forEach(btn=>{
  btn.addEventListener('click', ()=> setCount(parseInt(btn.dataset.n, 10)));
});

$('#btnRandom').addEventListener('click', fillRandomNames);
$('#btnStart').addEventListener('click', startTournament);
$('#btnSimulate').addEventListener('click', simulateAll);
$('#btnReset').addEventListener('click', resetTournament);

/* =====================================================================
   INICIO
   ===================================================================== */
setCount(8);
</script>
</body>
</html>
