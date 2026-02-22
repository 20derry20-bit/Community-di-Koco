<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Community di Koco</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700;900&family=Exo+2:wght@300;400;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --blue-deep: #050f2e;
      --blue-mid: #0a1f5c;
      --blue-bright: #1a4fff;
      --blue-neon: #3d9bff;
      --blue-glow: #00c3ff;
      --blue-light: #a8d4ff;
      --white: #f0f6ff;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--blue-deep);
      color: var(--white);
      font-family: 'Exo 2', sans-serif;
      overflow-x: hidden;
    }

    /* ── BACKGROUND ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background:
        radial-gradient(ellipse 80% 60% at 20% 10%, rgba(29,79,255,.25) 0%, transparent 60%),
        radial-gradient(ellipse 60% 50% at 80% 90%, rgba(0,195,255,.18) 0%, transparent 60%),
        repeating-linear-gradient(0deg, transparent, transparent 60px, rgba(61,155,255,.04) 60px, rgba(61,155,255,.04) 61px),
        repeating-linear-gradient(90deg, transparent, transparent 60px, rgba(61,155,255,.04) 60px, rgba(61,155,255,.04) 61px);
      z-index: 0;
      pointer-events: none;
    }

    section, nav, footer { position: relative; z-index: 1; }

    /* ── NAVBAR ── */
    nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.4rem 6vw;
      border-bottom: 1px solid rgba(61,155,255,.2);
      backdrop-filter: blur(10px);
      background: rgba(5,15,46,.7);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .logo {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.6rem;
      font-weight: 900;
      letter-spacing: .1em;
      color: var(--blue-glow);
      text-shadow: 0 0 20px var(--blue-glow), 0 0 40px rgba(0,195,255,.4);
    }

    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a {
      text-decoration: none;
      color: var(--blue-light);
      font-weight: 600;
      letter-spacing: .06em;
      font-size: .95rem;
      transition: color .25s;
    }
    .nav-links a:hover { color: var(--blue-glow); }

    /* ── HAMBURGER ── */
    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      background: none;
      border: none;
      padding: 4px;
    }
    .hamburger span {
      display: block;
      width: 26px;
      height: 2px;
      background: var(--blue-glow);
      border-radius: 2px;
      transition: all .3s;
    }

    /* ── HERO ── */
    .hero {
      min-height: 92vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 6rem 6vw;
    }

    .hero-badge {
      display: inline-block;
      border: 1px solid rgba(0,195,255,.5);
      color: var(--blue-glow);
      font-size: .8rem;
      letter-spacing: .2em;
      text-transform: uppercase;
      padding: .4rem 1.2rem;
      border-radius: 2rem;
      margin-bottom: 2rem;
      animation: fadeDown .8s ease both;
    }

    .hero h1 {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(3rem, 8vw, 7rem);
      font-weight: 900;
      line-height: 1.05;
      letter-spacing: .05em;
      text-shadow: 0 0 40px rgba(0,195,255,.5);
      animation: fadeDown .9s .1s ease both;
    }

    .hero h1 span {
      color: var(--blue-glow);
      text-shadow: 0 0 60px var(--blue-glow), 0 0 120px rgba(0,195,255,.3);
    }

    .hero p {
      max-width: 600px;
      margin: 1.8rem auto 0;
      font-size: 1.15rem;
      color: var(--blue-light);
      line-height: 1.7;
      font-weight: 300;
      animation: fadeDown 1s .2s ease both;
    }

    .hero-cta {
      display: flex;
      gap: 1rem;
      margin-top: 2.5rem;
      flex-wrap: wrap;
      justify-content: center;
      animation: fadeDown 1s .35s ease both;
    }

    /* ── SECTION SHARED ── */
    .section { padding: 7rem 6vw; }

    .section-title {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      letter-spacing: .08em;
      color: var(--white);
      margin-bottom: 1rem;
    }

    .section-title .accent { color: var(--blue-glow); }

    .divider {
      width: 80px;
      height: 3px;
      background: linear-gradient(90deg, var(--blue-bright), var(--blue-glow));
      border-radius: 2px;
      margin-bottom: 3rem;
      box-shadow: 0 0 12px var(--blue-glow);
    }

    /* ── CHI SIAMO ── */
    #chi-siamo {
      background: rgba(10,31,92,.25);
      border-top: 1px solid rgba(61,155,255,.15);
      border-bottom: 1px solid rgba(61,155,255,.15);
    }

    .chi-siamo-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: center;
    }

    .chi-siamo-text p {
      color: var(--blue-light);
      font-size: 1.05rem;
      line-height: 1.9;
      font-weight: 300;
      margin-bottom: 1.2rem;
    }

    .stats {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
    }

    .stat-card {
      background: rgba(26,79,255,.1);
      border: 1px solid rgba(61,155,255,.25);
      border-radius: 1rem;
      padding: 1.8rem;
      text-align: center;
      transition: transform .3s, box-shadow .3s;
    }

    .stat-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 12px 40px rgba(0,195,255,.2);
    }

    .stat-number {
      font-family: 'Orbitron', sans-serif;
      font-size: 2.2rem;
      font-weight: 900;
      color: var(--blue-glow);
      text-shadow: 0 0 20px var(--blue-glow);
    }

    .stat-label {
      font-size: .85rem;
      color: var(--blue-light);
      letter-spacing: .1em;
      margin-top: .4rem;
    }

    /* ── DISCORD ── */
    #discord { text-align: center; }

    .discord-card {
      display: inline-flex;
      flex-direction: column;
      align-items: center;
      gap: 2rem;
      background: rgba(88,101,242,.1);
      border: 1px solid rgba(88,101,242,.4);
      border-radius: 2rem;
      padding: 4rem 5rem;
      backdrop-filter: blur(10px);
      transition: box-shadow .3s;
    }

    .discord-card:hover { box-shadow: 0 0 60px rgba(88,101,242,.3); }

    .discord-logo-link {
      display: inline-block;
      text-decoration: none;
      transition: transform .3s, filter .3s;
    }

    .discord-logo-link:hover {
      transform: scale(1.12) rotate(-4deg);
      filter: drop-shadow(0 0 24px rgba(88,101,242,.9));
    }

    .discord-logo-link svg { width: 100px; height: 100px; }

    .discord-tagline {
      font-size: 1rem;
      color: var(--blue-light);
      font-weight: 300;
      max-width: 380px;
    }

    /* ── BUTTONS ── */
    .btn {
      display: inline-flex;
      align-items: center;
      gap: .7rem;
      padding: .9rem 2.2rem;
      border-radius: 3rem;
      font-family: 'Exo 2', sans-serif;
      font-weight: 600;
      font-size: 1rem;
      letter-spacing: .05em;
      text-decoration: none;
      cursor: pointer;
      border: none;
      transition: transform .25s, box-shadow .25s;
    }

    .btn-discord {
      background: linear-gradient(135deg, #5865F2, #7289da);
      color: #fff;
      box-shadow: 0 6px 30px rgba(88,101,242,.5);
    }

    .btn-discord:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 40px rgba(88,101,242,.7);
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--blue-bright), var(--blue-glow));
      color: #fff;
      box-shadow: 0 6px 30px rgba(0,195,255,.4);
    }

    .btn-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 40px rgba(0,195,255,.6);
    }

    .btn-outline {
      background: transparent;
      color: var(--blue-glow);
      border: 1px solid rgba(0,195,255,.5);
    }

    .btn-outline:hover {
      background: rgba(0,195,255,.08);
      transform: translateY(-3px);
    }

    /* ── MAGLIETTE ── */
    #magliette {
      text-align: center;
      background: rgba(10,31,92,.25);
      border-top: 1px solid rgba(61,155,255,.15);
      border-bottom: 1px solid rgba(61,155,255,.15);
    }

    #magliette .divider { margin-left: auto; margin-right: auto; }

    .shirt-showcase {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 2.5rem;
    }

    .shirt-icon {
      font-size: 8rem;
      line-height: 1;
      filter: drop-shadow(0 0 30px rgba(0,195,255,.6));
      animation: float 3s ease-in-out infinite;
    }

    .shirt-description {
      font-size: 1.05rem;
      color: var(--blue-light);
      font-weight: 300;
      max-width: 500px;
      line-height: 1.8;
    }

    .btn-shop {
      background: linear-gradient(135deg, var(--blue-bright), var(--blue-glow));
      color: #fff;
      font-size: 1.1rem;
      padding: 1rem 2.8rem;
      box-shadow: 0 6px 30px rgba(0,195,255,.4);
    }

    .btn-shop:hover {
      transform: translateY(-4px);
      box-shadow: 0 14px 50px rgba(0,195,255,.6);
    }

    /* ── FOOTER ── */
    footer {
      text-align: center;
      padding: 3rem 6vw;
      border-top: 1px solid rgba(61,155,255,.15);
      color: rgba(168,212,255,.5);
      font-size: .85rem;
      letter-spacing: .05em;
    }

    footer span { color: var(--blue-glow); }

    /* ── ANIMATIONS ── */
    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50%       { transform: translateY(-16px); }
    }

    /* ── REVEAL ON SCROLL ── */
    .reveal {
      opacity: 0;
      transform: translateY(40px);
      transition: opacity .7s ease, transform .7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      .chi-siamo-grid { grid-template-columns: 1fr; }
      .discord-card { padding: 2.5rem 2rem; }
      .nav-links { display: none; }
      .nav-links.open {
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 100%;
        left: 0; right: 0;
        background: rgba(5,15,46,.97);
        padding: 1.5rem 6vw;
        border-bottom: 1px solid rgba(61,155,255,.2);
        gap: 1.2rem;
      }
      .hamburger { display: flex; }
    }
  </style>
