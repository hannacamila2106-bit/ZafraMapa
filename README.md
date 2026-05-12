# ZafraMapa
<!DOCTYPE html>

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zafra Mapa — Tuxtepec, Oaxaca</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=Syne:wght@400;600;700;800&family=Lora:ital,wght@0,400;0,500;1,400;1,500&display=swap" rel="stylesheet">
<style>
:root {
  --ink:       #0d0f0a;
  --ink2:      #1a1d14;
  --paper:     #f0ebe0;
  --paper2:    #e8e0d0;
  --smoke:     #8a8878;
  --gold:      #c8a84b;
  --gold2:     #e8c86a;
  --green:     #2e5c3a;
  --green2:    #4a8a5c;
  --ember:     #c43a1a;
  --fog:       rgba(240,235,224,0.06);
  --line:      rgba(240,235,224,0.12);
}
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior:smooth; }
body {
  background: var(--ink);
  color: var(--paper);
  font-family: 'Lora', Georgia, serif;
  overflow-x: hidden;
}
body::before {
  content:'';
  position:fixed; inset:0; z-index:999; pointer-events:none;
  opacity:0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

/* NAV */
nav {
position:fixed; top:0; left:0; right:0; z-index:100;
display:flex; align-items:center; justify-content:space-between;
padding:20px 56px;
border-bottom:1px solid var(–line);
background:rgba(13,15,10,0.88);
backdrop-filter:blur(16px);
}
.nav-wordmark {
font-family:‘Syne’,sans-serif;
font-weight:800; font-size:1.1rem;
letter-spacing:0.12em; text-transform:uppercase;
color:var(–paper);
}
.nav-wordmark em { color:var(–gold); font-style:normal; }
.nav-links { display:flex; gap:36px; list-style:none; }
.nav-links a {
font-family:‘Syne’,sans-serif;
font-size:0.7rem; font-weight:600;
letter-spacing:0.14em; text-transform:uppercase;
color:var(–smoke); text-decoration:none;
transition:color 0.25s;
}
.nav-links a:hover { color:var(–paper); }
.nav-pill {
font-family:‘Syne’,sans-serif;
font-size:0.68rem; font-weight:700;
letter-spacing:0.12em; text-transform:uppercase;
color:var(–ink); background:var(–gold);
padding:9px 20px; border-radius:2px;
text-decoration:none; transition:background 0.2s;
}
.nav-pill:hover { background:var(–gold2); }

/* HERO */
#hero {
min-height:100vh;
display:grid; grid-template-rows:1fr auto;
position:relative; overflow:hidden;
}
.hero-cane-bg {
position:absolute; inset:0; z-index:0; overflow:hidden;
}
.hero-cane-bg svg { width:100%; height:100%; opacity:0.07; }

.ash-field { position:absolute; inset:0; z-index:1; pointer-events:none; }
.ash-particle {
position:absolute; border-radius:50%;
background:var(–paper);
animation:ashFall linear infinite; opacity:0;
}
@keyframes ashFall {
0%   { opacity:0; transform:translateY(-20px) rotate(0deg); }
10%  { opacity:0.4; }
90%  { opacity:0.1; }
100% { opacity:0; transform:translateY(100vh) rotate(200deg); }
}

.hero-inner {
position:relative; z-index:2;
display:grid; grid-template-columns:1fr 400px;
gap:0; align-items:end;
padding:160px 56px 0;
min-height:calc(100vh - 120px);
}

.hero-eyebrow {
display:inline-flex; align-items:center; gap:10px;
font-family:‘Syne’,sans-serif;
font-size:0.68rem; font-weight:700;
letter-spacing:0.18em; text-transform:uppercase;
color:var(–gold); margin-bottom:32px;
}
.hero-eyebrow::before {
content:’’; display:block; width:32px; height:1px; background:var(–gold);
}
.hero-h1 {
font-family:‘DM Serif Display’,serif;
font-size:clamp(4.5rem,9vw,8.5rem);
line-height:0.93; letter-spacing:-0.03em;
color:var(–paper); margin-bottom:48px;
}
.hero-h1 .it { font-style:italic; color:var(–gold); }
.hero-h1 .l2 { display:block; padding-left:80px; }
.hero-h1 .l3 { display:block; color:var(–green2); }

.hero-desc {
max-width:520px; font-size:1.05rem; line-height:1.8;
color:rgba(240,235,224,0.55); margin-bottom:48px;
}
.hero-desc strong { color:var(–paper); font-weight:500; }
.hero-actions { display:flex; gap:16px; align-items:center; }
.btn-dark {
font-family:‘Syne’,sans-serif; font-size:0.72rem; font-weight:700;
letter-spacing:0.14em; text-transform:uppercase;
background:var(–paper); color:var(–ink);
padding:14px 32px; border-radius:2px;
text-decoration:none; transition:all 0.2s;
}
.btn-dark:hover { background:var(–gold); }
.btn-ghost {
font-family:‘Syne’,sans-serif; font-size:0.72rem; font-weight:600;
letter-spacing:0.14em; text-transform:uppercase;
color:var(–smoke); text-decoration:none;
display:flex; align-items:center; gap:10px; transition:color 0.2s;
}
.btn-ghost:hover { color:var(–paper); }
.btn-ghost::after { content:‘↓’; font-size:1rem; }

.hero-right { padding:0 0 0 48px; align-self:end; }
.stats-card {
background:var(–fog); border:1px solid var(–line);
border-bottom:none; padding:36px 32px;
}
.stats-card-title {
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:700;
letter-spacing:0.18em; text-transform:uppercase;
color:var(–smoke); margin-bottom:28px;
}
.stat-row {
display:flex; justify-content:space-between; align-items:baseline;
padding:16px 0; border-bottom:1px solid var(–line);
}
.stat-row:last-of-type { border-bottom:none; }
.stat-val {
font-family:‘DM Serif Display’,serif;
font-size:2.8rem; color:var(–gold); line-height:1;
}
.stat-lbl {
font-family:‘Syne’,sans-serif; font-size:0.68rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase;
color:var(–smoke); text-align:right; max-width:120px;
}
.progress-row { padding:20px 0 0; }
.progress-label {
display:flex; justify-content:space-between;
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase;
color:var(–smoke); margin-bottom:8px;
}
.progress-track { height:3px; background:rgba(240,235,224,0.1); }
.progress-fill { height:100%; background:var(–gold); transition:width 1.5s cubic-bezier(0.4,0,0.2,1); }
.hero-note {
font-family:‘Syne’,sans-serif; font-size:0.6rem;
letter-spacing:0.1em; color:rgba(240,235,224,0.28);
text-align:center; margin-top:12px; font-style:italic;
}

.hero-ticker {
position:relative; z-index:2;
border-top:1px solid var(–line);
padding:20px 56px;
display:flex; gap:56px; align-items:center; overflow:hidden;
}
.ticker-item {
display:flex; gap:12px; align-items:center;
white-space:nowrap; flex-shrink:0;
font-family:‘Syne’,sans-serif; font-size:0.68rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase; color:var(–smoke);
}
.ticker-dot { width:6px; height:6px; border-radius:50%; background:var(–gold); }

/* SHARED */
.section-label {
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:700;
letter-spacing:0.2em; text-transform:uppercase; color:var(–gold);
display:flex; align-items:center; gap:12px; margin-bottom:20px;
}
.section-label::before { content:’’; display:block; width:24px; height:1px; background:var(–gold); }
h2.display {
font-family:‘DM Serif Display’,serif;
font-size:clamp(2.8rem,5vw,4.5rem);
line-height:1; letter-spacing:-0.02em;
color:var(–paper); margin-bottom:24px;
}
h2.display .it { font-style:italic; color:var(–gold); }
.lead-text { font-size:1.05rem; line-height:1.85; color:rgba(240,235,224,0.5); max-width:580px; }

/* PROYECTO */
#proyecto {
padding:120px 56px; border-top:1px solid var(–line); position:relative; overflow:hidden;
}
#proyecto::after {
content:‘01’; position:absolute; right:40px; top:60px;
font-family:‘DM Serif Display’,serif; font-size:20rem;
color:rgba(240,235,224,0.02); line-height:1;
pointer-events:none; user-select:none;
}
.proyecto-layout { display:grid; grid-template-columns:1fr 1fr; gap:80px; align-items:start; }
.proyecto-quote {
font-family:‘DM Serif Display’,serif; font-size:1.9rem; font-style:italic;
line-height:1.35; color:var(–gold);
border-left:2px solid var(–gold); padding-left:28px; margin:40px 0 48px;
}
.proyecto-body { font-size:0.88rem; line-height:1.85; color:var(–smoke); }
.pilares { display:grid; grid-template-columns:1fr 1fr; gap:1px; margin-top:60px; background:var(–line); }
.pilar {
background:var(–ink2); padding:28px 24px; transition:background 0.25s;
}
.pilar:hover { background:rgba(200,168,75,0.06); }
.pilar-num {
font-family:‘DM Serif Display’,serif; font-size:3rem;
color:rgba(200,168,75,0.2); line-height:1; margin-bottom:12px;
}
.pilar h4 {
font-family:‘Syne’,sans-serif; font-size:0.75rem; font-weight:700;
letter-spacing:0.1em; text-transform:uppercase; color:var(–paper); margin-bottom:10px;
}
.pilar p { font-size:0.8rem; line-height:1.65; color:var(–smoke); }

.proyecto-visual { position:sticky; top:100px; }
.cane-illustration {
width:100%; aspect-ratio:3/4;
border:1px solid var(–line); position:relative; overflow:hidden;
}
.cane-illustration svg { width:100%; height:100%; }
.cane-caption {
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:600;
letter-spacing:0.14em; text-transform:uppercase; color:var(–smoke);
margin-top:16px; padding-top:16px; border-top:1px solid var(–line);
}

/* COLECTOR */
#colector { border-top:1px solid var(–line); position:relative; }
#colector::after {
content:‘02’; position:absolute; right:40px; top:60px;
font-family:‘DM Serif Display’,serif; font-size:20rem;
color:rgba(240,235,224,0.02); line-height:1;
pointer-events:none; user-select:none;
}
.colector-header {
padding:80px 56px 60px;
display:grid; grid-template-columns:1fr 1fr; gap:80px; align-items:end;
}
.steps-grid { display:grid; grid-template-columns:repeat(3,1fr); background:var(–line); gap:1px; }
.step {
background:var(–ink); padding:40px 32px;
position:relative; overflow:hidden; transition:background 0.25s;
}
.step:hover { background:var(–fog); }
.step-n {
font-family:‘DM Serif Display’,serif; font-size:5rem;
color:rgba(200,168,75,0.12); line-height:1;
position:absolute; top:16px; right:20px;
}
.step-icon-wrap {
width:44px; height:44px; border:1px solid var(–line);
display:flex; align-items:center; justify-content:center;
font-size:1.3rem; margin-bottom:24px;
}
.step h3 {
font-family:‘Syne’,sans-serif; font-size:0.78rem; font-weight:700;
letter-spacing:0.1em; text-transform:uppercase; color:var(–paper); margin-bottom:14px;
}
.step p { font-size:0.8rem; line-height:1.7; color:var(–smoke); }
.step-spec {
margin-top:16px; font-family:‘Syne’,sans-serif; font-size:0.63rem; font-weight:700;
letter-spacing:0.12em; text-transform:uppercase; color:var(–gold);
display:flex; align-items:center; gap:6px;
}
.step-spec::before { content:’—’; }

