<!doctype html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>FitCalc Pro</title>
<style>
:root{--bg:#f2f5ee;--panel:#fff;--p2:#e9efe4;--line:#d2dccb;--text:#16241a;--muted:#5c6b5f;--acc:#2d7a46;--accfg:#fff;--acct:#23693b;--warn:#c27a12;--warnbg:#fbf1dc;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#111a14;--panel:#1a251e;--p2:#223028;--line:#33463a;--text:#eef4ec;--muted:#a3b3a6;--acc:#9fdc86;--accfg:#122015;--acct:#a9e592;--warn:#f0c46c;--warnbg:#2c281b}}
:root[data-theme="dark"]{--bg:#111a14;--panel:#1a251e;--p2:#223028;--line:#33463a;--text:#eef4ec;--muted:#a3b3a6;--acc:#9fdc86;--accfg:#122015;--acct:#a9e592;--warn:#f0c46c;--warnbg:#2c281b}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font:15px/1.5 "Segoe UI",system-ui,-apple-system,Roboto,sans-serif}
button,input,select,textarea{font:inherit;color:inherit}button{cursor:pointer}
.app{max-width:1060px;margin:auto;padding:18px 14px 60px}
.top{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-bottom:14px}
.brand{display:flex;gap:11px;align-items:center}.logo{width:40px;height:40px;border-radius:12px;background:var(--acc);color:var(--accfg);display:grid;place-items:center;font-weight:800;font-size:20px}
h1{font-size:21px;margin:0;letter-spacing:-.03em}.sub{color:var(--muted);font-size:12px}
.pill{border:1px solid var(--line);background:var(--panel);border-radius:99px;padding:6px 12px;font-size:13px;white-space:nowrap}
.tabs{display:flex;gap:6px;overflow:auto;padding-bottom:12px}.tab{border:1px solid var(--line);background:var(--panel);border-radius:10px;padding:9px 14px;white-space:nowrap;color:var(--muted)}
.tab.active{background:var(--acc);color:var(--accfg);border-color:var(--acc);font-weight:700}
.page{display:none}.page.active{display:block}
.grid{display:grid;grid-template-columns:minmax(0,1fr) minmax(0,1fr);gap:14px}
.card{background:var(--panel);border:1px solid var(--line);border-radius:16px;padding:17px;margin-bottom:14px}
.card h3{margin:0 0 3px;font-size:17px}.hint{color:var(--muted);font-size:12.5px;margin:0 0 13px}
.fields{display:grid;grid-template-columns:1fr 1fr;gap:10px}.field label{display:block;font-size:12px;color:var(--muted);margin-bottom:4px}
input,select,textarea{width:100%;background:var(--bg);border:1px solid var(--line);border-radius:10px;padding:10px;outline:none}
input:focus,select:focus,textarea:focus,button:focus-visible{outline:2px solid var(--acc);outline-offset:1px}
.row{display:grid;grid-template-columns:1fr 1fr 80px;gap:8px;margin-bottom:8px}.row.two{grid-template-columns:1fr 1fr}
.btn{border:0;border-radius:10px;padding:10px 14px;font-weight:700;background:var(--acc);color:var(--accfg)}
.btn.secondary{background:var(--p2);color:var(--text);border:1px solid var(--line)}.btn.sm{padding:4px 10px}.btnrow{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px}
.mg{display:grid;grid-template-columns:1fr 1fr;gap:9px}.metric{background:var(--p2);border-radius:12px;padding:12px}
.label{color:var(--muted);font-size:12px}.value{font-size:24px;font-weight:800;letter-spacing:-.03em}.value.accent{color:var(--acct)}.metric small{color:var(--muted)}
.bar{height:7px;background:var(--p2);border-radius:9px;overflow:hidden;margin:6px 0}.bar span{display:block;height:100%;background:var(--acc);border-radius:9px;transition:width .25s}
.ringwrap{display:flex;gap:16px;align-items:center}.macros{flex:1;min-width:0}.mbh{display:flex;justify-content:space-between;font-size:12.5px}
.note{margin-top:12px;border-left:3px solid var(--warn);background:var(--warnbg);padding:9px 12px;border-radius:0 10px 10px 0;font-size:12.5px}
.ins{padding:10px 12px;border-radius:10px;background:var(--p2);margin-bottom:8px;font-size:13.5px}.ins.warn{background:var(--warnbg);border-left:3px solid var(--warn)}
.daybtns{display:flex;gap:6px;overflow:auto;margin:10px 0}.daybtn{border:1px solid var(--line);background:transparent;border-radius:9px;padding:7px 12px;color:var(--muted);white-space:nowrap}
.daybtn.active{background:var(--p2);color:var(--acct);border-color:var(--acc);font-weight:700}
.list{display:grid;gap:6px;margin:8px 0}.item{display:flex;justify-content:space-between;gap:8px;text-align:left;background:var(--p2);border:1px solid var(--line);border-radius:10px;padding:9px 11px}.item small,.entry small,.work small,.food p{color:var(--muted);font-size:12px;margin:0;display:block}
.grp{margin:14px 0 2px;font-weight:700;font-size:13px;color:var(--acct)}.entry{display:flex;justify-content:space-between;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--line)}
.food,.work{background:var(--p2);border-radius:12px;padding:12px;margin-bottom:8px}.foodhead{display:flex;justify-content:space-between;gap:8px;font-weight:650}
.work{display:flex;gap:11px;align-items:center}.work input{width:20px;height:20px;accent-color:var(--acc)}
.empty{color:var(--muted);font-size:13px;padding:8px 0}summary{cursor:pointer;color:var(--muted);font-size:13px;margin:8px 0}
table{width:100%;border-collapse:collapse;font-size:13px}th,td{text-align:left;padding:8px 4px;border-bottom:1px solid var(--line)}th{color:var(--muted);font-weight:600}
#toast{position:fixed;left:50%;bottom:calc(18px + env(safe-area-inset-bottom,0px));transform:translate(-50%,20px);background:var(--text);color:var(--bg);padding:9px 16px;border-radius:99px;font-size:13px;opacity:0;pointer-events:none;transition:.2s}#toast.show{opacity:1;transform:translate(-50%,0)}
@media(max-width:760px){.grid{grid-template-columns:1fr}.ringwrap{flex-direction:column;align-items:stretch}.ringwrap svg{align-self:center}.row{grid-template-columns:1fr 1fr}.row .btn{grid-column:1/-1}}
@media(prefers-reduced-motion:reduce){*{transition:none!important}}
</style></head><body>
<div class="app">
<header class="top"><div class="brand"><div class="logo">F</div><div><h1>FitCalc Pro</h1><div class="sub">Plan, log and adjust. Data stays in this browser.</div></div></div><div class="pill" id="streak">0-day streak</div></header>
<nav class="tabs"><button class="tab active" data-pg="dash">Today</button><button class="tab" data-pg="food">Food log</button><button class="tab" data-pg="plan">Meal plan</button><button class="tab" data-pg="work">Workout</button><button class="tab" data-pg="prog">Progress</button></nav>

<section id="dash" class="page active"><div class="grid"><div>
<div class="card"><h3>Today</h3><p class="hint">Calories and macros against your target.</p><div id="ring"></div></div>
<div class="card"><h3>Last 7 days</h3><p class="hint" id="wkhint"></p><svg id="wk" viewBox="0 0 320 124" width="100%" role="img" aria-label="Calories logged in the last 7 days"></svg></div>
<div class="card"><h3>Water</h3><p class="hint" id="wathint"></p><div class="bar"><span id="watbar"></span></div><div class="btnrow" id="water"><button class="btn secondary" data-w="250">+250 ml</button><button class="btn secondary" data-w="500">+500 ml</button><button class="btn secondary" data-w="0">Reset</button></div></div>
</div><div>
<div class="card"><h3>Your details</h3><p class="hint">Everything updates as you type.</p><div class="fields">
<div class="field"><label for="p_age">Age</label><input id="p_age" type="number" min="18" max="100"></div>
<div class="field"><label for="p_sex">Sex (for formula)</label><select id="p_sex"><option value="male">Male</option><option value="female">Female</option></select></div>
<div class="field"><label for="p_w">Current weight (kg)</label><input id="p_w" type="number" step=".1" min="30" max="350"></div>
<div class="field"><label for="p_h">Height (cm)</label><input id="p_h" type="number" min="100" max="230"></div>
<div class="field"><label for="p_t">Target weight (kg)</label><input id="p_t" type="number" step=".1" min="30" max="300"></div>
<div class="field"><label for="p_act">Activity</label><select id="p_act"><option value="1.2">Mostly sitting</option><option value="1.375">Lightly active</option><option value="1.55">Moderately active</option><option value="1.725">Very active</option></select></div>
<div class="field" style="grid-column:1/-1"><label for="p_rate">Loss per week</label><select id="p_rate"><option value="0.25">0.25 kg, gradual</option><option value="0.5">0.5 kg, moderate</option><option value="0.75">0.75 kg, faster</option></select></div>
</div></div>
<div class="card" id="targets"></div>
<div class="card"><h3>Coach</h3><div id="ins"></div></div>
</div></div></section>

<section id="food" class="page"><div class="grid"><div>
<div class="card"><h3>Add food</h3><p class="hint">Search common Indian vegetarian foods, then tap to add.</p>
<div class="row two"><input type="date" id="fdate" aria-label="Date"><select id="fmeal" aria-label="Meal"><option>Breakfast</option><option>Lunch</option><option>Snack</option><option>Dinner</option></select></div>
<div class="row two"><input id="fsearch" placeholder="Search: dal, paneer, roti" aria-label="Search foods"><input id="fqty" type="number" value="1" step=".5" min=".5" aria-label="Servings"></div>
<div id="fres" class="list"></div>
<details><summary>Add a custom item</summary><div class="row two"><input id="cn" placeholder="Name"><input id="ck" type="number" placeholder="kcal"></div><div class="row"><input id="cp" type="number" placeholder="Protein g"><input id="cc" type="number" placeholder="Carbs g"><input id="cf" type="number" placeholder="Fat g"></div><button class="btn secondary" id="cadd">Add custom item</button></details></div>
</div><div><div class="card"><h3>Log for the day</h3><p class="hint" id="ftot"></p><div id="flog"></div></div></div></div></section>

<section id="plan" class="page"><div class="card"><h3>7-day Indian vegetarian plan</h3><p class="hint">Portions are estimates. Oil, brands and recipes change the totals. Adding a day scales it to your calorie target.</p><div class="daybtns" id="pdays"></div><div id="pcont"></div><div class="btnrow"><button class="btn" id="padd">Add this day to my log</button></div><div class="note">Carbs and fat are estimated from calories and protein when a day is added. Swap eggs, paneer and tofu as you like.</div></div></section>

<section id="work" class="page"><div class="card"><h3>6-day gym routine</h3><p class="hint" id="wsum"></p><div class="daybtns" id="wdays"></div><div id="wcont"></div><div class="note">Stop each set with 1–3 reps in reserve. Don't eat back machine-estimated calories; they are often inflated.</div></div></section>

<section id="prog" class="page"><div class="grid"><div>
<div class="card"><h3>Weekly check-in</h3><p class="hint">Weigh in at the same time each week, ideally in the morning.</p><div class="fields">
<div class="field"><label for="cd">Date</label><input id="cd" type="date"></div><div class="field"><label for="cw">Weight (kg)</label><input id="cw" type="number" step=".1" min="30" max="350"></div>
<div class="field"><label for="cs">Waist (inches)</label><input id="cs" type="number" step=".1"></div><div class="field"><label for="cst">Avg daily steps</label><input id="cst" type="number"></div>
<div class="field" style="grid-column:1/-1"><label for="csl">Avg sleep (hours)</label><input id="csl" type="number" step=".5" max="24"></div></div>
<div class="btnrow"><button class="btn" id="addChk">Save check-in</button></div></div>
<div class="card"><h3>History</h3><div id="hist"></div></div>
<div class="card"><h3>Backup</h3><p class="hint">Copy the text to keep a backup. Paste it back and restore on any device.</p><textarea id="bkt" rows="4" placeholder="Backup text appears here"></textarea><div class="btnrow"><button class="btn secondary" id="bk">Show backup</button><button class="btn secondary" id="csv">Show CSV</button><button class="btn" id="rs">Restore</button><button class="btn secondary" id="clr">Clear check-ins</button></div></div>
</div><div>
<div class="card"><h3>Snapshot</h3><div class="mg"><div class="metric"><div class="label">Weight change</div><div class="value" id="sw">-</div><small>first to latest</small></div><div class="metric"><div class="label">Waist change</div><div class="value" id="ss">-</div><small>first to latest</small></div><div class="metric"><div class="label">Goal progress</div><div class="value accent" id="sg">-</div><small>of total to lose</small></div><div class="metric"><div class="label">Weekly trend</div><div class="value" id="st">-</div><small>kg per week</small></div></div>
<div class="sub" style="margin-top:14px">Weight (kg): grey is each entry, green is the 3-entry average, dashed is target</div><svg id="chart" viewBox="0 0 320 160" width="100%" role="img" aria-label="Weight history chart"></svg></div>
<div class="card"><h3>How to adjust</h3><div class="food"><div class="foodhead">Trend is falling steadily</div><p>Hold the plan if energy, training and hunger are fine.</p></div><div class="food"><div class="foodhead">Flat for 2–3 weeks</div><p>Check logging accuracy, steps and sleep first. Then trim 100–150 kcal.</p></div><div class="food"><div class="foodhead">Dizzy or exhausted</div><p>Eat more, not less, and speak to a doctor or dietitian.</p></div></div>
</div></div></section>
</div><div id="toast" role="status"></div>
<script>
const $=s=>document.querySelector(s),$$=s=>[...document.querySelectorAll(s)];
const K='fitcalc_pro_v2',iso=d=>new Date(d.getTime()-d.getTimezoneOffset()*6e4).toISOString().slice(0,10),TD=()=>iso(new Date());
const D={p:{age:21,sex:'male',w:73,h:162,t:55,act:1.375,rate:.5},foods:[],chk:[],water:{},wk:{}};
const cl=o=>JSON.parse(JSON.stringify(o));let S=cl(D);
try{const x=JSON.parse(localStorage.getItem(K)||'null');if(x)S={...S,...x,p:{...D.p,...x.p}}}catch(e){}
const save=()=>{try{localStorage.setItem(K,JSON.stringify(S))}catch(e){}};
const esc=s=>String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const r1=n=>Math.round(n*10)/10,uid=()=>Math.random().toString(36).slice(2,9);
const toast=t=>{const e=$('#toast');e.textContent=t;e.classList.add('show');clearTimeout(e._t);e._t=setTimeout(()=>e.classList.remove('show'),2300)};
const MEALS=['Breakfast','Lunch','Snack','Dinner'],DAYS=['Mon','Tue','Wed','Thu','Fri','Sat','Sun'];
const DB=[['Roti (1 medium)',100,3,19,1.5],['Cooked rice (1 cup)',205,4,45,.4],['Dal (1 bowl)',150,9,22,3],['Rajma (1 bowl)',210,11,32,4],['Chole (1 bowl)',230,10,34,6],['Paneer (100 g)',265,18,4,20],['Tofu (100 g)',120,13,3,7],['Soya chunks (30 g dry)',105,16,10,.5],['Curd (100 g)',60,3.5,5,3],['Toned milk (200 ml)',120,6.5,9.5,6],['Besan chilla (1)',130,6,15,5],['Idli (2)',130,4,26,.5],['Dosa (1 plain)',165,4,28,4],['Sambar (1 bowl)',110,5,16,3],['Poha (1 plate)',250,5,45,6],['Upma (1 plate)',270,6,40,9],['Oats (40 g) with milk',230,10,35,6],['Egg (1 boiled)',75,6.5,.5,5],['Mixed sabzi (1 bowl)',100,3,12,4],['Roasted chana (30 g)',110,6,17,2],['Sprouts salad (1 bowl)',120,9,19,1],['Banana (1)',105,1.3,27,.4],['Apple (1)',95,.5,25,.3],['Peanuts (20 g)',115,5,3,10],['Whey protein (1 scoop)',120,24,3,1.5],['Chai with milk and sugar',90,2,13,3]];
const PLAN=[
[['Besan chilla + curd',330,17,'2 chillas, 100 g curd'],['Dal, roti, sabzi',500,20,'1 bowl dal, 2 rotis, 1 bowl sabzi'],['Roasted chana + chai',180,7,'30 g chana, measured milk'],['Tofu bhurji + roti',430,25,'150 g tofu, 2 small rotis']],
[['Paneer roti + curd',390,20,'1 roti with 70 g paneer, 100 g curd'],['Rajma + roti',480,19,'1 bowl rajma, 2 rotis, salad'],['Fruit + milk',200,7,'1 fruit, 200 ml toned milk'],['Soya keema + roti',420,28,'40 g dry soya, 2 small rotis']],
[['Oats with milk + nuts',330,14,'40 g oats, 200 ml milk, 5 almonds'],['Chole + rice',520,18,'1 bowl chole, 3/4 cup rice, salad'],['Sprouts salad',150,10,'1 bowl, lemon, onion'],['Paneer sabzi + roti',450,24,'80 g paneer, 2 rotis']],
[['Moong dal chilla',300,16,'2 chillas, mint chutney'],['Sambar rice + curd',480,16,'1 cup rice, sambar, 100 g curd'],['Whey shake + banana',230,25,'1 scoop, 1 banana'],['Tofu stir-fry + roti',400,24,'150 g tofu, vegetables, 2 rotis']],
[['Idli + sambar',300,11,'3 idlis, 1 bowl sambar'],['Dal khichdi + curd',480,19,'1.5 cups khichdi, 100 g curd'],['Buttermilk + chana',150,8,'1 glass, 25 g chana'],['Soya pulao',430,27,'40 g dry soya, 3/4 cup rice, raita']],
[['Poha + curd',350,12,'1 plate with peanuts, 100 g curd'],['Rajma + roti',480,20,'1 bowl rajma, 2 rotis'],['Fruit + curd',180,6,'1 fruit, 100 g curd'],['Paneer bhurji + roti',450,26,'100 g paneer, 2 rotis']],
[['Veg upma + milk',360,12,'1 plate upma, 150 ml milk'],['Dal, roti, sabzi',500,20,'1 bowl dal, 2 rotis, sabzi'],['Sprouts chaat',170,9,'1 bowl sprouts, tomato, lemon'],['Palak tofu + roti',400,24,'150 g tofu, 2 rotis']]];
const WK=[{n:'Push',ex:[['Chest press','3 x 8–10'],['Incline dumbbell press','3 x 10'],['Shoulder press','3 x 10'],['Lateral raise','3 x 15'],['Triceps pushdown','3 x 12']]},
{n:'Pull',ex:[['Lat pulldown','3 x 10'],['Seated row','3 x 10'],['Face pull','3 x 15'],['Dumbbell curl','3 x 12'],['Back extension','2 x 12']]},
{n:'Legs',ex:[['Goblet squat or leg press','3 x 10'],['Romanian deadlift','3 x 10'],['Walking lunge','3 x 12'],['Leg curl','3 x 12'],['Calf raise','3 x 15']]},
{n:'Upper',ex:[['Incline machine press','3 x 10'],['Cable row','3 x 10'],['Arnold press','3 x 10'],['Cable fly','2 x 15'],['Hammer curl','2 x 12']]},
{n:'Lower and core',ex:[['Leg press','3 x 12'],['Hip thrust','3 x 10'],['Step-up','3 x 10'],['Plank','3 x 40 s'],['Hanging knee raise','3 x 12']]},
{n:'Cardio and mobility',ex:[['Incline walk, easy pace','30 min'],['Mobility flow','10 min'],['Core circuit','2 rounds']]},
{n:'Rest day',ex:[['Easy walk','20–30 min'],['Stretching','10 min']]}];
function calc(){const p=S.p,bmr=10*p.w+6.25*p.h-5*p.age+(p.sex=='male'?5:-161),tdee=Math.round(bmr*p.act),fl=p.sex=='male'?1500:1200,raw=Math.round((tdee-p.rate*1100)/50)*50,cal=Math.max(fl,raw),pro=Math.round(p.w*1.6),fat=Math.round(cal*.25/9),carb=Math.max(0,Math.round((cal-pro*4-fat*9)/4)),lose=p.w-p.t,eff=Math.max(0,(tdee-cal)/1100);
return{tdee,fl,raw,cal,pro,fat,carb,lose,bmi:p.w/(p.h/100)**2,tbmi:p.t/(p.h/100)**2,wks:eff>0&&lose>0?Math.ceil(lose/eff):0,water:r1(p.w*.035)}}
function dayTot(d){return S.foods.filter(f=>f.d==d).reduce((a,f)=>(a.k+=f.k,a.p+=f.p,a.c+=f.c,a.f+=f.f,a.n++,a),{k:0,p:0,c:0,f:0,n:0})}
function trend(){const a=[...S.chk].sort((x,y)=>x.d>y.d?1:-1),n=a.length;if(n<3)return null;const t0=new Date(a[0].d),xs=a.map(e=>(new Date(e.d)-t0)/864e5),ys=a.map(e=>e.w);if(xs[n-1]<10)return null;const mx=xs.reduce((s,v)=>s+v)/n,my=ys.reduce((s,v)=>s+v)/n,den=xs.reduce((s,v)=>s+(v-mx)**2,0);return den?-(xs.reduce((s,v,i)=>s+(v-mx)*(ys[i]-my),0)/den)*7:null}
const mbar=(n,v,g,u)=>`<div><div class="mbh"><span>${n}</span><span>${Math.round(v)} / ${g} ${u}</span></div><div class="bar"><span style="width:${Math.min(100,v/g*100)}%"></span></div></div>`;
const met=(l,v,s,a)=>`<div class="metric"><div class="label">${l}</div><div class="value ${a?'accent':''}">${v}</div><small>${s}</small></div>`;
function rDash(){const c=calc(),t=dayTot(TD()),R=52,C=2*Math.PI*R,over=t.k>c.cal,pct=Math.min(1,t.k/c.cal);
$('#ring').innerHTML=`<div class="ringwrap"><svg viewBox="0 0 120 120" width="132" height="132" role="img" aria-label="${Math.round(t.k)} of ${c.cal} calories"><circle cx="60" cy="60" r="${R}" fill="none" stroke="var(--p2)" stroke-width="11"/><circle cx="60" cy="60" r="${R}" fill="none" stroke="${over?'var(--warn)':'var(--acc)'}" stroke-width="11" stroke-linecap="round" stroke-dasharray="${C}" stroke-dashoffset="${C*(1-pct)}" transform="rotate(-90 60 60)"/><text x="60" y="58" text-anchor="middle" font-size="22" font-weight="800" fill="var(--text)">${Math.round(t.k)}</text><text x="60" y="74" text-anchor="middle" font-size="9" fill="var(--muted)">of ${c.cal} kcal</text></svg><div class="macros">${mbar('Protein',t.p,c.pro,'g')}${mbar('Carbs',t.c,c.ca