</head>
<body>

<!-- NAVBAR -->
<nav>
  <div class="logo">KOCO</div>
  <ul class="nav-links" id="navLinks">
    <li><a href="#chi-siamo">Chi Siamo</a></li>
    <li><a href="#discord">Discord</a></li>
    <li><a href="#magliette">Magliette</a></li>
  </ul>
  <button class="hamburger" id="hamburger" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">✦ Community Ufficiale</div>
  <h1>Community<br/>di <span>Koco</span></h1>
  <p>Benvenuto nella community di Koco — il posto dove nascono amicizie, avventure e tutto ciò che rende il gioco indimenticabile.</p>
  <div class="hero-cta">
    <a class="btn btn-primary" href="#discord">Entra nella Community</a>
    <a class="btn btn-outline" href="#chi-siamo">Scopri di più</a>
  </div>
</section>

<!-- CHI SIAMO -->
<section class="section" id="chi-siamo">
  <div class="chi-siamo-grid">
    <div class="chi-siamo-text reveal">
      <div class="section-title"><span class="accent">Chi</span> Siamo</div>
      <div class="divider"></div>
      <p>Siamo una community nata dalla passione per il gioco e per la condivisione. Koco è un luogo virtuale dove ogni giocatore trova il proprio spazio: per divertirsi, crescere e fare nuove amicizie.</p>
      <p>Il nostro obiettivo è creare un ambiente inclusivo, rispettoso e sempre pieno di energia. Organizziamo eventi, tornei e tante attività per tenere viva la community ogni giorno.</p>
      <p>Che tu sia un veterano o un nuovo arrivato, qui sei sempre il benvenuto. Unisciti a noi e scopri cosa vuol dire far parte di qualcosa di speciale.</p>
    </div>
    <div class="stats reveal">
      <div class="stat-card">
        <div class="stat-number">100+</div>
        <div class="stat-label">MEMBRI ATTIVI</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">100+</div>
        <div class="stat-label">EVENTI</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">∞</div>
        <div class="stat-label">DIVERTIMENTO</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">24/7</div>
        <div class="stat-label">SEMPRE ATTIVI</div>
      </div>
    </div>
  </div>
