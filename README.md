<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BioByte | Research & Insights</title>
  <style>
    :root {
      --bg: #ffffff;
      --card-bg: #f5f5f7;
      --text: #1d1d1f;
      --secondary: #86868b;
      --accent: #0066cc;
      --border: #d2d2d7;
    }
    
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.47059;
      letter-spacing: -0.022em;
    }

    /* Minimalist Navigation */
    nav {
      position: sticky; top: 0;
      background: rgba(255,255,255,0.8); backdrop-filter: blur(20px);
      padding: 0 2rem; height: 52px; display: flex; align-items: center; justify-content: space-between;
      border-bottom: 1px solid var(--border); z-index: 1000;
    }
    .logo { font-weight: 600; font-size: 14px; }
    .nav-links { display: flex; gap: 2rem; }
    .nav-links a { font-size: 12px; color: var(--text); text-decoration: none; opacity: 0.8; transition: opacity 0.2s; }
    .nav-links a:hover { opacity: 1; }

    /* Hero Section */
    .hero { text-align: center; padding: 120px 20px; }
    .hero h1 { font-size: 56px; font-weight: 600; letter-spacing: -0.005em; margin-bottom: 16px; }
    .hero p { font-size: 24px; color: var(--secondary); max-width: 600px; margin: 0 auto; font-weight: 400; }

    /* Card System */
    .section { max-width: 980px; margin: 0 auto; padding: 80px 20px; }
    .card-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
    
    .card {
      background: var(--card-bg);
      border-radius: 18px;
      padding: 40px;
      min-height: 400px;
      display: flex; flex-direction: column;
      justify-content: flex-end;
      text-decoration: none; color: inherit;
      transition: transform 0.5s cubic-bezier(0.25, 0.1, 0.25, 1), 
                  box-shadow 0.5s cubic-bezier(0.25, 0.1, 0.25, 1);
    }
    
    .card:hover {
      transform: scale(1.015);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.08);
    }

    .card h2 { font-size: 32px; margin-bottom: 8px; }
    .card p { font-size: 19px; color: var(--secondary); margin-bottom: 16px; }
    .cta { color: var(--accent); font-weight: 500; }

    footer { padding: 40px 20px; text-align: center; color: var(--secondary); font-size: 12px; }
  </style>
</head>
<body>

  <nav>
    <div class="logo">BioByte</div>
    <div class="nav-links">
      <a href="#">Research</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </div>
  </nav>

  <section class="hero">
    <h1>Exploring the code of life.</h1>
    <p>A PhD journal on the intersection of Bioinformatics, AI, and Machine Intelligence.</p>
  </section>

  <div class="section">
    <div class="card-grid">
      <a href="#" class="card">
        <h2>Graph Neural Networks</h2>
        <p>Redefining protein interaction modeling in 2026.</p>
        <span class="cta">Learn more ></span>
      </a>
      <a href="#" class="card">
        <h2>Genomic Transformers</h2>
        <p>How attention mechanisms are reading DNA.</p>
        <span class="cta">Read the paper ></span>
      </a>
    </div>
  </div>

  <footer>
    © 2026 BioByte Inc. All rights reserved.
  </footer>

</body>
</html>
