<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Studio Balma — Visualização Arquitetônica</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Montserrat:wght@200;300;400;500;600&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
:root{
  --black:#000;
  --black-soft:#0a0a0a;
  --black-mid:#111;
  --black-card:#161616;
  --gold:#C9A84C;
  --gold-light:#E2C07A;
  --gold-pale:#F0D9A0;
  --gold-dim:#8A6E2F;
  --white:#F5F0E8;
  --grey:#888;
}
html{scroll-behavior:smooth}
body{background:var(--black);color:var(--white);font-family:'Montserrat',sans-serif;font-weight:300;font-size:13px;letter-spacing:.04em;overflow-x:hidden}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--black)}
::-webkit-scrollbar-thumb{background:var(--gold-dim);border-radius:2px}

/* ── NAV ── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;
  padding:22px 60px;
  background:linear-gradient(to bottom,rgba(0,0,0,.97) 0%,transparent 100%);
  transition:background .3s;
}
nav.scrolled{background:rgba(0,0,0,.97);border-bottom:1px solid rgba(201,168,76,.15)}
.nav-logo{display:flex;align-items:center;gap:14px;text-decoration:none}
.nav-logo-icon{
  width:44px;height:44px;
  border:1px solid var(--gold);border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  font-size:18px;color:var(--gold);
}
.nav-logo-text{display:flex;flex-direction:column;line-height:1}
.nav-logo-studio{font-family:'Montserrat',sans-serif;font-size:9px;letter-spacing:.4em;text-transform:uppercase;color:var(--grey);font-weight:300}
.nav-logo-balma{font-family:'Montserrat',sans-serif;font-size:18px;letter-spacing:.2em;font-weight:600;color:var(--white)}
.nav-links{display:flex;gap:36px;list-style:none}
.nav-links a{color:var(--grey);text-decoration:none;font-size:10px;letter-spacing:.18em;text-transform:uppercase;transition:color .3s}
.nav-links a:hover{color:var(--gold)}
.nav-cta{font-size:10px;letter-spacing:.18em;text-transform:uppercase;color:var(--gold);border:1px solid var(--gold);padding:10px 26px;text-decoration:none;transition:all .3s}
.nav-cta:hover{background:var(--gold);color:var(--black)}

/* ── HERO ── */
.hero{height:100vh;position:relative;display:flex;align-items:flex-end;padding:0 60px 80px;overflow:hidden}
.hero-media{position:absolute;inset:0;overflow:hidden}
.hero-media img{width:100%;height:100%;object-fit:cover;opacity:.75}
.hero-media::after{
  content:'';position:absolute;inset:0;
  background:
    linear-gradient(to right,rgba(0,0,0,.93) 0%,rgba(0,0,0,.55) 50%,rgba(0,0,0,.15) 100%),
    linear-gradient(to top,rgba(0,0,0,.8) 0%,transparent 55%);
}
.hero-media::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(201,168,76,.1) 0%,transparent 55%);
  z-index:1;
}
/* linha dourada lateral */
.hero-line{
  position:absolute;left:0;top:0;bottom:0;width:3px;z-index:5;
  background:linear-gradient(to bottom,transparent,var(--gold),transparent);
  opacity:.6;
}
.hero-content{position:relative;z-index:3;max-width:600px}
.hero-eyebrow{
  display:flex;align-items:center;gap:14px;margin-bottom:28px;
  font-size:10px;letter-spacing:.35em;text-transform:uppercase;color:var(--gold);
}
.hero-eyebrow::before{content:'';display:block;width:40px;height:1px;background:var(--gold)}
.hero-title{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(48px,6vw,84px);font-weight:300;line-height:1.06;
  color:var(--white);margin-bottom:12px;
}
.hero-title em{font-style:italic;color:var(--gold-light)}
.hero-tagline{
  font-family:'Montserrat',sans-serif;font-size:11px;
  letter-spacing:.25em;text-transform:uppercase;
  color:var(--gold-dim);margin-bottom:28px;
}
.hero-sub{font-size:14px;line-height:1.9;color:var(--grey);max-width:440px;margin-bottom:52px}
.hero-actions{display:flex;gap:20px;align-items:center}
.btn-primary{
  background:var(--gold);color:var(--black);
  padding:14px 40px;font-size:10px;letter-spacing:.2em;
  text-transform:uppercase;text-decoration:none;
  font-family:'Montserrat',sans-serif;font-weight:600;
  transition:background .3s;display:inline-block;
}
.btn-primary:hover{background:var(--gold-light)}
.btn-outline{
  color:var(--white);font-size:10px;letter-spacing:.2em;text-transform:uppercase;
  text-decoration:none;border:1px solid rgba(255,255,255,.25);
  padding:14px 32px;transition:all .3s;
}
.btn-outline:hover{border-color:var(--gold);color:var(--gold)}
/* ornamento canto */
.hero-badge{
  position:absolute;bottom:48px;right:60px;z-index:3;
  width:72px;height:72px;border:1px solid rgba(201,168,76,.4);
  transform:rotate(45deg);
}
.hero-badge::before{
  content:'';position:absolute;inset:8px;
  border:1px solid rgba(201,168,76,.2);
}