</section>

<!-- DISCORD -->
<section class="section" id="discord">
  <div class="section-title reveal" style="text-align:center"><span class="accent">Unisciti</span> al nostro Discord</div>
  <div class="divider" style="margin:0 auto 3rem;"></div>
  <div class="discord-card reveal">
    <a class="discord-logo-link" href="https://discord.gg/SEPn3sqQdk" target="_blank" rel="noopener" title="Entra nel server Discord di Koco">
      <svg viewBox="0 0 127.14 96.36" xmlns="http://www.w3.org/2000/svg" fill="#5865F2">
        <path d="M107.7,8.07A105.15,105.15,0,0,0,81.47,0a72.06,72.06,0,0,0-3.36,6.83A97.68,97.68,0,0,0,49,6.83,72.37,72.37,0,0,0,45.64,0,105.89,105.89,0,0,0,19.39,8.09C2.79,32.65-1.71,56.6.54,80.21h0A105.73,105.73,0,0,0,32.71,96.36,77.7,77.7,0,0,0,39.6,85.25a68.42,68.42,0,0,1-10.85-5.18c.91-.66,1.8-1.34,2.66-2a75.57,75.57,0,0,0,64.32,0c.87.71,1.76,1.39,2.66,2a68.68,68.68,0,0,1-10.87,5.19,77,77,0,0,0,6.89,11.1A105.25,105.25,0,0,0,126.6,80.22h0C129.24,52.84,122.09,29.11,107.7,8.07ZM42.45,65.69C36.18,65.69,31,60,31,53s5-12.74,11.43-12.74S54,46,53.89,53,48.84,65.69,42.45,65.69Zm42.24,0C78.41,65.69,73.25,60,73.25,53s5-12.74,11.44-12.74S96.23,46,96.12,53,91.08,65.69,84.69,65.69Z"/>
      </svg>
    </a>
    <p class="discord-tagline">Chatta, gioca e divertiti con tutta la community di Koco — entra nel nostro server Discord!</p>
    <a class="btn btn-discord" href="https://discord.gg/SEPn3sqQdk" target="_blank" rel="noopener">
      Entra nel Server
    </a>
  </div>
