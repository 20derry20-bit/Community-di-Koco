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
</section>
<section class="section" id="social">
  <div class="section-title reveal" style="text-align:center"><span class="accent">Tutti i link social</span> di Koco</div>
  <div class="divider reveal" style="margin-left:auto;margin-right:auto;"></div>
  <div class="social-grid reveal">

    <a class="btn-social btn-whatsapp" href="https://tr.ee/m9JUER9u6r" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      WhatsApp
    </a>

    <a class="btn-social btn-tiktok" href="https://tr.ee/q0cScySJSr" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.33 6.33 0 00-.79-.05 6.34 6.34 0 00-6.34 6.34 6.34 6.34 0 006.34 6.34 6.34 6.34 0 006.33-6.34V8.69a8.18 8.18 0 004.78 1.52V6.76a4.85 4.85 0 01-1.01-.07z"/></svg>
      TikTok
    </a>

    <a class="btn-social btn-instagram" href="https://tr.ee/sXTKG9rJoJ" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
      Instagram
    </a>

    <a class="btn-social btn-youtube" href="https://tr.ee/M3SrY-ALVN" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M23.498 6.186a3.016 3.016 0 00-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 00.502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 002.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 002.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
      YouTube
    </a>

    <a class="btn-social btn-spotify" href="https://tr.ee/7slcmrjjgT" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.66 0 12 0zm5.521 17.34c-.24.359-.66.48-1.021.24-2.82-1.74-6.36-2.101-10.561-1.141-.418.122-.779-.179-.899-.539-.12-.421.18-.78.54-.9 4.56-1.021 8.52-.6 11.64 1.32.42.18.479.659.301 1.02zm1.44-3.3c-.301.42-.841.6-1.262.3-3.239-1.98-8.159-2.58-11.939-1.38-.479.12-1.02-.12-1.14-.6-.12-.48.12-1.021.6-1.141C9.6 9.9 15 10.561 18.72 12.84c.361.181.54.78.241 1.2zm.12-3.36C15.24 8.4 8.82 8.16 5.16 9.301c-.6.179-1.2-.181-1.38-.721-.18-.601.18-1.2.72-1.381 4.26-1.26 11.28-1.02 15.721 1.621.539.3.719 1.02.419 1.56-.299.421-1.02.599-1.559.3z"/></svg>
      Spotify
    </a>

    <a class="btn-social btn-twitch" href="https://tr.ee/1cfWlSb_g9" target="_blank" rel="noopener">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M11.571 4.714h1.715v5.143H11.57zm4.715 0H18v5.143h-1.714zM6 0L1.714 4.286v15.428h5.143V24l4.286-4.286h3.428L22.286 12V0zm14.571 11.143l-3.428 3.428h-3.429l-3 3v-3H6.857V1.714h13.714z"/></svg>
      Twitch
    </a>
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