.colector-strip { display:grid; grid-template-columns:1fr 1fr; background:var(–line); gap:1px; border-top:1px solid var(–line); }
.strip-col { background:var(–ink); padding:60px 56px; }

.cartulina-demo {
width:180px; height:234px; border:1.5px solid rgba(200,168,75,0.4);
background:rgba(240,235,224,0.02); position:relative; margin:0 auto 20px;
}
.tape-layer { position:absolute; inset:10px; border:1px dashed rgba(200,168,75,0.2); }
.ash-sim { position:absolute; border-radius:50%; background:rgba(240,235,224,0.65); }
.dim-label {
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:700;
letter-spacing:0.14em; text-transform:uppercase; color:var(–gold);
text-align:center; display:block;
}

.spec-list { list-style:none; }
.spec-list li {
display:flex; gap:16px; align-items:flex-start;
padding:16px 0; border-bottom:1px solid var(–line);
font-size:0.82rem; line-height:1.6;
}
.spec-list li:last-child { border-bottom:none; }
.spec-list .ico { font-size:1rem; flex-shrink:0; margin-top:1px; width:22px; text-align:center; }
.spec-list strong { display:block; color:var(–paper); font-weight:500; font-style:italic; }
.spec-list span { color:var(–smoke); }

/* MÉTODO */
#metodo { padding:120px 56px; border-top:1px solid var(–line); position:relative; }
#metodo::after {
content:‘03’; position:absolute; right:40px; top:60px;
font-family:‘DM Serif Display’,serif; font-size:20rem;
color:rgba(240,235,224,0.02); line-height:1;
pointer-events:none; user-select:none;
}
.metodo-layout { display:grid; grid-template-columns:1fr 1fr; gap:80px; margin-top:60px; }
.metodo-explainer p { font-size:0.9rem; line-height:1.88; color:var(–smoke); margin-bottom:20px; }
.metodo-explainer p strong { color:var(–paper); font-weight:500; }

.process-steps { margin-top:40px; }
.process-step {
display:grid; grid-template-columns:48px 1fr; gap:20px;
padding:20px 0; border-bottom:1px solid var(–line); align-items:start;
}
.process-step:last-child { border-bottom:none; }
.ps-num { font-family:‘DM Serif Display’,serif; font-size:1.8rem; color:var(–gold); line-height:1; }
.ps-text h4 {
font-family:‘Syne’,sans-serif; font-size:0.73rem; font-weight:700;
letter-spacing:0.1em; text-transform:uppercase; color:var(–paper); margin-bottom:6px;
}
.ps-text p { font-size:0.78rem; line-height:1.65; color:var(–smoke); }

.fotos-panel { background:var(–ink2); border:1px solid var(–line); padding:40px; }
.fotos-panel h3 {
font-family:‘DM Serif Display’,serif; font-size:1.8rem; font-style:italic;
color:var(–paper); margin-bottom:6px;
}
.fotos-panel .sub {
font-family:‘Syne’,sans-serif; font-size:0.63rem; font-weight:600;
letter-spacing:0.14em; text-transform:uppercase; color:var(–smoke); margin-bottom:32px;
}
.foto-pair { display:grid; grid-template-columns:1fr 1fr; gap:16px; }
.foto-box { border:1px solid var(–line); padding:20px; }
.foto-tag {
font-family:‘Syne’,sans-serif; font-size:0.58rem; font-weight:700;
letter-spacing:0.16em; text-transform:uppercase; color:var(–gold);
margin-bottom:14px; display:block;
}
.foto-frame {
width:100%; aspect-ratio:4/3; border:1px dashed rgba(240,235,224,0.1);
display:flex; align-items:center; justify-content:center; font-size:1.8rem;
margin-bottom:14px; position:relative; background:rgba(240,235,224,0.02);
}
.foto-dist-badge {
position:absolute; bottom:8px; right:8px;
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:700; letter-spacing:0.1em;
background:var(–gold); color:var(–ink); padding:3px 8px;
}
.foto-box h4 {
font-family:‘Syne’,sans-serif; font-size:0.7rem; font-weight:700;
letter-spacing:0.08em; text-transform:uppercase; color:var(–paper); margin-bottom:6px;
}
.foto-box p { font-size:0.73rem; line-height:1.55; color:var(–smoke); }

.density-scale { margin-top:28px; padding-top:24px; border-top:1px solid var(–line); }
.density-scale-title {
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:700;
letter-spacing:0.16em; text-transform:uppercase; color:var(–smoke); margin-bottom:12px;
}
.scale-bar {
height:8px; border-radius:1px; margin-bottom:8px;
background:linear-gradient(90deg,#6aad80,#c8a84b,#e07040,#1a3a6a);
}
.scale-labels {
display:flex; justify-content:space-between;
font-family:‘Syne’,sans-serif; font-size:0.58rem; font-weight:600;
letter-spacing:0.08em; color:var(–smoke);
}
.density-pills { display:flex; gap:8px; flex-wrap:wrap; margin-top:16px; }
.dpill {
display:flex; align-items:center; gap:8px;
border:1px solid var(–line); padding:5px 10px;
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:600;
letter-spacing:0.08em; text-transform:uppercase; color:var(–smoke);
}
.dpill-dot { width:7px; height:7px; border-radius:50%; }

/* MAPA */
#mapa { border-top:1px solid var(–line); position:relative; }
#mapa::after {
content:‘04’; position:absolute; right:40px; top:60px;
font-family:‘DM Serif Display’,serif; font-size:20rem;
color:rgba(240,235,224,0.02); line-height:1;
pointer-events:none; user-select:none; z-index:0;
}
.mapa-header { padding:80px 56px 40px; position:relative; z-index:1; }
.mapa-wrap { border-top:1px solid var(–line); position:relative; z-index:1; }
#svgmap-container { width:100%; height:560px; background:#080b06; overflow:hidden; cursor:crosshair; }
#svgmap-container svg { width:100%; height:100%; }
.mapa-footer {
padding:22px 56px; border-top:1px solid var(–line);
display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:16px;
}
.leyenda { display:flex; gap:24px; flex-wrap:wrap; }
.ley-item {
display:flex; align-items:center; gap:8px;
font-family:‘Syne’,sans-serif; font-size:0.62rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase; color:var(–smoke);
}
.ley-dot { width:10px; height:10px; border-radius:50%; }
.mapa-sim-note {
font-family:‘Syne’,sans-serif; font-size:0.58rem;
letter-spacing:0.1em; color:rgba(240,235,224,0.22); font-style:italic;
}

/* PARTICIPA */
#participa { border-top:1px solid var(–line); display:grid; grid-template-columns:1fr 1fr; background:var(–line); gap:1px; }
.participa-col { background:var(–ink); padding:80px 56px; }

.form-label {
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:700;
letter-spacing:0.14em; text-transform:uppercase; color:var(–smoke);
display:block; margin-bottom:8px;
}
.form-input, .form-select, .form-textarea {
width:100%; background:transparent; border:none;
border-bottom:1px solid var(–line); color:var(–paper);
font-family:‘Lora’,serif; font-size:0.88rem;
padding:10px 0; outline:none; transition:border-color 0.25s; margin-bottom:28px;
}
.form-input:focus, .form-select:focus, .form-textarea:focus { border-bottom-color:var(–gold); }
.form-input::placeholder, .form-textarea::placeholder { color:rgba(240,235,224,0.2); }
.form-select option { background:var(–ink2); color:var(–paper); }
.form-textarea { resize:vertical; min-height:80px; }

.upload-zone {
border:1px dashed rgba(200,168,75,0.3); padding:28px; text-align:center;
cursor:pointer; margin-bottom:28px; transition:background 0.2s;
}
.upload-zone:hover { background:rgba(200,168,75,0.04); }
.upload-zone .uz-icon { font-size:1.6rem; margin-bottom:8px; }
.upload-zone p {
font-family:‘Syne’,sans-serif; font-size:0.63rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase; color:var(–smoke);
}
.upload-zone strong { color:var(–gold); }

.radio-row { display:flex; gap:10px; margin-bottom:28px; }
.radio-chip {
border:1px solid var(–line); padding:8px 14px; cursor:pointer;
font-family:‘Syne’,sans-serif; font-size:0.63rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase; color:var(–smoke); transition:all 0.2s;
}
.radio-chip:hover, .radio-chip.active { border-color:var(–gold); color:var(–gold); background:rgba(200,168,75,0.06); }

.btn-submit {
width:100%; padding:18px; background:var(–gold); color:var(–ink);
font-family:‘Syne’,sans-serif; font-size:0.75rem; font-weight:800;
letter-spacing:0.18em; text-transform:uppercase;
border:none; cursor:pointer; transition:background 0.2s;
}
.btn-submit:hover { background:var(–gold2); }

.info-item {
padding:28px 0; border-bottom:1px solid var(–line);
display:grid; grid-template-columns:40px 1fr; gap:20px; align-items:start;
}
.info-item:last-child { border-bottom:none; }
.info-ico { font-size:1.1rem; margin-top:2px; }
.info-item h4 {
font-family:‘Syne’,sans-serif; font-size:0.73rem; font-weight:700;
letter-spacing:0.1em; text-transform:uppercase; color:var(–paper); margin-bottom:8px;
}
.info-item p { font-size:0.82rem; line-height:1.72; color:var(–smoke); }

/* NOSOTROS */
#nosotros { border-top:1px solid var(–line); display:grid; grid-template-columns:1fr 1fr; background:var(–line); gap:1px; }
.nosotros-col { background:var(–ink); padding:80px 56px; }
.nosotros-col.tinted { background:var(–fog); }

.persona-initials {
width:80px; height:80px; border:1px solid var(–line);
display:flex; align-items:center; justify-content:center;
font-family:‘DM Serif Display’,serif; font-size:1.3rem; color:var(–gold);
margin-bottom:28px; letter-spacing:0.05em;
}
.persona-name {
font-family:‘DM Serif Display’,serif; font-size:2.2rem;
line-height:1.1; color:var(–paper); margin-bottom:8px;
}
.persona-role {
font-family:‘Syne’,sans-serif; font-size:0.63rem; font-weight:700;
letter-spacing:0.18em; text-transform:uppercase; color:var(–gold); margin-bottom:28px;
}
.persona-bio { font-size:0.88rem; line-height:1.82; color:var(–smoke); margin-bottom:16px; }
.inst-block { margin-top:40px; padding-top:32px; border-top:1px solid var(–line); }
.inst-tag {
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:700;
letter-spacing:0.18em; text-transform:uppercase; color:var(–smoke); margin-bottom:8px;
}
.inst-name { font-family:‘DM Serif Display’,serif; font-size:1.4rem; color:var(–paper); margin-bottom:8px; }
.inst-desc { font-size:0.82rem; line-height:1.72; color:var(–smoke); }

