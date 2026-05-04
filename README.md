# App-analyse-Immo-
<!DOCTYPE html>

<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Oiko Pro">
<meta name="theme-color" content="#0a0a0a">
<title>Oiko Pro</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@300;400;500&family=Unbounded:wght@300;400;700;900&display=swap" rel="stylesheet">
<style>
:root{--bg:#0a0a0a;--surface:#111;--card:#161616;--border:#222;--accent:#c8f03e;--green:#1a7a3a;--green2:#23a350;--danger:#ff4d4d;--warn:#ffb84d;--text:#f0f0f0;--muted:#555;--muted2:#888;}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent;}
body{background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;font-size:13px;min-height:100dvh;overflow-x:hidden;}
.header{position:sticky;top:0;z-index:200;background:rgba(10,10,10,.97);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:11px 16px 9px;display:flex;align-items:center;justify-content:space-between;}
.header-left{display:flex;align-items:center;gap:10px;}
.back-btn{background:var(--card);border:1px solid var(--border);border-radius:6px;color:var(--text);font-size:11px;padding:5px 10px;cursor:pointer;display:none;font-family:'DM Mono',monospace;}
.header-title{font-family:'Unbounded',sans-serif;font-size:11px;font-weight:700;letter-spacing:.12em;color:var(--accent);}
.header-sub{font-size:9px;color:var(--muted2);margin-top:1px;}
.badge{background:var(--green2);color:#fff;font-family:'Unbounded',sans-serif;font-size:8px;font-weight:900;padding:3px 7px;border-radius:3px;}
.home{padding:24px 16px;display:flex;flex-direction:column;gap:14px;}
.home-hero{text-align:center;padding:20px 0 10px;}
.home-logo{font-family:'Unbounded',sans-serif;font-size:28px;font-weight:900;color:var(--accent);letter-spacing:.06em;}
.home-tagline{font-size:11px;color:var(--muted2);margin-top:6px;letter-spacing:.08em;}
.module-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:20px;cursor:pointer;transition:border-color .2s;display:flex;align-items:center;gap:16px;}
.module-card.green-mod{border-color:rgba(35,163,80,.3);}
.module-card.accent-mod{border-color:rgba(200,240,62,.2);}
.module-icon{font-size:32px;flex-shrink:0;}
.module-title{font-family:'Unbounded',sans-serif;font-size:13px;font-weight:700;margin-bottom:4px;}
.module-card.green-mod .module-title{color:var(--green2);}
.module-card.accent-mod .module-title{color:var(--accent);}
.module-desc{font-size:10px;color:var(--muted2);line-height:1.5;}
.module-arrow{margin-left:auto;color:var(--muted);font-size:16px;flex-shrink:0;}
.nav{display:flex;border-bottom:1px solid var(--border);background:var(--bg);overflow-x:auto;scrollbar-width:none;}
.nav::-webkit-scrollbar{display:none;}
.nav-tab{flex:1;min-width:65px;padding:10px 4px;text-align:center;font-family:'DM Mono',monospace;font-size:9px;letter-spacing:.05em;color:var(--muted2);cursor:pointer;border:none;background:none;border-bottom:2px solid transparent;transition:all .2s;white-space:nowrap;}
.nav-tab.active{color:var(--accent);border-bottom-color:var(--accent);}
.nav-tab.gtab.active{color:var(--green2);border-bottom-color:var(--green2);}
.page{display:none;}.page.active{display:block;}
.section{display:none;}.section.active{display:block;}
.step-header{padding:14px 16px 6px;display:flex;align-items:center;gap:10px;}
.step-num{font-family:'Unbounded',sans-serif;font-size:10px;font-weight:900;border-radius:4px;padding:3px 8px;}
.step-num.g{color:var(--green2);background:rgba(35,163,80,.1);border:1px solid rgba(35,163,80,.2);}
.step-num.a{color:var(--accent);background:rgba(200,240,62,.1);border:1px solid rgba(200,240,62,.2);}
.step-title{font-family:'Unbounded',sans-serif;font-size:10px;font-weight:700;letter-spacing:.1em;color:var(--text);}
.form-wrap{padding:4px 16px 8px;display:flex;flex-direction:column;gap:10px;}
.fg{background:var(--card);border:1px solid var(--border);border-radius:8px;overflow:hidden;}
.fgt{font-family:'Unbounded',sans-serif;font-size:8px;font-weight:700;letter-spacing:.14em;padding:9px 14px 7px;border-bottom:1px solid var(--border);text-transform:uppercase;}
.fgt.g{color:var(--green2);}
.fgt.a{color:var(--accent);}
.field{display:flex;align-items:center;justify-content:space-between;padding:9px 14px;border-bottom:1px solid var(--border);gap:8px;}
.field:last-child{border-bottom:none;}
.fl{font-size:11px;color:#aaa;flex:1;line-height:1.3;}
.fu{font-size:10px;color:var(--muted2);margin-right:4px;white-space:nowrap;flex-shrink:0;}
.fn{font-size:9px;color:var(--muted);padding:4px 14px 7px;line-height:1.5;border-bottom:1px solid var(--border);}
.fn:last-child{border-bottom:none;}
input[type="number"],input[type="text"],input[type="date"],textarea,select{background:var(--surface);border:1px solid #2a2a2a;border-radius:5px;color:var(--text);font-family:'DM Mono',monospace;font-size:12px;padding:7px 8px;width:100px;text-align:right;outline:none;-webkit-appearance:none;transition:border-color .15s;}
input[type="text"],input[type="date"]{text-align:left;width:160px;}
textarea{text-align:left;width:100%;resize:vertical;min-height:80px;}
input:focus,select:focus,textarea:focus{border-color:var(--green2);}
.af input:focus,.af select:focus,.af textarea:focus{border-color:var(--accent);}
select{text-align:left;cursor:pointer;}
.aw{display:flex;gap:5px;align-items:center;}
.aw select{width:52px;padding:7px 4px;font-size:11px;}
.aw input{width:85px;}
.ir{padding:5px 14px 7px;font-size:9px;color:var(--muted2);line-height:1.5;border-bottom:1px solid var(--border);}
.btn{margin:6px 16px 16px;border:none;border-radius:8px;font-family:'Unbounded',sans-serif;font-size:11px;font-weight:900;letter-spacing:.1em;padding:15px;width:calc(100% - 32px);cursor:pointer;text-transform:uppercase;transition:opacity .15s,transform .1s;}
.btn:active{transform:scale(.98);opacity:.9;}
.btn-g{background:var(--green2);color:#fff;}
.btn-a{background:var(--accent);color:#000;}
.brow{display:flex;gap:8px;margin:6px 16px 8px;}
.brow .btn{margin:0;flex:1;width:auto;font-size:10px;padding:11px;}

/* DVF LOADER */
.dvf-loader{margin:0 16px 12px;background:var(–card);border:1px solid var(–border);border-radius:8px;overflow:hidden;}
.dvf-search-bar{display:flex;padding:10px 12px;gap:8px;border-bottom:1px solid var(–border);}
.dvf-search-bar input{flex:1;width:auto;text-align:left;font-size:12px;}
.dvf-search-btn{background:var(–green2);color:#fff;border:none;border-radius:6px;padding:8px 14px;font-family:‘Unbounded’,sans-serif;font-size:9px;font-weight:700;cursor:pointer;white-space:nowrap;flex-shrink:0;}
.dvf-status{padding:10px 14px;font-size:10px;color:var(–muted2);display:flex;align-items:center;gap:8px;}
.dvf-spinner{width:14px;height:14px;border:2px solid var(–border);border-top-color:var(–green2);border-radius:50%;animation:spin .8s linear infinite;flex-shrink:0;}
@keyframes spin{to{transform:rotate(360deg);}}
.dvf-results{padding:12px 14px;}
.dvf-stat-row{display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px solid var(–border);font-size:11px;}
.dvf-stat-row:last-child{border-bottom:none;}
.dvf-stat-key{color:#aaa;}
.dvf-stat-val{font-family:‘Unbounded’,sans-serif;font-size:11px;font-weight:700;color:var(–green2);}
.dvf-btn-row{display:flex;gap:8px;padding:10px 14px;border-top:1px solid var(–border);}
.dvf-ext-btn{flex:1;background:rgba(35,163,80,.08);border:1px solid rgba(35,163,80,.2);border-radius:6px;padding:9px 6px;text-align:center;cursor:pointer;text-decoration:none;display:block;}
.dvf-ext-label{font-family:‘Unbounded’,sans-serif;font-size:8px;font-weight:700;color:var(–green2);}
.dvf-ext-sub{font-size:8px;color:var(–muted2);margin-top:2px;}

/* COMP */
.comp-list{display:flex;flex-direction:column;gap:8px;margin:0 16px 8px;}
.cc{background:var(–card);border:1px solid var(–border);border-radius:8px;padding:12px 14px;}
.cc-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
.cc-num{font-family:‘Unbounded’,sans-serif;font-size:9px;color:var(–green2);background:rgba(35,163,80,.1);border:1px solid rgba(35,163,80,.2);border-radius:3px;padding:2px 7px;}
.cc-del{background:rgba(255,77,77,.1);border:1px solid rgba(255,77,77,.2);color:var(–danger);border-radius:4px;font-size:10px;padding:3px 8px;cursor:pointer;}
.cc-auto{background:rgba(35,163,80,.08);border:1px solid rgba(35,163,80,.2);border-radius:4px;font-size:8px;color:var(–green2);padding:2px 6px;margin-left:6px;}
.cg{display:grid;grid-template-columns:1fr 1fr;gap:6px;}
.cf label{font-size:9px;color:var(–muted2);display:block;margin-bottom:3px;}
.cf input{width:100%;font-size:11px;padding:6px 8px;}
.cf.full{grid-column:1/-1;}
.add-comp{margin:0 16px 8px;background:rgba(35,163,80,.08);border:1px solid rgba(35,163,80,.2);border-radius:8px;color:var(–green2);font-family:‘DM Mono’,monospace;font-size:11px;padding:12px;width:calc(100% - 32px);cursor:pointer;text-align:center;}

/* POINTS */
.pts-g{display:grid;grid-template-columns:1fr 1fr;gap:8px;}
.pts-c{background:var(–card);border:1px solid var(–border);border-radius:8px;overflow:hidden;}
.pts-h{padding:8px 12px;font-family:‘Unbounded’,sans-serif;font-size:8px;font-weight:700;letter-spacing:.1em;border-bottom:1px solid var(–border);}
.pts-h.pos{color:#4ade80;background:rgba(74,222,128,.05);}
.pts-h.neg{color:var(–warn);background:rgba(255,184,77,.05);}
.pts-i{padding:7px 12px;font-size:10px;color:#aaa;border-bottom:1px solid var(–border);display:flex;align-items:flex-start;gap:6px;line-height:1.4;}
.pts-i:last-child{border-bottom:none;}

/* RESULTS */
.rw{padding:14px 16px;display:flex;flex-direction:column;gap:10px;}
.st{font-family:‘Unbounded’,sans-serif;font-size:9px;font-weight:700;letter-spacing:.12em;text-transform:uppercase;margin-bottom:8px;}
.st.g{color:var(–green2);}
.st.a{color:var(–accent);}
.dt{background:var(–card);border:1px solid var(–border);border-radius:8px;overflow:hidden;}
.dr{display:flex;justify-content:space-between;align-items:center;padding:9px 14px;border-bottom:1px solid var(–border);font-size:11px;gap:8px;}
.dr:last-child{border-bottom:none;}
.dr.sub{background:rgba(255,255,255,.02);}
.dr.tg{background:rgba(35,163,80,.06);font-family:‘Unbounded’,sans-serif;font-size:10px;font-weight:700;}
.dr.ta{background:rgba(200,240,62,.05);font-family:‘Unbounded’,sans-serif;font-size:10px;font-weight:700;}
.dk{color:#aaa;flex:1;}
.dv{font-family:‘DM Mono’,monospace;font-weight:500;white-space:nowrap;}
.dv.pos{color:var(–accent);}.dv.neg{color:var(–danger);}.dv.warn{color:var(–warn);}.dv.gv{color:var(–green2);}
.mg{display:grid;grid-template-columns:1fr 1fr;gap:8px;}
.mc{background:var(–card);border:1px solid var(–border);border-radius:8px;padding:12px;}
.mc.full{grid-column:1/-1;}
.ml{font-size:8px;color:var(–muted2);letter-spacing:.1em;text-transform:uppercase;margin-bottom:5px;}
.mv{font-family:‘Unbounded’,sans-serif;font-size:17px;font-weight:700;}
.mv.g{color:var(–green2);}.mv.pos{color:var(–accent);}.mv.neg{color:var(–danger);}.mv.warn{color:var(–warn);}
.ms{font-size:9px;color:var(–muted2);margin-top:3px;line-height:1.5;}

/* ESTIMATION */
.em{background:var(–green);border:2px solid var(–green2);border-radius:12px;padding:20px;text-align:center;}
.el{font-size:10px;color:rgba(255,255,255,.6);letter-spacing:.1em;text-transform:uppercase;margin-bottom:8px;}
.ep{font-family:‘Unbounded’,sans-serif;font-size:32px;font-weight:900;color:#fff;}
.em2{font-size:11px;color:rgba(255,255,255,.6);margin-top:4px;}
.eh{font-size:9px;color:rgba(255,255,255,.5);margin-top:6px;}
.er{display:grid;grid-template-columns:1fr 1fr;gap:8px;}
.es{background:var(–card);border:1px solid var(–border);border-radius:8px;padding:12px;text-align:center;}
.esl{font-size:8px;color:var(–muted2);letter-spacing:.08em;text-transform:uppercase;margin-bottom:4px;}
.esp{font-family:‘Unbounded’,sans-serif;font-size:14px;font-weight:700;}
.esm{font-size:9px;color:var(–muted2);margin-top:2px;}
.comp-disp{display:flex;flex-direction:column;gap:8px;}
.cdc{background:var(–card);border:1px solid var(–border);border-radius:8px;padding:12px 14px;}
.cdt{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:6px;}
.cda{font-size:11px;color:var(–text);flex:1;line-height:1.3;}
.cdn{font-family:‘Unbounded’,sans-serif;font-size:9px;color:var(–green2);background:rgba(35,163,80,.1);border:1px solid rgba(35,163,80,.2);border-radius:3px;padding:2px 7px;flex-shrink:0;margin-left:8px;}
.cds{display:flex;gap:8px;flex-wrap:wrap;}
.cs{font-size:10px;color:var(–muted2);}
.cs strong{color:var(–text);}

/* VERDICT */
.vc{border-radius:10px;padding:18px 16px;display:flex;align-items:center;gap:14px;border:2px solid;}
.vc.go{background:rgba(200,240,62,.07);border-color:var(–accent);}
.vc.arb{background:rgba(255,184,77,.07);border-color:var(–warn);}
.vc.nogo{background:rgba(255,77,77,.07);border-color:var(–danger);}
.vi{font-size:30px;flex-shrink:0;}
.vl{font-family:‘Unbounded’,sans-serif;font-size:20px;font-weight:900;}
.vc.go .vl{color:var(–accent);}.vc.arb .vl{color:var(–warn);}.vc.nogo .vl{color:var(–danger);}
.vs{font-size:10px;color:#aaa;margin-top:4px;line-height:1.4;}

/* FISCAL */
.ft{background:var(–card);border:1px solid var(–border);border-radius:8px;overflow:hidden;}
.fr{display:flex;align-items:center;justify-content:space-between;padding:10px 14px;border-bottom:1px solid var(–border);gap:8px;}
.fr:last-child{border-bottom:none;}
.fr.best{background:rgba(200,240,62,.06);}
.fn2{font-size:11px;color:#bbb;flex:1;}
.fr.best .fn2{color:var(–accent);}
.fv{text-align:right;}
.fc{font-family:‘Unbounded’,sans-serif;font-size:12px;font-weight:700;}
.fi{font-size:9px;color:var(–muted2);margin-top:2px;}
.ftag{font-size:8px;padding:2px 6px;border-radius:3px;background:rgba(200,240,62,.15);color:var(–accent);font-weight:700;margin-left:6px;}
.pt{background:var(–card);border:1px solid var(–border);border-radius:8px;overflow:hidden;}
.pr{display:grid;grid-template-columns:36px 1fr 1fr 1fr;padding:8px 12px;border-bottom:1px solid var(–border);font-size:10px;gap:4px;align-items:center;}
.pr:last-child{border-bottom:none;}
.pr.h{font-size:8px;color:var(–muted2);letter-spacing:.08em;text-transform:uppercase;background:rgba(255,255,255,.02);}
.pr .v{text-align:right;}

/* MISC */
.nb{background:rgba(255,184,77,.06);border:1px solid rgba(255,184,77,.2);border-radius:6px;padding:10px 12px;font-size:10px;color:var(–warn);line-height:1.5;}
.nb.g{background:rgba(35,163,80,.06);border-color:rgba(35,163,80,.2);color:var(–green2);}
.nb.b{background:rgba(200,240,62,.04);border-color:rgba(200,240,62,.15);color:var(–accent);}
.dpe-b{display:inline-block;width:22px;height:18px;border-radius:3px;text-align:center;line-height:18px;font-size:10px;font-weight:700;}
.empty{padding:50px 20px;text-align:center;color:var(–muted2);}
.empty-icon{font-size:44px;margin-bottom:14px;}
.empty-text{font-size:12px;line-height:1.6;}

@media print{
body{background:#fff;color:#000;font-family:Arial,sans-serif;}
.header,.nav,.btn,.brow,.back-btn,.add-comp,.dvf-loader,.dvf-btn-row,.no-print{display:none!important;}
.ph{display:flex!important;justify-content:space-between;align-items:center;padding:20px;border-bottom:3px solid #1a7a3a;margin-bottom:20px;}
.ph-logo{font-size:20px;font-weight:900;color:#1a7a3a;}
.ph-contact{font-size:10px;color:#666;text-align:right;line-height:1.6;}
.rw{padding:0 20px;}
.dt,.mc,.em,.cdc,.pts-c{border:1px solid #ddd!important;background:#fff!important;}
.dk,.fl{color:#333!important;}
.dv,.mv{color:#000!important;}
.dv.gv,.mv.g{color:#1a7a3a!important;}
.em{background:#1a7a3a!important;}
.ep{color:#fff!important;}
.st.g{color:#1a7a3a!important;}
}
.ph{display:none;}
</style>

</head>
<body>

<div class="header">
  <div class="header-left">
    <button class="back-btn" id="backBtn" onclick="goHome()">← Accueil</button>
    <div>
      <div class="header-title" id="hTitle">OIKO PRO</div>
      <div class="header-sub" id="hSub">Suite immobilière · Oiko Gestion</div>
    </div>
  </div>
  <div class="badge" id="hBadge">PRO</div>
</div>

<!-- HOME -->

<div id="page-home" class="page active">
  <div class="home">
    <div class="home-hero">
      <div class="home-logo">OIKO PRO</div>
      <div class="home-tagline">SUITE IMMOBILIÈRE PROFESSIONNELLE</div>
    </div>
    <div class="module-card green-mod" onclick="openModule('avis')">
      <div class="module-icon">🏠</div>
      <div>
        <div class="module-title">Avis de valeur</div>
        <div class="module-desc">Estimation · Comparables DVF automatiques · Rapport PDF Oiko Gestion</div>
      </div>
      <div class="module-arrow">›</div>
    </div>
    <div class="module-card accent-mod" onclick="openModule('loc')">
      <div class="module-icon">📊</div>
      <div>
        <div class="module-title">Analyse locative</div>
        <div class="module-desc">BP LMNP complet · 6 régimes fiscaux · TRI · Projection 10 ans</div>
      </div>
      <div class="module-arrow">›</div>
    </div>
    <div style="text-align:center;font-size:9px;color:var(--muted);padding:8px 0;">Eléïs de Barry · Asset Manager · Oiko Gestion<br>eleis.debarry@oikogestion.fr · +33 7 86 17 01 38</div>
  </div>
</div>

<!-- AVIS DE VALEUR -->

<div id="page-avis" class="page">
  <div class="nav" id="nav-avis">
    <button class="nav-tab gtab active" onclick="showAvis('bien',this)">BIEN</button>
    <button class="nav-tab gtab" onclick="showAvis('marche',this)">MARCHÉ</button>
    <button class="nav-tab gtab" onclick="showAvis('comp',this)">COMPAR.</button>
    <button class="nav-tab gtab" onclick="showAvis('estim',this)">ESTIM.</button>
    <button class="nav-tab gtab" onclick="showAvis('rapport',this)">RAPPORT</button>
  </div>

  <!-- BIEN -->

  <div id="avis-bien" class="section active">
    <div class="step-header"><span class="step-num g">01</span><span class="step-title">FICHE DU BIEN</span></div>
    <div class="form-wrap">
      <div class="fg">
        <div class="fgt g">Identification</div>
        <div class="field"><span class="fl">Adresse complète</span><input type="text" id="av_adr" placeholder="84bis Av. 8 Mai 1945, 13240 Septèmes" style="width:185px;font-size:11px;"></div>
        <div class="field"><span class="fl">Destinataire</span><input type="text" id="av_client" placeholder="Madame Rodriguez" style="width:185px;font-size:11px;"></div>
        <div class="field"><span class="fl">Type de bien</span><input type="text" id="av_type" placeholder="Duplex 3 pièces" style="width:150px;font-size:11px;"></div>
        <div class="field"><span class="fl">Surface Carrez</span><span class="fu">m²</span><input type="number" id="av_surf" value="100" min="1"></div>
        <div class="field"><span class="fl">Étage / ascenseur</span><input type="text" id="av_etage" placeholder="Dernier / non" style="width:150px;font-size:11px;"></div>
        <div class="field"><span class="fl">Année de construction</span><input type="number" id="av_annee" value="2022" min="1800" max="2025" style="width:100px;"></div>
        <div class="field"><span class="fl">DPE</span><select id="av_dpe" style="width:100px;"><option value="A">A</option><option value="B" selected>B</option><option value="C">C</option><option value="D">D</option><option value="E">E</option><option value="F">F</option><option value="G">G</option></select></div>
        <div class="field"><span class="fl">Terrasse / extérieur</span><span class="fu">m²</span><input type="number" id="av_ter" value="0" min="0"></div>
        <div class="field"><span class="fl">Places de stationnement</span><input type="number" id="av_park" value="0" min="0" style="width:100px;"></div>
        <div class="field"><span class="fl">Cave / cellier</span><select id="av_cave" style="width:100px;"><option value="non">Non</option><option value="oui">Oui</option></select></div>
        <div class="field"><span class="fl">Honoraires agence</span><span class="fu">%</span><input type="number" id="av_hono" value="5" step="0.5" min="0"></div>
      </div>
      <div class="fg">
        <div class="fgt g">Points positifs</div>
        <div id="pp_list"></div>
        <div class="field" style="padding:8px 14px;gap:6px;"><input type="text" id="pp_in" placeholder="Bon standing, lumineux…" style="width:100%;font-size:11px;"><button onclick="addPt('pos')" style="background:rgba(35,163,80,.15);border:1px solid rgba(35,163,80,.3);color:var(--green2);border-radius:5px;padding:7px 10px;cursor:pointer;font-size:13px;flex-shrink:0;">+</button></div>
      </div>
      <div class="fg">
        <div class="fgt g">Points d'attention</div>
        <div id="pn_list"></div>
        <div class="field" style="padding:8px 14px;gap:6px;"><input type="text" id="pn_in" placeholder="Concurrence directe…" style="width:100%;font-size:11px;"><button onclick="addPt('neg')" style="background:rgba(255,184,77,.08);border:1px solid rgba(255,184,77,.2);color:var(--warn);border-radius:5px;padding:7px 10px;cursor:pointer;font-size:13px;flex-shrink:0;">+</button></div>
      </div>
    </div>
    <button class="btn btn-g" onclick="showAvis('marche',document.querySelectorAll('#nav-avis .nav-tab')[1])">SUIVANT → MARCHÉ</button>
  </div>

  <!-- MARCHÉ -->

  <div id="avis-marche" class="section">
    <div class="step-header"><span class="step-num g">02</span><span class="step-title">STATISTIQUES MARCHÉ — DVF AUTO</span></div>

```
<!-- DVF AUTO LOADER -->
<div class="dvf-loader">
  <div class="dvf-search-bar">
    <input type="text" id="dvf_addr" placeholder="Adresse du bien à analyser…" style="width:auto;text-align:left;font-size:12px;">
    <button class="dvf-search-btn" onclick="lancerDVF()">ANALYSER</button>
  </div>
  <div class="dvf-status" id="dvf_status">
    <span style="color:var(--muted2);">Saisis l'adresse et lance l'analyse DVF automatique</span>
  </div>
  <div id="dvf_results" style="display:none;"></div>
  <div class="dvf-btn-row">
    <a class="dvf-ext-btn" href="#" onclick="openDVFext(event)"><div class="dvf-ext-label">🏛️ DVF ETALAB</div><div class="dvf-ext-sub">Carte interactive</div></a>
    <a class="dvf-ext-btn" href="#" onclick="openMA(event)"><div class="dvf-ext-label">📊 MEILLEURS AGENTS</div><div class="dvf-ext-sub">Prix du quartier</div></a>
  </div>
</div>

<div class="form-wrap">
  <div class="fg">
    <div class="fgt g">Données de marché (auto-remplies ou modifiables)</div>
    <div class="field"><span class="fl">Prix médian secteur</span><span class="fu">€/m²</span><input type="number" id="av_med" value="3261" step="10"></div>
    <div class="field"><span class="fl">Source des données</span><input type="text" id="av_src" placeholder="DVF 24 mois" style="width:160px;font-size:11px;"></div>
    <div class="field"><span class="fl">Évolution 24 mois</span><span class="fu">%</span><input type="number" id="av_evol" value="0" step="0.1"></div>
    <div class="field"><span class="fl">Nb transactions analysées</span><input type="number" id="av_ntx" value="0" style="width:100px;"></div>
  </div>
  <div class="fg">
    <div class="fgt g">Secteurs de référence</div>
    <div id="sect_list"></div>
    <div class="field" style="padding:8px 14px;gap:4px;">
      <input type="text" id="s_nom" placeholder="Secteur" style="width:36%;font-size:10px;">
      <input type="number" id="s_prix" placeholder="€/m²" style="width:26%;font-size:10px;">
      <input type="number" id="s_evol" placeholder="±%" step="0.1" style="width:20%;font-size:10px;">
      <button onclick="addSect()" style="background:rgba(35,163,80,.15);border:1px solid rgba(35,163,80,.3);color:var(--green2);border-radius:5px;padding:7px 8px;cursor:pointer;font-size:11px;flex-shrink:0;">+</button>
    </div>
  </div>
</div>
<button class="btn btn-g" onclick="showAvis('comp',document.querySelectorAll('#nav-avis .nav-tab')[2])">SUIVANT → COMPARABLES</button>
```

  </div>

  <!-- COMPARABLES -->

  <div id="avis-comp" class="section">
    <div class="step-header"><span class="step-num g">03</span><span class="step-title">BIENS COMPARABLES DVF</span></div>
    <div class="form-wrap" style="padding-bottom:4px;">
      <div class="nb g" id="comp_dvf_hint">Lance l'analyse DVF dans l'onglet MARCHÉ pour importer des comparables automatiquement.</div>
    </div>
    <div class="comp-list" id="comp_list"></div>
    <button class="add-comp" onclick="addComp()">+ Ajouter un comparable manuellement</button>
    <button class="btn btn-g" onclick="showAvis('estim',document.querySelectorAll('#nav-avis .nav-tab')[3])">SUIVANT → ESTIMATION</button>
  </div>

  <!-- ESTIMATION -->

  <div id="avis-estim" class="section">
    <div class="step-header"><span class="step-num g">04</span><span class="step-title">ESTIMATION DE PRIX</span></div>
    <div class="form-wrap">
      <div class="fg">
        <div class="fgt g">Fourchette d'estimation HAI</div>
        <div class="field"><span class="fl">Prix estimé</span><span class="fu">€</span><input type="number" id="av_est" value="410000" step="1000"></div>
        <div class="field"><span class="fl">Marge haute</span><span class="fu">€</span><input type="number" id="av_haut" value="420000" step="1000"></div>
        <div class="field"><span class="fl">Marge basse</span><span class="fu">€</span><input type="number" id="av_bas" value="390000" step="1000"></div>
      </div>
      <div class="fg">
        <div class="fgt g">Commentaire & recommandation</div>
        <div class="field" style="align-items:flex-start;padding:10px 14px;"><textarea id="av_com" placeholder="Synthèse et recommandation pour le client…"></textarea></div>
      </div>
    </div>
    <button class="btn btn-g" onclick="genRapport()">↳ GÉNÉRER LE RAPPORT</button>
  </div>

  <!-- RAPPORT -->

  <div id="avis-rapport" class="section">
    <div id="rapport_content"><div class="empty"><div class="empty-icon">📄</div><div class="empty-text">Génère le rapport depuis ESTIM.</div></div></div>
    <div class="brow no-print" id="rapport_btns" style="display:none;">
      <button class="btn btn-g" style="font-size:10px;" onclick="window.print()">🖨️ IMPRIMER / SAUVER PDF</button>
    </div>
  </div>
</div>

<!-- ANALYSE LOCATIVE -->

<div id="page-loc" class="page">
  <div class="nav" id="nav-loc">
    <button class="nav-tab active" onclick="showLoc('bien',this)">BIEN</button>
    <button class="nav-tab" onclick="showLoc('fin',this)">CRÉDIT</button>
    <button class="nav-tab" onclick="showLoc('rev',this)">REVENUS</button>
    <button class="nav-tab" onclick="showLoc('chg',this)">CHARGES</button>
    <button class="nav-tab" onclick="showLoc('res',this)">RÉSULTATS</button>
    <button class="nav-tab" onclick="showLoc('fis',this)">FISCAL</button>
    <button class="nav-tab" onclick="showLoc('prj',this)">PROJECTION</button>
  </div>
  <div id="loc-bien" class="section active">
    <div class="step-header"><span class="step-num a">01</span><span class="step-title">FICHE DU BIEN</span></div>
    <div class="form-wrap af">
      <div class="fg"><div class="fgt a">Identification</div>
        <div class="field"><span class="fl">Adresse</span><input type="text" id="l_adr" placeholder="12 rue de la Paix, 13001" style="width:160px;font-size:11px;"></div>
        <div class="field"><span class="fl">Type de bien</span><select id="l_type" style="width:100px;"><option>T1</option><option selected>T2</option><option>T3</option><option>T4</option><option>T5+</option></select></div>
        <div class="field"><span class="fl">Surface Carrez</span><span class="fu">m²</span><input type="number" id="l_surf" value="40" min="1"></div>
        <div class="field"><span class="fl">Année construction</span><input type="number" id="l_ann" value="1990" style="width:100px;"></div>
        <div class="field"><span class="fl">DPE</span><select id="l_dpe" style="width:100px;"><option>A</option><option>B</option><option>C</option><option selected>D</option><option>E</option><option>F</option><option>G</option></select></div>
      </div>
      <div class="fg"><div class="fgt a">Prix & frais d'acquisition</div>
        <div class="field"><span class="fl">Prix FAI</span><span class="fu">€</span><input type="number" id="l_prix" value="200000" step="1000" min="0"></div>
        <div class="field"><span class="fl">Taux frais de notaire</span><span class="fu">%</span><input type="number" id="l_fno" value="7.5" step="0.1"></div>
        <div class="fn">~7,5–8% ancien · ~3% neuf</div>
        <div class="field"><span class="fl">Honoraires agent</span><span class="fu">%</span><input type="number" id="l_hono" value="0" step="0.5"></div>
        <div class="field"><span class="fl">Travaux estimés</span><span class="fu">€</span><input type="number" id="l_trav" value="0" step="500"></div>
        <div class="field"><span class="fl">Mobilier / divers</span><span class="fu">€</span><input type="number" id="l_mob" value="5000" step="500"></div>
        <div class="field"><span class="fl">Prorata charges achat</span><span class="fu">€</span><input type="number" id="l_pro" value="0" step="100"></div>
      </div>
    </div>
    <button class="btn btn-a" onclick="showLoc('fin',document.querySelectorAll('#nav-loc .nav-tab')[1])">SUIVANT → CRÉDIT</button>
  </div>
  <div id="loc-fin" class="section">
    <div class="step-header"><span class="step-num a">02</span><span class="step-title">FINANCEMENT & CRÉDIT</span></div>
    <div class="form-wrap af">
      <div class="fg"><div class="fgt a">Apport</div>
        <div class="field"><span class="fl">Apport personnel</span><div class="aw"><select id="l_am" onchange="togAp()"><option value="pct">%</option><option value="eur">€</option></select><input type="number" id="l_ap" value="10" step="1" min="0"></div></div>
        <div class="ir" id="l_ai">% du montant total financé</div>
      </div>
      <div class="fg"><div class="fgt a">Conditions du prêt</div>
        <div class="field"><span class="fl">Taux nominal</span><span class="fu">%</span><input type="number" id="l_tx" value="3.5" step="0.05"></div>
        <div class="field"><span class="fl">Durée</span><span class="fu">ans</span><input type="number" id="l_dur" value="20" min="1" max="30"></div>
        <div class="field"><span class="fl">Assurance emprunteur</span><span class="fu">%/an</span><input type="number" id="l_ade" value="0.30" step="0.01"></div>
      </div>
      <div class="fg"><div class="fgt a">Frais annexes</div>
        <div class="field"><span class="fl">Frais de dossier</span><span class="fu">€</span><input type="number" id="l_fdos" value="1000" step="100"></div>
        <div class="fn">~1 000 à 1 500 € selon banque</div>
        <div class="field"><span class="fl">Garantie</span><select id="l_gar" style="width:150px;font-size:11px;"><option value="caution">Caution (~0,8%)</option><option value="hypotheque">Hypothèque (~1,5%)</option></select></div>
      </div>
    </div>
    <button class="btn btn-a" onclick="showLoc('rev',document.querySelectorAll('#nav-loc .nav-tab')[2])">SUIVANT → REVENUS</button>
  </div>
  <div id="loc-rev" class="section">
    <div class="step-header"><span class="step-num a">03</span><span class="step-title">REVENUS LOCATIFS</span></div>
    <div class="form-wrap af">
      <div class="fg"><div class="fgt a">Loyers</div>
        <div class="field"><span class="fl">Loyer mensuel HC</span><span class="fu">€</span><input type="number" id="l_loy" value="800" step="10"></div>
        <div class="field"><span class="fl">Taux de vacance</span><span class="fu">%</span><input type="number" id="l_vac" value="8" step="1" min="0" max="100"></div>
        <div class="fn">8% ≈ 1 mois vide/an</div>
      </div>
      <div class="fg"><div class="fgt a">Revalorisation</div>
        <div class="field"><span class="fl">Loyer / an</span><span class="fu">%</span><input type="number" id="l_rl" value="1.5" step="0.1"></div>
        <div class="field"><span class="fl">Bien / an</span><span class="fu">%</span><input type="number" id="l_rb" value="2" step="0.1"></div>
      </div>
    </div>
    <button class="btn btn-a" onclick="showLoc('chg',document.querySelectorAll('#nav-loc .nav-tab')[3])">SUIVANT → CHARGES</button>
  </div>
  <div id="loc-chg" class="section">
    <div class="step-header"><span class="step-num a">04</span><span class="step-title">CHARGES ANNUELLES</span></div>
    <div class="form-wrap af">
      <div class="fg"><div class="fgt a">Fiscalité locale</div>
        <div class="field"><span class="fl">Taxe foncière</span><span class="fu">€/an</span><input type="number" id="l_tf" value="800" step="50"></div>
      </div>
      <div class="fg"><div class="fgt a">Copropriété</div>
        <div class="field"><span class="fl">Charges courantes</span><span class="fu">€/an</span><input type="number" id="l_cc" value="1200" step="100"></div>
        <div class="field"><span class="fl">Fonds de travaux ALUR</span><span class="fu">€/an</span><input type="number" id="l_ft" value="300" step="50"></div>
      </div>
      <div class="fg"><div class="fgt a">Assurances</div>
        <div class="field"><span class="fl">Assurance PNO</span><span class="fu">€/an</span><input type="number" id="l_pno" value="300" step="50"></div>
        <div class="field"><span class="fl">CRL (loyers impayés)</span><span class="fu">%</span><input type="number" id="l_crl" value="0" step="0.5"></div>
      </div>
      <div class="fg"><div class="fgt a">Gestion & comptabilité</div>
        <div class="field"><span class="fl">Gestion locative</span><span class="fu">%</span><input type="number" id="l_ges" value="0" step="0.5"></div>
        <div class="field"><span class="fl">Comptabilité LMNP</span><span class="fu">€/an</span><input type="number" id="l_cpt" value="450" step="50"></div>
        <div class="field"><span class="fl">Autres frais</span><span class="fu">€/an</span><input type="number" id="l_aut" value="0" step="100"></div>
      </div>
      <div class="fg"><div class="fgt a">Profil fiscal</div>
        <div class="field"><span class="fl">TMI</span><select id="l_tmi" style="width:100px;"><option value="0">0%</option><option value="11">11%</option><option value="30" selected>30%</option><option value="41">41%</option><option value="45">45%</option></select></div>
      </div>
    </div>
    <button class="btn btn-a" onclick="calcLoc()">↳ ANALYSER L'INVESTISSEMENT</button>
  </div>
  <div id="loc-res" class="section"><div id="loc_res_c"><div class="empty"><div class="empty-icon">📊</div><div class="empty-text">Lance l'analyse</div></div></div></div>
  <div id="loc-fis" class="section"><div id="loc_fis_c"><div class="empty"><div class="empty-icon">🧾</div><div class="empty-text">Lance l'analyse</div></div></div></div>
  <div id="loc-prj" class="section"><div id="loc_prj_c"><div class="empty"><div class="empty-icon">📈</div><div class="empty-text">Lance l'analyse</div></div></div></div>
</div>

<script>
// ---- NAV ----
function openModule(m){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page-'+m).classList.add('active');
  document.getElementById('backBtn').style.display='flex';
  if(m==='avis'){document.getElementById('hTitle').textContent='AVIS DE VALEUR';document.getElementById('hSub').textContent='Estimation · DVF Auto';}
  else{document.getElementById('hTitle').textContent='ANALYSE LOCATIVE';document.getElementById('hSub').textContent='LMNP · LFSS 2026 · LF 2025';}
  window.scrollTo(0,0);
}
function goHome(){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page-home').classList.add('active');
  document.getElementById('backBtn').style.display='none';
  document.getElementById('hTitle').textContent='OIKO PRO';
  document.getElementById('hSub').textContent='Suite immobilière · Oiko Gestion';
  window.scrollTo(0,0);
}
function showAvis(t,btn){
  document.querySelectorAll('#page-avis .section').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('#nav-avis .nav-tab').forEach(b=>b.classList.remove('active'));
  document.getElementById('avis-'+t).classList.add('active');
  if(btn)btn.classList.add('active');
  window.scrollTo(0,0);
}
function showLoc(t,btn){
  document.querySelectorAll('#page-loc .section').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('#nav-loc .nav-tab').forEach(b=>b.classList.remove('active'));
  document.getElementById('loc-'+t).classList.add('active');
  if(btn)btn.classList.add('active');
  window.scrollTo(0,0);
}

// ---- FORMAT ----
function fmt(n,d=0){return new Intl.NumberFormat('fr-FR',{minimumFractionDigits:d,maximumFractionDigits:d}).format(n);}
function fE(n,d=0){return fmt(n,d)+' €';}
function fP(n,d=1){return fmt(n,d)+' %';}
function cv(v,p=0,w=-150){return v>p?'pos':v>w?'warn':'neg';}
function mn(c,t,d){if(t===0||c<=0)return c<=0?0:c/(d*12);const r=t/100/12,n=d*12;return c*r*Math.pow(1+r,n)/(Math.pow(1+r,n)-1);}

// ---- DVF AUTO ----
let dvfLat=null, dvfLon=null, dvfData=null;

function syncAddrDVF(){
  const a=document.getElementById('av_adr').value;
  if(a) document.getElementById('dvf_addr').value=a;
}

async function lancerDVF(){
  const addr = document.getElementById('dvf_addr').value.trim();
  if(!addr){alert('Saisis une adresse');return;}

  const statusEl = document.getElementById('dvf_status');
  const resultsEl = document.getElementById('dvf_results');
  resultsEl.style.display='none';
  statusEl.innerHTML='<div class="dvf-spinner"></div><span>Géocodage de l\'adresse…</span>';

  try {
    // 1. Géocoder l'adresse
    const geoResp = await fetch(`https://api-adresse.data.gouv.fr/search/?q=${encodeURIComponent(addr)}&limit=1`);
    const geoData = await geoResp.json();
    if(!geoData.features||geoData.features.length===0){
      statusEl.innerHTML='<span style="color:var(--danger);">❌ Adresse introuvable — vérifie la saisie</span>';
      return;
    }
    const feat = geoData.features[0];
    dvfLon = feat.geometry.coordinates[0];
    dvfLat = feat.geometry.coordinates[1];
    const label = feat.properties.label;
    statusEl.innerHTML=`<div class="dvf-spinner"></div><span>📍 ${label} — Récupération des ventes DVF…</span>`;

    // 2. Requête DVF API (Christian Quest - CORS autorisé)
    const dvfResp = await fetch(`https://api.cquest.org/dvf?lat=${dvfLat}&lon=${dvfLon}&dist=500&nature_mutation=Vente`);
    if(!dvfResp.ok) throw new Error('API DVF indisponible');
    dvfData = await dvfResp.json();

    const txs = dvfData.resultats || dvfData.results || dvfData || [];
    // Filtrer : appartements uniquement, surface > 10m², prix > 10000€
    const apparts = txs.filter(t => {
      const nature = (t.type_local||'').toLowerCase();
      const surf = parseFloat(t.surface_reelle_bati||t.surface_carrez||0);
      const prix = parseFloat(t.valeur_fonciere||0);
      return (nature.includes('appart')||nature.includes('maison')) && surf>10 && prix>10000;
    });

    if(apparts.length===0){
      statusEl.innerHTML=`<span style="color:var(--warn);">⚠️ Adresse localisée mais aucune vente trouvée dans un rayon de 500m. Essaie de lancer DVF Etalab manuellement.</span>`;
      return;
    }

    // Calculs statistiques
    const pm2s = apparts.map(t=>{
      const surf=parseFloat(t.surface_reelle_bati||t.surface_carrez||1);
      const prix=parseFloat(t.valeur_fonciere||0);
      return prix/surf;
    }).filter(v=>v>500&&v<20000).sort((a,b)=>a-b);

    const median = pm2s[Math.floor(pm2s.length/2)];
    const moy = pm2s.reduce((a,b)=>a+b,0)/pm2s.length;
    const minV = Math.min(...pm2s);
    const maxV = Math.max(...pm2s);

    // Calcul évolution : comparer transactions < 12 mois vs > 12 mois
    const now = new Date();
    const recent = apparts.filter(t=>{const d=new Date(t.date_mutation);return(now-d)<365*24*3600*1000;});
    const ancien = apparts.filter(t=>{const d=new Date(t.date_mutation);const age=(now-d)/(365*24*3600*1000);return age>=1&&age<=2;});
    let evol=0;
    if(recent.length>0&&ancien.length>0){
      const medR=recent.map(t=>parseFloat(t.valeur_fonciere||0)/parseFloat(t.surface_reelle_bati||t.surface_carrez||1)).filter(v=>v>500).sort((a,b)=>a-b);
      const medA=ancien.map(t=>parseFloat(t.valeur_fonciere||0)/parseFloat(t.surface_reelle_bati||t.surface_carrez||1)).filter(v=>v>500).sort((a,b)=>a-b);
      if(medR.length>0&&medA.length>0){
        const mR=medR[Math.floor(medR.length/2)];
        const mA=medA[Math.floor(medA.length/2)];
        evol=((mR-mA)/mA)*100;
      }
    }

    // Remplir les champs auto
    document.getElementById('av_med').value=Math.round(median);
    document.getElementById('av_src').value=`DVF API · ${apparts.length} ventes · 500m`;
    document.getElementById('av_evol').value=evol.toFixed(1);
    document.getElementById('av_ntx').value=apparts.length;

    // Afficher le résumé
    resultsEl.style.display='block';
    resultsEl.innerHTML=`<div class="dvf-results">
      <div class="dvf-stat-row"><span class="dvf-stat-key">📍 Zone analysée</span><span class="dvf-stat-val" style="font-size:10px;">${label}</span></div>
      <div class="dvf-stat-row"><span class="dvf-stat-key">Transactions analysées</span><span class="dvf-stat-val">${apparts.length} ventes</span></div>
      <div class="dvf-stat-row"><span class="dvf-stat-key">Prix médian</span><span class="dvf-stat-val">${fmt(Math.round(median))} €/m²</span></div>
      <div class="dvf-stat-row"><span class="dvf-stat-key">Prix moyen</span><span class="dvf-stat-val">${fmt(Math.round(moy))} €/m²</span></div>
      <div class="dvf-stat-row"><span class="dvf-stat-key">Fourchette</span><span class="dvf-stat-val" style="font-size:10px;">${fmt(Math.round(minV))} – ${fmt(Math.round(maxV))} €/m²</span></div>
      <div class="dvf-stat-row"><span class="dvf-stat-key">Évolution estimée</span><span class="dvf-stat-val" style="color:${evol>=0?'var(--green2)':'var(--danger)'};">${evol>=0?'+':''}${evol.toFixed(1)}%</span></div>
    </div>`;

    statusEl.innerHTML=`<span style="color:var(--green2);">✅ Analyse DVF terminée — données importées automatiquement</span>`;

    // Importer les 6 premières transactions comme comparables suggérés
    importerComparables(apparts.slice(0,6));

  } catch(e) {
    console.error(e);
    statusEl.innerHTML=`<span style="color:var(--danger);">❌ Erreur : ${e.message}. Utilise les raccourcis DVF/MA ci-dessous.</span>`;
  }
}

function importerComparables(txs){
  // Ajouter les transactions DVF comme comparables pré-remplis
  txs.forEach(t=>{
    const surf=parseFloat(t.surface_reelle_bati||t.surface_carrez||0);
    const prix=parseFloat(t.valeur_fonciere||0);
    if(surf<10||prix<10000)return;
    const pm2=Math.round(prix/surf);
    compId++;
    comparables.push({
      id:compId,
      adresse:t.adresse_numero?(t.adresse_numero+' '+t.adresse_nom_voie+', '+t.code_postal+' '+t.nom_commune):(t.nom_commune||'—'),
      type:t.type_local||'Appartement',
      surface:Math.round(surf),
      prix:Math.round(prix),
      pm2,
      date:t.date_mutation||'',
      auto:true
    });
  });
  renderComps();
  document.getElementById('comp_dvf_hint').textContent=`✅ ${txs.length} biens importés automatiquement depuis DVF`;
  document.getElementById('comp_dvf_hint').className='nb g';
}

function openDVFext(e){
  e.preventDefault();
  if(dvfLat&&dvfLon){window.open(`https://explore.data.gouv.fr/immobilier?lat=${dvfLat}&lng=${dvfLon}&zoom=15`,'_blank');}
  else{window.open('https://app.dvf.etalab.gouv.fr/','_blank');}
}
function openMA(e){
  e.preventDefault();
  const a=document.getElementById('av_adr').value||document.getElementById('dvf_addr').value||'';
  window.open(`https://www.meilleursagents.com/prix-immobilier/?q=${encodeURIComponent(a)}`,'_blank');
}

// ---- POINTS +/- ----
let ptsPos=[],ptsNeg=[];
function addPt(t){
  const inp=document.getElementById(t==='pos'?'pp_in':'pn_in');
  const v=inp.value.trim();if(!v)return;
  (t==='pos'?ptsPos:ptsNeg).push(v);inp.value='';renderPts();
}
function rmPt(t,i){(t==='pos'?ptsPos:ptsNeg).splice(i,1);renderPts();}
function renderPts(){
  ['pos','neg'].forEach(t=>{
    document.getElementById(t==='pos'?'pp_list':'pn_list').innerHTML=
      (t==='pos'?ptsPos:ptsNeg).map((p,i)=>`<div class="field" style="padding:7px 14px;"><span class="fl" style="font-size:11px;">${t==='pos'?'✅':'⚠️'} ${p}</span><button onclick="rmPt('${t}',${i})" style="background:none;border:none;color:var(--muted2);cursor:pointer;font-size:13px;">×</button></div>`).join('');
  });
}

// ---- SECTEURS ----
let secteurs=[];
function addSect(){
  const n=document.getElementById('s_nom').value.trim(),p=+document.getElementById('s_prix').value,e=+document.getElementById('s_evol').value;
  if(!n||!p)return;
  secteurs.push({n,p,e});
  document.getElementById('s_nom').value='';document.getElementById('s_prix').value='';document.getElementById('s_evol').value='';
  renderSects();
}
function rmSect(i){secteurs.splice(i,1);renderSects();}
function renderSects(){
  document.getElementById('sect_list').innerHTML=secteurs.map((s,i)=>`<div class="field"><span class="fl" style="font-size:11px;">${s.n}</span><span style="font-size:10px;color:var(--green2);margin-right:8px;">${fmt(s.p)} €/m² <span style="color:${s.e>=0?'#4ade80':'var(--danger)'};">${s.e>=0?'+':''}${s.e}%</span></span><button onclick="rmSect(${i})" style="background:none;border:none;color:var(--muted2);cursor:pointer;font-size:13px;">×</button></div>`).join('');
}

// ---- COMPARABLES ----
let comparables=[],compId=0;
function addComp(){
  compId++;comparables.push({id:compId,adresse:'',type:'',surface:'',prix:'',pm2:'',date:'',auto:false});renderComps();
}
function rmComp(id){comparables=comparables.filter(c=>c.id!==id);renderComps();}
function upComp(id,f,v){
  const c=comparables.find(c=>c.id===id);if(!c)return;
  c[f]=v;
  if(f==='prix'||f==='surface'){const p=+c.prix,s=+c.surface;if(p&&s){c.pm2=Math.round(p/s);const el=document.getElementById('cpm2_'+id);if(el)el.value=c.pm2;}}
}
function renderComps(){
  document.getElementById('comp_list').innerHTML=comparables.map((c,i)=>`
    <div class="cc">
      <div class="cc-head"><span class="cc-num">Bien ${i+1}${c.auto?'<span class="cc-auto">DVF AUTO</span>':''}</span><button class="cc-del" onclick="rmComp(${c.id})">×</button></div>
      <div class="cg">
        <div class="cf full"><label>Adresse</label><input type="text" value="${c.adresse}" placeholder="Adresse" oninput="upComp(${c.id},'adresse',this.value)"></div>
        <div class="cf"><label>Type</label><input type="text" value="${c.type}" placeholder="Appart." oninput="upComp(${c.id},'type',this.value)"></div>
        <div class="cf"><label>Surface m²</label><input type="number" value="${c.surface}" placeholder="86" oninput="upComp(${c.id},'surface',this.value)"></div>
        <div class="cf"><label>Prix € (NV)</label><input type="number" value="${c.prix}" placeholder="350000" oninput="upComp(${c.id},'prix',this.value)"></div>
        <div class="cf"><label>€/m² (auto)</label><input type="number" id="cpm2_${c.id}" value="${c.pm2}" readonly style="background:#0a0a0a;color:var(--green2);"></div>
        <div class="cf"><label>Date de vente</label><input type="date" value="${c.date}" oninput="upComp(${c.id},'date',this.value)" style="width:100%;text-align:left;"></div>
      </div>
    </div>`).join('');
}

// ---- RAPPORT ----
function genRapport(){
  const adr=document.getElementById('av_adr').value||'—';
  const client=document.getElementById('av_client').value||'—';
  const type=document.getElementById('av_type').value||'—';
  const surf=+document.getElementById('av_surf').value;
  const etage=document.getElementById('av_etage').value||'—';
  const annee=document.getElementById('av_annee').value||'—';
  const dpe=document.getElementById('av_dpe').value;
  const ter=+document.getElementById('av_ter').value;
  const park=+document.getElementById('av_park').value;
  const cave=document.getElementById('av_cave').value;
  const hono=+document.getElementById('av_hono').value;
  const med=+document.getElementById('av_med').value;
  const src=document.getElementById('av_src').value||'DVF / Observatoires';
  const evol=+document.getElementById('av_evol').value;
  const ntx=+document.getElementById('av_ntx').value;
  const est=+document.getElementById('av_est').value;
  const haut=+document.getElementById('av_haut').value;
  const bas=+document.getElementById('av_bas').value;
  const com=document.getElementById('av_com').value||'';
  const honoMt=est*hono/100;
  const nv=est-honoMt;
  const dpeCols={A:'#009a44',B:'#4cb848',C:'#c8d400',D:'#f7a600',E:'#e9421e',F:'#c81c16',G:'#8b0000'};
  const compV=comparables.filter(c=>c.prix&&c.surface);
  const pm2moy=compV.length>0?Math.round(compV.reduce((a,c)=>a+(+c.prix/+c.surface),0)/compV.length):0;
  const pmoy=compV.length>0?Math.round(compV.reduce((a,c)=>a+(+c.prix),0)/compV.length):0;
  const today=new Date().toLocaleDateString('fr-FR',{day:'2-digit',month:'long',year:'numeric'});

  document.getElementById('rapport_content').innerHTML=`
    <div class="ph"><div><div style="font-size:20px;font-weight:900;color:#1a7a3a;font-family:Arial;">OIKO GESTION</div><div style="font-size:10px;color:#666;">17 rue de la République · 13002 Marseille</div></div><div style="font-size:10px;color:#666;text-align:right;">Eléïs de Barry · Asset Manager<br>eleis.debarry@oikogestion.fr<br>+33 7 86 17 01 38</div></div>
    <div class="rw">
      <div class="st g">AVIS DE VALEUR MARCHÉ — ${today}</div>
      <div class="dt">
        <div class="dr tg"><span class="dk">À l'attention de</span><span class="dv gv">${client}</span></div>
        <div class="dr"><span class="dk">Bien</span><span class="dv">${type}</span></div>
        <div class="dr"><span class="dk">Adresse</span><span class="dv" style="font-size:10px;max-width:190px;text-align:right;word-break:break-word;">${adr}</span></div>
        <div class="dr"><span class="dk">Surface Carrez</span><span class="dv">${surf} m²</span></div>
        <div class="dr"><span class="dk">Étage / ascenseur</span><span class="dv">${etage}</span></div>
        <div class="dr"><span class="dk">Année de construction</span><span class="dv">${annee}</span></div>
        <div class="dr"><span class="dk">DPE</span><span class="dv"><span class="dpe-b" style="background:${dpeCols[dpe]};color:#fff">${dpe}</span></span></div>
        ${ter>0?`<div class="dr"><span class="dk">Terrasse / extérieur</span><span class="dv">${ter} m²</span></div>`:''}
        ${park>0?`<div class="dr"><span class="dk">Stationnement</span><span class="dv">${park} place${park>1?'s':''}</span></div>`:''}
        ${cave==='oui'?`<div class="dr"><span class="dk">Cave / cellier</span><span class="dv">Oui</span></div>`:''}
      </div>
      ${ptsPos.length>0||ptsNeg.length>0?`
      <div class="st g">CARACTÉRISTIQUES DU BIEN</div>
      <div class="pts-g">
        ${ptsPos.length>0?`<div class="pts-c"><div class="pts-h pos">POINTS POSITIFS</div>${ptsPos.map(p=>`<div class="pts-i"><span style="color:#4ade80">✓</span>${p}</div>`).join('')}</div>`:''}
        ${ptsNeg.length>0?`<div class="pts-c"><div class="pts-h neg">POINTS D'ATTENTION</div>${ptsNeg.map(p=>`<div class="pts-i"><span style="color:var(--warn)">!</span>${p}</div>`).join('')}</div>`:''}
      </div>`:''}
      <div class="st g">STATISTIQUES MARCHÉ LOCAL</div>
      <div class="dt">
        <div class="dr"><span class="dk">Prix médian secteur</span><span class="dv gv">${fmt(med)} €/m²</span></div>
        <div class="dr"><span class="dk">Source</span><span class="dv" style="font-size:10px;">${src}</span></div>
        ${ntx>0?`<div class="dr"><span class="dk">Transactions analysées</span><span class="dv">${ntx}</span></div>`:''}
        <div class="dr"><span class="dk">Évolution 24 mois</span><span class="dv ${evol>=0?'gv':'neg'}">${evol>=0?'+':''}${fP(evol)}</span></div>
      </div>
      ${secteurs.length>0?`<div class="dt">${secteurs.map(s=>`<div class="dr"><span class="dk" style="font-size:10px;">${s.n}</span><span class="dv" style="font-size:10px;">${fmt(s.p)} €/m² <span style="color:${s.e>=0?'#4ade80':'var(--danger)'};">${s.e>=0?'+':''}${s.e}%</span></span></div>`).join('')}</div>`:''}
      ${comparables.length>0?`
      <div class="st g">BIENS VENDUS COMPARABLES</div>
      <div class="comp-disp">${comparables.map((c,i)=>`<div class="cdc"><div class="cdt"><span class="cda">${c.adresse||'—'}</span><span class="cdn">Bien ${i+1}${c.auto?' · DVF':''}</span></div><div class="cds"><span class="cs"><strong>${c.type||'—'}</strong></span><span class="cs"><strong>${c.surface||'—'} m²</strong></span><span class="cs" style="color:var(--green2);"><strong>${fE(+c.prix||0)}</strong></span><span class="cs">${c.pm2?fmt(c.pm2)+' €/m²':'—'}</span>${c.date?`<span class="cs">${new Date(c.date).toLocaleDateString('fr-FR')}</span>`:''}</div></div>`).join('')}</div>
      ${pm2moy>0?`<div class="dt"><div class="dr tg"><span class="dk">PRIX MOYEN DE LA SÉLECTION</span><span class="dv gv">${fE(pmoy)} · ${fmt(pm2moy)} €/m²</span></div></div>`:''}`:''}
      <div class="st g">ESTIMATION DE PRIX</div>
      <div class="em"><div class="el">PRIX ESTIMÉ (HONORAIRES INCLUS)</div><div class="ep">${fE(est)}</div><div class="em2">${fmt(Math.round(est/surf))} €/m²</div><div class="eh">Honoraires ${fP(hono)} inclus · Net vendeur : ${fE(nv)}</div></div>
      <div class="er">
        <div class="es"><div class="esl">↑ MARGE HAUTE</div><div class="esp">${fE(haut)}</div><div class="esm">${fmt(Math.round(haut/surf))} €/m²</div></div>
        <div class="es"><div class="esl">↓ MARGE BASSE</div><div class="esp">${fE(bas)}</div><div class="esm">${fmt(Math.round(bas/surf))} €/m²</div></div>
      </div>
      ${com?`<div class="st g">COMMENTAIRES & RECOMMANDATION</div><div class="dt"><div class="dr" style="align-items:flex-start;"><span class="dk" style="line-height:1.6;color:#ccc;font-size:11px;">${com.replace(/\n/g,'<br>')}</span></div></div>`:''}
      <div class="nb g" style="font-size:9px;">Les indicateurs de cette étude sont communiqués sous l'entière responsabilité du professionnel. Cette estimation, non contractuelle, est un avis de valeur qui ne peut se substituer à une expertise immobilière.</div>
      <div style="text-align:center;padding:8px 0;font-size:9px;color:var(--muted2);">OIKO GESTION · 17 rue de la République · 13002 Marseille · eleis.debarry@oikogestion.fr · oikogestion.fr</div>
    </div>`;
  document.getElementById('rapport_btns').style.display='flex';
  showAvis('rapport',document.querySelectorAll('#nav-avis .nav-tab')[4]);
}

// ---- ANALYSE LOCATIVE ----
function togAp(){const m=document.getElementById('l_am').value,i=document.getElementById('l_ai'),inp=document.getElementById('l_ap');if(m==='pct'){i.textContent='% du total financé';inp.step=1;inp.value=10;}else{i.textContent='Montant en euros';inp.step=1000;inp.value=20000;}}

function calcLoc(){
  const prix=+document.getElementById('l_prix').value;
  const fno=+document.getElementById('l_fno').value;
  const hono=+document.getElementById('l_hono').value;
  const trav=+document.getElementById('l_trav').value;
  const mob=+document.getElementById('l_mob').value;
  const pro=+document.getElementById('l_pro').value;
  const surf=+document.getElementById('l_surf').value;
  const dpe=document.getElementById('l_dpe').value;
  const am=document.getElementById('l_am').value;
  const av=+document.getElementById('l_ap').value;
  const tx=+document.getElementById('l_tx').value;
  const dur=+document.getElementById('l_dur').value;
  const ade=+document.getElementById('l_ade').value;
  const fdos=+document.getElementById('l_fdos').value;
  const gar=document.getElementById('l_gar').value;
  const tg=gar==='caution'?0.008:0.015;
  const loy=+document.getElementById('l_loy').value;
  const vac=+document.getElementById('l_vac').value;
  const rl=+document.getElementById('l_rl').value/100;
  const rb=+document.getElementById('l_rb').value/100;
  const tf=+document.getElementById('l_tf').value;
  const cc=+document.getElementById('l_cc').value;
  const ft=+document.getElementById('l_ft').value;
  const pno=+document.getElementById('l_pno').value;
  const crl=+document.getElementById('l_crl').value;
  const ges=+document.getElementById('l_ges').value;
  const cpt=+document.getElementById('l_cpt').value;
  const aut=+document.getElementById('l_aut').value;
  const tmi=+document.getElementById('l_tmi').value;

  const fn=prix*fno/100, ho=prix*hono/100;
  const cAcq=prix+fn+ho+trav+mob+pro;
  let apm,emp,fg;
  if(am==='pct'){const p=av/100;const tfi=(cAcq+fdos)/(1-tg*(1-p));apm=tfi*p;emp=tfi-apm;fg=emp*tg;}
  else{apm=av;emp=(cAcq+fdos-apm)/(1-tg);fg=emp*tg;}
  const tF=cAcq+fdos+fg;
  const apr=tF>0?(apm/tF)*100:0;
  const mhi=mn(emp,tx,dur);
  const am2=emp*(ade/100)/12;
  const mt=mhi+am2;
  const aa=mt*12;
  const cred=mhi*dur*12-emp;
  const int1=emp>0?emp*tx/100:0;
  const la=loy*12;
  const le=la*(1-vac/100);
  const crla=le*crl/100;
  const ga=le*ges/100;
  const tc=tf+cc+ft+pno+crla+ga+cpt+aut;
  const rb2=prix>0?(la/prix)*100:0;
  const rn=cAcq>0?((le-tc)/cAcq)*100:0;
  const cf0=le-tc-aa;
  const PS=0.172,PB=0.186;
  const iF=le*0.70*(tmi/100+PS);
  const rFR=Math.max(0,le-tc-int1);const iFR=rFR*(tmi/100+PS);
  const iMB=le*0.50*(tmi/100+PB);
  const aB=prix*0.85/30,aM=mob>0?mob/7:0,aT=trav>0?trav/10:0,aTo=aB+aM+aT;
  const rLR=Math.max(0,le-tc-int1-aTo);const iLR=rLR*(tmi/100+PB);
  const rIS=le-tc-int1-aB;const is=rIS<=0?0:rIS<=42500?rIS*0.15:42500*0.15+(rIS-42500)*0.25;
  const cfn=i=>le-tc-aa-i;
  const regs=[{n:'Micro-foncier',t:'Nu',i:iF,cf:cfn(iF)},{n:'Foncier réel',t:'Nu',i:iFR,cf:cfn(iFR)},{n:'Micro-BIC (LMNP)',t:'Meublé',i:iMB,cf:cfn(iMB)},{n:'LMNP réel',t:'Meublé',i:iLR,cf:cfn(iLR)},{n:'SCI IR',t:'Société',i:iFR,cf:cfn(iFR)},{n:'SCI IS',t:'Société',i:is,cf:cfn(is)}];
  const best=regs.reduce((a,b)=>b.cf>a.cf?b:a);
  const cfO=best.cf;
  const eff=Math.max(0,-cfO/12);
  const rec=cfO>0?apm/cfO:null;
  function tRI(fl,inv){if(inv<=0)return 0;let r=0.05;for(let i=0;i<100;i++){let n=-inv,dn=0;fl.forEach((f,j)=>{const p=Math.pow(1+r,j+1);n+=f/p;dn-=(j+1)*f/(p*(1+r));});const rN=r-n/dn;if(Math.abs(rN-r)<0.00001){r=rN;break;}r=rN;}return r*100;}
  let prs=[],cum=0,fTRI=[];
  for(let a=1;a<=10;a++){
    const mL=Math.pow(1+rl,a-1),mC=Math.pow(1.02,a-1);
    const lA=le*mL,cA=tc*mC;
    const cb=lA-cA-aa;
    const ie=Math.max(0,(lA-cA-int1-aTo)*(tmi/100+PB));
    const cn=cb-ie;cum+=cn;
    const vB=prix*Math.pow(1+rb,a);
    const r2=tx/100/12,n2=dur*12,mR=Math.max(0,n2-a*12);
    const crd=emp>0&&tx>0?mhi*(1-Math.pow(1+r2,-mR))/r2:Math.max(0,emp-a*(aa-int1));
    fTRI.push(cn+(a===10?vB-crd:0));
    prs.push({a,cm:cn/12,cum,vB,crd});
  }
  const tri=tRI(fTRI,apm||cAcq);
  let vCls,vIc,vLb,vSb;
  if(cfO/12>50&&rn>4){vCls='go';vIc='✅';vLb='GO';vSb='Cashflow positif · Rendement solide';}
  else if(cfO/12>-150||rn>3){vCls='arb';vIc='⚖️';vLb='À ARBITRER';vSb='Cashflow limité · À optimiser fiscalement';}
  else{vCls='nogo';vIc='❌';vLb='NO GO';vSb='Effort d\'épargne significatif';}
  const dpeCols={A:'#009a44',B:'#4cb848',C:'#c8d400',D:'#f7a600',E:'#e9421e',F:'#c81c16',G:'#8b0000'};
  const dW=['E','F','G'].includes(dpe)?`<div class="nb" style="margin-bottom:10px;">⚠️ DPE ${dpe} — Restriction locative imminente.</div>`:dpe==='D'?`<div class="nb" style="margin-bottom:10px;">⚠️ DPE D — Interdit à la location en 2028 sans travaux.</div>`:'';

  document.getElementById('loc_res_c').innerHTML=`<div class="rw">
    ${dW}
    <div class="vc ${vCls}"><div class="vi">${vIc}</div><div><div class="vl">${vLb}</div><div class="vs">${vSb}<br><span style="color:var(--muted2);font-size:9px;">Régime optimal : ${best.n}</span></div></div></div>
    <div class="mg">
      <div class="mc"><div class="ml">Rendement brut</div><div class="mv ${rb2>6?'pos':rb2>4?'warn':'neg'}">${fP(rb2)}</div><div class="ms">Loyers/Prix FAI</div></div>
      <div class="mc"><div class="ml">Rendement net</div><div class="mv ${rn>4?'pos':rn>2.5?'warn':'neg'}">${fP(rn)}</div><div class="ms">Après charges</div></div>
      <div class="mc"><div class="ml">Cashflow/mois</div><div class="mv ${cv(cfO/12,50,-150)}">${fE(cfO/12)}</div><div class="ms">${best.n}</div></div>
      <div class="mc"><div class="ml">TRI 10 ans</div><div class="mv ${tri>8?'pos':tri>4?'warn':'neg'}">${fP(tri)}</div><div class="ms">Avec revente</div></div>
      ${eff>0?`<div class="mc"><div class="ml">Effort/mois</div><div class="mv warn">${fE(eff)}</div></div>`:''}
      ${rec?`<div class="mc"><div class="ml">Récup. apport</div><div class="mv">${fmt(rec,1)} ans</div></div>`:''}
    </div>
    <div class="st a">PLAN DE FINANCEMENT</div>
    <div class="dt">
      <div class="dr"><span class="dk">Prix FAI</span><span class="dv">${fE(prix)}</span></div>
      <div class="dr"><span class="dk">Frais de notaire</span><span class="dv">${fE(fn)}</span></div>
      ${trav>0?`<div class="dr"><span class="dk">Travaux</span><span class="dv">${fE(trav)}</span></div>`:''}
      ${mob>0?`<div class="dr"><span class="dk">Mobilier</span><span class="dv">${fE(mob)}</span></div>`:''}
      <div class="dr sub"><span class="dk">Coût total acquisition</span><span class="dv">${fE(cAcq)}</span></div>
      <div class="dr"><span class="dk">Frais dossier + garantie</span><span class="dv">${fE(fdos+fg)}</span></div>
      <div class="dr ta"><span class="dk">TOTAL FINANCÉ</span><span class="dv">${fE(tF)}</span></div>
      <div class="dr"><span class="dk">Apport (${fP(apr)})</span><span class="dv pos">${fE(apm)}</span></div>
      <div class="dr"><span class="dk">Montant emprunté</span><span class="dv">${fE(emp)}</span></div>
      <div class="dr ta"><span class="dk">MENSUALITÉ TOTALE</span><span class="dv neg">${fE(mt)}/mois</span></div>
      <div class="dr"><span class="dk">Coût total des intérêts</span><span class="dv neg">${fE(cred)}</span></div>
    </div>
    <div class="st a">REVENUS & CHARGES</div>
    <div class="dt">
      <div class="dr"><span class="dk">Loyer annuel brut HC</span><span class="dv pos">${fE(la)}</span></div>
      <div class="dr"><span class="dk">Vacance (${fP(vac)})</span><span class="dv neg">−${fE(la*vac/100)}</span></div>
      <div class="dr sub"><span class="dk">Revenus locatifs nets</span><span class="dv pos">${fE(le)}</span></div>
      <div class="dr"><span class="dk">Total charges (hors crédit)</span><span class="dv neg">${fE(tc)}</span></div>
      <div class="dr"><span class="dk">Mensualité annualisée</span><span class="dv neg">${fE(aa)}</span></div>
      <div class="dr ta"><span class="dk">CASHFLOW AVANT IMPÔT</span><span class="dv ${cv(cf0)}">${fE(cf0)}/an</span></div>
    </div>
  </div>`;

  const regS=[...regs].sort((a,b)=>b.cf-a.cf);
  document.getElementById('loc_fis_c').innerHTML=`<div class="rw">
    <div class="st a">Comparatif 6 régimes fiscaux</div>
    <div class="ft">${regS.map((r,i)=>`<div class="fr ${i===0?'best':''}"><div><div class="fn2">${r.n} <span style="font-size:8px;color:var(--muted2)">${r.t}</span>${i===0?'<span class="ftag">OPTIMAL</span>':''}</div><div class="fi">Impôt an 1 : ${fE(r.i)}</div></div><div class="fv"><div class="fc" style="color:${r.cf/12>0?'var(--accent)':r.cf/12>-150?'var(--warn)':'var(--danger)'}">${fE(r.cf/12)}/m</div><div class="fi">${fE(r.cf)}/an</div></div></div>`).join('')}</div>
    <div class="st a" style="margin-top:12px;">AMORTISSEMENTS LMNP RÉEL</div>
    <div class="dt">
      <div class="dr"><span class="dk">Bien immo (85%·30 ans)</span><span class="dv">${fE(aB)}/an</span></div>
      ${mob>0?`<div class="dr"><span class="dk">Mobilier (7 ans)</span><span class="dv">${fE(aM)}/an</span></div>`:''}
      ${trav>0?`<div class="dr"><span class="dk">Travaux (10 ans)</span><span class="dv">${fE(aT)}/an</span></div>`:''}
      <div class="dr ta"><span class="dk">Total amortissement</span><span class="dv">${fE(aTo)}/an</span></div>
      <div class="dr"><span class="dk">Résultat imposable LMNP réel</span><span class="dv ${rLR===0?'pos':'warn'}">${rLR===0?'0 € — déficit reportable':fE(rLR)}</span></div>
    </div>
    <div class="nb">⚠ LFSS 2026 : PS 17,2% · BIC 18,6%<br>⚠ LF 2025 : réintégration amortissements en plus-value LMNP</div>
  </div>`;

  document.getElementById('loc_prj_c').innerHTML=`<div class="rw">
    <div class="st a">Projection 10 ans — ${best.n}</div>
    <div class="pt"><div class="pr h"><span>AN</span><span class="v">CF/mois</span><span class="v">CUMUL</span><span class="v">VALEUR</span></div>${prs.map(r=>`<div class="pr"><span>${r.a}</span><span class="v ${r.cm>0?'pos':r.cm>-150?'warn':'neg'}">${fE(r.cm)}</span><span class="v ${r.cum>0?'pos':'neg'}">${fmt(r.cum/1000,0)}k</span><span class="v">${fmt(r.vB/1000,0)}k</span></div>`).join('')}</div>
    <div class="dt"><div class="dr"><span class="dk">Valeur estimée an 10</span><span class="dv">${fE(prs[9].vB)}</span></div><div class="dr"><span class="dk">Capital restant dû an 10</span><span class="dv neg">${fE(prs[9].crd)}</span></div><div class="dr ta"><span class="dk">PATRIMOINE NET AN 10</span><span class="dv pos">${fE(prs[9].vB-prs[9].crd)}</span></div></div>
    <div class="nb">Hypothèses : loyers +${fP(rl*100)}/an · bien +${fP(rb*100)}/an · charges +2%/an</div>
  </div>`;

  showLoc('res',document.querySelectorAll('#nav-loc .nav-tab')[4]);
}

// Sync adresse depuis BIEN → champ DVF
document.getElementById('av_adr').addEventListener('blur',syncAddrDVF);
</script>

</body>
</html>