/* ── DIVIDER ── */
.gold-line{width:100%;height:1px;background:linear-gradient(to right,transparent,var(--gold-dim),transparent);opacity:.5}

/* ── SEÇÃO BASE ── */
.sec{padding:110px 60px}
.sec-tag{font-size:9px;letter-spacing:.35em;text-transform:uppercase;color:var(--gold);margin-bottom:14px}
.sec-title{font-family:'Cormorant Garamond',serif;font-size:clamp(32px,4vw,50px);font-weight:300;color:var(--white);line-height:1.1}
.sec-title em{font-style:italic;color:var(--gold-light)}
.sec-header{display:flex;align-items:flex-end;justify-content:space-between;margin-bottom:70px;padding-bottom:28px;border-bottom:1px solid rgba(201,168,76,.15)}
.sec-desc{font-size:13px;color:var(--grey);line-height:1.8;max-width:280px;text-align:right}

/* ── CONCEITO ── */
.conceito{background:var(--black-mid);padding:110px 60px;display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:center}
.conceito-img{
  position:relative;
  border:1px solid rgba(201,168,76,.25);
  padding:4px;
}
.conceito-img img{width:100%;height:420px;object-fit:cover;display:block}
.conceito-label{
  position:absolute;top:16px;right:16px;
  font-size:9px;letter-spacing:.25em;text-transform:uppercase;
  color:var(--gold);background:rgba(0,0,0,.7);padding:6px 12px;
  border:1px solid rgba(201,168,76,.3);
}
.conceito-content .sec-tag{margin-bottom:8px}
.conceito-big{
  font-family:'Cormorant Garamond',serif;font-size:clamp(42px,5vw,68px);
  font-weight:400;color:var(--gold);line-height:1;margin-bottom:24px;letter-spacing:.05em;
}
.conceito-body{font-size:14px;line-height:2;color:var(--grey);margin-bottom:20px}
.conceito-body strong{color:var(--white);font-weight:400}
.conceito-quote{
  border-left:2px solid var(--gold);padding-left:20px;
  font-family:'Cormorant Garamond',serif;font-size:18px;
  font-style:italic;color:var(--white);line-height:1.6;margin-top:32px;
}

/* ── PORTFÓLIO TABS ── */
.portfolio{background:var(--black);padding:110px 60px}
.nicho-tabs{display:flex;gap:0;margin-bottom:44px;border-bottom:1px solid rgba(201,168,76,.12)}
.nicho-tab{
  padding:14px 28px;font-size:10px;letter-spacing:.18em;text-transform:uppercase;
  color:var(--grey);border-bottom:2px solid transparent;margin-bottom:-1px;
  transition:color .3s,border-color .3s;background:none;
  border-top:none;border-left:none;border-right:none;
  font-family:'Montserrat',sans-serif;cursor:pointer;
}
.nicho-tab:hover{color:var(--white)}
.nicho-tab.active{color:var(--gold);border-bottom-color:var(--gold)}
.nicho-panel{display:none}
.nicho-panel.active{display:block}
.projects-grid{display:grid;grid-template-columns:repeat(12,1fr);gap:2px}
.project-card{position:relative;overflow:hidden;background:var(--black-card);cursor:pointer}
.project-card:nth-child(1){grid-column:span 7;grid-row:span 2}
.project-card:nth-child(2){grid-column:span 5}
.project-card:nth-child(3){grid-column:span 5}
.project-card:nth-child(4){grid-column:span 4}
.project-card:nth-child(5){grid-column:span 4}
.project-card:nth-child(6){grid-column:span 4}
.project-card .img-wrap{width:100%;padding-top:75%;position:relative;overflow:hidden;background:var(--black-mid)}
.project-card:nth-child(1) .img-wrap{padding-top:100%}
.project-card .img-wrap img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;transition:transform .7s ease;display:block}
.project-card:hover .img-wrap img{transform:scale(1.05)}
.project-card .overlay{
  position:absolute;inset:0;
  background:linear-gradient(to top,rgba(0,0,0,.7) 0%,transparent 50%);
  opacity:0;transition:opacity .4s;
}
.project-card:hover .overlay{opacity:1}
.proj-placeholder{
  position:absolute;inset:0;display:flex;flex-direction:column;
  align-items:center;justify-content:center;gap:8px;
  color:rgba(201,168,76,.2);font-size:10px;letter-spacing:.2em;text-transform:uppercase;
}
.proj-placeholder .ico{font-size:20px}
.project-info{
  padding:16px 20px;display:flex;align-items:center;justify-content:space-between;
  border-top:1px solid rgba(201,168,76,.08);
}
.project-name{font-family:'Cormorant Garamond',serif;font-size:16px;font-weight:300;color:var(--white)}
.project-type{font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--grey);margin-top:2px}
.project-arrow{color:var(--gold);font-size:14px;opacity:0;transform:translateX(-8px);transition:all .3s}
.project-card:hover .project-arrow{opacity:1;transform:translateX(0)}