.mision-h {
font-family:‘DM Serif Display’,serif; font-size:2.4rem; font-style:italic;
line-height:1.15; color:var(–paper); margin-bottom:28px; margin-top:28px;
}
.mision-body { font-size:0.88rem; line-height:1.85; color:var(–smoke); margin-bottom:18px; }
.tag-cloud { display:flex; flex-wrap:wrap; gap:8px; margin-top:32px; }
.tag-pill {
border:1px solid var(–line); padding:6px 14px;
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:600;
letter-spacing:0.1em; text-transform:uppercase; color:var(–smoke); transition:all 0.2s;
}
.tag-pill:hover { border-color:var(–gold); color:var(–gold); }

/* FAQ */
#faq {
border-top:1px solid var(–line); padding:80px 56px;
display:grid; grid-template-columns:260px 1fr; gap:80px;
}
.faq-sidebar h2 { margin-bottom:20px; }
.faq-sidebar .lead-text { font-size:0.86rem; }
.faq-contact { margin-top:40px; padding-top:32px; border-top:1px solid var(–line); }
.faq-contact p { font-size:0.8rem; line-height:1.7; color:var(–smoke); margin-bottom:20px; }
.btn-email {
font-family:‘Syne’,sans-serif; font-size:0.68rem; font-weight:700;
letter-spacing:0.12em; text-transform:uppercase; color:var(–gold);
text-decoration:none; display:flex; align-items:center; gap:8px; transition:gap 0.2s;
}
.btn-email:hover { gap:14px; }
.btn-email::after { content:‘→’; }

.faq-item { border-bottom:1px solid var(–line); }
.faq-q {
padding:24px 0; display:flex; justify-content:space-between; align-items:center;
cursor:pointer; gap:24px; font-size:0.95rem; font-weight:500;
color:rgba(240,235,224,0.7); transition:color 0.2s; user-select:none;
}
.faq-q:hover { color:var(–paper); }
.faq-toggle {
font-family:‘Syne’,sans-serif; font-size:0.7rem; font-weight:700;
color:var(–gold); flex-shrink:0; transition:transform 0.3s;
}
.faq-item.open .faq-toggle { transform:rotate(45deg); }
.faq-item.open .faq-q { color:var(–paper); }
.faq-a {
max-height:0; overflow:hidden;
transition:max-height 0.35s ease,padding 0.35s;
font-size:0.85rem; line-height:1.82; color:var(–smoke);
}
.faq-item.open .faq-a { max-height:300px; padding-bottom:24px; }

/* FOOTER */
footer {
border-top:1px solid var(–line); padding:60px 56px;
display:grid; grid-template-columns:1fr 1fr 1fr; gap:40px;
}
.footer-wordmark {
font-family:‘DM Serif Display’,serif; font-size:2.5rem;
color:var(–paper); line-height:1; margin-bottom:16px;
}
.footer-wordmark em { font-style:italic; color:var(–gold); }
.footer-tagline { font-size:0.82rem; line-height:1.7; color:var(–smoke); }
.footer-col-title {
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:700;
letter-spacing:0.16em; text-transform:uppercase; color:var(–smoke); margin-bottom:20px;
}
.footer-col a {
display:block; font-size:0.8rem; color:rgba(240,235,224,0.35);
text-decoration:none; margin-bottom:10px; transition:color 0.2s;
}
.footer-col a:hover { color:var(–paper); }
.footer-bottom {
border-top:1px solid var(–line); padding:22px 56px;
display:flex; justify-content:space-between; align-items:center;
font-family:‘Syne’,sans-serif; font-size:0.6rem; font-weight:600;
letter-spacing:0.12em; text-transform:uppercase; color:rgba(240,235,224,0.22);
}

/* ANIMATIONS */
.fade-up { opacity:0; transform:translateY(28px); transition:opacity 0.8s ease,transform 0.8s ease; }
.fade-up.in { opacity:1; transform:translateY(0); }
.fade-up.d1 { transition-delay:0.1s; }
.fade-up.d2 { transition-delay:0.2s; }
.fade-up.d3 { transition-delay:0.3s; }

/* RESPONSIVE */
@media(max-width:960px){
nav{padding:16px 24px;}
.nav-links{display:none;}
.hero-inner{grid-template-columns:1fr;padding:120px 24px 40px;}
.hero-right{padding:0;}
.hero-h1{font-size:3.8rem;}
.hero-h1 .l2{padding-left:30px;}
.hero-ticker{padding:16px 24px;}
#proyecto,#metodo,#faq,footer{padding-left:24px;padding-right:24px;}
.proyecto-layout,.metodo-layout{grid-template-columns:1fr;gap:40px;}
.colector-header{padding:60px 24px;grid-template-columns:1fr;}
.steps-grid{grid-template-columns:1fr;}
.colector-strip,.strip-col{padding-left:24px;padding-right:24px;}
#participa,#nosotros{grid-template-columns:1fr;}
.participa-col,.nosotros-col{padding:60px 24px;}
.mapa-header,.mapa-footer{padding-left:24px;padding-right:24px;}
#faq{grid-template-columns:1fr;gap:40px;padding:60px 24px;}
footer{grid-template-columns:1fr;padding:40px 24px;}
.footer-bottom{padding:16px 24px;flex-direction:column;gap:8px;text-align:center;}
}
</style>

</head>
<body>

<!-- NAV -->

<nav>
  <div class="nav-wordmark">Zafra <em>Mapa</em></div>
  <ul class="nav-links">
    <li><a href="#proyecto">Proyecto</a></li>
    <li><a href="#ciencia-ciudadana">Ciencia ciudadana</a></li>
    <li><a href="#colector">Participar</a></li>
    <li><a href="#metodo">Método</a></li>
    <li><a href="#mapa">Mapa</a></li>
    <li><a href="#nosotros">Nosotros</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="#participa" class="nav-pill">Enviar datos →</a>
</nav>

<!-- HERO -->

<section id="hero">
  <div class="hero-cane-bg">
    <svg viewBox="0 0 1440 900" preserveAspectRatio="xMidYMid slice" xmlns="http://www.w3.org/2000/svg">
      <g stroke="#c8a84b" stroke-width="1.5" fill="none">
        <path d="M80,900 Q92,680 78,460 Q64,240 86,20"/>
        <path d="M130,900 Q145,700 130,480 Q115,260 136,40"/>
        <path d="M180,900 Q168,720 180,500 Q192,280 174,60"/>
        <path d="M230,900 Q245,690 230,470 Q215,250 236,30"/>
        <path d="M280,900 Q268,710 280,490 Q293,270 276,50"/>
        <path d="M78,460 Q126,442 148,416" stroke-width="1"/>
        <path d="M78,460 Q30,446 8,420" stroke-width="1"/>
        <path d="M130,480 Q178,462 200,436" stroke-width="1"/>
        <path d="M130,480 Q82,466 60,440" stroke-width="1"/>
        <path d="M180,500 Q228,482 250,456" stroke-width="1"/>
        <path d="M86,240 Q132,224 154,198" stroke-width="1"/>
        <path d="M136,260 Q100,246 78,220" stroke-width="1"/>
        <path d="M1200,900 Q1215,680 1200,460 Q1185,240 1206,20"/>
        <path d="M1260,900 Q1248,720 1260,500 Q1273,280 1256,60"/>
        <path d="M1320,900 Q1335,700 1320,480 Q1305,260 1326,40"/>
        <path d="M1380,900 Q1368,710 1380,490 Q1393,270 1376,50"/>
        <path d="M1200,460 Q1248,442 1270,416" stroke-width="1"/>
        <path d="M1260,500 Q1308,482 1330,456" stroke-width="1"/>
        <path d="M1260,500 Q1212,484 1190,458" stroke-width="1"/>
        <path d="M1206,240 Q1252,224 1274,198" stroke-width="1"/>
      </g>
      <g fill="#f0ebe0" opacity="0.2">
        <circle cx="500" cy="180" r="2"/><circle cx="700" cy="130" r="1.5"/>
        <circle cx="850" cy="280" r="2.5"/><circle cx="650" cy="420" r="1"/>
        <circle cx="920" cy="180" r="2"/><circle cx="450" cy="380" r="1.5"/>
      </g>
    </svg>
  </div>
  <div class="ash-field" id="ashField"></div>

  <div class="hero-inner">
    <div class="hero-left">
      <div class="hero-eyebrow fade-up">Ciencia ciudadana · Tuxtepec, Oaxaca · UNAM</div>
      <h1 class="hero-h1 fade-up d1">
        <span>Tú</span>
        <span class="it l2">mides</span>
        <span class="l3">la ceniza</span>
      </h1>
      <p class="hero-desc fade-up d2">
        Cada año, la quema de caña cubre Tuxtepec de ceniza. <strong>¿Cuánta llega a tu colonia?</strong> Con una cartulina, cinta doble cara y tu celular, construimos juntos el primer mapa ciudadano de contaminación por zafra.
      </p>
      <div class="hero-actions fade-up d3">
        <a href="#colector" class="btn-dark">Quiero participar</a>
        <a href="#proyecto" class="btn-ghost">Conocer el proyecto</a>
      </div>
    </div>
    <div class="hero-right fade-up d2">
      <div class="stats-card">
        <div class="stats-card-title">Estado del monitoreo · Zafra 2025–26</div>
        <div class="stat-row"><div class="stat-val">47</div><div class="stat-lbl">Colectores activos</div></div>
        <div class="stat-row"><div class="stat-val">18</div><div class="stat-lbl">Colonias mapeadas</div></div>
        <div class="stat-row"><div class="stat-val">12</div><div class="stat-lbl">Escuelas participantes</div></div>
        <div class="progress-row">
          <div class="progress-label"><span>Cobertura de la ciudad</span><span>62%</span></div>
          <div class="progress-track"><div class="progress-fill" id="pf1" style="width:0%"></div></div>
        </div>
        <div class="progress-row">
          <div class="progress-label"><span>Avance del período</span><span>83%</span></div>
          <div class="progress-track"><div class="progress-fill" id="pf2" style="width:0%"></div></div>
        </div>
      </div>
      <div class="hero-note">⚠ Datos simulados · temporada de prueba</div>
    </div>
  </div>

  <div class="hero-ticker">
    <div class="ticker-item"><div class="ticker-dot"></div>Material particulado</div>
    <div class="ticker-item"><div class="ticker-dot"></div>Eficiencia fotovoltaica</div>
    <div class="ticker-item"><div class="ticker-dot"></div>Salud respiratoria</div>
    <div class="ticker-item"><div class="ticker-dot"></div>Ciencia ciudadana</div>
    <div class="ticker-item"><div class="ticker-dot"></div>UNAM · IER</div>
    <div class="ticker-item"><div class="ticker-dot"></div>Tuxtepec, Oaxaca</div>
    <div class="ticker-item"><div class="ticker-dot"></div>Zafra 2025–2026</div>
  </div>
