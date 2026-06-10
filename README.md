<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BioByte | Bioinformatics · AI · Machine Learning</title>
  <meta name="description" content="A PhD student's journal on bioinformatics, machine learning, and AI — written for students and curious minds." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg:          #0B1120;
      --bg-surface:  #111827;
      --bg-card:     #151f32;
      --teal:        #00D4AA;
      --teal-dim:    #00a882;
      --lavender:    #C4B5FD;
      --lavender-dim:#a992f5;
      --offwhite:    #F0EEF8;
      --slate:       #8892A4;
      --border:      #1e2d47;
      --tag-bg:      #0d1e35;
      --font-display: 'Space Grotesk', sans-serif;
      --font-body:    'Inter', sans-serif;
      --font-mono:    'JetBrains Mono', monospace;
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: var(--font-body);
      background: var(--bg);
      color: var(--offwhite);
      line-height: 1.7;
      overflow-x: hidden;
    }
    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }

    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1rem 2.5rem;
      background: rgba(11, 17, 32, 0.85);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo { font-family: var(--font-display); font-size: 1.25rem; font-weight: 700; letter-spacing: -0.02em; }
    .nav-logo span { color: var(--teal); }
    .nav-links { display: flex; gap: 2rem; align-items: center; }
    .nav-links a { font-size: 0.875rem; font-weight: 500; color: var(--slate); transition: color 0.2s; }
    .nav-links a:hover { color: var(--offwhite); }
    .nav-cta { font-size: 0.8rem !important; font-weight: 600 !important; padding: 0.45rem 1.1rem; border: 1px solid var(--teal); border-radius: 6px; color: var(--teal) !important; transition: background 0.2s, color 0.2s !important; }
    .nav-cta:hover { background: var(--teal); color: var(--bg) !important; }
    .nav-burger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
    .nav-burger span { width: 22px; height: 2px; background: var(--offwhite); border-radius: 2px; }

    .hero {
      position: relative; min-height: 100vh;
      display: flex; flex-direction: column;
      justify-content: center; align-items: flex-start;
      padding: 8rem 2.5rem 4rem;
      overflow: hidden;
    }
    #hero-canvas { position: absolute; inset: 0; z-index: 0; opacity: 0.55; }
    .hero-content { position: relative; z-index: 1; max-width: 680px; }
    .hero-eyebrow {
      display: inline-flex; align-items: center; gap: 0.5rem;
      font-family: var(--font-mono); font-size: 0.75rem; letter-spacing: 0.12em; text-transform: uppercase;
      color: var(--teal); margin-bottom: 1.5rem;
    }
    .hero-eyebrow::before { content: ''; display: block; width: 32px; height: 1px; background: var(--teal); }
    .hero h1 {
      font-family: var(--font-display); font-size: clamp(2.6rem, 6vw, 4.4rem);
      font-weight: 700; line-height: 1.1; letter-spacing: -0.03em; margin-bottom: 1.5rem;
    }
    .hero h1 em {
      font-style: normal;
      background: linear-gradient(90deg, var(--teal), var(--lavender));
      -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    }
    .hero-desc { font-size: 1.05rem; color: var(--slate); max-width: 520px; margin-bottom: 2.5rem; }
    .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }
    .btn-primary {
      padding: 0.75rem 1.75rem; background: var(--teal); color: var(--bg);
      font-family: var(--font-display); font-weight: 600; font-size: 0.9rem;
      border-radius: 8px; border: none; cursor: pointer;
      transition: background 0.2s, transform 0.15s; display: inline-block;
    }
    .btn-primary:hover { background: #00f0c5; transform: translateY(-1px); }
    .btn-ghost {
      padding: 0.75rem 1.75rem; background: transparent; color: var(--offwhite);
      font-family: var(--font-display); font-weight: 500; font-size: 0.9rem;
      border-radius: 8px; border: 1px solid var(--border); cursor: pointer;
      transition: border-color 0.2s; display: inline-block;
    }
    .btn-ghost:hover { border-color: var(--lavender); color: var(--lavender); }
    .hero-scroll {
      position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
      z-index: 1; display: flex; flex-direction: column; align-items: center; gap: 0.4rem;
      font-size: 0.7rem; font-family: var(--font-mono); color: var(--slate);
      letter-spacing: 0.1em; text-transform: uppercase;
    }
    .scroll-line { width: 1px; height: 40px; background: linear-gradient(to bottom, var(--slate), transparent); animation: scrollPulse 2s ease-in-out infinite; }
    @keyframes scrollPulse { 0%, 100% { opacity: 0.3; } 50% { opacity: 1; } }

    .stats-bar {
      background: var(--bg-surface);
      border-top: 1px solid var(--border); border-bottom: 1px solid var(--border);
      padding: 1.75rem 2.5rem;
      display: flex; gap: 3rem; flex-wrap: wrap; justify-content: center;
    }
    .stat { text-align: center; }
    .stat-num { font-family: var(--font-display); font-size: 1.75rem; font-weight: 700; color: var(--teal); display: block; }
    .stat-label { font-size: 0.75rem; color: var(--slate); text-transform: uppercase; letter-spacing: 0.1em; }

    .section { padding: 5rem 2.5rem; max-width: 1100px; margin: 0 auto; }
    .section-header { margin-bottom: 3rem; }
    .section-eyebrow { font-family: var(--font-mono); font-size: 0.72rem; color: var(--teal); text-transform: uppercase; letter-spacing: 0.14em; margin-bottom: 0.75rem; }
    .section-title { font-family: var(--font-display); font-size: clamp(1.6rem, 3.5vw, 2.4rem); font-weight: 700; letter-spacing: -0.025em; }
    .section-title span { color: var(--lavender); }

    .featured-card {
      display: grid; grid-template-columns: 1fr 1fr; gap: 0;
      background: var(--bg-card); border: 1px solid var(--border);
      border-radius: 16px; overflow: hidden; margin-bottom: 2rem;
      transition: border-color 0.2s;
    }
    .featured-card:hover { border-color: var(--teal); }
    .featured-visual {
      background: linear-gradient(135deg, #0d1e35 0%, #0b2040 40%, #0d1530 100%);
      display: flex; align-items: center; justify-content: center;
      padding: 2rem; min-height: 300px; position: relative; overflow: hidden;
    }
    .featured-visual svg { width: 100%; max-width: 280px; opacity: 0.9; }
    .featured-body { padding: 2.5rem; display: flex; flex-direction: column; justify-content: center; }
    .post-meta {
      display: flex; align-items: center; gap: 0.75rem;
      font-family: var(--font-mono); font-size: 0.72rem; color: var(--slate); margin-bottom: 1.25rem;
    }
    .post-meta-dot { color: var(--border); }
    .featured-body h2 { font-family: var(--font-display); font-size: 1.5rem; font-weight: 600; letter-spacing: -0.02em; margin-bottom: 1rem; line-height: 1.3; }
    .featured-body p { color: var(--slate); font-size: 0.95rem; margin-bottom: 1.5rem; }
    .read-link { display: inline-flex; align-items: center; gap: 0.5rem; font-family: var(--font-display); font-weight: 600; font-size: 0.875rem; color: var(--teal); transition: gap 0.2s; }
    .read-link:hover { gap: 0.75rem; }

    .tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1rem; }
    .tag { font-family: var(--font-mono); font-size: 0.68rem; padding: 0.25rem 0.65rem; background: var(--tag-bg); border: 1px solid var(--border); border-radius: 4px; color: var(--slate); text-transform: uppercase; letter-spacing: 0.08em; }
    .tag.teal { color: var(--teal); border-color: rgba(0,212,170,0.3); background: rgba(0,212,170,0.07); }
    .tag.lavender { color: var(--lavender); border-color: rgba(196,181,253,0.3); background: rgba(196,181,253,0.07); }

    .post-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1.5rem; }
    .post-card {
      background: var(--bg-card); border: 1px solid var(--border); border-radius: 12px;
      padding: 1.75rem; display: flex; flex-direction: column;
      transition: border-color 0.2s, transform 0.2s;
    }
    .post-card:hover { border-color: var(--lavender); transform: translateY(-3px); }
    .post-card-icon { width: 48px; height: 48px; border-radius: 10px; background: var(--tag-bg); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-size: 1.4rem; margin-bottom: 1.25rem; }
    .post-card h3 { font-family: var(--font-display); font-size: 1.05rem; font-weight: 600; letter-spacing: -0.01em; margin-bottom: 0.6rem; line-height: 1.4; }
    .post-card p { color: var(--slate); font-size: 0.875rem; flex: 1; margin-bottom: 1.25rem; }
    .post-card .read-link { font-size: 0.8rem; }

    .topics-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 1rem; }
    .topic-card { padding: 1.5rem; border: 1px solid var(--border); border-radius: 12px; background: var(--bg-surface); text-align: center; transition: border-color 0.2s, background 0.2s; cursor: default; }
    .topic-card:hover { border-color: var(--teal); background: rgba(0,212,170,0.04); }
    .topic-icon { font-size: 2rem; margin-bottom: 0.75rem; }
    .topic-name { font-family: var(--font-display); font-weight: 600; font-size: 0.95rem; margin-bottom: 0.35rem; }
    .topic-count { font-size: 0.75rem; color: var(--slate); font-family: var(--font-mono); }

    .about-section { background: var(--bg-surface); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
    .about-inner { max-width: 1100px; margin: 0 auto; padding: 5rem 2.5rem; display: grid; grid-template-columns: auto 1fr; gap: 4rem; align-items: center; }
    .about-avatar {
      width: 160px; height: 160px; border-radius: 50%;
      background: linear-gradient(135deg, #0d2040, #1a0d40);
      border: 2px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 3.5rem; flex-shrink: 0; position: relative;
    }
    .about-avatar::after {
      content: ''; position: absolute; inset: -6px; border-radius: 50%;
      border: 1px solid transparent;
      background: linear-gradient(135deg, var(--teal), var(--lavender)) border-box;
      -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out; mask-composite: exclude;
    }
    .about-text .section-eyebrow { margin-bottom: 0.5rem; }
    .about-text h2 { font-family: var(--font-display); font-size: 2rem; font-weight: 700; letter-spacing: -0.025em; margin-bottom: 1rem; }
    .about-text p { color: var(--slate); font-size: 0.95rem; margin-bottom: 1rem; max-width: 560px; }
    .about-badges { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.5rem; }
    .badge { display: inline-flex; align-items: center; gap: 0.4rem; padding: 0.35rem 0.8rem; font-family: var(--font-mono); font-size: 0.72rem; background: var(--bg-card); border: 1px solid var(--border); border-radius: 100px; color: var(--offwhite); }
    .badge-dot { width: 6px; height: 6px; border-radius: 50%; }

    .newsletter-box {
      background: linear-gradient(135deg, #0d1e35 0%, #140d2a 100%);
      border: 1px solid var(--border); border-radius: 16px; padding: 3rem;
      text-align: center; max-width: 1100px; margin: 5rem auto 0;
    }
    .newsletter-box h2 { font-family: var(--font-display); font-size: 1.75rem; font-weight: 700; letter-spacing: -0.02em; margin-bottom: 0.75rem; }
    .newsletter-box p { color: var(--slate); margin-bottom: 2rem; font-size: 0.95rem; }
    .newsletter-form { display: flex; gap: 0.75rem; max-width: 460px; margin: 0 auto; flex-wrap: wrap; justify-content: center; }
    .newsletter-form input { flex: 1; min-width: 200px; padding: 0.7rem 1rem; background: var(--bg); border: 1px solid var(--border); border-radius: 8px; color: var(--offwhite); font-family: var(--font-body); font-size: 0.875rem; outline: none; transition: border-color 0.2s; }
    .newsletter-form input:focus { border-color: var(--teal); }
    .newsletter-form input::placeholder { color: var(--slate); }

    footer {
      background: var(--bg-surface); border-top: 1px solid var(--border);
      padding: 3rem 2.5rem; margin-top: 5rem;
      display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1.5rem;
    }
    .footer-logo { font-family: var(--font-display); font-weight: 700; font-size: 1.1rem; }
    .footer-logo span { color: var(--teal); }
    .footer-links { display: flex; gap: 1.5rem; flex-wrap: wrap; }
    .footer-links a { font-size: 0.85rem; color: var(--slate); transition: color 0.2s; }
    .footer-links a:hover { color: var(--offwhite); }
    .footer-copy { font-size: 0.78rem; color: var(--slate); font-family: var(--font-mono); }
    .full-divider { border: none; border-top: 1px solid var(--border); margin: 0; }

    @media (max-width: 768px) {
      nav { padding: 1rem 1.25rem; }
      .nav-links { display: none; flex-direction: column; position: absolute; top: 100%; left: 0; right: 0; background: var(--bg-surface); padding: 1.5rem; border-bottom: 1px solid var(--border); gap: 1.25rem; }
      .nav-links.open { display: flex; }
      .nav-burger { display: flex; }
      .hero { padding: 7rem 1.25rem 4rem; }
      .section { padding: 3.5rem 1.25rem; }
      .featured-card { grid-template-columns: 1fr; }
      .featured-visual { min-height: 200px; }
      .about-inner { grid-template-columns: 1fr; gap: 2rem; text-align: center; }
      .about-avatar { margin: 0 auto; }
      .about-badges { justify-content: center; }
      .newsletter-box { margin: 3.5rem 1.25rem 0; padding: 2rem 1.25rem; }
      footer { padding: 2rem 1.25rem; flex-direction: column; text-align: center; }
      .stats-bar { gap: 1.5rem; padding: 1.5rem 1.25rem; }
    }
  </style>
</head>
<body>

  <nav id="navbar">
    <div class="nav-logo">Bio<span>Byte</span></div>
    <div class="nav-links" id="nav-links">
      <a href="#posts">Posts</a>
      <a href="#topics">Topics</a>
      <a href="#about">About</a>
      <a href="https://github.com/YOUR-USERNAME" target="_blank" class="nav-cta">GitHub ↗</a>
    </div>
    <div class="nav-burger" id="burger" aria-label="Menu">
      <span></span><span></span><span></span>
    </div>
  </nav>

  <section class="hero">
    <canvas id="hero-canvas"></canvas>
    <div class="hero-content">
      <div class="hero-eyebrow">PhD · Bioinformatics · AI · ML</div>
      <h1>Where <em>biology</em> meets<br>machine intelligence</h1>
      <p class="hero-desc">
        A personal journal from a PhD student breaking down complex ideas in bioinformatics, machine learning, and AI — written so any curious mind can follow along.
      </p>
      <div class="hero-actions">
        <a href="#posts" class="btn-primary">Read the Blog</a>
        <a href="#about" class="btn-ghost">About Me</a>
      </div>
    </div>
    <div class="hero-scroll">
      <div class="scroll-line"></div>
      scroll
    </div>
  </section>

  <div class="stats-bar">
    <div class="stat"><span class="stat-num">24</span><span class="stat-label">Articles</span></div>
    <div class="stat"><span class="stat-num">3</span><span class="stat-label">Research Areas</span></div>
    <div class="stat"><span class="stat-num">PhD</span><span class="stat-label">In Progress</span></div>
    <div class="stat"><span class="stat-num">∞</span><span class="stat-label">Curiosity</span></div>
  </div>

  <div class="section" id="posts">
    <div class="section-header">
      <div class="section-eyebrow">// latest post</div>
      <h2 class="section-title">Featured <span>Article</span></h2>
    </div>
    <a href="#" class="featured-card">
      <div class="featured-visual">
        <svg viewBox="0 0 280 200" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g opacity="0.6">
            <circle cx="140" cy="100" r="12" fill="#00D4AA" opacity="0.8"/>
            <circle cx="80"  cy="60"  r="8"  fill="#C4B5FD" opacity="0.7"/>
            <circle cx="200" cy="60"  r="8"  fill="#C4B5FD" opacity="0.7"/>
            <circle cx="60"  cy="130" r="6"  fill="#00D4AA" opacity="0.5"/>
            <circle cx="220" cy="130" r="6"  fill="#00D4AA" opacity="0.5"/>
            <circle cx="110" cy="160" r="7"  fill="#C4B5FD" opacity="0.6"/>
            <circle cx="170" cy="160" r="7"  fill="#C4B5FD" opacity="0.6"/>
            <circle cx="40"  cy="90"  r="5"  fill="#8892A4" opacity="0.5"/>
            <circle cx="240" cy="90"  r="5"  fill="#8892A4" opacity="0.5"/>
            <line x1="140" y1="100" x2="80"  y2="60"  stroke="#00D4AA" stroke-width="1" opacity="0.5"/>
            <line x1="140" y1="100" x2="200" y2="60"  stroke="#00D4AA" stroke-width="1" opacity="0.5"/>
            <line x1="140" y1="100" x2="60"  y2="130" stroke="#C4B5FD" stroke-width="1" opacity="0.4"/>
            <line x1="140" y1="100" x2="220" y2="130" stroke="#C4B5FD" stroke-width="1" opacity="0.4"/>
            <line x1="140" y1="100" x2="110" y2="160" stroke="#00D4AA" stroke-width="1" opacity="0.4"/>
            <line x1="140" y1="100" x2="170" y2="160" stroke="#00D4AA" stroke-width="1" opacity="0.4"/>
            <line x1="80"  y1="60"  x2="40"  y2="90"  stroke="#C4B5FD" stroke-width="0.75" opacity="0.3"/>
            <line x1="200" y1="60"  x2="240" y2="90"  stroke="#C4B5FD" stroke-width="0.75" opacity="0.3"/>
            <line x1="60"  y1="130" x2="110" y2="160" stroke="#8892A4" stroke-width="0.75" opacity="0.3"/>
            <line x1="220" y1="130" x2="170" y2="160" stroke="#8892A4" stroke-width="0.75" opacity="0.3"/>
          </g>
          <path d="M 20 30 Q 70 10 120 30 Q 170 50 220 30 Q 250 15 270 30" stroke="#00D4AA" stroke-width="1.5" fill="none" opacity="0.4" stroke-dasharray="4 3"/>
          <path d="M 20 45 Q 70 65 120 45 Q 170 25 220 45 Q 250 60 270 45" stroke="#C4B5FD" stroke-width="1.5" fill="none" opacity="0.4" stroke-dasharray="4 3"/>
        </svg>
      </div>
      <div class="featured-body">
        <div class="tags">
          <span class="tag teal">Bioinformatics</span>
          <span class="tag lavender">Deep Learning</span>
        </div>
        <div class="post-meta">
          <span>June 2025</span><span class="post-meta-dot">·</span><span>8 min read</span>
        </div>
        <h2>Graph Neural Networks for Protein–Protein Interaction Prediction</h2>
        <p>Traditional approaches struggle with the complexity of molecular graphs. Here's how GNNs are reshaping our ability to model protein interactions — and why it matters for drug discovery.</p>
        <span class="read-link">Read Article <span>→</span></span>
      </div>
    </a>
  </div>

  <div class="section" style="padding-top: 0;">
    <div class="section-header">
      <div class="section-eyebrow">// recent writing</div>
      <h2 class="section-title">More <span>Posts</span></h2>
    </div>
    <div class="post-grid">

      <a href="#" class="post-card">
        <div class="post-card-icon">🧬</div>
        <div class="tags"><span class="tag teal">Genomics</span></div>
        <h3>Understanding Transformer Models in Genomic Sequence Analysis</h3>
        <p>BERT-based architectures aren't just for text — they're revolutionising how we read DNA. A beginner-friendly breakdown.</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>May 2025</span><span class="post-meta-dot">·</span><span>6 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

      <a href="#" class="post-card">
        <div class="post-card-icon">🤖</div>
        <div class="tags"><span class="tag lavender">ML Concepts</span></div>
        <h3>Attention Mechanisms Explained Without the Math Overload</h3>
        <p>A visual, intuition-first guide to the mechanism behind every major LLM — no linear algebra required to get the core idea.</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>Apr 2025</span><span class="post-meta-dot">·</span><span>7 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

      <a href="#" class="post-card">
        <div class="post-card-icon">🔬</div>
        <div class="tags"><span class="tag teal">Single-Cell</span></div>
        <h3>From Raw Counts to Cell Types: A scRNA-seq Pipeline Walkthrough</h3>
        <p>Single-cell RNA sequencing generates millions of data points. Here's how to go from raw data to meaningful biological clusters step by step.</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>Mar 2025</span><span class="post-meta-dot">·</span><span>10 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

      <a href="#" class="post-card">
        <div class="post-card-icon">📊</div>
        <div class="tags"><span class="tag lavender">Statistics</span></div>
        <h3>Why p-values Are Misunderstood (and What to Use Instead)</h3>
        <p>A frank look at statistical significance, effect sizes, and Bayesian alternatives — essential reading before you publish your first result.</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>Feb 2025</span><span class="post-meta-dot">·</span><span>5 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

      <a href="#" class="post-card">
        <div class="post-card-icon">⚗️</div>
        <div class="tags"><span class="tag teal">Drug Discovery</span></div>
        <h3>AI in Drug Discovery: Hype vs. Real Progress in 2025</h3>
        <p>AlphaFold changed protein structure prediction forever. But where are we really at when it comes to AI-designed therapeutics?</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>Jan 2025</span><span class="post-meta-dot">·</span><span>9 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

      <a href="#" class="post-card">
        <div class="post-card-icon">🧠</div>
        <div class="tags"><span class="tag lavender">PhD Life</span></div>
        <h3>How I Structure My Research Days as a Computational PhD Student</h3>
        <p>Balancing coding, reading papers, writing, and not going insane — practical systems that actually work from the trenches of grad school.</p>
        <div class="post-meta" style="margin-bottom:1rem;"><span>Dec 2024</span><span class="post-meta-dot">·</span><span>4 min</span></div>
        <span class="read-link">Read <span>→</span></span>
      </a>

    </div>
  </div>

  <hr class="full-divider" />

  <div class="section" id="topics">
    <div class="section-header">
      <div class="section-eyebrow">// explore by subject</div>
      <h2 class="section-title">Research <span>Topics</span></h2>
    </div>
    <div class="topics-grid">
      <div class="topic-card"><div class="topic-icon">🧬</div><div class="topic-name">Genomics & NGS</div><div class="topic-count">6 articles</div></div>
      <div class="topic-card"><div class="topic-icon">🤖</div><div class="topic-name">Machine Learning</div><div class="topic-count">8 articles</div></div>
      <div class="topic-card"><div class="topic-icon">🧠</div><div class="topic-name">Deep Learning</div><div class="topic-count">5 articles</div></div>
      <div class="topic-card"><div class="topic-icon">🔬</div><div class="topic-name">Single-Cell</div><div class="topic-count">3 articles</div></div>
      <div class="topic-card"><div class="topic-icon">⚗️</div><div class="topic-name">Drug Discovery</div><div class="topic-count">4 articles</div></div>
      <div class="topic-card"><div class="topic-icon">🎓</div><div class="topic-name">PhD Life</div><div class="topic-count">4 articles</div></div>
    </div>
  </div>

  <div class="about-section" id="about">
    <div class="about-inner">
      <div class="about-avatar">🧑‍🔬</div>
      <div class="about-text">
        <div class="section-eyebrow">// about the author</div>
        <h2>PhD Student &<br>Science Communicator</h2>
        <p>I'm a PhD student in computational biology, working at the intersection of machine learning and genomics. My research involves building predictive models for gene regulatory networks and protein interactions.</p>
        <p>This blog exists because I believe complex science should be accessible. Whether you're a fellow researcher, an ML practitioner curious about biology, or simply a curious human — you're welcome here.</p>
        <div class="about-badges">
          <span class="badge"><span class="badge-dot" style="background:#00D4AA"></span>Python · R · PyTorch</span>
          <span class="badge"><span class="badge-dot" style="background:#C4B5FD"></span>Bioinformatics</span>
          <span class="badge"><span class="badge-dot" style="background:#00D4AA"></span>Open Source</span>
          <span class="badge"><span class="badge-dot" style="background:#C4B5FD"></span>Science Comm</span>
        </div>
      </div>
    </div>
  </div>

  <div class="newsletter-box" style="padding: 3rem; margin: 5rem auto;">
    <h2>Stay in the loop 🧬</h2>
    <p>New post every week or two. No spam, no noise — just good science and code.</p>
    <div class="newsletter-form">
      <input type="email" placeholder="your@email.com" />
      <button class="btn-primary" type="button">Subscribe</button>
    </div>
  </div>

  <footer>
    <div class="footer-logo">Bio<span>Byte</span></div>
    <div class="footer-links">
      <a href="#posts">Blog</a>
      <a href="#topics">Topics</a>
      <a href="#about">About</a>
      <a href="https://github.com/YOUR-USERNAME" target="_blank">GitHub</a>
      <a href="https://twitter.com/YOUR-HANDLE" target="_blank">Twitter / X</a>
    </div>
    <div class="footer-copy">© 2025 BioByte · Built with curiosity</div>
  </footer>

  <script>
    const burger = document.getElementById('burger');
    const navLinks = document.getElementById('nav-links');
    burger.addEventListener('click', () => navLinks.classList.toggle('open'));

    const canvas = document.getElementById('hero-canvas');
    const ctx = canvas.getContext('2d');
    let W, H, nodes;

    function resize() {
      W = canvas.width  = canvas.offsetWidth;
      H = canvas.height = canvas.offsetHeight;
    }

    function initNodes() {
      nodes = Array.from({ length: 55 }, () => ({
        x: Math.random() * W,
        y: Math.random() * H,
        vx: (Math.random() - 0.5) * 0.35,
        vy: (Math.random() - 0.5) * 0.35,
        r: Math.random() * 2.5 + 1,
        color: Math.random() > 0.5 ? '#00D4AA' : '#C4B5FD',
      }));
    }

    function draw() {
      ctx.clearRect(0, 0, W, H);
      for (let i = 0; i < nodes.length; i++) {
        for (let j = i + 1; j < nodes.length; j++) {
          const dx = nodes[i].x - nodes[j].x;
          const dy = nodes[i].y - nodes[j].y;
          const dist = Math.sqrt(dx * dx + dy * dy);
          if (dist < 130) {
            ctx.beginPath();
            ctx.moveTo(nodes[i].x, nodes[i].y);
            ctx.lineTo(nodes[j].x, nodes[j].y);
            ctx.strokeStyle = `rgba(0,212,170,${0.25 * (1 - dist / 130)})`;
            ctx.lineWidth = 0.7;
            ctx.stroke();
          }
        }
      }
      nodes.forEach(n => {
        ctx.beginPath();
        ctx.arc(n.x, n.y, n.r, 0, Math.PI * 2);
        ctx.fillStyle = n.color;
        ctx.globalAlpha = 0.75;
        ctx.fill();
        ctx.globalAlpha = 1;
      });
    }

    function update() {
      nodes.forEach(n => {
        n.x += n.vx; n.y += n.vy;
        if (n.x < 0 || n.x > W) n.vx *= -1;
        if (n.y < 0 || n.y > H) n.vy *= -1;
      });
    }

    function loop() {
      update(); draw();
      requestAnimationFrame(loop);
    }

    const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)');
    resize(); initNodes();
    if (!prefersReduced.matches) loop(); else draw();
    window.addEventListener('resize', () => { resize(); if (prefersReduced.matches) draw(); });
  </script>
</body>
</html>