/* ── SOBRE / SAMUEL ── */
.sobre{background:var(--black-mid);padding:110px 60px;display:grid;grid-template-columns:1fr 1fr;gap:90px;align-items:center;border-top:1px solid rgba(201,168,76,.12);border-bottom:1px solid rgba(201,168,76,.12)}
.sobre-foto{
  position:relative;
  width:340px;border:1px solid rgba(201,168,76,.3);padding:4px;
  margin:auto;
}
.sobre-foto img{width:100%;height:420px;object-fit:cover;object-position:top;display:block;filter:grayscale(30%)}
.sobre-foto-nome{
  position:absolute;bottom:0;left:0;right:0;
  background:linear-gradient(to top,rgba(0,0,0,.9),transparent);
  padding:32px 20px 16px;
}
.sobre-foto-nome h3{font-family:'Cormorant Garamond',serif;font-size:26px;font-weight:300;color:var(--white)}
.sobre-foto-nome span{font-size:9px;letter-spacing:.25em;text-transform:uppercase;color:var(--gold)}
.sobre-accent{position:absolute;bottom:-14px;right:-14px;width:120px;height:120px;border:1px solid rgba(201,168,76,.3)}
.sobre-text{font-size:14px;line-height:2;color:var(--grey);margin-bottom:40px}
.sobre-text strong{color:var(--white);font-weight:400}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:28px;margin-bottom:40px;padding-top:36px;border-top:1px solid rgba(201,168,76,.18)}
.stat-num{font-family:'Cormorant Garamond',serif;font-size:38px;font-weight:300;color:var(--gold);line-height:1;margin-bottom:5px}
.stat-label{font-size:9px;letter-spacing:.16em;text-transform:uppercase;color:var(--grey)}
.sobre-localidade{
  display:flex;align-items:center;gap:10px;
  font-size:11px;letter-spacing:.1em;color:var(--grey);margin-top:20px;
}
.sobre-localidade span{color:var(--gold)}

/* ── SERVIÇOS ── */
.servicos{background:var(--black);padding:110px 60px}
.servicos-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;margin-top:0}
.servico-card{
  padding:44px 28px;background:var(--black-card);
  position:relative;overflow:hidden;transition:background .4s;
  border-left:2px solid transparent;
}
.servico-card:hover{background:#120e00;border-left-color:var(--gold)}
.servico-num{font-family:'Cormorant Garamond',serif;font-size:48px;color:var(--gold);opacity:.1;line-height:1;margin-bottom:24px}
.servico-icon{font-size:22px;margin-bottom:16px;color:var(--gold)}
.servico-name{font-family:'Cormorant Garamond',serif;font-size:20px;font-weight:300;color:var(--white);margin-bottom:10px}
.servico-desc{font-size:12px;line-height:1.8;color:var(--grey)}
/* lista de serviços técnicos */
.servicos-lista{margin-top:56px}
.servicos-lista-title{font-size:9px;letter-spacing:.3em;text-transform:uppercase;color:var(--gold-dim);margin-bottom:24px;display:flex;align-items:center;gap:14px}
.servicos-lista-title::after{content:'';flex:1;height:1px;background:rgba(201,168,76,.15)}
.servico-item{
  display:flex;align-items:center;gap:16px;
  padding:14px 0;border-bottom:1px solid rgba(201,168,76,.07);
  font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--grey);
  transition:color .3s;
}
.servico-item:hover{color:var(--white)}
.servico-item-icon{color:var(--gold);font-size:16px;width:24px;text-align:center;flex-shrink:0}
.servico-item-dot{width:4px;height:4px;border-radius:50%;background:var(--gold);flex-shrink:0}