</section>

<!-- PROYECTO -->

<section id="proyecto">
  <div class="proyecto-layout">
    <div>
      <div class="section-label fade-up">El proyecto</div>
      <h2 class="display fade-up d1">¿Por qué <span class="it">importa</span><br>la ceniza?</h2>
      <p class="lead-text fade-up d2">La zafra es la columna vertebral de Tuxtepec. Pero cada temporada, la quema de caña libera toneladas de ceniza sobre la ciudad sin que nadie sepa exactamente dónde cae más.</p>
      <blockquote class="proyecto-quote fade-up d2">"Entre más oscura tu cartulina, más ceniza recibió tu colonia."</blockquote>
      <p class="proyecto-body fade-up d3">Zafra Mapa nació de una pregunta simple: si todos sabemos que la zafra contamina, ¿por qué no tenemos datos de dónde contamina más? El proyecto convierte esa pregunta en ciencia colectiva — con herramientas accesibles, resultados visibles y un impacto real para Tuxtepec.</p>
      <div class="pilares fade-up d3">
        <div class="pilar"><div class="pilar-num">01</div><h4>Salud respiratoria</h4><p>Las partículas de ceniza afectan vías respiratorias, especialmente en niños y adultos mayores. Identificar las zonas de mayor exposición permite focalizar intervenciones.</p></div>
        <div class="pilar"><div class="pilar-num">02</div><h4>Eficiencia solar</h4><p>La ceniza sobre paneles fotovoltaicos puede reducir su eficiencia hasta un 30% — un dato crítico para la transición energética en ciudades cañeras.</p></div>
        <div class="pilar"><div class="pilar-num">03</div><h4>Mapa inédito</h4><p>El primer registro geográfico de deposición de ceniza en Tuxtepec, hecho por y para su comunidad, con datos abiertos y accesibles.</p></div>
        <div class="pilar"><div class="pilar-num">04</div><h4>Protocolo replicable</h4><p>El método puede adoptarse en cualquier ciudad cañera de México: Veracruz, Morelos, Jalisco. El problema no es solo de Tuxtepec.</p></div>
      </div>
    </div>
    <div class="proyecto-visual fade-up d1">
      <div class="cane-illustration">
        <svg viewBox="0 0 400 530" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="530" fill="#0a0d08"/>
          <g stroke="rgba(240,235,224,0.04)" stroke-width="1">
            <line x1="0" y1="100" x2="400" y2="100"/><line x1="0" y1="200" x2="400" y2="200"/>
            <line x1="0" y1="300" x2="400" y2="300"/><line x1="0" y1="400" x2="400" y2="400"/>
            <line x1="100" y1="0" x2="100" y2="530"/><line x1="200" y1="0" x2="200" y2="530"/>
            <line x1="300" y1="0" x2="300" y2="530"/>
          </g>
          <g stroke="#c8a84b" stroke-width="2.5" fill="none">
            <path d="M55,530 Q67,390 53,260 Q39,130 58,10"/>
            <path d="M115,530 Q128,380 113,250 Q98,120 118,0"/>
            <path d="M185,530 Q172,400 185,270 Q198,140 180,20"/>
            <path d="M255,530 Q268,390 253,260 Q238,130 258,10"/>
            <path d="M325,530 Q312,410 325,280 Q338,150 320,30"/>
          </g>
          <g stroke="#4a8a5c" stroke-width="1.5" fill="none" opacity="0.75">
            <path d="M53,260 Q100,242 122,218"/><path d="M53,260 Q6,246 -16,220"/>
            <path d="M113,250 Q160,232 182,208"/><path d="M113,250 Q66,236 44,210"/>
            <path d="M185,270 Q232,252 254,228"/><path d="M185,270 Q138,256 116,230"/>
            <path d="M253,260 Q300,242 322,218"/><path d="M253,260 Q206,246 184,220"/>
            <path d="M58,130 Q104,112 126,88"/><path d="M118,120 Q82,106 60,80"/>
            <path d="M320,280 Q274,264 252,238"/>
            <path d="M58,20 Q96,4 116,-18"/><path d="M185,40 Q224,24 244,0"/>
          </g>
          <g fill="#f0ebe0">
            <circle cx="145" cy="110" r="2.5" opacity="0.55"/><circle cx="275" cy="75" r="1.8" opacity="0.45"/>
            <circle cx="78" cy="190" r="3" opacity="0.35"/><circle cx="348" cy="150" r="2" opacity="0.5"/>
            <circle cx="218" cy="215" r="1.5" opacity="0.4"/><circle cx="165" cy="345" r="2.8" opacity="0.3"/>
            <circle cx="308" cy="315" r="1.8" opacity="0.45"/><circle cx="42" cy="375" r="2.2" opacity="0.35"/>
            <circle cx="378" cy="395" r="1.5" opacity="0.4"/><circle cx="228" cy="445" r="3" opacity="0.25"/>
          </g>
          <text x="200" y="515" text-anchor="middle" font-family="'Syne',sans-serif" font-size="8.5" fill="rgba(240,235,224,0.25)" letter-spacing="3">SACCHARUM OFFICINARUM</text>
        </svg>
      </div>
      <div class="cane-caption">Saccharum officinarum · Caña de azúcar · Tuxtepec, Oaxaca</div>
    </div>
  </div>
</section>

<!-- COLECTOR -->

<section id="colector">
  <div class="colector-header">
    <div>
      <div class="section-label fade-up">Cómo participar</div>
      <h2 class="display fade-up d1">Construye tu <span class="it">colector</span></h2>
    </div>
    <div class="fade-up d2">
      <p class="lead-text">Un colector pasivo atrapa partículas de ceniza que caen del aire. Con materiales que cuestan menos de $30 pesos en cualquier papelería de Tuxtepec.</p>
    </div>
  </div>
  <div class="steps-grid">
    <div class="step fade-up"><div class="step-n">1</div><div class="step-icon-wrap">🛒</div><h3>Consigue los materiales</h3><p>Solo necesitas una cartulina blanca tamaño pliego y un rollo de cinta doble cara. Disponibles en cualquier papelería.</p><div class="step-spec">Cartulina blanca · 50 × 65 cm</div></div>
    <div class="step fade-up d1"><div class="step-n">2</div><div class="step-icon-wrap">📋</div><h3>Prepara el colector</h3><p>Cubre toda la superficie de la cartulina con tiras paralelas de cinta doble cara, sin dejar espacios. La cinta es la trampa de las partículas.</p><div class="step-spec">Cubrir toda la superficie uniformemente</div></div>
    <div class="step fade-up d2"><div class="step-n">3</div><div class="step-icon-wrap">🏠</div><h3>Colócalo en tu casa</h3><p>En la parte más alta: azotea o terraza. Completamente horizontal, mirando al cielo, a cielo abierto. Sin techo ni cubierta encima.</p><div class="step-spec">Horizontal · cielo abierto · lo más alto posible</div></div>
    <div class="step fade-up"><div class="step-n">4</div><div class="step-icon-wrap">⏳</div><h3>Espera 10 días exactos</h3><p>Deja el colector sin tocarlo. Si hay lluvia intensa, retíralo bajo techo y anótalo. Reinicia el conteo con uno nuevo si es necesario.</p><div class="step-spec">10 días · no mover · no tocar</div></div>
    <div class="step fade-up d1"><div class="step-n">5</div><div class="step-icon-wrap">📸</div><h3>Fotografía el colector</h3><p>Dos fotos siguiendo el protocolo exacto: una cenital desde 30 cm y una lateral desde 5 cm. Luz natural, sin sombras.</p><div class="step-spec">Luz natural · sin sombras · mediodía ideal</div></div>
    <div class="step fade-up d2"><div class="step-n">6</div><div class="step-icon-wrap">📤</div><h3>Envía tus datos</h3><p>Completa el formulario con tus fotos, colonia y fechas. Sin necesidad de cuenta. Tu punto aparece en el mapa en menos de 48 horas.</p><div class="step-spec">Tu dato aparece en el mapa colectivo</div></div>
  </div>
  <div class="colector-strip">
    <div class="strip-col">
      <div style="font-family:'Syne',sans-serif;font-size:0.62rem;font-weight:700;letter-spacing:0.16em;text-transform:uppercase;color:var(--smoke);margin-bottom:32px;">Vista del colector</div>
      <div style="text-align:center;">
        <div class="cartulina-demo">
          <div class="tape-layer"></div>
          <div class="ash-sim" style="width:5px;height:5px;top:22%;left:28%"></div>
          <div class="ash-sim" style="width:3px;height:3px;top:38%;left:58%"></div>
          <div class="ash-sim" style="width:7px;height:7px;top:52%;left:42%"></div>
          <div class="ash-sim" style="width:4px;height:4px;top:62%;left:72%"></div>
          <div class="ash-sim" style="width:3px;height:3px;top:28%;left:78%"></div>
          <div class="ash-sim" style="width:2px;height:2px;top:72%;left:22%"></div>
          <div class="ash-sim" style="width:4px;height:4px;top:82%;left:62%"></div>
          <div class="ash-sim" style="width:6px;height:6px;top:44%;left:17%"></div>
          <div class="ash-sim" style="width:3px;height:3px;top:16%;left:50%"></div>
          <div class="ash-sim" style="width:5px;height:5px;top:68%;left:40%"></div>
        </div>
        <span class="dim-label" style="margin-top:14px;display:block;">50 × 65 cm · Cartulina blanca</span>
        <p style="font-size:0.75rem;color:var(--smoke);margin-top:10px;line-height:1.6;">Superficie cubierta con cinta doble cara.<br>Los puntos oscuros son partículas de ceniza atrapadas.</p>
      </div>
    </div>
    <div class="strip-col">
      <div style="font-family:'Syne',sans-serif;font-size:0.62rem;font-weight:700;letter-spacing:0.16em;text-transform:uppercase;color:var(--smoke);margin-bottom:32px;">Especificaciones técnicas</div>
      <ul class="spec-list">
        <li><div class="ico">📐</div><div><strong>Tamaño estandarizado</strong><span>Cartulina blanca de 50 × 65 cm (tamaño pliego). El tamaño fijo permite comparar resultados entre todos los participantes.</span></div></li>
        <li><div class="ico">📏</div><div><strong>Orientación horizontal</strong><span>Completamente plana, acostada, mirando al cielo. Si queda inclinada, la deposición no será uniforme.</span></div></li>
        <li><div class="ico">🏔️</div><div><strong>Altura y cielo abierto</strong><span>Azotea o techo, sin ninguna cubierta encima. Alejado de árboles o paredes que generen corrientes artificiales.</span></div></li>
        <li><div class="ico">🌧️</div><div><strong>Si llueve</strong><span>Llovizna: aceptable. Lluvia intensa: retira el colector, anótalo en observaciones y reinicia con uno nuevo.</span></div></li>
        <li><div class="ico">🚫</div><div><strong>No tocar durante 10 días</strong><span>Cualquier contacto puede desplazar partículas y alterar el resultado.</span></div></li>
      </ul>
    </div>
  </div>