</section>

<!-- MAGLIETTE -->
<section class="section" id="magliette">
  <div class="section-title reveal" style="margin-left:auto;margin-right:auto;text-align:center"><span class="accent">Magliette</span> di Koco</div>
  <div class="divider" style="margin-left:auto;margin-right:auto;" class="reveal"></div>
  <div class="shirt-showcase reveal">
    <div class="shirt-icon">👕</div>
    <p class="shirt-description">Indossa i colori di Koco! Le nostre magliette ufficiali sono disponibili su Roblox — mostra a tutti di far parte della community.</p>
    <a class="btn btn-shop" href="https://www.roblox.com/catalog/104818449553705" target="_blank" rel="noopener">
      👕 Compra la Maglietta
    </a>
  </div>

<!-- FOOTER -->
<footer>
  <p>© 2025 <span>Community di Koco</span> — Tutti i diritti riservati.</p>
</footer>

<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));

  // Hamburger menu
  const hamburger = document.getElementById('hamburger');
  const navLinks = document.getElementById('navLinks');
  hamburger.addEventListener('click', () => {
    navLinks.classList.toggle('open');
  });
  navLinks.querySelectorAll('a').forEach(a => {
    a.addEventListener('click', () => navLinks.classList.remove('open'));
  });
</script>

</body>
</html>