/* ── PROCESSO ── */
.processo{background:var(--black-mid);padding:110px 60px}
.processo-steps{display:grid;grid-template-columns:repeat(4,1fr);gap:0;margin-top:72px;position:relative}
.processo-steps::before{
  content:'';position:absolute;top:32px;left:12.5%;right:12.5%;
  height:1px;background:rgba(201,168,76,.2);
}
.step{padding:0 28px;text-align:center;position:relative}
.step-num{
  width:64px;height:64px;border:1px solid var(--gold);
  display:flex;align-items:center;justify-content:center;margin:0 auto 28px;
  font-family:'Cormorant Garamond',serif;font-size:22px;color:var(--gold);
  background:var(--black-mid);position:relative;z-index:1;transition:all .3s;
}
.step:hover .step-num{background:var(--gold);color:var(--black)}
.step-title{font-family:'Cormorant Garamond',serif;font-size:19px;font-weight:300;color:var(--white);margin-bottom:10px}
.step-desc{font-size:12px;color:var(--grey);line-height:1.8}

/* ── CONTATO ── */
.contato{background:var(--black);padding:110px 60px;display:grid;grid-template-columns:1fr 1fr;gap:90px;border-top:1px solid rgba(201,168,76,.12)}
.contato-text{font-size:14px;line-height:2;color:var(--grey);margin-bottom:44px}
.contato-links{display:flex;flex-direction:column;gap:0}
.contato-link{
  display:flex;align-items:center;gap:16px;color:var(--grey);
  text-decoration:none;font-size:13px;transition:color .3s;
  padding:16px 0;border-bottom:1px solid rgba(201,168,76,.1);
}
.contato-link:hover{color:var(--gold)}
.contato-link-icon{color:var(--gold);font-size:15px;width:20px}
.form-group{margin-bottom:22px}
.form-label{display:block;font-size:9px;letter-spacing:.25em;text-transform:uppercase;color:var(--gold);margin-bottom:9px}
.form-input,.form-select,.form-textarea{
  width:100%;background:transparent;border:none;
  border-bottom:1px solid rgba(201,168,76,.25);color:var(--white);
  padding:11px 0;font-family:'Montserrat',sans-serif;font-size:13px;font-weight:300;
  outline:none;transition:border-color .3s;cursor:pointer;
}
.form-input:focus,.form-textarea:focus,.form-select:focus{border-bottom-color:var(--gold)}
.form-select{appearance:none}
.form-textarea{resize:none;height:76px}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.form-submit{
  width:100%;background:var(--gold);color:var(--black);border:none;padding:15px;
  font-family:'Montserrat',sans-serif;font-size:10px;letter-spacing:.25em;
  text-transform:uppercase;font-weight:600;cursor:pointer;transition:background .3s;margin-top:6px;
}
.form-submit:hover{background:var(--gold-light)}

/* ── FOOTER ── */
footer{
  background:var(--black);padding:40px 60px;
  display:flex;align-items:center;justify-content:space-between;
  border-top:1px solid rgba(201,168,76,.18);
}
.footer-logo{display:flex;align-items:center;gap:12px}
.footer-logo-circle{
  width:36px;height:36px;border:1px solid var(--gold-dim);border-radius:50%;
  display:flex;align-items:center;justify-content:center;font-size:14px;color:var(--gold-dim);
}
.footer-brand{font-family:'Montserrat',sans-serif;font-size:13px;letter-spacing:.2em;font-weight:600;color:rgba(245,240,232,.35)}
.footer-copy{font-size:10px;color:rgba(136,136,136,.4);letter-spacing:.1em}
.footer-social{display:flex;gap:22px}
.footer-social a{font-size:10px;color:var(--grey);text-decoration:none;letter-spacing:.1em;transition:color .3s}
.footer-social a:hover{color:var(--gold)}

/* ── ANIMATIONS ── */
@keyframes fadeUp{from{opacity:0;transform:translateY(28px)}to{opacity:1;transform:translateY(0)}}
.hero-eyebrow{animation:fadeUp .9s ease .2s both}
.hero-title{animation:fadeUp .9s ease .4s both}
.hero-tagline{animation:fadeUp .9s ease .5s both}
.hero-sub{animation:fadeUp .9s ease .6s both}
.hero-actions{animation:fadeUp .9s ease .8s both}