</section>

<!-- MÉTODO -->

<section id="metodo">
  <div class="section-label fade-up">El método científico</div>
  <h2 class="display fade-up d1">Cómo medimos <span class="it">la ceniza</span></h2>
  <p class="lead-text fade-up d2">Las fotos que tomas no son solo documentación — son datos. Con un programa científico gratuito, calculamos cuánta ceniza cayó exactamente en tu zona.</p>
  <div class="metodo-layout">
    <div class="metodo-explainer fade-up">
      <p>La cartulina es blanca. La ceniza es oscura. Eso hace que cualquier cámara pueda detectar la diferencia. Analizando el contraste de la foto, calculamos qué porcentaje de la cartulina quedó cubierto por partículas — a eso lo llamamos <strong>densidad de deposición</strong>.</p>
      <p>Ese número, combinado con tu colonia, se convierte en un punto en el mapa. Cuando sumamos decenas de puntos de toda la ciudad, emerge un patrón geográfico: las zonas más expuestas, las más protegidas, los gradientes entre la periferia cañera y el centro urbano.</p>
      <p>El análisis lo hace el equipo del proyecto usando <strong>ImageJ</strong>, un software científico gratuito del NIH de EE.UU. Tú no necesitas instalarlo — solo envías las fotos.</p>
      <div class="process-steps">
        <div class="process-step"><div class="ps-num">1</div><div class="ps-text"><h4>Foto → Escala de grises</h4><p>Convierte la imagen a blanco y negro para enfocarse en el contraste oscuro/claro, eliminando variaciones de color irrelevantes.</p></div></div>
        <div class="process-step"><div class="ps-num">2</div><div class="ps-text"><h4>Umbral de detección</h4><p>Se define el punto de corte: qué tan oscuro debe ser un píxel para contarse como partícula. Se calibra con muestras de control.</p></div></div>
        <div class="process-step"><div class="ps-num">3</div><div class="ps-text"><h4>Conteo automático</h4><p>ImageJ cuenta cuántos píxeles son ceniza vs. fondo blanco y calcula el porcentaje de área cubierta.</p></div></div>
        <div class="process-step"><div class="ps-num">4</div><div class="ps-text"><h4>Punto al mapa</h4><p>El porcentaje de cobertura se asigna a la colonia del participante y aparece con el color de su nivel de deposición.</p></div></div>
      </div>
    </div>
    <div class="fade-up d1">
      <div class="fotos-panel">
        <h3>Las dos fotos</h3>
        <div class="sub">Protocolo exacto · al retirar el colector</div>
        <div class="foto-pair">
          <div class="foto-box">
            <span class="foto-tag">Foto 1 — Cenital</span>
            <div class="foto-frame">🔲<div class="foto-dist-badge">30 cm</div></div>
            <h4>Desde arriba</h4>
            <p>Perpendicular a la cartulina, sin ángulo, sin sombra de tu mano. Captura toda la superficie.</p>
          </div>
          <div class="foto-box">
            <span class="foto-tag">Foto 2 — Lateral</span>
            <div class="foto-frame">📏<div class="foto-dist-badge">5 cm</div></div>
            <h4>De perfil</h4>
            <p>A la altura del borde. Muestra acumulación visible en casos de alta deposición.</p>
          </div>
        </div>
        <div class="density-scale">
          <div class="density-scale-title">Escala de densidad de deposición</div>
          <div class="scale-bar"></div>
          <div class="scale-labels"><span>Limpio</span><span>Muy contaminado</span></div>
          <div class="density-pills">
            <div class="dpill"><div class="dpill-dot" style="background:#6aad80"></div>Baja 0–10%</div>
            <div class="dpill"><div class="dpill-dot" style="background:#c8a84b"></div>Media 10–30%</div>
            <div class="dpill"><div class="dpill-dot" style="background:#e07040"></div>Alta 30–60%</div>
            <div class="dpill"><div class="dpill-dot" style="background:#2a5a9a"></div>Muy alta +60%</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- MAPA -->

<section id="mapa">
  <div class="mapa-header">
    <div class="section-label fade-up">Mapa en tiempo real</div>
    <h2 class="display fade-up d1">Ceniza sobre <span class="it">Tuxtepec</span></h2>
    <p class="lead-text fade-up d2">Cada punto es un colector ciudadano. El color indica la densidad de deposición de ceniza por zona durante la temporada de zafra.</p>
  </div>
  <div class="mapa-wrap fade-up">
    <div id="svgmap-container">
      <svg id="svgmap" viewBox="0 0 1000 560" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg">
        <rect width="1000" height="560" fill="#080b06"/>
        <g stroke="rgba(240,235,224,0.035)" stroke-width="1">
          <line x1="0" y1="140" x2="1000" y2="140"/><line x1="0" y1="280" x2="1000" y2="280"/>
          <line x1="0" y1="420" x2="1000" y2="420"/>
          <line x1="200" y1="0" x2="200" y2="560"/><line x1="400" y1="0" x2="400" y2="560"/>
          <line x1="600" y1="0" x2="600" y2="560"/><line x1="800" y1="0" x2="800" y2="560"/>
        </g>
        <path d="M0,430 Q150,415 300,425 Q450,435 580,415 Q720,398 900,408 Q950,412 1000,405" fill="none" stroke="#1a3a5a" stroke-width="22" opacity="0.6"/>
        <path d="M0,430 Q150,415 300,425 Q450,435 580,415 Q720,398 900,408 Q950,412 1000,405" fill="none" stroke="#2a5a8a" stroke-width="10" opacity="0.3"/>
        <text x="500" y="448" font-family="'Lora',serif" font-size="11" fill="#2a5a8a" text-anchor="middle" font-style="italic" opacity="0.65">Río Papaloapan</text>
        <ellipse cx="190" cy="492" rx="165" ry="50" fill="#0e1e08" opacity="0.6"/>
        <text x="190" y="496" font-family="'Syne',sans-serif" font-size="9" fill="#3a7a2a" text-anchor="middle" letter-spacing="2" opacity="0.7">ZONA CAÑERA</text>
        <g stroke="rgba(240,235,224,0.055)" stroke-width="1.5">
          <line x1="200" y1="90" x2="200" y2="420"/><line x1="350" y1="90" x2="350" y2="420"/>
          <line x1="500" y1="90" x2="500" y2="420"/><line x1="650" y1="90" x2="650" y2="420"/>
          <line x1="800" y1="90" x2="800" y2="420"/>
          <line x1="100" y1="175" x2="900" y2="175"/><line x1="100" y1="265" x2="900" y2="265"/>
          <line x1="100" y1="345" x2="900" y2="345"/>
        </g>
        <line x1="100" y1="268" x2="900" y2="268" stroke="rgba(240,235,224,0.09)" stroke-width="4"/>
        <line x1="500" y1="75" x2="500" y2="425" stroke="rgba(240,235,224,0.09)" stroke-width="4"/>
        <text x="500" y="38" font-family="'DM Serif Display',serif" font-size="18" fill="rgba(240,235,224,0.45)" text-anchor="middle">Tuxtepec</text>
        <text x="500" y="56" font-family="'Syne',sans-serif" font-size="8" fill="rgba(240,235,224,0.18)" text-anchor="middle" letter-spacing="3">OAXACA · MÉXICO</text>
        <g transform="translate(940,88)">
          <circle cx="0" cy="0" r="22" fill="rgba(240,235,224,0.03)" stroke="rgba(240,235,224,0.12)" stroke-width="1"/>
          <text x="0" y="-8" text-anchor="middle" font-family="'Syne',sans-serif" font-size="10" font-weight="700" fill="rgba(240,235,224,0.65)" letter-spacing="1">N</text>
          <polygon points="0,-17 2.5,-5 0,-8 -2.5,-5" fill="#c8a84b"/>
          <polygon points="0,17 2.5,5 0,8 -2.5,5" fill="rgba(240,235,224,0.18)"/>
        </g>
        <!-- Data points -->
        <circle cx="500" cy="268" r="11" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Centro" data-pct="72" data-tipo="Hogar"/>
        <circle cx="590" cy="210" r="10" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Barrio Nuevo" data-pct="65" data-tipo="Hogar"/>
        <circle cx="368" cy="318" r="12" fill="#e07040" stroke="#2d5a3d" stroke-width="2.5" class="mp" data-name="Col. Morelos" data-pct="48" data-tipo="Escuela"/>
        <circle cx="442" cy="352" r="11" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Periferia Norte" data-pct="81" data-tipo="Hogar"/>
        <circle cx="268" cy="200" r="10" fill="#e07040" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Independencia" data-pct="35" data-tipo="Hogar"/>
        <circle cx="388" cy="468" r="12" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Zona Cañera Sur" data-pct="90" data-tipo="Hogar"/>
        <circle cx="708" cy="150" r="12" fill="#c8a84b" stroke="#2d5a3d" stroke-width="2.5" class="mp" data-name="Col. Las Flores" data-pct="22" data-tipo="Escuela"/>
        <circle cx="212" cy="280" r="10" fill="#c8a84b" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Revolución" data-pct="18" data-tipo="Hogar"/>
        <circle cx="322" cy="378" r="10" fill="#e07040" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Ejidal" data-pct="58" data-tipo="Hogar"/>
        <circle cx="618" cy="292" r="10" fill="#e07040" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Reforma" data-pct="41" data-tipo="Hogar"/>
        <circle cx="228" cy="448" r="11" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Rancho El Palmar" data-pct="88" data-tipo="Hogar"/>
        <circle cx="568" cy="146" r="12" fill="#6aad80" stroke="#2d5a3d" stroke-width="2.5" class="mp" data-name="Col. Deportiva" data-pct="12" data-tipo="Escuela"/>
        <circle cx="414" cy="242" r="10" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Progreso" data-pct="67" data-tipo="Hogar"/>
        <circle cx="212" cy="182" r="10" fill="#6aad80" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Residencial" data-pct="9" data-tipo="Hogar"/>
        <circle cx="632" cy="332" r="12" fill="#e07040" stroke="#2d5a3d" stroke-width="2.5" class="mp" data-name="Col. Benito Juárez" data-pct="55" data-tipo="Escuela"/>
        <circle cx="258" cy="418" r="11" fill="#2a5a9a" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Fracc. Los Mangos" data-pct="76" data-tipo="Hogar"/>
        <circle cx="768" cy="198" r="10" fill="#6aad80" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Del Valle" data-pct="14" data-tipo="Hogar"/>
        <circle cx="542" cy="368" r="10" fill="#e07040" stroke="rgba(240,235,224,0.25)" stroke-width="1.5" class="mp" data-name="Col. Las Palmas" data-pct="43" data-tipo="Hogar"/>
        <!-- Tooltip -->
        <g id="mtt" style="display:none;pointer-events:none;">
          <rect id="mtt-bg" rx="2" fill="#0d0f0a" stroke="rgba(200,168,75,0.5)" stroke-width="1"/>
          <text id="mtt-name" font-family="'DM Serif Display',serif" font-size="13" fill="#f0ebe0"/>
          <text id="mtt-tipo" font-family="'Syne',sans-serif" font-size="8.5" fill="#8a8878" letter-spacing="1"/>
          <circle id="mtt-dot" r="5"/>
          <text id="mtt-pct" font-family="'Syne',sans-serif" font-size="10" font-weight="700" fill="#f0ebe0" letter-spacing="0.5"/>
        </g>
      </svg>
    </div>
    <div class="mapa-footer">
      <div class="leyenda">
        <div class="ley-item"><div class="ley-dot" style="background:#6aad80"></div>Baja (0–10%)</div>
        <div class="ley-item"><div class="ley-dot" style="background:#c8a84b"></div>Media (10–30%)</div>
        <div class="ley-item"><div class="ley-dot" style="background:#e07040"></div>Alta (30–60%)</div>
        <div class="ley-item"><div class="ley-dot" style="background:#2a5a9a"></div>Muy alta (+60%)</div>
        <div class="ley-item"><div class="ley-dot" style="background:#6aad80;outline:2px solid #2d5a3d;outline-offset:1px;"></div>Escuela</div>
      </div>
      <div class="mapa-sim-note">⚠ Datos simulados · versión de prueba · zafra 2025–26</div>
    </div>
  </div>
