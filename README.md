<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Studio Balma — Renderização Arquitetônica</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Montserrat:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --black:       #000000;
    --black-soft:  #0a0a0a;
    --black-mid:   #111111;
    --black-card:  #151515;
    --gold:        #C9A84C;
    --gold-light:  #E2C07A;
    --gold-pale:   #F0D9A0;
    --gold-dim:    #8A6E2F;
    --white:       #F5F0E8;
    --grey:        #888;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    font-size: 13px;
    letter-spacing: 0.04em;
    overflow-x: hidden;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--black); }
  ::-webkit-scrollbar-thumb { background: var(--gold-dim); border-radius: 2px; }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 28px 60px;
    background: linear-gradient(to bottom, rgba(0,0,0,0.97) 0%, rgba(0,0,0,0) 100%);
  }
  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px; font-weight: 400;
    letter-spacing: 0.25em;
    color: var(--white); text-decoration: none;
  }
  .nav-logo span { color: var(--gold); }
  .nav-links { display: flex; gap: 40px; list-style: none; }
  .nav-links a {
    color: var(--grey); text-decoration: none;
    font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold); border: 1px solid var(--gold);
    padding: 10px 28px; text-decoration: none;
    transition: all 0.3s;
  }
  .nav-cta:hover { background: var(--gold); color: var(--black); }

  /* ── HERO ── */
  .hero {
    height: 100vh; position: relative;
    display: flex; align-items: flex-end;
    padding: 0 60px 80px; overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: var(--black);
  }
  .hero-img {
    position: absolute; inset: 0;
    overflow: hidden;
  }
  .hero-img img {
    width: 100%; height: 100%;
    object-fit: cover;
    opacity: 0.75;
    filter: brightness(0.85) saturate(1.1);
  }
  /* gradiente dourado sobre a imagem */
  .hero-img::after {
    content: '';
    position: absolute; inset: 0;
    background:
      linear-gradient(to right, rgba(0,0,0,0.92) 0%, rgba(0,0,0,0.5) 50%, rgba(0,0,0,0.2) 100%),
      linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 50%);
  }
  /* borda dourada sutil */
  .hero-img::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,0.12) 0%, transparent 60%);
    z-index: 1;
  }
  .hero-content { position: relative; z-index: 3; max-width: 580px; }
  .hero-tag {
    font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 28px;
    display: flex; align-items: center; gap: 14px;
  }
  .hero-tag::before { content: ''; display: block; width: 40px; height: 1px; background: var(--gold); }
  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(52px, 6vw, 82px);
    font-weight: 300; line-height: 1.05; margin-bottom: 32px;
    color: var(--white);
  }
  .hero-title em { font-style: italic; color: var(--gold-light); }
  .hero-sub {
    font-size: 13px; line-height: 1.9; color: var(--grey);
    max-width: 420px; margin-bottom: 52px;
  }
  .hero-actions { display: flex; gap: 24px; align-items: center; }
  .btn-primary {
    background: var(--gold); color: var(--black);
    padding: 14px 40px; font-size: 10px; letter-spacing: 0.2em;
    text-transform: uppercase; text-decoration: none;
    font-family: 'Montserrat', sans-serif; font-weight: 500;
    transition: background 0.3s; display: inline-block;
  }
  .btn-primary:hover { background: var(--gold-light); }
  .btn-ghost {
    color: var(--white); font-size: 10px; letter-spacing: 0.2em;
    text-transform: uppercase; text-decoration: none;
    display: flex; align-items: center; gap: 8px; transition: color 0.3s;
  }
  .btn-ghost:hover { color: var(--gold); }
  .btn-ghost::after { content: '↓'; font-size: 14px; }

  /* ornamento dourado canto */
  .hero-ornament {
    position: absolute; bottom: 40px; right: 60px; z-index: 3;
    width: 80px; height: 80px;
    border: 1px solid rgba(201,168,76,0.4);
    transform: rotate(45deg);
  }
  .hero-ornament::before {
    content: '';
    position: absolute; inset: 8px;
    border: 1px solid rgba(201,168,76,0.2);
  }

  /* ── DIVIDER ── */
  .gold-divider {
    width: 100%; height: 1px;
    background: linear-gradient(to right, transparent, var(--gold-dim), transparent);
  }

  /* ── NICHOS ── */
  .nichos { padding: 120px 60px; background: var(--black); }
  .section-header {
    display: flex; align-items: flex-end; justify-content: space-between;
    margin-bottom: 80px; padding-bottom: 32px;
    border-bottom: 1px solid rgba(201,168,76,0.2);
  }
  .section-tag {
    font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 16px;
  }
  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(36px, 4vw, 52px); font-weight: 300; line-height: 1.1;
    color: var(--white);
  }
  .section-title em { font-style: italic; color: var(--gold-light); }
  .section-desc {
    font-size: 13px; color: var(--grey);
    line-height: 1.8; max-width: 300px; text-align: right;
  }

  /* TABS */
  .nicho-tabs {
    display: flex; gap: 0; margin-bottom: 48px;
    border-bottom: 1px solid rgba(201,168,76,0.15);
  }
  .nicho-tab {
    padding: 16px 32px; font-size: 10px; letter-spacing: 0.2em;
    text-transform: uppercase; color: var(--grey);
    border-bottom: 2px solid transparent; margin-bottom: -1px;
    transition: color 0.3s, border-color 0.3s;
    background: none; border-top: none; border-left: none; border-right: none;
    font-family: 'Montserrat', sans-serif; cursor: pointer;
  }
  .nicho-tab:hover { color: var(--white); }
  .nicho-tab.active { color: var(--gold); border-bottom-color: var(--gold); }

  /* GRID */
  .nicho-panel { display: none; }
  .nicho-panel.active { display: block; }
  .projects-grid {
    display: grid; grid-template-columns: repeat(12, 1fr); gap: 2px;
  }
  .project-card {
    position: relative; overflow: hidden;
    background: var(--black-card); cursor: pointer;
  }
  .project-card:nth-child(1) { grid-column: span 7; grid-row: span 2; }
  .project-card:nth-child(2) { grid-column: span 5; }
  .project-card:nth-child(3) { grid-column: span 5; }
  .project-card:nth-child(4) { grid-column: span 4; }
  .project-card:nth-child(5) { grid-column: span 4; }
  .project-card:nth-child(6) { grid-column: span 4; }
  .project-card .img-wrap {
    width: 100%; padding-top: 75%; position: relative; overflow: hidden;
    background: var(--black-mid);
  }
  .project-card:nth-child(1) .img-wrap { padding-top: 100%; }
  .project-card .img-wrap img {
    position: absolute; inset: 0; width: 100%; height: 100%;
    object-fit: cover; transition: transform 0.7s ease; display: block;
  }
  .project-card:hover .img-wrap img { transform: scale(1.05); }
  .img-placeholder {
    position: absolute; inset: 0; display: flex; flex-direction: column;
    align-items: center; justify-content: center; gap: 8px;
    color: rgba(201,168,76,0.25); font-size: 10px;
    letter-spacing: 0.2em; text-transform: uppercase;
  }
  .img-placeholder .icon { font-size: 22px; opacity: 0.4; }
  .project-info {
    padding: 18px 22px;
    display: flex; align-items: center; justify-content: space-between;
    border-top: 1px solid rgba(201,168,76,0.1);
  }
  .project-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 17px; font-weight: 300; color: var(--white);
  }
  .project-type { font-size: 9px; letter-spacing: 0.18em; text-transform: uppercase; color: var(--grey); margin-top: 3px; }
  .project-arrow { color: var(--gold); font-size: 16px; opacity: 0; transform: translateX(-8px); transition: all 0.3s; }
  .project-card:hover .project-arrow { opacity: 1; transform: translateX(0); }

  /* ── SOBRE ── */
  .sobre {
    padding: 120px 60px; display: grid;
    grid-template-columns: 1fr 1fr; gap: 100px; align-items: center;
    background: var(--black-mid);
    border-top: 1px solid rgba(201,168,76,0.15);
    border-bottom: 1px solid rgba(201,168,76,0.15);
  }
  .sobre-visual { position: relative; height: 600px; }
  .sobre-img { width: 82%; height: 100%; background: var(--black-card); position: relative; overflow: hidden; }
  .sobre-img img { width: 100%; height: 100%; object-fit: cover; }
  .sobre-accent {
    position: absolute; right: 0; bottom: -20px;
    width: 180px; height: 180px;
    border: 1px solid rgba(201,168,76,0.35);
  }
  .sobre-accent::before {
    content: ''; position: absolute; inset: 12px;
    border: 1px solid rgba(201,168,76,0.15);
  }
  .sobre-num {
    position: absolute; top: 20px; right: -10px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 140px; color: var(--gold); opacity: 0.04; line-height: 1;
    pointer-events: none;
  }
  .sobre-text { font-size: 14px; line-height: 2; color: var(--grey); margin-bottom: 48px; }
  .stats {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 32px; margin-bottom: 48px; padding-top: 40px;
    border-top: 1px solid rgba(201,168,76,0.2);
  }
  .stat-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 40px; font-weight: 300; color: var(--gold); line-height: 1; margin-bottom: 6px;
  }
  .stat-label { font-size: 9px; letter-spacing: 0.18em; text-transform: uppercase; color: var(--grey); }

  /* ── SERVIÇOS ── */
  .servicos { padding: 120px 60px; background: var(--black); }
  .servicos-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 1px; margin-top: 60px; }
  .servico-card {
    padding: 48px 28px; background: var(--black-card);
    position: relative; overflow: hidden; transition: background 0.4s;
  }
  .servico-card::after {
    content: ''; position: absolute; bottom: 0; left: 0; right: 0;
    height: 2px; background: linear-gradient(to right, var(--gold-dim), var(--gold));
    transform: scaleX(0); transition: transform 0.4s; transform-origin: left;
  }
  .servico-card:hover { background: #1a1500; }
  .servico-card:hover::after { transform: scaleX(1); }
  .servico-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 52px; color: var(--gold); opacity: 0.12; line-height: 1; margin-bottom: 28px;
  }
  .servico-icon { font-size: 24px; margin-bottom: 18px; color: var(--gold); }
  .servico-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 20px; font-weight: 300; color: var(--white); margin-bottom: 12px;
  }
  .servico-desc { font-size: 12px; line-height: 1.8; color: var(--grey); }

  /* ── PROCESSO ── */
  .processo { padding: 120px 60px; background: var(--black-mid); }
  .processo-steps {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 0; margin-top: 80px; position: relative;
  }
  .processo-steps::before {
    content: ''; position: absolute; top: 32px; left: 12.5%; right: 12.5%;
    height: 1px; background: linear-gradient(to right, var(--gold-dim), var(--gold-dim));
    opacity: 0.3;
  }
  .step { padding: 0 32px; text-align: center; position: relative; }
  .step-num {
    width: 64px; height: 64px;
    border: 1px solid var(--gold); display: flex; align-items: center; justify-content: center;
    margin: 0 auto 32px;
    font-family: 'Cormorant Garamond', serif; font-size: 22px; color: var(--gold);
    background: var(--black-mid); position: relative; z-index: 1;
    transition: all 0.3s;
  }
  .step:hover .step-num { background: var(--gold); color: var(--black); }
  .step-title {
    font-family: 'Cormorant Garamond', serif; font-size: 20px; font-weight: 300;
    color: var(--white); margin-bottom: 12px;
  }
  .step-desc { font-size: 12px; color: var(--grey); line-height: 1.8; }

  /* ── CONTATO ── */
  .contato {
    padding: 120px 60px; background: var(--black);
    display: grid; grid-template-columns: 1fr 1fr; gap: 100px;
    border-top: 1px solid rgba(201,168,76,0.15);
  }
  .contato-text { font-size: 14px; line-height: 2; color: var(--grey); margin-bottom: 48px; }
  .contato-links { display: flex; flex-direction: column; gap: 0; }
  .contato-link {
    display: flex; align-items: center; gap: 16px;
    color: var(--grey); text-decoration: none; font-size: 13px;
    transition: color 0.3s; padding: 18px 0;
    border-bottom: 1px solid rgba(201,168,76,0.12);
  }
  .contato-link:hover { color: var(--gold); }
  .contato-link-icon { color: var(--gold); font-size: 16px; width: 20px; }

  /* FORM */
  .form-group { margin-bottom: 24px; }
  .form-label { display: block; font-size: 9px; letter-spacing: 0.25em; text-transform: uppercase; color: var(--gold); margin-bottom: 10px; }
  .form-input, .form-select, .form-textarea {
    width: 100%; background: transparent;
    border: none; border-bottom: 1px solid rgba(201,168,76,0.3);
    color: var(--white); padding: 12px 0;
    font-family: 'Montserrat', sans-serif; font-size: 13px; font-weight: 300;
    outline: none; transition: border-color 0.3s; cursor: pointer;
  }
  .form-input:focus, .form-textarea:focus, .form-select:focus { border-bottom-color: var(--gold); }
  .form-select { appearance: none; }
  .form-textarea { resize: none; height: 80px; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
  .form-submit {
    width: 100%; background: var(--gold); color: var(--black);
    border: none; padding: 16px;
    font-family: 'Montserrat', sans-serif; font-size: 10px;
    letter-spacing: 0.25em; text-transform: uppercase; font-weight: 500;
    cursor: pointer; transition: background 0.3s; margin-top: 8px;
  }
  .form-submit:hover { background: var(--gold-light); }

  /* ── FOOTER ── */
  footer {
    padding: 40px 60px;
    display: flex; align-items: center; justify-content: space-between;
    border-top: 1px solid rgba(201,168,76,0.2);
    background: var(--black);
  }
  .footer-logo { font-family: 'Cormorant Garamond', serif; font-size: 18px; letter-spacing: 0.25em; color: rgba(245,240,232,0.4); }
  .footer-logo span { color: var(--gold-dim); }
  .footer-copy { font-size: 10px; color: rgba(136,136,136,0.5); letter-spacing: 0.1em; }
  .footer-social { display: flex; gap: 24px; }
  .footer-social a { font-size: 10px; color: var(--grey); text-decoration: none; letter-spacing: 0.1em; transition: color 0.3s; }
  .footer-social a:hover { color: var(--gold); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
  .hero-tag   { animation: fadeUp 0.9s ease 0.2s both; }
  .hero-title { animation: fadeUp 0.9s ease 0.4s both; }
  .hero-sub   { animation: fadeUp 0.9s ease 0.6s both; }
  .hero-actions { animation: fadeUp 0.9s ease 0.8s both; }

  @media (max-width: 1024px) {
    nav { padding: 22px 28px; }
    .hero, .nichos, .sobre, .servicos, .processo, .contato { padding-left: 28px; padding-right: 28px; }
    .nav-links { display: none; }
    .servicos-grid { grid-template-columns: repeat(2,1fr); }
    .processo-steps { grid-template-columns: repeat(2,1fr); gap: 40px; }
    .processo-steps::before { display: none; }
    .sobre, .contato { grid-template-columns: 1fr; gap: 60px; }
    .sobre-visual { height: 380px; }
    .project-card:nth-child(1) { grid-column: span 12; }
    .project-card:nth-child(2), .project-card:nth-child(3) { grid-column: span 6; }
    .project-card:nth-child(4), .project-card:nth-child(5), .project-card:nth-child(6) { grid-column: span 4; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">STUDIO <span>BALMA</span></a>
  <ul class="nav-links">
    <li><a href="#nichos">Portfólio</a></li>
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#sobre">Studio</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
  <a href="#contato" class="nav-cta">Orçamento</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-img">
    <img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7" 
         id="heroGif"
         alt="Studio Balma — Renderização Arquitetônica">
  </div>
  <div class="hero-content">
    <div class="hero-tag">Renderização Arquitetônica de Alto Padrão</div>
    <h1 class="hero-title">
      Seu projeto<br>
      visto no<br>
      <em>valor real</em>
    </h1>
    <p class="hero-sub">
      Não apenas imagens bonitas — direção artística focada em fazer o seu projeto vender por si mesmo.
    </p>
    <div class="hero-actions">
      <a href="#nichos" class="btn-primary">Ver Portfólio</a>
      <a href="#contato" class="btn-ghost">Orçamento</a>
    </div>
  </div>
  <div class="hero-ornament"></div>
</section>

<div class="gold-divider"></div>

<!-- NICHOS -->
<section class="nichos" id="nichos">
  <div class="section-header">
    <div>
      <div class="section-tag">Portfólio</div>
      <h2 class="section-title">Projetos por <em>nicho</em></h2>
    </div>
    <p class="section-desc">Cada nicho exige uma linguagem visual diferente. Dominamos todas.</p>
  </div>

  <div class="nicho-tabs">
    <button class="nicho-tab active" onclick="showNicho('interiores',this)">Interiores</button>
    <button class="nicho-tab" onclick="showNicho('fachadas',this)">Fachadas</button>
    <button class="nicho-tab" onclick="showNicho('comercial',this)">Comercial</button>
    <button class="nicho-tab" onclick="showNicho('tecnico',this)">3D Técnico</button>
  </div>

  <div class="nicho-panel active" id="panel-interiores">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 01</div></div><div class="project-info"><div><div class="project-name">Residência Alphaville</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 02</div></div><div class="project-info"><div><div class="project-name">Apartamento Minimalista</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 03</div></div><div class="project-info"><div><div class="project-name">Loft Industrial</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 04</div></div><div class="project-info"><div><div class="project-name">Casa de Campo</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 05</div></div><div class="project-info"><div><div class="project-name">Penthouse</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🛋</span>interiores — 06</div></div><div class="project-info"><div><div class="project-name">Home Office Premium</div><div class="project-type">Interior Residencial</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>

  <div class="nicho-panel" id="panel-fachadas">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 01</div></div><div class="project-info"><div><div class="project-name">Residência Contemporânea</div><div class="project-type">Fachada Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 02</div></div><div class="project-info"><div><div class="project-name">Edifício Torres</div><div class="project-type">Fachada Vertical</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 03</div></div><div class="project-info"><div><div class="project-name">Casa Minimalista</div><div class="project-type">Fachada Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 04</div></div><div class="project-info"><div><div class="project-name">Condomínio Alto Padrão</div><div class="project-type">Fachada Residencial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 05</div></div><div class="project-info"><div><div class="project-name">Vila Gourmet</div><div class="project-type">Exterior</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏛</span>fachadas — 06</div></div><div class="project-info"><div><div class="project-name">Sobrado Moderno</div><div class="project-type">Fachada Residencial</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>

  <div class="nicho-panel" id="panel-comercial">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 01</div></div><div class="project-info"><div><div class="project-name">Escritório Corporativo</div><div class="project-type">Projeto Comercial</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 02</div></div><div class="project-info"><div><div class="project-name">Loja Flagship</div><div class="project-type">Varejo</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 03</div></div><div class="project-info"><div><div class="project-name">Restaurante Gourmet</div><div class="project-type">Food & Beverage</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 04</div></div><div class="project-info"><div><div class="project-name">Clínica Premium</div><div class="project-type">Saúde</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 05</div></div><div class="project-info"><div><div class="project-name">Coworking</div><div class="project-type">Escritório</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">🏢</span>comercial — 06</div></div><div class="project-info"><div><div class="project-name">Hotel Boutique</div><div class="project-type">Hospitalidade</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>

  <div class="nicho-panel" id="panel-tecnico">
    <div class="projects-grid">
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 01</div></div><div class="project-info"><div><div class="project-name">Planta Baixa 3D</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 02</div></div><div class="project-info"><div><div class="project-name">Corte Esquemático</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 03</div></div><div class="project-info"><div><div class="project-name">Implantação Geral</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 04</div></div><div class="project-info"><div><div class="project-name">Perspectiva Aérea</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 05</div></div><div class="project-info"><div><div class="project-name">Detalhamento</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
      <div class="project-card"><div class="img-wrap"><div class="img-placeholder"><span class="icon">📐</span>3d técnico — 06</div></div><div class="project-info"><div><div class="project-name">Maquete Virtual</div><div class="project-type">3D Técnico</div></div><div class="project-arrow">→</div></div></div>
    </div>
  </div>
</section>

<div class="gold-divider"></div>

<!-- SOBRE -->
<section class="sobre" id="sobre">
  <div class="sobre-visual">
    <div class="sobre-img">
      <div class="img-placeholder" style="position:absolute;inset:0;">Imagem do Studio</div>
    </div>
    <div class="sobre-accent"></div>
    <div class="sobre-num">B</div>
  </div>
  <div class="sobre-content">
    <div class="section-tag">Studio Balma</div>
    <h2 class="section-title">Mais do que<br><em>imagens bonitas</em></h2>
    <p class="sobre-text">
      Somos um studio de renderização arquitetônica de alto padrão. Não entregamos só imagens — entregamos direção artística focada em um objetivo: aumentar a percepção de valor do seu projeto e te ajudar a vender mais.
      <br><br>
      Trabalhamos com arquitetos, designers de interiores, incorporadoras e corretores que entendem que a apresentação do projeto é parte da venda.
    </p>
    <div class="stats">
      <div><div class="stat-num">+150</div><div class="stat-label">Projetos entregues</div></div>
      <div><div class="stat-num">+80</div><div class="stat-label">Clientes ativos</div></div>
      <div><div class="stat-num">5★</div><div class="stat-label">Avaliação média</div></div>
    </div>
    <a href="#contato" class="btn-primary">Fale com o Studio</a>
  </div>
</section>

<!-- SERVIÇOS -->
<section class="servicos" id="servicos">
  <div class="section-header">
    <div>
      <div class="section-tag">O que fazemos</div>
      <h2 class="section-title">Nossos <em>serviços</em></h2>
    </div>
    <p class="section-desc">Do técnico ao premium — cada entrega com direção artística e foco em resultado.</p>
  </div>
  <div class="servicos-grid">
    <div class="servico-card"><div class="servico-num">01</div><div class="servico-icon">✓</div><div class="servico-name">Render para Aprovação</div><p class="servico-desc">Imagens claras e objetivas para aprovação com clientes e órgãos competentes.</p></div>
    <div class="servico-card"><div class="servico-num">02</div><div class="servico-icon">◈</div><div class="servico-name">Render Comercial</div><p class="servico-desc">Renders com qualidade comercial para apresentações, propostas e materiais de venda.</p></div>
    <div class="servico-card" style="border:1px solid rgba(201,168,76,0.25);"><div class="servico-num" style="opacity:0.3;">03</div><div class="servico-icon">◆</div><div class="servico-name">Render Premium</div><p class="servico-desc">Direção artística completa, realismo cinematográfico, foco em valorização máxima do projeto.</p></div>
    <div class="servico-card"><div class="servico-num">04</div><div class="servico-icon">⊞</div><div class="servico-name">Projetos 3D e Plantas</div><p class="servico-desc">Modelagem 3D completa, plantas baixas e representação técnica com acabamento visual de alto padrão.</p></div>
    <div class="servico-card"><div class="servico-num">05</div><div class="servico-icon">⬡</div><div class="servico-name">Interiores</div><p class="servico-desc">Renderização especializada em ambientes internos — iluminação, materiais e atmosfera com precisão.</p></div>
  </div>
</section>

<!-- PROCESSO -->
<section class="processo">
  <div class="section-header">
    <div>
      <div class="section-tag">Como trabalhamos</div>
      <h2 class="section-title">O nosso <em>processo</em></h2>
    </div>
  </div>
  <div class="processo-steps">
    <div class="step"><div class="step-num">01</div><div class="step-title">Briefing</div><p class="step-desc">Entendemos o projeto, o público-alvo e o objetivo da renderização.</p></div>
    <div class="step"><div class="step-num">02</div><div class="step-title">Direção Artística</div><p class="step-desc">Definimos paleta, atmosfera, ângulos e linguagem visual junto com você.</p></div>
    <div class="step"><div class="step-num">03</div><div class="step-title">Produção</div><p class="step-desc">Modelagem, iluminação e renderização com revisões inclusas.</p></div>
    <div class="step"><div class="step-num">04</div><div class="step-title">Entrega</div><p class="step-desc">Arquivos em alta resolução prontos para usar em qualquer canal.</p></div>
  </div>
</section>

<div class="gold-divider"></div>

<!-- CONTATO -->
<section class="contato" id="contato">
  <div class="contato-content">
    <div class="section-tag">Contato</div>
    <h2 class="section-title">Vamos trabalhar<br><em>juntos</em></h2>
    <p class="contato-text">Cada projeto começa com uma conversa. Me conta o que você precisa e a gente encontra a melhor solução.</p>
    <div class="contato-links">
      <a href="https://wa.me/55SEUNUMERO" class="contato-link" target="_blank"><span class="contato-link-icon">↗</span>WhatsApp — (xx) xxxxx-xxxx</a>
      <a href="mailto:contato@studiobalma.com.br" class="contato-link"><span class="contato-link-icon">↗</span>contato@studiobalma.com.br</a>
      <a href="https://instagram.com/studiobalma" class="contato-link" target="_blank"><span class="contato-link-icon">↗</span>@studiobalma</a>
    </div>
  </div>
  <div class="contato-form">
    <div class="form-row">
      <div class="form-group"><label class="form-label">Nome</label><input type="text" class="form-input" placeholder="Seu nome"></div>
      <div class="form-group"><label class="form-label">Empresa / Escritório</label><input type="text" class="form-input" placeholder="Opcional"></div>
    </div>
    <div class="form-group"><label class="form-label">Você é</label><select class="form-select"><option value="">Selecione seu perfil</option><option>Arquiteto(a)</option><option>Designer de Interiores</option><option>Incorporadora</option><option>Corretor(a)</option><option>Outro</option></select></div>
    <div class="form-group"><label class="form-label">Serviço de interesse</label><select class="form-select"><option value="">Selecione o serviço</option><option>Render para Aprovação</option><option>Render Comercial</option><option>Render Premium</option><option>Projetos 3D / Plantas</option><option>Interiores</option></select></div>
    <div class="form-group"><label class="form-label">Sobre o projeto</label><textarea class="form-textarea" placeholder="Tipo de projeto, prazo, referências..."></textarea></div>
    <button class="form-submit" onclick="handleSubmit()">Enviar mensagem →</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">STUDIO <span>BALMA</span></div>
  <div class="footer-copy">© 2025 Studio Balma. Todos os direitos reservados.</div>
  <div class="footer-social">
    <a href="#">Instagram</a>
    <a href="#">Behance</a>
    <a href="#">WhatsApp</a>
  </div>
</footer>

<script>
  // Carregar GIF enviado pelo usuário
  (function() {
    const img = document.getElementById('heroGif');
    // A imagem enviada pelo usuário — usa a URL do blob ou base64 se disponível
    // Por padrão exibe o placeholder visual dourado
    img.onerror = function() {
      this.style.display = 'none';
    };
  })();

  // Tabs
  function showNicho(id, btn) {
    document.querySelectorAll('.nicho-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.nicho-tab').forEach(t => t.classList.remove('active'));
    document.getElementById('panel-' + id).classList.add('active');
    btn.classList.add('active');
  }

  // Form
  function handleSubmit() {
    const btn = document.querySelector('.form-submit');
    btn.textContent = 'Mensagem enviada ✓';
    btn.style.background = '#4a7c59';
    setTimeout(() => { btn.textContent = 'Enviar mensagem →'; btn.style.background = ''; }, 3000);
  }

  // Scroll reveal
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.08 });

  document.querySelectorAll('.servico-card, .step, .project-card, .stat-num').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    obs.observe(el);
  });
</script>
</body>
</html>