@media(max-width:1100px){
  nav{padding:18px 24px}
  .sec,.conceito,.sobre,.servicos,.processo,.contato,.portfolio{padding:80px 24px}
  .nav-links{display:none}
  .hero{padding:0 24px 60px}
  .conceito,.sobre,.contato{grid-template-columns:1fr;gap:50px}
  .servicos-grid{grid-template-columns:1fr 1fr}
  .processo-steps{grid-template-columns:1fr 1fr;gap:40px}
  .processo-steps::before{display:none}
  .project-card:nth-child(1){grid-column:span 12}
  .project-card:nth-child(2),.project-card:nth-child(3){grid-column:span 6}
  .project-card:nth-child(4),.project-card:nth-child(5),.project-card:nth-child(6){grid-column:span 4}
}
</style>
</head>
<body>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="nav-logo">
    <div class="nav-logo-icon">🏛</div>
    <div class="nav-logo-text">
      <span class="nav-logo-studio">Studio</span>
      <span class="nav-logo-balma">BALMA</span>
    </div>
  </a>
  <ul class="nav-links">
    <li><a href="#conceito">Conceito</a></li>
    <li><a href="#portfolio">Portfólio</a></li>
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#sobre">Studio</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
  <a href="https://wa.me/5547996349072" target="_blank" class="nav-cta">WhatsApp</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-line"></div>
  <div class="hero-media">
    <!-- GIF do Edifício Saguaçu -->
    <img id="heroImg" src="" alt="Studio Balma — Edifício Saguaçu">
  </div>
  <div class="hero-content">
    <div class="hero-eyebrow">Visualização Arquitetônica</div>
    <h1 class="hero-title">
      Transformamos<br>
      traços em <em>vida.</em>
    </h1>
    <p class="hero-tagline">Arquitetura &amp; Engenharia — Joinville, SC</p>
    <p class="hero-sub">
      Studio Balma é responsável por visualização arquitetônica. Transformando projetos em experiências visuais claras, estratégicas e sensíveis.
    </p>
    <div class="hero-actions">
      <a href="#portfolio" class="btn-primary">Ver Portfólio</a>
      <a href="#contato" class="btn-outline">Solicitar Orçamento</a>
    </div>
  </div>
  <div class="hero-badge"></div>
</section>

<div class="gold-line"></div>

<!-- CONCEITO -->
<section class="conceito" id="conceito">
  <div class="conceito-img">
    <img src="" alt="Edifício Kolb — Studio Balma" id="conceitoImg"
         style="background:var(--black-card);display:flex;align-items:center;justify-content:center">
    <div class="conceito-label">Edifício Kolb.</div>
  </div>
  <div class="conceito-content">
    <div class="sec-tag">Conceito</div>
    <div class="conceito-big">BALMA.</div>
    <p class="conceito-body">
      <strong>Studio Balma é responsável por visualização arquitetônica.</strong>
      Transformando projetos em experiências visuais claras, estratégicas e sensíveis.
    </p>
    <p class="conceito-body">
      Nosso compromisso é traduzir o imaginado em algo visível, tornando o futuro espaço compreensível no presente.
    </p>
    <div class="conceito-quote">
      Acreditamos que arquitetura não deve ser apenas explicada. Ela deve ser compreendida de forma intuitiva.
    </div>
  </div>
</section>

<div class="gold-line"></div>