</section>

<!-- PARTICIPA -->

<section id="participa">
  <div class="participa-col">
    <div class="section-label fade-up">Únete</div>
    <h2 class="display fade-up d1">Envía tus <span class="it">resultados</span></h2>
    <p style="font-size:0.88rem;line-height:1.78;color:var(--smoke);margin-bottom:40px;" class="fade-up d2">Sin cuenta. Sin requisitos. Solo tus fotos, colonia y fechas. Tu dato aparece en el mapa en menos de 48 horas.</p>
    <div class="fade-up d2" id="form-wrap">
      <!-- ══════════════════════════════════════════════
           FORMULARIO CONECTADO A GOOGLE FORMS
           URL base: https://forms.gle/P8CjFF27h5egMWB29

```
       INSTRUCCIONES PARA ACTUALIZAR LOS entry IDs:
       1. Abre tu Google Form en modo Vista previa
       2. Clic derecho en cada campo → Inspeccionar
       3. Busca el atributo name="entry.XXXXXXXXX"
       4. Reemplaza cada entry.XXXXXXXXXX abajo con el ID real
       ══════════════════════════════════════════════ -->
  <form id="zaframapa-form" target="hidden_iframe" onsubmit="handleSubmit(event)">

    <label class="form-label">Nombre o apodo</label>
    <input type="text" name="entry.1000001" class="form-input" placeholder="Cómo quieres aparecer en el mapa" required>

    <label class="form-label">Colonia o barrio *</label>
    <input type="text" name="entry.1000002" class="form-input" placeholder="Ej: Col. Centro, Barrio Nuevo..." required>

    <label class="form-label">Tipo de participante *</label>
    <div class="radio-row" id="tipo-row">
      <div class="radio-chip active" data-val="Hogar">🏠 Hogar</div>
      <div class="radio-chip" data-val="Escuela">🏫 Escuela</div>
    </div>
    <input type="hidden" name="entry.1000003" id="tipo-val" value="Hogar">

    <label class="form-label">Fecha de instalación *</label>
    <input type="date" name="entry.1000004" class="form-input" required>

    <label class="form-label">Fecha de retiro *</label>
    <input type="date" name="entry.1000005" class="form-input" required>

    <label class="form-label">Foto 1 — Vista cenital (desde arriba · 30 cm) *</label>
    <div class="upload-zone" onclick="document.getElementById('foto1').click()">
      <div class="uz-icon">📸</div>
      <p id="foto1-label"><strong>Toca para subir</strong> · Perpendicular · 30 cm · Luz natural</p>
      <input type="file" id="foto1" accept="image/*" style="display:none" onchange="updateLabel('foto1','foto1-label')">
    </div>

    <label class="form-label">Foto 2 — Vista lateral (perfil del borde · 5 cm) *</label>
    <div class="upload-zone" onclick="document.getElementById('foto2').click()">
      <div class="uz-icon">📷</div>
      <p id="foto2-label"><strong>Toca para subir</strong> · Perfil del borde · 5 cm</p>
      <input type="file" id="foto2" accept="image/*" style="display:none" onchange="updateLabel('foto2','foto2-label')">
    </div>

    <label class="form-label">¿Hay paneles solares en tu casa o cerca?</label>
    <div class="radio-row" id="solar-row">
      <div class="radio-chip" data-val="Sí">Sí</div>
      <div class="radio-chip active" data-val="No">No</div>
      <div class="radio-chip" data-val="No sé">No sé</div>
    </div>
    <input type="hidden" name="entry.1000006" id="solar-val" value="No">

    <label class="form-label">¿Síntomas respiratorios en el hogar durante los 10 días?</label>
    <div class="radio-row" id="sintomas-row">
      <div class="radio-chip" data-val="Sí">Sí</div>
      <div class="radio-chip active" data-val="No">No</div>
    </div>
    <input type="hidden" name="entry.1000007" id="sintomas-val" value="No">

    <label class="form-label">Observaciones (lluvia, viento, incidentes)</label>
    <textarea name="entry.1000008" class="form-textarea" placeholder="Opcional: cualquier situación que haya podido afectar tu colector..."></textarea>

    <div style="margin-bottom:24px;">
      <label style="display:flex;align-items:flex-start;gap:12px;cursor:pointer;font-size:0.78rem;line-height:1.6;color:var(--smoke);">
        <input type="checkbox" id="consent-check" style="margin-top:3px;accent-color:var(--gold);flex-shrink:0;" required>
        <span>He leído y acepto el <a href="#aviso-privacidad" style="color:var(--gold);text-decoration:underline;">Aviso de Privacidad</a> y los <a href="#terminos" style="color:var(--gold);text-decoration:underline;">Términos y Condiciones</a>. Entiendo que mis datos serán usados exclusivamente para fines académicos.</span>
      </label>
    </div>

    <button type="submit" class="btn-submit" id="submit-btn">Enviar mi colector →</button>
  </form>

  <!-- Success message (oculto por defecto) -->
  <div id="form-success" style="display:none;padding:40px;border:1px solid rgba(200,168,75,0.4);text-align:center;">
    <div style="font-size:2.5rem;margin-bottom:16px;">🌾</div>
    <h3 style="font-family:'DM Serif Display',serif;font-size:1.8rem;color:var(--paper);margin-bottom:12px;">¡Gracias por participar!</h3>
    <p style="font-size:0.88rem;line-height:1.75;color:var(--smoke);">Tu colector ha sido registrado. En máximo 48 horas hábiles recibirás un correo con el resultado del análisis y el link a tu punto en el mapa.</p>
    <p style="font-size:0.78rem;color:var(--smoke);margin-top:12px;font-style:italic;">Nota: las fotos deberás enviarlas por separado al correo zaframapa@ier.unam.mx indicando tu nombre y colonia, ya que Google Forms no soporta archivos desde páginas externas.</p>
  </div>

  <!-- iframe oculto para capturar respuesta de Google Forms -->
  <iframe name="hidden_iframe" id="hidden_iframe" style="display:none;"></iframe>
</div>
```

  <div class="participa-col">
    <div style="height:80px;"></div>
    <div class="info-item"><div class="info-ico">📅</div><div><h4>¿Cuándo participar?</h4><p>Durante la zafra, de noviembre a abril. Puedes participar en cualquier momento. Cada ronda de 10 días es un dato valioso.</p></div></div>
    <div class="info-item"><div class="info-ico">👨‍👩‍👧</div><div><h4>¿Quién puede participar?</h4><p>Cualquier hogar o escuela en Tuxtepec. No se necesitan conocimientos científicos — el protocolo está diseñado para cualquier persona.</p></div></div>
    <div class="info-item"><div class="info-ico">💰</div><div><h4>¿Tiene costo?</h4><p>Los materiales (cartulina + cinta doble cara) cuestan menos de $30 pesos en cualquier papelería de Tuxtepec.</p></div></div>
    <div class="info-item"><div class="info-ico">🗺️</div><div><h4>¿Cuándo veré mi dato?</h4><p>En máximo 48 horas hábiles. Recibirás un correo con el porcentaje de deposición y el link a tu punto en el mapa.</p></div></div>
    <div class="info-item"><div class="info-ico">🔒</div><div><h4>Privacidad</h4><p>En el mapa aparece solo tu colonia. Nunca tu nombre ni dirección exacta. Datos exclusivamente para fines académicos, sin terceros.</p></div></div>
  </div>
</section>

<!-- CIENCIA CIUDADANA -->

