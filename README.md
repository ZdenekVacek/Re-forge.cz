<!DOCTYPE html>
<html lang="cs">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#183c35">
  <meta name="description" content="Re-forge: Nezávislí IT a procesní architekti. Zanalyzujeme vaše potřeby, vybereme správné technologie a pohlídáme dodavatele od výběru po realizaci.">
  <title>Re-forge | Nezávislý IT a procesní dohled pro firmy</title>
  <style>
    :root {
      --forest: #183c35;
      --forest-2: #244d43;
      --ink: #172923;
      --muted: #64736d;
      --cream: #f4f2eb;
      --paper: #fbfaf6;
      --line: #e2e5de;
      --gold: #c49a62;
      --white: #fff;
      --radius: 18px;
      --shadow: 0 18px 55px rgba(22, 49, 40, .09);
    }
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0; color: var(--ink); background: var(--paper);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.65; -webkit-font-smoothing: antialiased;
    }
    a { color: inherit; text-decoration: none; }
    button, input, textarea { font: inherit; }
    .wrap { width: min(1160px, calc(100% - 48px)); margin: 0 auto; }
    .topbar {
      position: sticky; top: 0; z-index: 20; background: rgba(251,250,246,.92);
      backdrop-filter: blur(14px); border-bottom: 1px solid rgba(226,229,222,.8);
    }
    .nav { height: 78px; display: flex; align-items: center; justify-content: space-between; gap: 24px; }
    .brand { display: inline-flex; align-items: center; gap: 11px; font-weight: 850; letter-spacing: -.065em; font-size: 1.45rem; }
    .brand-mark { width: 31px; height: 31px; border: 2px solid var(--forest); border-radius: 9px 9px 9px 2px; position: relative; transform: rotate(-8deg); }
    .brand-mark:after { content: ""; position: absolute; width: 13px; height: 13px; right: -5px; bottom: -5px; background: var(--gold); border-radius: 50%; border: 3px solid var(--paper); }
    .brand span { color: var(--forest); }
    .nav-links { display: flex; align-items: center; gap: 29px; color: #52625b; font-size: .91rem; font-weight: 600; }
    .nav-links a:hover { color: var(--forest); }
    .nav-cta, .btn {
      display: inline-flex; align-items: center; justify-content: center; gap: 10px;
      border-radius: 999px; padding: 13px 21px; font-weight: 700; transition: .2s ease;
    }
    .nav-cta, .btn-primary { background: var(--forest); color: var(--white); }
    .nav-cta:hover, .btn-primary:hover { background: var(--forest-2); transform: translateY(-2px); }
    .btn-secondary { border: 1px solid rgba(255,255,255,.36); color: white; }
    .btn-secondary:hover { background: rgba(255,255,255,.1); }
    .menu-toggle { display: none; border: 0; background: none; color: var(--forest); font-size: 1.6rem; cursor: pointer; }
    .hero {
      position: relative; overflow: hidden; color: white; background: var(--forest);
      padding: 104px 0 96px;
    }
    .hero:before {
      content: ""; position: absolute; width: 620px; height: 620px; border-radius: 50%;
      border: 1px solid rgba(255,255,255,.1); right: -100px; top: -220px;
      box-shadow: 0 0 0 65px rgba(255,255,255,.025), 0 0 0 130px rgba(255,255,255,.02);
    }
    .hero:after {
      content: ""; position: absolute; width: 420px; height: 420px; right: 8%; bottom: -330px;
      border-radius: 50%; background: rgba(196,154,98,.18); filter: blur(2px);
    }
    .hero-grid { position: relative; z-index: 1; display: grid; grid-template-columns: 1.15fr .85fr; gap: 70px; align-items: center; }
    .eyebrow { display: inline-flex; align-items: center; gap: 10px; text-transform: uppercase; letter-spacing: .16em; font-size: .72rem; font-weight: 800; color: var(--gold); }
    .eyebrow:before { content: ""; width: 25px; height: 1px; background: currentColor; }
    h1 { margin: 22px 0 25px; font-size: clamp(3.3rem, 7vw, 5.5rem); line-height: 1.05; letter-spacing: -.05em; font-weight: 760; }
    h1 em { color: #d9bd94; font-style: normal; }
    .hero-copy { max-width: 610px; color: rgba(255,255,255,.77); font-size: 1.15rem; line-height: 1.8; }
    .hero-actions { display: flex; flex-wrap: wrap; gap: 13px; margin-top: 34px; }
    .hero-note { margin-top: 27px; color: rgba(255,255,255,.54); font-size: .82rem; }
    .hero-visual { min-height: 390px; display: flex; align-items: center; justify-content: center; position: relative; }
    .orbit { width: min(390px, 100%); aspect-ratio: 1; border: 1px solid rgba(255,255,255,.2); border-radius: 50%; position: relative; display: grid; place-items: center; }
    .orbit:before, .orbit:after { content: ""; position: absolute; border: 1px solid rgba(255,255,255,.14); border-radius: 50%; }
    .orbit:before { inset: 35px; } .orbit:after { inset: 75px; }
    .orbit-center { width: 142px; height: 142px; border-radius: 35px; transform: rotate(-8deg); background: #f1eadb; color: var(--forest); display: grid; place-items: center; text-align: center; box-shadow: 0 25px 65px rgba(0,0,0,.22); }
    .orbit-center strong { font-size: 1.3rem; letter-spacing: -.06em; transform: rotate(8deg); }
    .orbit-center small { display: block; font-size: .65rem; letter-spacing: .12em; text-transform: uppercase; font-weight: 800; transform: rotate(8deg); }
    .orbit-label { position: absolute; padding: 10px 14px; border: 1px solid rgba(255,255,255,.2); border-radius: 999px; background: rgba(255,255,255,.08); backdrop-filter: blur(8px); font-size: .78rem; color: rgba(255,255,255,.88); }
    .label-a { top: 12%; left: 4%; } .label-b { top: 19%; right: -2%; } .label-c { bottom: 13%; left: 0; } .label-d { bottom: 8%; right: 5%; }
    section { padding: 100px 0; }
    .section-head { max-width: 720px; margin-bottom: 48px; }
    .kicker { color: #9a7548; text-transform: uppercase; letter-spacing: .15em; font-size: .72rem; font-weight: 800; }
    h2 { margin: 13px 0 17px; font-size: clamp(2.1rem, 4vw, 3.5rem); line-height: 1.08; letter-spacing: -.065em; font-weight: 740; }
    .lead { color: var(--muted); font-size: 1.1rem; max-width: 690px; }
    .intro-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: start; }
    .statement { font-size: clamp(1.5rem, 2.6vw, 2.2rem); line-height: 1.35; letter-spacing: -.04em; font-weight: 650; }
    .statement span { color: #9a7548; }
    .intro-text { color: var(--muted); }
    .principles { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-top: 54px; }
    .principle { padding: 25px; background: white; border: 1px solid var(--line); border-radius: var(--radius); }
    .number { color: var(--gold); font-size: .76rem; font-weight: 800; letter-spacing: .1em; }
    .principle h3 { margin: 12px 0 8px; font-size: 1.08rem; letter-spacing: -.025em; }
    .principle p { margin: 0; color: var(--muted); font-size: .92rem; }
    .cream-section { background: var(--cream); }
    .service-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
    .service { background: rgba(255,255,255,.78); border: 1px solid #e4e2d9; border-radius: var(--radius); padding: 28px; min-height: 240px; transition: .22s ease; }
    .service:hover { transform: translateY(-5px); box-shadow: var(--shadow); background: white; }
    .service-icon { width: 43px; height: 43px; border-radius: 13px; background: #e9eee8; color: var(--forest); display: grid; place-items: center; font-size: 1.25rem; }
    .service h3 { margin: 20px 0 9px; font-size: 1.12rem; letter-spacing: -.03em; }
    .service p { color: var(--muted); margin: 0; font-size: .92rem; }
    .service-foot { margin-top: 27px; color: #8d6c45; font-size: .9rem; font-weight: 700; }
    .process { display: grid; grid-template-columns: repeat(6, 1fr); gap: 0; position: relative; margin-top: 48px; }
    .process:before { content: ""; position: absolute; top: 22px; left: 4%; right: 4%; height: 1px; background: #d9ded7; }
    .step { position: relative; padding: 0 15px 0 0; }
    .step-dot { width: 45px; height: 45px; display: grid; place-items: center; border: 1px solid #cbd5cc; border-radius: 50%; background: var(--paper); color: var(--forest); font-size: .8rem; font-weight: 800; position: relative; z-index: 1; }
    .step h3 { font-size: .98rem; margin: 18px 0 7px; letter-spacing: -.02em; }
    .step p { font-size: .84rem; color: var(--muted); margin: 0; }
    .dark-panel { background: var(--forest); color: white; border-radius: 26px; padding: 56px; display: grid; grid-template-columns: 1fr .8fr; gap: 55px; align-items: center; overflow: hidden; position: relative; }
    .dark-panel:after { content: ""; position: absolute; width: 300px; height: 300px; border: 1px solid rgba(255,255,255,.13); border-radius: 50%; right: -100px; bottom: -190px; box-shadow: 0 0 0 45px rgba(255,255,255,.025),0 0 0 90px rgba(255,255,255,.02); }
    .dark-panel h2 { font-size: clamp(2rem, 3.5vw, 3.1rem); }
    .dark-panel p { color: rgba(255,255,255,.7); }
    .partner-list { position: relative; z-index: 1; display: grid; gap: 13px; }
    .partner-item { padding: 17px 19px; border: 1px solid rgba(255,255,255,.16); border-radius: 14px; background: rgba(255,255,255,.06); }
    .partner-item strong { display: block; font-size: .96rem; }
    .partner-item span { color: rgba(255,255,255,.6); font-size: .82rem; }
    .trust-grid { display: grid; grid-template-columns: .85fr 1.15fr; gap: 80px; }
    .trust-points { display: grid; gap: 22px; }
    .trust-point { display: grid; grid-template-columns: 35px 1fr; gap: 15px; }
    .check { width: 30px; height: 30px; border-radius: 50%; background: #e7eee7; color: var(--forest); display: grid; place-items: center; font-weight: 900; }
    .trust-point h3 { margin: 0 0 4px; font-size: 1rem; }
    .trust-point p { margin: 0; color: var(--muted); font-size: .91rem; }
    .contact { background: #f0eee6; }
    .contact-grid { display: grid; grid-template-columns: .9fr 1.1fr; gap: 70px; align-items: start; }
    .contact-card { background: white; padding: 34px; border-radius: 22px; border: 1px solid var(--line); box-shadow: var(--shadow); }
    .contact-card label { display: block; margin: 15px 0 6px; font-size: .83rem; font-weight: 700; }
    .contact-card input, .contact-card textarea { width: 100%; border: 1px solid #dce2db; border-radius: 10px; padding: 13px 14px; outline: none; background: #fdfdfb; color: var(--ink); }
    .contact-card input:focus, .contact-card textarea:focus { border-color: #789588; box-shadow: 0 0 0 3px rgba(36,77,67,.08); }
    .contact-card textarea { min-height: 125px; resize: vertical; }
    .contact-card button { border: 0; cursor: pointer; margin-top: 20px; width: 100%; }
    .form-note { color: #79857f; font-size: .75rem; margin: 12px 0 0; }
    .contact-detail { margin-top: 28px; color: var(--muted); font-size: .93rem; }
    .contact-detail strong { color: var(--ink); display: block; margin-bottom: 4px; }
    footer { background: #142f2a; color: white; padding: 34px 0; }
    .footer-inner { display: flex; justify-content: space-between; align-items: center; gap: 20px; }
    .footer-inner p { margin: 0; color: rgba(255,255,255,.55); font-size: .8rem; }
    .footer-links { display: flex; gap: 20px; color: rgba(255,255,255,.72); font-size: .82rem; }
    .reveal { opacity: 0; transform: translateY(18px); transition: opacity .65s ease, transform .65s ease; }
    .reveal.visible { opacity: 1; transform: none; }
    @media (max-width: 900px) {
      .nav-links { gap: 16px; } .hero-grid, .intro-grid, .dark-panel, .trust-grid, .contact-grid { grid-template-columns: 1fr; }
      .hero-grid { gap: 30px; } .hero-visual { min-height: 330px; } .orbit { width: 310px; }
      .service-grid { grid-template-columns: repeat(2, 1fr); } .process { grid-template-columns: repeat(3, 1fr); row-gap: 35px; }
      .process:before { display: none; } .dark-panel { padding: 40px; gap: 30px; }
    }
    @media (max-width: 650px) {
      .wrap { width: min(100% - 34px, 1160px); } .nav { height: 68px; }
      .menu-toggle { display: block; } .nav-cta { display: none; }
      .nav-links { display: none; position: absolute; top: 68px; left: 0; right: 0; padding: 18px 24px 24px; background: var(--paper); border-bottom: 1px solid var(--line); flex-direction: column; align-items: stretch; }
      .nav-links.open { display: flex; } .nav-links a { padding: 8px 0; }
      .hero { padding: 76px 0 60px; } h1 { font-size: clamp(3.15rem, 16vw, 4rem); }
      .hero-copy { font-size: 1rem; } .hero-visual { min-height: 285px; } .orbit { width: 270px; }
      .orbit-center { width: 112px; height: 112px; border-radius: 28px; } .orbit-center strong { font-size: 1.08rem; }
      .orbit-label { font-size: .67rem; padding: 8px 10px; } .label-b { right: -3%; }
      section { padding: 72px 0; } .principles, .service-grid { grid-template-columns: 1fr; }
      .process { grid-template-columns: repeat(2, 1fr); row-gap: 28px; }
      .dark-panel { padding: 30px 24px; } .contact-grid { gap: 30px; } .contact-card { padding: 24px; }
      .footer-inner { align-items: flex-start; flex-direction: column; } .footer-links { flex-wrap: wrap; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; } *, *:before, *:after { transition-duration: .01ms !important; animation-duration: .01ms !important; }
      .reveal { opacity: 1; transform: none; }
    }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="wrap nav">
      <a class="brand" href="#domu" aria-label="Re-forge – úvod"><i class="brand-mark"></i><span>RE-FORGE</span></a>
      <button class="menu-toggle" aria-label="Otevřít navigaci" aria-expanded="false">☰</button>
      <nav class="nav-links" aria-label="Hlavní navigace">
        <a href="#jak-pomahame">Jak pomáháme</a>
        <a href="#oblasti">Co řešíme</a>
        <a href="#spoluprace">Spolupráce</a>
        <a href="#o-nas">Náš přístup</a>
      </nav>
      <a class="nav-cta" href="#kontakt">Domluvit hovor <span>↗</span></a>
    </div>
  </header>

  <main>
    <section class="hero" id="domu">
      <div class="wrap hero-grid">
        <div>
          <div class="eyebrow">Nezávislý IT a procesní dohled pro firmy</div>
          <h1>Najdeme správné <em>technologie</em><br>a dodavatele.</h1>
          <p class="hero-copy">Zbavíme vás chaosu při výběru IT systémů a řízení projektů. Zanalyzujeme vaše skutečné potřeby, navrhneme architekturu a dohlédneme na prověřené specialisty od výběru po realizaci. Bez provizí a skrytých háčků.</p>
          <div class="hero-actions">
            <a class="btn btn-primary" href="#kontakt">Domluvit nezávaznou konzultaci <span>↗</span></a>
            <a class="btn btn-secondary" href="#jak-pomahame">Jak to funguje</a>
          </div>
          <div class="hero-note">Získejte expertní pohled zvenčí. Vy řídíte svůj byznys, my pohlídáme zbytek.</div>
        </div>
        <div class="hero-visual" aria-label="Propojení firmy, lidí, procesů a řešení">
          <div class="orbit">
            <span class="orbit-label label-a">Lidé</span>
            <span class="orbit-label label-b">Technologie</span>
            <span class="orbit-label label-c">Procesy</span>
            <span class="orbit-label label-d">Dodavatelé</span>
            <div class="orbit-center"><div><strong>RE-FORGE</strong><small>nezávislý dozor</small></div></div>
          </div>
        </div>
      </div>
    </section>

    <section id="jak-pomahame">
      <div class="wrap">
        <div class="intro-grid reveal">
          <div>
            <div class="kicker">Zastupujeme vaše zájmy</div>
            <p class="statement">Neprodáváme software ani hardware. <span>Hledáme to, co vám ušetří čas a peníze.</span></p>
          </div>
          <div class="intro-text">
            <p>Firmy často ztrácí statisíce na IT systémech, které nepotřebují, nebo které spolu navzájem nekomunikují. My vystupujeme jako váš nezávislý architekt.</p>
            <p>Nejprve zmapujeme vaše aktuální procesy a odhalíme úzká hrdla. Teprve poté navrhneme optimální řešení a vysoutěžíme na trhu dodavatele, kteří ho prokazatelně umí dodat.</p>
          </div>
        </div>
        <div class="principles">
          <article class="principle reveal"><div class="number">01 / AUDIT STAVU</div><h3>Analyzujeme potřeby</h3><p>Neřešíme technologii pro technologii. Zjišťujeme, kde vám zbytečně utíkají peníze nebo kapacity lidí.</p></article>
          <article class="principle reveal"><div class="number">02 / NÁVRH ŘEŠENÍ</div><h3>Tvoříme zadání</h3><p>Připravíme srozumitelnou architekturu, porovnáme varianty na trhu a spočítáme reálné náklady i návratnost.</p></article>
          <article class="principle reveal"><div class="number">03 / REALIZACE</div><h3>Hlídáme výsledek</h3><p>Propojíme vás s prověřenými dodavateli a převezmeme roli projektového manažera při samotném nasazování.</p></article>
        </div>
      </div>
    </section>

    <section class="cream-section" id="oblasti">
      <div class="wrap">
        <div class="section-head reveal">
          <div class="kicker">Kde fungujeme jako architekti</div>
          <h2>Nemusíte být experti na vše. My vás zastoupíme.</h2>
          <p class="lead">Zorientujeme se ve vašem problému a sestavíme pro daný projekt tým správných dodavatelů, jejichž práci pohlídáme od začátku do konce.</p>
        </div>
        <div class="service-grid">
          <article class="service reveal"><div class="service-icon">⌘</div><h3>Software a firemní systémy</h3><p>Zmapujeme procesy a pomůžeme s výběrem i integrací ERP, CRM, automatizace nebo vhodného zapojení umělé inteligence.</p><div class="service-foot">Systémy na míru vašim procesům.</div></article>
          <article class="service reveal"><div class="service-icon">▣</div><h3>Hardware a infrastruktura</h3><p>Navrhneme vhodnou architekturu (od serverů po cloudové služby) a vysoutěžíme nejlepší dodavatele techniky.</p><div class="service-foot">Výkon, který reálně potřebujete.</div></article>
          <article class="service reveal"><div class="service-icon">⌁</div><h3>Sítě a konektivita</h3><p>Odhalíme slabá místa firemní sítě a zadáme její modernizaci tak, aby komunikace poboček fungovala zcela spolehlivě.</p><div class="service-foot">Infrastruktura bez výpadků.</div></article>
          <article class="service reveal"><div class="service-icon">◈</div><h3>Bezpečnost a zálohování</h3><p>Připravíme nezávislý návrh kybernetické ochrany dat, zavedeme politiku přístupů a pohlídáme kontinuitu vašeho provozu.</p><div class="service-foot">Vaše firemní data v bezpečí.</div></article>
          <article class="service reveal"><div class="service-icon">↗</div><h3>Sestavení IT týmů</h3><p>Pokud potřebujete vývojáře nebo úzce profilované specialisty, najdeme je, otestujeme a integrujeme do vašeho projektu.</p><div class="service-foot">Lidé s prověřeným know-how.</div></article>
          <article class="service reveal"><div class="service-icon">◎</div><h3>Optimalizace procesů</h3><p>Identifikujeme zbytečnou ruční rutinu a navrhneme změny, které zaměstnancům ušetří hodiny času týdně.</p><div class="service-foot">Měřitelné zvýšení efektivity.</div></article>
        </div>
      </div>
    </section>

    <section id="spoluprace">
      <div class="wrap">
        <div class="section-head reveal">
          <div class="kicker">Od problému k výsledku</div>
          <h2>Jak vypadá spolupráce v praxi.</h2>
          <p class="lead">Žádné zbytečné schůzky. Jasný postup, transparentní rozpočet a převzetí zodpovědnosti za hladký průběh.</p>
        </div>
        <div class="process">
          <article class="step reveal"><div class="step-dot">01</div><h3>Úvodní hovor</h3><p>Na 30 minut si sedneme a zjistíme, co vás ve firmě trápí a kde tlačí bota.</p></article>
          <article class="step reveal"><div class="step-dot">02</div><h3>Analýza</h3><p>Projdeme stávající stav, odhalíme technický dluh a definujeme rozsah projektu.</p></article>
          <article class="step reveal"><div class="step-dot">03</div><h3>Návrh postupu</h3><p>Předložíme varianty řešení včetně odhadu nezbytných nákladů a přínosů.</p></article>
          <article class="step reveal"><div class="step-dot">04</div><h3>Výběr dodavatelů</h3><p>Z naší prověřené sítě či trhu vysoutěžíme konkrétní realizátory technologií.</p></article>
          <article class="step reveal"><div class="step-dot">05</div><h3>Řízení projektu</h3><p>Převezmeme dohled nad nasazením a hlídáme dodržení termínů i kvality.</p></article>
          <article class="step reveal"><div class="step-dot">06</div><h3>Předání a podpora</h3><p>Dohlédneme na úspěšný start a zůstáváme k ruce pro další rozvoj.</p></article>
        </div>
      </div>
    </section>

    <section class="cream-section" id="o-nas">
      <div class="wrap">
        <div class="dark-panel reveal">
          <div>
            <div class="eyebrow">Nezávislost v praxi</div>
            <h2>Platíte nás vy.<br>Ne dodavatelé IT.</h2>
            <p>Náš obchodní model je maximálně transparentní. Nejsme závislí na prodeji licencí konkrétní značky a nebereme od softwarových firem skryté provize za to, že vám doporučíme jejich produkt.</p>
            <p>Jsme honorováni přímo vámi za konzultace, architekturu a projektové řízení. Díky tomu máme všichni stejný cíl: najít řešení, které bude nejefektivnější pro vaši peněženku a provoz.</p>
          </div>
          <div class="partner-list">
            <div class="partner-item"><strong>Naše role (Re-forge)</strong><span>Analýza, architektura zadání a nezávislý dozor nad dodavateli.</span></div>
            <div class="partner-item"><strong>Specialisté (Dodavatelé)</strong><span>Samotné kódování, tahání kabelů nebo nasazení systémů.</span></div>
            <div class="partner-item"><strong>Vaše firma (Klient)</strong><span>Šetří čas manažerů a získává funkční řešení s garancí.</span></div>
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="wrap trust-grid">
        <div class="reveal">
          <div class="kicker">Proč my</div>
          <h2>Na vaší straně stolu. Vždycky.</h2>
          <p class="lead">Firmy se často bojí najmout IT specialisty, protože nerozumí jejich žargonu a nepoznají, zda cena odpovídá realitě. My jsme váš štít.</p>
        </div>
        <div class="trust-points">
          <article class="trust-point reveal"><div class="check">✓</div><div><h3>Jsme váš překladatel</h3><p>Mluvíme řečí vašeho byznysu i řečí vývojářů. Přeložíme vaše požadavky do přesného technického zadání.</p></div></article>
          <article class="trust-point reveal"><div class="check">✓</div><div><h3>Šetříme váš čas</h3><p>Nemusíte obvolávat desítky firem a číst nesrozumitelné technické specifikace. My ty nabídky vyhodnotíme za vás.</p></div></article>
          <article class="trust-point reveal"><div class="check">✓</div><div><h3>Chráníme váš rozpočet</h3><p>Zamezíme tomu, aby se projekt zbytečně prodražoval nebo aby vám někdo prodal zbytečně naddimenzovaný systém.</p></div></article>
          <article class="trust-point reveal"><div class="check">✓</div><div><h3>Ručíme za funkčnost</h3><p>Nenecháme vás na holičkách v polovině cesty. Hlídáme integraci až do momentu, kdy vše skutečně funguje.</p></div></article>
        </div>
      </div>
    </section>

    <section class="contact" id="kontakt">
      <div class="wrap contact-grid">
        <div class="reveal">
          <div class="kicker">Úvodní konzultace zdarma</div>
          <h2>Pojďme probrat, kde vám to drhne.</h2>
          <p class="lead">Nemusíte mít přesné technické zadání. Stačí nám popsat, jaký problém ve firmě momentálně řešíte. Zjistíme, zda vám můžeme pomoci.</p>
          <div class="contact-detail"><strong>Re-forge s.r.o.</strong><br>IČO: 12345678 (DOPLNIT)<br>Sídlo: Ulice 123, Město (DOPLNIT)</div>
          <div class="contact-detail"><strong>Kontakt</strong>Telefon: +420 123 456 789 (DOPLNIT)<br><a href="mailto:doplnit@re-forge.cz">doplnit@re-forge.cz</a></div>
        </div>
        <!-- V produkci nahraďte tento form standardním backend řešením (např. PHP / Formspree) -->
        <form class="contact-card reveal" id="contactForm">
          <h3 style="margin:0 0 5px;font-size:1.3rem;letter-spacing:-.04em">Napište nám</h3>
          <p style="margin:0;color:#718078;font-size:.9rem">Krátce nám představte svou potřebu.</p>
          <label for="name">Jméno a firma</label>
          <input id="name" name="name" autocomplete="name" placeholder="Jak vám máme říkat?" required>
          <label for="email">E-mail</label>
          <input id="email" name="email" type="email" autocomplete="email" placeholder="vas@email.cz" required>
          <label for="message">Co potřebujete vyřešit?</label>
          <textarea id="message" name="message" placeholder="Popište nám stručně, co vás ve firmě trápí nebo co chcete zlepšit..." required></textarea>
          <button class="btn btn-primary" type="submit">Odeslat nezávaznou poptávku <span>↗</span></button>
          <p class="form-note">Do 24 hodin se vám ozveme zpět. Odesláním souhlasíte se zpracováním osobních údajů.</p>
        </form>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap footer-inner">
      <a class="brand" href="#domu" style="color:white"><i class="brand-mark" style="border-color:#d9e3dc"></i><span style="color:white">RE-FORGE</span></a>
      <p>© <span id="year"></span> Re-forge. Nezávislí architekti pro vaše podnikání.</p>
      <div class="footer-links">
        <a href="#jak-pomahame">Jak pomáháme</a>
        <a href="#oblasti">Co řešíme</a>
        <a href="#kontakt">Kontakt</a>
        <a href="#">Zásady ochrany osobních údajů (DOPLNIT ODKAZ)</a>
      </div>
    </div>
  </footer>

  <script>
    const menuButton = document.querySelector('.menu-toggle');
    const navLinks = document.querySelector('.nav-links');
    menuButton.addEventListener('click', () => {
      const isOpen = navLinks.classList.toggle('open');
      menuButton.setAttribute('aria-expanded', String(isOpen));
      menuButton.textContent = isOpen ? '×' : '☰';
    });
    navLinks.querySelectorAll('a').forEach(link => link.addEventListener('click', () => {
      navLinks.classList.remove('open');
      menuButton.setAttribute('aria-expanded', 'false');
      menuButton.textContent = '☰';
    }));
    document.getElementById('year').textContent = new Date().getFullYear();

    const revealObserver = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          revealObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });
    document.querySelectorAll('.reveal').forEach(el => revealObserver.observe(el));

    // Skript dočasně ponechán na "mailto:" pro účely návrhu.
    // Před nasazením napojte na reálný server (např. PHP mailer, Formspree atd.)
    document.getElementById('contactForm').addEventListener('submit', event => {
      event.preventDefault();
      const form = new FormData(event.currentTarget);
      const subject = encodeURIComponent('Nezávazná poptávka / Re-forge');
      const body = encodeURIComponent(
        `Dobrý den,\n\njméno a firma: ${form.get('name')}\ne-mail: ${form.get('email')}\n\nCo potřebuji vyřešit:\n${form.get('message')}\n\n`
      );
      window.location.href = `mailto:doplnit@re-forge.cz?subject=${subject}&body=${body}`;
    });
  </script>
</body>
</html>