<!-- PORTFÓLIO -->
<section class="portfolio" id="portfolio">
  <div class="sec-header">
    <div>
      <div class="sec-tag">Portfólio</div>
      <h2 class="sec-title">Nossos <em>projetos</em></h2>
    </div>
    <p class="sec-desc">Cada projeto entregue com direção artística e foco em resultado.</p>
  </div>

  <div class="nicho-tabs">
    <button class="nicho-tab active" onclick="showNicho('fachadas',this)">Fachadas</button>
    <button class="nicho-tab" onclick="showNicho('interiores',this)">Interiores</button>
    <button class="nicho-tab" onclick="showNicho('residencial',this)">Residencial</button>
    <button class="nicho-tab" onclick="showNicho('plantas',this)">Plantas 3D</button>
  </div>

  <!-- FACHADAS -->
  <div class="nicho-panel active" id="panel-fachadas">
    <div class="projects-grid">
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏢</span>Edifício Saguaçu — Vista Frontal Dia</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Vista Frontal — Dia</div></div><div class="project-arrow">→</div></div>
      </div>
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">🌙</span>Edifício Saguaçu — Noturno</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Vista Frontal — Noite</div></div><div class="project-arrow">→</div></div>
      </div>
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏗</span>Vista Aérea</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Vista Aérea</div></div><div class="project-arrow">→</div></div>
      </div>
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏛</span>Edifício Kolb</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Kolb</div><div class="project-type">Fachada Residencial</div></div><div class="project-arrow">→</div></div>
      </div>
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">☕</span>Café do Pátio</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Café do Pátio</div><div class="project-type">Vista Inferior</div></div><div class="project-arrow">→</div></div>
      </div>
      <div class="project-card">
        <div class="img-wrap"><div class="proj-placeholder"><span class="ico">🌅</span>Vista Oblíqua</div></div>
        <div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Vista Frontal Oblíqua</div></div><div class="project-arrow">→</div></div>
      </div>
    </div>
  </div>

  <!-- INTERIORES -->
  <div class="nicho-panel" id="panel-interiores">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🍳</span>Cozinha Premium</div></div><div class="project-info"><div><div class="project-name">Cozinha Premium</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🛏</span>Suite Master</div></div><div class="project-info"><div><div class="project-name">Suíte Master</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🍽</span>Cozinha Gourmet</div></div><div class="project-info"><div><div class="project-name">Cozinha Gourmet</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🚿</span>Banheiro Luxo</div></div><div class="project-info"><div><div class="project-name">Banheiro Luxo</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🍴</span>Sala de Jantar</div></div><div class="project-info"><div><div class="project-name">Sala de Jantar</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🚿</span>Banheiro Moderno</div></div><div class="project-info"><div><div class="project-name">Banheiro Moderno</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>

  <!-- RESIDENCIAL -->
  <div class="nicho-panel" id="panel-residencial">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏠</span>Residencial Três Coroas</div></div><div class="project-info"><div><div class="project-name">Residencial Três Coroas</div><div class="project-type">Vista Inferior</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏊</span>Porto Alegre</div></div><div class="project-info"><div><div class="project-name">Condomínio Porto Alegre</div><div class="project-type">Vista Frontal</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🌴</span>Residencial Caxias</div></div><div class="project-info"><div><div class="project-name">Residencial Caxias</div><div class="project-type">Vista Frontal — Noite</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🌅</span>Vista Sunset</div></div><div class="project-info"><div><div class="project-name">Residencial Caxias</div><div class="project-type">Vista Oblíqua — Dia</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🌃</span>Vista Noturna</div></div><div class="project-info"><div><div class="project-name">Residencial Caxias</div><div class="project-type">Vista Oblíqua — Noite</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏡</span>Detalhes</div></div><div class="project-info"><div><div class="project-name">Detalhes que Valorizam</div><div class="project-type">Residencial Caxias</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>

  <!-- PLANTAS 3D -->
  <div class="nicho-panel" id="panel-plantas">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">📋</span>Planta 2D</div></div><div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Planta Baixa 2D</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">📐</span>Planta 3D</div></div><div class="project-info"><div><div class="project-name">Edifício Saguaçu</div><div class="project-type">Planta Baixa 3D</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🗺</span>Implantação</div></div><div class="project-info"><div><div class="project-name">Implantação Geral</div><div class="project-type">Vista Aérea</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">📏</span>Corte</div></div><div class="project-info"><div><div class="project-name">Corte Esquemático</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🔲</span>Detalhe</div></div><div class="project-info"><div><div class="project-name">Detalhamento</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="proj-placeholder"><span class="ico">🏗</span>Maquete</div></div><div class="project-info"><div><div class="project-name">Maquete Virtual</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>
</section>

<div class="gold-line"></div>