<section id="ciencia-ciudadana" style="padding:120px 56px;border-top:1px solid var(--line);position:relative;overflow:hidden;">
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:start;">
    <div>
      <div class="section-label fade-up">Ciencia ciudadana</div>
      <h2 class="display fade-up d1">La ciencia que <span class="it">todos</span> podemos hacer</h2>
      <p class="lead-text fade-up d2">La ciencia ciudadana es la práctica en la que personas comunes — sin necesidad de ser investigadoras — recopilan datos reales que contribuyen a proyectos científicos genuinos.</p>
      <blockquote class="proyecto-quote fade-up d2" style="margin-top:36px;">"Cuando miles de personas observan su entorno, generan lo que ningún laboratorio puede hacer solo: datos a escala humana."</blockquote>
      <p class="proyecto-body fade-up d3">No es un experimento simulado ni una actividad didáctica. Es ciencia real. Los datos que tú recopiles en tu azotea serán analizados con los mismos métodos que usa la investigación académica y publicados como parte de una tesina universitaria formal avalada por el IER-UNAM.</p>
    </div>
    <div class="fade-up d1">
      <div style="display:grid;grid-template-columns:1fr;gap:1px;background:var(--line);">
        <div style="background:var(--ink2);padding:28px 24px;"><div style="font-family:'DM Serif Display',serif;font-size:3rem;color:rgba(200,168,75,0.2);line-height:1;margin-bottom:12px;">01</div><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">¿Qué es exactamente?</h4><p style="font-size:0.8rem;line-height:1.7;color:var(--smoke);">Es un modelo de investigación donde ciudadanos actúan como observadores científicos. Se usa en astronomía, biología, climatología y ahora en monitoreo ambiental urbano como este proyecto.</p></div>
        <div style="background:var(--ink2);padding:28px 24px;"><div style="font-family:'DM Serif Display',serif;font-size:3rem;color:rgba(200,168,75,0.2);line-height:1;margin-bottom:12px;">02</div><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">¿Por qué importa para ti?</h4><p style="font-size:0.8rem;line-height:1.7;color:var(--smoke);">Porque los datos que generas hablan de tu propia colonia. No de un promedio abstracto: del aire que respiras tú, tu familia y tus vecinos cada temporada de zafra.</p></div>
        <div style="background:var(--ink2);padding:28px 24px;"><div style="font-family:'DM Serif Display',serif;font-size:3rem;color:rgba(200,168,75,0.2);line-height:1;margin-bottom:12px;">03</div><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">¿Cómo aporta Zafra Mapa?</h4><p style="font-size:0.8rem;line-height:1.7;color:var(--smoke);">Cada colector que instalas es un sensor. Juntos formamos la red de monitoreo ambiental más completa que Tuxtepec ha tenido, con datos que quedan documentados y accesibles para toda la comunidad.</p></div>
        <div style="background:var(--ink2);padding:28px 24px;"><div style="font-family:'DM Serif Display',serif;font-size:3rem;color:rgba(200,168,75,0.2);line-height:1;margin-bottom:12px;">04</div><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">¿Qué pasa con tus datos?</h4><p style="font-size:0.8rem;line-height:1.7;color:var(--smoke);">Se analizan, se integran al mapa y se documentan en una tesina universitaria con respaldo del IER-UNAM. Los resultados serán públicos y accesibles para toda la comunidad de Tuxtepec.</p></div>
      </div>
    </div>
  </div>
</section>

<!-- NOSOTROS -->

<section id="nosotros">
  <div class="nosotros-col">
    <div class="section-label fade-up">Quiénes somos</div>
    <div class="fade-up d1">
      <div class="persona-initials">HCD</div>
      <div class="persona-name">Hanna Camila<br>Domínguez Negrete</div>
      <div class="persona-role">Líder del proyecto</div>
      <p class="persona-bio">Originaria de Tuxtepec, Oaxaca. Estudiante de ingeniería en energías renovables en el IER-UNAM. Zafra Mapa nació de su experiencia creciendo en una ciudad donde la zafra define el año, y de la pregunta que siempre tuvo: ¿qué tan contaminado estamos, realmente?</p>
      <p class="persona-bio">El proyecto es parte de su tesina de licenciatura y está concebido para que sus resultados sirvan directamente a la comunidad de Tuxtepec.</p>
    </div>
    <div class="inst-block fade-up d2">
      <div class="inst-tag">Institución académica</div>
      <div class="inst-name">IER — UNAM</div>
      <p class="inst-desc">Instituto de Energías Renovables de la Universidad Nacional Autónoma de México. Principal centro de investigación en energías renovables del país. Zafra Mapa se desarrolla bajo el marco académico del IER con respaldo institucional de la UNAM.</p>
    </div>
  </div>
  <div class="nosotros-col tinted">
    <div class="section-label fade-up">Misión</div>
    <h3 class="mision-h fade-up d1">Un proyecto de<br>Tuxtepec<br>para Tuxtepec</h3>
    <p class="mision-body fade-up d2">Zafra Mapa no es un proyecto externo que llega a estudiar la ciudad. Es una iniciativa que nació aquí, hecha por alguien que conoce la zafra desde adentro, y que cree que la ciencia ciudadana puede generar datos útiles para las comunidades que más los necesitan.</p>
    <p class="mision-body fade-up d2">Los resultados del proyecto serán públicos y accesibles para escuelas, autoridades municipales, organizaciones de salud y cualquier persona interesada en el impacto ambiental de la zafra.</p>
    <p class="mision-body fade-up d3">Si eres maestra, maestro, director de escuela o tienes una organización comunitaria en Tuxtepec y quieres participar de forma colectiva, escríbenos.</p>
    <div class="tag-cloud fade-up d3">
      <div class="tag-pill">🌾 Tuxtepec</div>
      <div class="tag-pill">🔬 Ciencia ciudadana</div>
      <div class="tag-pill">☀️ Energías renovables</div>
      <div class="tag-pill">🫁 Salud ambiental</div>
      <div class="tag-pill">🗺️ Cartografía</div>
      <div class="tag-pill">🎓 UNAM · IER</div>
    </div>
  </div>
</section>

<!-- FAQ -->

<section id="faq">
  <div class="faq-sidebar">
    <div class="section-label fade-up">FAQ</div>
    <h2 class="display fade-up d1" style="font-size:2.8rem;">Tus <span class="it">dudas</span></h2>
    <p class="lead-text fade-up d2" style="font-size:0.84rem;">Las preguntas más frecuentes del proyecto respondidas aquí.</p>
    <div class="faq-contact fade-up d3">
      <p>¿No encontraste tu respuesta? Escríbeme directamente.</p>
      <a href="mailto:zaframapa@ier.unam.mx" class="btn-email">Enviar correo</a>
    </div>
  </div>
  <div class="faq-list fade-up">
    <div class="faq-item"><div class="faq-q">¿Cómo preparo exactamente la cartulina? <span class="faq-toggle">+</span></div><div class="faq-a">Consigue una cartulina blanca de 50×65 cm. Cubre toda su superficie con tiras paralelas de cinta doble cara, sin dejar espacios. La cinta es la superficie activa que atrapa las partículas. No uses vaselina ni ningún otro pegamento.</div></div>
    <div class="faq-item"><div class="faq-q">¿Qué pasa si llueve durante los 10 días? <span class="faq-toggle">+</span></div><div class="faq-a">Lluvias ligeras no afectan significativamente el resultado. Si hay lluvia intensa o tormenta, retira el colector, guárdalo bajo techo y anota la fecha. Reinicia el conteo con un colector nuevo si puedes.</div></div>
    <div class="faq-item"><div class="faq-q">¿En qué parte de mi casa lo coloco? <span class="faq-toggle">+</span></div><div class="faq-a">En el punto más alto con cielo abierto: azotea, terraza o techo plano. Completamente horizontal (acostado mirando al cielo), alejado de paredes o árboles cercanos.</div></div>
    <div class="faq-item"><div class="faq-q">¿Cómo tomo bien las fotos? <span class="faq-toggle">+</span></div><div class="faq-a">Tómalas al mediodía con luz natural directa y sin sombras sobre la cartulina. Foto 1: sostienes el celular a 30 cm apuntando directo hacia abajo, perpendicular. Foto 2: a 5 cm del borde lateral, a la altura del grosor de la cartulina.</div></div>
    <div class="faq-item"><div class="faq-q">¿Puedo hacer más de un colector? <span class="faq-toggle">+</span></div><div class="faq-a">Sí, y es muy valioso. Si colocas colectores en diferentes partes de tu casa o en diferentes momentos de la zafra, envía cada uno como participación separada. Más datos equivale a un mejor mapa.</div></div>
    <div class="faq-item"><div class="faq-q">¿Cuándo estará mi dato en el mapa? <span class="faq-toggle">+</span></div><div class="faq-a">En máximo 48 horas hábiles. Recibirás un correo con el porcentaje de deposición y el link a tu punto en el mapa. Si no recibes nada en 3 días, revisa spam o escríbenos.</div></div>
    <div class="faq-item"><div class="faq-q">¿Para qué sirven los datos sobre paneles solares? <span class="faq-toggle">+</span></div><div class="faq-a">La ceniza depositada en paneles fotovoltaicos reduce su eficiencia. Saber qué zonas reciben más ceniza ayuda a entender dónde es más urgente limpiar los paneles y a cuantificar el impacto económico de la zafra en la energía solar de la ciudad.</div></div>
    <div class="faq-item"><div class="faq-q">¿Mis datos personales están seguros? <span class="faq-toggle">+</span></div><div class="faq-a">Sí. En el mapa solo aparece tu colonia, nunca tu nombre ni dirección exacta. Tus datos se usan exclusivamente para fines académicos y no se comparten con terceros.</div></div>
  </div>
</section>

<!-- TÉRMINOS Y CONDICIONES -->

<section id="terminos" style="border-top:1px solid var(--line);padding:80px 56px;display:grid;grid-template-columns:280px 1fr;gap:80px;">
  <div>
    <div class="section-label fade-up">Legal</div>
    <h2 class="display fade-up d1" style="font-size:2.8rem;">Términos y <span class="it">condiciones</span></h2>
    <p class="fade-up d2" style="font-size:0.84rem;line-height:1.75;color:var(--smoke);margin-top:12px;">Última actualización: 2025. Al usar este sitio, aceptas los siguientes términos.</p>
  </div>
  <div class="fade-up d1">
    <div style="display:grid;gap:0;">
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">1. Uso educativo del sitio</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">El contenido, formularios y herramientas disponibles en esta página están diseñados para actividades de aprendizaje y ciencia ciudadana realizadas en el marco de un proyecto académico. Aunque el sitio pueda encontrarse mediante un enlace público, no está destinado al uso general del público, sino al trabajo académico de los estudiantes.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">2. Responsabilidad del usuario</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">Toda persona que decida ingresar información, fotografías o comentarios en este sitio es responsable de la veracidad y contenido de los datos que proporcione. Acepta que cualquier dato personal incluido de manera voluntaria o accidental es responsabilidad exclusiva del usuario. Reconoce que el envío de información por parte de terceros ajenos al proyecto se realiza bajo su propio riesgo.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">3. Acceso por terceros</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">El acceso al sitio por personas externas al curso o institución educativa no está previsto ni promovido por el responsable del proyecto, no genera responsabilidad alguna para la universidad ni para el alumno desarrollador, y cualquier uso o envío de datos por parte de terceros es exclusivamente responsabilidad de dichos usuarios.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">4. Limitación de responsabilidad</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">El alumno desarrollador y la institución educativa no garantizan la exactitud, permanencia o disponibilidad del contenido del sitio; no asumen responsabilidad por el uso indebido del sitio, accesos no autorizados o información enviada por terceros; ni se hacen responsables de decisiones, interpretaciones o acciones derivadas del contenido publicado.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">5. Propósito del contenido</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">La información generada a partir de las fotografías y datos enviados no constituye asesoría profesional ni técnica, no representa una postura oficial de la universidad, y se utiliza únicamente con fines educativos, estadísticos y de divulgación científica.</p></div>
      <div style="padding:24px 0;"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">6. Aceptación de los términos</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">El uso de este sitio implica la aceptación plena de estos Términos y Condiciones. Si usted no está de acuerdo con alguno de los puntos anteriores, se recomienda no utilizar el sitio ni enviar información.</p></div>
    </div>
  </div>
</section>

<!-- AVISO DE PRIVACIDAD -->

<section id="aviso-privacidad" style="border-top:1px solid var(--line);padding:80px 56px;display:grid;grid-template-columns:280px 1fr;gap:80px;">
  <div>
    <div class="section-label fade-up">Privacidad</div>
    <h2 class="display fade-up d1" style="font-size:2.8rem;">Aviso de <span class="it">privacidad</span></h2>
    <p class="fade-up d2" style="font-size:0.84rem;line-height:1.75;color:var(--smoke);margin-top:12px;">En cumplimiento con la Ley Federal de Protección de Datos Personales en Posesión de los Particulares.</p>
  </div>
  <div class="fade-up d1">
    <div style="display:grid;gap:0;">
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">1. Responsable del manejo de datos</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">El responsable del tratamiento y resguardo de los datos personales es un alumno del Instituto de Energías Renovables, en el marco de un proyecto académico con fines exclusivamente educativos. Cualquier solicitud de aclaración, corrección, cancelación o ejercicio de derechos deberá dirigirse al responsable mediante los datos de contacto proporcionados en esta página, o al IER-UNAM a través de sus canales institucionales.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">2. Naturaleza educativa del proyecto</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">Este sitio web forma parte de un proyecto académico con fines exclusivamente educativos. El contenido, análisis y resultados generados no constituyen asesoría profesional o científica certificada, no generan obligaciones legales para la institución educativa, y no representan una postura oficial de la universidad.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">3. Datos personales sometidos a tratamiento</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);"><strong style="color:var(--paper);font-weight:500;">Datos obligatorios:</strong> correo electrónico, código postal o ubicación aproximada, fotografías de objetos o experimentos sin personas identificables. <strong style="color:var(--paper);font-weight:500;">Datos opcionales:</strong> nombre, comentarios o descripciones, cualquier otro dato que el participante decida incluir voluntariamente. No se solicitarán datos personales sensibles.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">4. Finalidades del tratamiento</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);"><strong style="color:var(--paper);font-weight:500;">Primarias (necesarias):</strong> registrar la participación, analizar fotografías y datos para fines educativos y estadísticos, generar mapas y resultados agregados, contactar al participante para aclaraciones. <strong style="color:var(--paper);font-weight:500;">Secundarias (requieren consentimiento):</strong> publicar fotografías o datos disociados en materiales de divulgación, enviar información sobre actividades relacionadas.</p></div>
      <div style="padding:24px 0;border-bottom:1px solid var(--line);"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">5. Transferencias, seguridad y publicación</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">No se realizarán transferencias de datos personales a terceros, salvo obligaciones legales o datos disociados. Se implementarán medidas de seguridad administrativas, técnicas y físicas para proteger los datos. Solo se publicarán fotografías o datos que no permitan identificar a una persona, y únicamente con consentimiento expreso del participante.</p></div>
      <div style="padding:24px 0;"><h4 style="font-family:'Syne',sans-serif;font-size:0.75rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:var(--paper);margin-bottom:10px;">6. Consentimiento y cambios</h4><p style="font-size:0.82rem;line-height:1.75;color:var(--smoke);">Al enviar sus datos, el participante otorga consentimiento tácito para las finalidades primarias. Las finalidades secundarias requerirán consentimiento expreso. Cualquier modificación al presente aviso será publicada en esta misma página y, cuando afecte finalidades que requieran consentimiento, se notificará al correo proporcionado.</p></div>
    </div>
  </div>
</section>

<!-- FOOTER -->

<footer>
  <div>
    <div class="footer-wordmark">Zafra <em>Mapa</em></div>
    <p class="footer-tagline">Monitoreo ciudadano de ceniza<br>por quema de caña · Tuxtepec, Oaxaca<br>Instituto de Energías Renovables · UNAM</p>
  </div>
  <div class="footer-col">
    <div class="footer-col-title">Secciones</div>
    <a href="#proyecto">El proyecto</a>
    <a href="#ciencia-ciudadana">Ciencia ciudadana</a>
    <a href="#colector">Cómo participar</a>
    <a href="#metodo">El método</a>
    <a href="#mapa">Mapa en vivo</a>
    <a href="#nosotros">Sobre nosotros</a>
    <a href="#faq">Preguntas frecuentes</a>
  </div>
  <div class="footer-col">
    <div class="footer-col-title">Legal</div>
    <a href="#aviso-privacidad">Aviso de privacidad</a>
    <a href="#terminos">Términos y condiciones</a>
    <a href="#metodo">Metodología científica</a>
    <a href="mailto:zaframapa@ier.unam.mx">Contacto</a>
  </div>
</footer>
<div class="footer-bottom">
  <span>© 2025–2026 Zafra Mapa · Uso de datos exclusivamente académico</span>
  <span>Hecho en Tuxtepec, Oaxaca</span>
</div>

<script>
/* ASH PARTICLES */
const field = document.getElementById('ashField');
for(let i=0;i<28;i++){
  const p=document.createElement('div');
  p.className='ash-particle';
  const s=Math.random()*4+1;
  p.style.cssText=`width:${s}px;height:${s}px;left:${Math.random()*100}%;top:${Math.random()*-20}%;animation-duration:${Math.random()*14+8}s;animation-delay:${Math.random()*12}s;`;
  field.appendChild(p);
}

/* PROGRESS BARS */
setTimeout(()=>{
  document.getElementById('pf1').style.width='62%';
  document.getElementById('pf2').style.width='83%';
},600);

/* SCROLL REVEAL */
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');obs.unobserve(e.target);}});
},{threshold:0.08});
document.querySelectorAll('.fade-up').forEach(el=>obs.observe(el));

/* FAQ */
document.querySelectorAll('.faq-q').forEach(q=>{
  q.addEventListener('click',()=>{
    const item=q.parentElement;
    const open=item.classList.contains('open');
    document.querySelectorAll('.faq-item.open').forEach(i=>i.classList.remove('open'));
    if(!open)item.classList.add('open');
  });
});

/* FORM SUBMISSION → GOOGLE FORMS
   ════════════════════════════════
   PASOS PARA ACTIVAR:
   1. Abre tu Google Form → Vista previa (ícono del ojo)
   2. Clic derecho en cada campo → Inspeccionar → busca name="entry.XXXXXXXXX"
   3. Reemplaza los entry IDs de abajo con los reales de tu form
   4. El action del form debe ser la URL de tu Google Form terminada en /formResponse
      Ejemplo: https://docs.google.com/forms/d/e/TU_FORM_ID/formResponse
   ════════════════════════════════ */

// URL DE TU GOOGLE FORM — reemplaza con la URL real de formResponse
const GFORM_URL = 'https://docs.google.com/forms/d/e/1FAIpQLSfP8CjFF27h5egMWB29/formResponse';

function updateLabel(inputId, labelId) {
  const input = document.getElementById(inputId);
  const label = document.getElementById(labelId);
  if(input.files && input.files[0]) {
    label.innerHTML = `<strong style="color:var(--gold)">✓ ${input.files[0].name}</strong>`;
  }
}

// Radio chips con grupos nombrados
document.querySelectorAll('.radio-row').forEach(row => {
  const hiddenId = row.id.replace('-row','-val');
  const hidden = document.getElementById(hiddenId);
  row.querySelectorAll('.radio-chip').forEach(chip => {
    chip.addEventListener('click', () => {
      row.querySelectorAll('.radio-chip').forEach(c => c.classList.remove('active'));
      chip.classList.add('active');
      if(hidden) hidden.value = chip.dataset.val || chip.textContent.trim();
    });
  });
});

function handleSubmit(e) {
  e.preventDefault();
  const form = document.getElementById('zaframapa-form');
  const btn = document.getElementById('submit-btn');

  // Validate
  if(!document.getElementById('consent-check').checked) {
    alert('Por favor acepta el Aviso de Privacidad y los Términos y Condiciones para continuar.');
    return;
  }

  btn.textContent = 'Enviando...';
  btn.disabled = true;
  btn.style.opacity = '0.7';

  // Build form data for Google Forms
  const data = new FormData(form);
  const params = new URLSearchParams();
  for(const [key, val] of data.entries()) {
    if(!key.startsWith('entry.')) continue;
    params.append(key, val);
  }

  // Submit via fetch (no-cors for Google Forms)
  fetch(GFORM_URL, {
    method: 'POST',
    mode: 'no-cors',
    headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    body: params.toString()
  })
  .then(() => {
    document.getElementById('zaframapa-form').style.display = 'none';
    document.getElementById('form-success').style.display = 'block';
  })
  .catch(() => {
    // no-cors always throws — treat as success
    document.getElementById('zaframapa-form').style.display = 'none';
    document.getElementById('form-success').style.display = 'block';
  });
}

/* SVG MAP */
const svg=document.getElementById('svgmap');
const tt=document.getElementById('mtt');
const ttBg=document.getElementById('mtt-bg');
const ttName=document.getElementById('mtt-name');
const ttTipo=document.getElementById('mtt-tipo');
const ttDot=document.getElementById('mtt-dot');
const ttPct=document.getElementById('mtt-pct');

function pctColor(p){
  if(p>60)return'#2a5a9a';
  if(p>30)return'#e07040';
  if(p>10)return'#c8a84b';
  return'#6aad80';
}

document.querySelectorAll('.mp').forEach(pt=>{
  pt.style.cursor='pointer';
  const origR=parseFloat(pt.getAttribute('r'));
  pt.addEventListener('mouseenter',function(){
    this.setAttribute('r',origR+4);
    const pct=parseInt(this.dataset.pct);
    const color=pctColor(pct);
    ttName.textContent=this.dataset.name;
    ttTipo.textContent=this.dataset.tipo==='Escuela'?'ESCUELA PARTICIPANTE':'HOGAR PARTICIPANTE';
    ttDot.setAttribute('fill',color);
    ttPct.textContent=pct+'% cobertura de ceniza';
    const cx=parseFloat(this.getAttribute('cx'));
    const cy=parseFloat(this.getAttribute('cy'));
    const W=178,H=70;
    let tx=cx+16,ty=cy-82;
    if(tx+W>985)tx=cx-W-10;
    if(ty<8)ty=cy+18;
    ttBg.setAttribute('x',tx);ttBg.setAttribute('y',ty);
    ttBg.setAttribute('width',W);ttBg.setAttribute('height',H);
    ttName.setAttribute('x',tx+12);ttName.setAttribute('y',ty+20);
    ttTipo.setAttribute('x',tx+12);ttTipo.setAttribute('y',ty+33);
    ttDot.setAttribute('cx',tx+17);ttDot.setAttribute('cy',ty+52);
    ttPct.setAttribute('x',tx+28);ttPct.setAttribute('y',ty+56);
    tt.style.display='block';
    svg.appendChild(tt);
  });
  pt.addEventListener('mouseleave',function(){
    this.setAttribute('r',origR);
    tt.style.display='none';
  });
});
</script>

</body>
</html>