<!-- SOBRE / SAMUEL -->
<section class="sobre" id="sobre">
  <div style="position:relative">
    <div class="sobre-foto">
      <img src="" alt="Samuel Bueno — Fundador Studio Balma" id="samuelImg"
           style="background:var(--black-card);min-height:420px">
      <div class="sobre-foto-nome">
        <h3>Samuel Bueno</h3>
        <span>Fundador & Diretor Criativo</span>
      </div>
    </div>
    <div class="sobre-accent"></div>
  </div>
  <div>
    <div class="sec-tag">Studio Balma</div>
    <h2 class="sec-title" style="margin-bottom:28px">Imagem com <em>direção.</em></h2>
    <p class="sobre-text">
      <strong>Samuel Bueno</strong> fundou o Studio Balma com um objetivo claro: entregar imagens que não apenas mostram o projeto, mas <strong>vendem o projeto.</strong>
      <br><br>
      Cada render é pensado estrategicamente — do ângulo à iluminação, dos materiais à atmosfera. Não entregamos só arquivos, entregamos <strong>percepção de valor.</strong>
    </p>
    <div class="stats">
      <div><div class="stat-num">+150</div><div class="stat-label">Projetos entregues</div></div>
      <div><div class="stat-num">+80</div><div class="stat-label">Clientes ativos</div></div>
      <div><div class="stat-num">5★</div><div class="stat-label">Avaliação média</div></div>
    </div>
    <a href="#contato" class="btn-primary">Fale com o Studio</a>
    <div class="sobre-localidade">
      <span>📍</span> Joinville, Santa Catarina
    </div>
  </div>
</section>

<!-- SERVIÇOS -->
<section class="servicos" id="servicos">
  <div class="sec-header">
    <div>
      <div class="sec-tag">O que fazemos</div>
      <h2 class="sec-title">Nossos <em>serviços</em></h2>
    </div>
    <p class="sec-desc">Visualização arquitetônica completa — do conceito ao detalhe.</p>
  </div>
  <div class="servicos-grid">
    <div class="servico-card"><div class="servico-num">01</div><div class="servico-icon">🏛</div><div class="servico-name">Renders Externos</div><p class="servico-desc">Fachadas, vistas aéreas e externas com iluminação natural ou noturna. Realismo cinematográfico.</p></div>
    <div class="servico-card"><div class="servico-num">02</div><div class="servico-icon">🛋</div><div class="servico-name">Renders Interiores</div><p class="servico-desc">Ambientes internos com iluminação, materiais e atmosfera. Cozinhas, suítes, salas, banheiros.</p></div>
    <div class="servico-card" style="border-left:2px solid var(--gold)"><div class="servico-num" style="opacity:.3">03</div><div class="servico-icon">◆</div><div class="servico-name">Render Premium</div><p class="servico-desc">Direção artística completa. Máxima valorização do projeto. Foco em vendas e lançamentos.</p></div>
    <div class="servico-card"><div class="servico-num">04</div><div class="servico-icon">📐</div><div class="servico-name">Plantas 3D</div><p class="servico-desc">Plantas baixas em 3D com acabamento fotorrealista. Transforma traços técnicos em experiência visual.</p></div>
    <div class="servico-card"><div class="servico-num">05</div><div class="servico-icon">🏠</div><div class="servico-name">Residencial</div><p class="servico-desc">Casas, condomínios e residências. Detalhe que valoriza: piscinas, jardins, áreas externas.</p></div>
    <div class="servico-card"><div class="servico-num">06</div><div class="servico-icon">🏢</div><div class="servico-name">Comercial</div><p class="servico-desc">Edifícios, galpões, lojas e escritórios. Perspectivas que comunicam escala e qualidade.</p></div>
  </div>

  <!-- Serviços Técnicos -->
  <div class="servicos-lista">
    <div class="servicos-lista-title">Serviços Técnicos de Engenharia</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:0">
      <div class="servico-item"><div class="servico-item-dot"></div>Projeto Executivo de Estruturas em Concreto Armado</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Projetos Executivos de Instalações Elétricas e Comunicação</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Instalações Hidrossanitárias e Drenagem de Águas Pluviais</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Projeto de Prevenção e Combate à Incêndio e Pânico</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Estudo de Viabilidade de Terreno</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Muro de Contenção / Arrimo</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Projeto de Terraplenagem</div>
      <div class="servico-item"><div class="servico-item-dot"></div>Acompanhamento de Obra &amp; Parecer Técnico</div>
    </div>
  </div>
</section>

<div class="gold-line"></div>

<!-- PROCESSO -->
<section class="processo">
  <div class="sec-header">
    <div>
      <div class="sec-tag">Como trabalhamos</div>
      <h2 class="sec-title">O nosso <em>processo</em></h2>
    </div>
  </div>
  <div class="processo-steps">
    <div class="step"><div class="step-num">01</div><div class="step-title">Briefing</div><p class="step-desc">Entendemos o projeto, o público-alvo e o objetivo da visualização.</p></div>
    <div class="step"><div class="step-num">02</div><div class="step-title">Direção Artística</div><p class="step-desc">Definimos paleta, atmosfera, ângulos e linguagem visual junto com você.</p></div>
    <div class="step"><div class="step-num">03</div><div class="step-title">Produção</div><p class="step-desc">Modelagem, iluminação e renderização com revisões inclusas.</p></div>
    <div class="step"><div class="step-num">04</div><div class="step-title">Entrega</div><p class="step-desc">Arquivos em alta resolução prontos para uso em qualquer canal de venda.</p></div>
  </div>
</section>

<div class="gold-line"></div>

<!-- CONTATO -->
<section class="contato" id="contato">
  <div>
    <div class="sec-tag">Contato</div>
    <h2 class="sec-title" style="margin-bottom:24px">Vamos trabalhar<br><em>juntos.</em></h2>
    <p class="contato-text">Cada projeto começa com uma conversa. Me conta o que você precisa e a gente encontra a melhor solução.</p>
    <div class="contato-links">
      <a href="https://wa.me/5547996349072" class="contato-link" target="_blank">
        <span class="contato-link-icon">📱</span>(47) 99634-9072
      </a>
      <a href="mailto:studiobalma@outlook.com" class="contato-link">
        <span class="contato-link-icon">✉</span>studiobalma@outlook.com
      </a>
      <a href="https://instagram.com/studio.balma" class="contato-link" target="_blank">
        <span class="contato-link-icon">📷</span>@studio.balma
      </a>
      <a href="#" class="contato-link">
        <span class="contato-link-icon">📍</span>Joinville, Santa Catarina
      </a>
    </div>
  </div>
  <div>
    <div class="form-row">
      <div class="form-group"><label class="form-label">Nome</label><input type="text" class="form-input" placeholder="Seu nome"></div>
      <div class="form-group"><label class="form-label">Empresa / Escritório</label><input type="text" class="form-input" placeholder="Opcional"></div>
    </div>
    <div class="form-group"><label class="form-label">Você é</label>
      <select class="form-select"><option value="">Selecione seu perfil</option><option>Arquiteto(a)</option><option>Designer de Interiores</option><option>Incorporadora</option><option>Corretor(a)</option><option>Engenheiro(a)</option><option>Outro</option></select>
    </div>
    <div class="form-group"><label class="form-label">Serviço de interesse</label>
      <select class="form-select"><option value="">Selecione o serviço</option><option>Render Externo / Fachada</option><option>Render Interior</option><option>Render Premium</option><option>Plantas 3D</option><option>Projeto Técnico de Engenharia</option><option>Não sei ainda</option></select>
    </div>
    <div class="form-group"><label class="form-label">Sobre o projeto</label>
      <textarea class="form-textarea" placeholder="Tipo de projeto, prazo, referências..."></textarea>
    </div>
    <button class="form-submit" onclick="handleSubmit()">Enviar mensagem →</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">
    <div class="footer-logo-circle">🏛</div>
    <span class="footer-brand">STUDIO BALMA</span>
  </div>
  <div class="footer-copy">© 2025 Studio Balma. Joinville, SC. Todos os direitos reservados.</div>
  <div class="footer-social">
    <a href="https://instagram.com/studio.balma" target="_blank">Instagram</a>
    <a href="mailto:studiobalma@outlook.com">E-mail</a>
    <a href="https://wa.me/5547996349072" target="_blank">WhatsApp</a>
  </div>
</footer>

<script>
// Nav scroll
window.addEventListener('scroll',()=>{
  document.getElementById('nav').classList.toggle('scrolled',window.scrollY>60)
})

// Tabs portfólio
function showNicho(id,btn){
  document.querySelectorAll('.nicho-panel').forEach(p=>p.classList.remove('active'))
  document.querySelectorAll('.nicho-tab').forEach(t=>t.classList.remove('active'))
  document.getElementById('panel-'+id).classList.add('active')
  btn.classList.add('active')
}

// Form
function handleSubmit(){
  const btn=document.querySelector('.form-submit')
  btn.textContent='Mensagem enviada ✓'
  btn.style.background='#4a7c59'
  setTimeout(()=>{btn.textContent='Enviar mensagem →';btn.style.background=''},3500)
}

// Scroll reveal
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){e.target.style.opacity='1';e.target.style.transform='translateY(0)'}
  })
},{threshold:.08})
document.querySelectorAll('.servico-card,.step,.project-card,.stat-num,.servico-item').forEach(el=>{
  el.style.opacity='0';el.style.transform='translateY(18px)'
  el.style.transition='opacity .55s ease, transform .55s ease'
  obs.observe(el)
})
</script>
</body>
</html>
