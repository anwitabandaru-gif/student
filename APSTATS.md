---
permalink: /apstats
---

<html lang="en">
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AP Statistics — Complete Study Guide</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Source+Serif+4:ital,wght@0,300;0,400;0,600;1,300;1,400&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0d1b2a;
    --navy2: #162032;
    --navy3: #1e2d40;
    --gold: #c9a84c;
    --gold2: #e8c96e;
    --cream: #f5f0e8;
    --cream2: #ede7d8;
    --red: #c0392b;
    --green: #1a6b3c;
    --blue: #1a4a7a;
    --text: #1a1a2e;
    --muted: #5a5a7a;
    --border: #d4c9a8;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Source Serif 4', Georgia, serif;
    background: var(--cream);
    color: var(--text);
    line-height: 1.7;
  }

  /* HEADER */
  header {
    background: var(--navy);
    padding: 0;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 20px rgba(0,0,0,0.4);
  }

  .header-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 32px;
  }

  .logo {
    font-family: 'Playfair Display', serif;
    color: var(--gold);
    font-size: 1.3rem;
    font-weight: 900;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  .logo span { color: #fff; }

  nav {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
  }

  nav a {
    color: var(--cream2);
    text-decoration: none;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    padding: 5px 10px;
    border-radius: 3px;
    border: 1px solid rgba(201,168,76,0.3);
    transition: all 0.2s;
    white-space: nowrap;
  }

  nav a:hover { background: var(--gold); color: var(--navy); border-color: var(--gold); }

  /* HERO */
  .hero {
    background: linear-gradient(135deg, var(--navy) 0%, var(--navy3) 60%, #1a2e4a 100%);
    padding: 72px 40px 64px;
    text-align: center;
    border-bottom: 3px solid var(--gold);
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      45deg,
      transparent,
      transparent 40px,
      rgba(201,168,76,0.03) 40px,
      rgba(201,168,76,0.03) 41px
    );
  }

  .hero-tag {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--gold);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    border: 1px solid var(--gold);
    padding: 4px 14px;
    border-radius: 2px;
    margin-bottom: 20px;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.4rem, 5vw, 4rem);
    font-weight: 900;
    color: #fff;
    line-height: 1.15;
    margin-bottom: 16px;
  }

  .hero h1 em {
    color: var(--gold);
    font-style: normal;
  }

  .hero p {
    color: rgba(245,240,232,0.75);
    font-size: 1.05rem;
    max-width: 560px;
    margin: 0 auto;
    font-weight: 300;
  }

  .unit-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-top: 28px;
  }

  .unit-pill {
    background: rgba(201,168,76,0.15);
    border: 1px solid rgba(201,168,76,0.4);
    color: var(--gold2);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    padding: 5px 12px;
    border-radius: 20px;
    letter-spacing: 0.05em;
  }

  /* LAYOUT */
  .container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 48px 32px;
  }

  /* UNIT SECTIONS */
  .unit {
    margin-bottom: 56px;
    border-radius: 6px;
    overflow: hidden;
    box-shadow: 0 2px 16px rgba(13,27,42,0.08);
    border: 1px solid var(--border);
    background: #fff;
  }

  .unit-header {
    background: var(--navy);
    padding: 24px 32px;
    display: flex;
    align-items: center;
    gap: 20px;
    cursor: pointer;
    user-select: none;
  }

  .unit-header:hover { background: var(--navy3); }

  .unit-number {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    color: var(--gold);
    background: rgba(201,168,76,0.15);
    border: 1px solid rgba(201,168,76,0.4);
    padding: 3px 10px;
    border-radius: 2px;
    letter-spacing: 0.1em;
    white-space: nowrap;
  }

  .unit-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: #fff;
    flex: 1;
  }

  .unit-toggle {
    color: var(--gold);
    font-size: 1.2rem;
    transition: transform 0.3s;
  }

  .unit-body { padding: 32px; }

  /* TOPIC CARDS */
  .topic {
    margin-bottom: 32px;
    padding-bottom: 32px;
    border-bottom: 1px solid var(--cream2);
  }

  .topic:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }

  .topic-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.15rem;
    font-weight: 700;
    color: var(--navy);
    margin-bottom: 14px;
    padding-bottom: 8px;
    border-bottom: 2px solid var(--gold);
    display: inline-block;
  }

  .topic-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 16px;
  }

  @media (max-width: 720px) {
    .topic-grid { grid-template-columns: 1fr; }
    nav { display: none; }
  }

  .card {
    background: var(--cream);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 18px 20px;
  }

  .card-full { grid-column: 1 / -1; }

  .card h4 {
    font-family: 'Playfair Display', serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--navy);
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  .card p, .card li {
    font-size: 0.88rem;
    line-height: 1.7;
    color: #2a2a3e !important;
  }

  .card ul { padding-left: 18px; }
  .card ul li { margin-bottom: 5px; }

  /* TERM DEFINITIONS */
  .def-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 12px;
    margin-top: 14px;
  }

  .def-item {
    background: var(--navy);
    border-radius: 4px;
    padding: 14px 16px;
  }

  .def-term {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--gold);
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    display: block;
    margin-bottom: 6px;
  }

  .def-desc {
    font-size: 0.83rem;
    color: rgba(245,240,232,0.85);
    line-height: 1.55;
  }

  /* FORMULA BOXES */
  .formula-box {
    background: var(--navy);
    border-left: 4px solid var(--gold);
    border-radius: 0 4px 4px 0;
    padding: 18px 22px;
    margin: 14px 0;
  }

  .formula-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    color: var(--gold);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 8px;
    display: block;
  }

  .formula {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.9rem;
    color: #fff;
    line-height: 1.8;
  }

  .formula em {
    color: var(--gold2);
    font-style: normal;
  }

  /* CONDITIONS BOX */
  .conditions {
    background: #eef7f0;
    border: 1px solid #b8d9c4;
    border-left: 4px solid var(--green);
    border-radius: 0 4px 4px 0;
    padding: 16px 20px;
    margin: 14px 0;
  }

  .conditions h5 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--green);
    margin-bottom: 8px;
  }

  .conditions ul { padding-left: 16px; }

  .conditions li {
    font-size: 0.86rem;
    line-height: 1.6;
    color: #1a3a2a;
    margin-bottom: 4px;
  }

  /* ALERT / WARNING */
  .alert {
    background: #fdf2f0;
    border: 1px solid #f0c0b8;
    border-left: 4px solid var(--red);
    border-radius: 0 4px 4px 0;
    padding: 14px 18px;
    margin: 12px 0;
  }

  .alert h5 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 6px;
  }

  .alert p { font-size: 0.86rem; color: #5a1a14; line-height: 1.6; }

  /* INFO BOX */
  .info {
    background: #eef4fb;
    border: 1px solid #b8cfe8;
    border-left: 4px solid var(--blue);
    border-radius: 0 4px 4px 0;
    padding: 14px 18px;
    margin: 12px 0;
  }

  .info h5 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--blue);
    margin-bottom: 6px;
  }

  .info p, .info li { font-size: 0.86rem; color: #0d2a4a; line-height: 1.6; }

  /* CALCULATOR SECTION */
  .calc-section {
    background: #1a1a2e;
    border: 1px solid #333355;
    border-radius: 6px;
    padding: 20px 24px;
    margin-top: 20px;
  }

  .calc-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 16px;
    padding-bottom: 12px;
    border-bottom: 1px solid #333355;
  }

  .calc-badge {
    background: var(--gold);
    color: var(--navy);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    padding: 3px 10px;
    border-radius: 2px;
    text-transform: uppercase;
  }

  .calc-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.85rem;
    color: rgba(255,255,255,0.8);
  }

  .calc-steps {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .calc-step {
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }

  .step-num {
    background: rgba(201,168,76,0.2);
    color: var(--gold);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    font-weight: 700;
    min-width: 22px;
    height: 22px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 2px;
    flex-shrink: 0;
  }

  .step-text {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: rgba(245,240,232,0.8);
    line-height: 1.55;
  }

  .step-text .menu-path {
    color: var(--gold2);
  }

  /* TABLE */
  .stats-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 14px;
    font-size: 0.84rem;
  }

  .stats-table th {
    background: var(--navy);
    color: var(--gold);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    padding: 10px 14px;
    text-align: left;
  }

  .stats-table td {
    padding: 9px 14px;
    border-bottom: 1px solid var(--cream2);
    vertical-align: top;
  }

  .stats-table tr:nth-child(even) td { background: var(--cream); }

  /* FOUR-STEP */
  .four-step {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin: 14px 0;
  }

  @media (max-width: 600px) {
    .four-step { grid-template-columns: 1fr 1fr; }
  }

  .step-card {
    background: var(--navy);
    border-radius: 4px;
    padding: 14px;
    text-align: center;
  }

  .step-letter {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    color: var(--gold);
    display: block;
    line-height: 1;
    margin-bottom: 6px;
  }

  .step-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.62rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(245,240,232,0.7);
    display: block;
    margin-bottom: 8px;
  }

  .step-desc {
    font-size: 0.78rem;
    color: rgba(245,240,232,0.85);
    line-height: 1.5;
  }

  /* TOC */
  .toc {
    background: var(--navy);
    border-radius: 6px;
    padding: 28px 32px;
    margin-bottom: 48px;
  }

  .toc-title {
    font-family: 'Playfair Display', serif;
    color: var(--gold);
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .toc-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
  }

  .toc-link {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    padding: 10px 14px;
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 4px;
    transition: all 0.2s;
  }

  .toc-link:hover {
    background: rgba(201,168,76,0.1);
    border-color: rgba(201,168,76,0.5);
  }

  .toc-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.62rem;
    color: var(--gold);
    background: rgba(201,168,76,0.15);
    padding: 2px 7px;
    border-radius: 2px;
    white-space: nowrap;
  }

  .toc-name {
    font-size: 0.82rem;
    color: rgba(245,240,232,0.85);
    line-height: 1.3;
  }

  /* BACK TO TOP */
  #back-top {
    position: fixed;
    bottom: 28px;
    right: 28px;
    background: var(--gold);
    color: var(--navy);
    border: none;
    width: 42px;
    height: 42px;
    border-radius: 50%;
    font-size: 1.1rem;
    cursor: pointer;
    box-shadow: 0 4px 16px rgba(0,0,0,0.25);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    font-weight: 700;
  }

  #back-top:hover { background: var(--gold2); transform: translateY(-2px); }

  .section-divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 24px 0;
  }

  .two-col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-top: 14px;
  }

  @media (max-width: 700px) { .two-col { grid-template-columns: 1fr; } }

  strong { color: var(--navy); }

  .tag {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.62rem;
    padding: 2px 8px;
    border-radius: 2px;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-right: 4px;
    vertical-align: middle;
  }

  .tag-z { background: #dceeff; color: #1a4a7a; }
  .tag-t { background: #fff0d4; color: #7a4a00; }
  .tag-chi { background: #ffe8f0; color: #7a001a; }
  .tag-prop { background: #e8ffe8; color: #006620; }
  .tag-mean { background: #f0e8ff; color: #440077; }
</style>



<header>
  <div class="header-inner">
    <div class="logo">AP <span>Statistics</span></div>
    <nav>
      <a href="#u1">Unit 1</a>
      <a href="#u2">Unit 2</a>
      <a href="#u3">Unit 3</a>
      <a href="#u4">Unit 4</a>
      <a href="#u5">Unit 5</a>
      <a href="#u6">Unit 6</a>
      <a href="#u7">Unit 7</a>
      <a href="#u8">Unit 8</a>
    </nav>
  </div>
</header>

<div class="hero">
  <div class="hero-tag">Complete Study Guide</div>
  <h1>AP <em>Statistics</em><br>Master Reference</h1>
  <p>Every concept, formula, condition, and TI-nspire CX calculator step — all 8 units in one place.</p>
  <div class="unit-pills">
    <span class="unit-pill">Unit 1 · Descriptive Statistics</span>
    <span class="unit-pill">Unit 2 · Study Design</span>
    <span class="unit-pill">Unit 3 · Probability</span>
    <span class="unit-pill">Unit 4 · Sampling Distributions</span>
    <span class="unit-pill">Unit 5 · Confidence Intervals</span>
    <span class="unit-pill">Unit 6 · Significance Tests</span>
    <span class="unit-pill">Unit 7 · Chi-Square</span>
    <span class="unit-pill">Unit 8 · Linear Regression</span>
  </div>
</div>

<div class="container">

  <!-- TOC -->
  <div class="toc">
    <div class="toc-title">📋 Table of Contents</div>
    <div class="toc-grid">
      <a class="toc-link" href="#u1"><span class="toc-num">U1</span><span class="toc-name">Descriptive Statistics</span></a>
      <a class="toc-link" href="#u2"><span class="toc-num">U2</span><span class="toc-name">Study Design</span></a>
      <a class="toc-link" href="#u3"><span class="toc-num">U3</span><span class="toc-name">Probability</span></a>
      <a class="toc-link" href="#u4"><span class="toc-num">U4</span><span class="toc-name">Sampling Distributions</span></a>
      <a class="toc-link" href="#u5"><span class="toc-num">U5</span><span class="toc-name">Confidence Intervals</span></a>
      <a class="toc-link" href="#u6a"><span class="toc-num">U6a</span><span class="toc-name">Significance Tests</span></a>
      <a class="toc-link" href="#u6b"><span class="toc-num">U6b</span><span class="toc-name">Two-Population Inference</span></a>
      <a class="toc-link" href="#u7"><span class="toc-num">U7</span><span class="toc-name">Chi-Square</span></a>
      <a class="toc-link" href="#u8"><span class="toc-num">U8</span><span class="toc-name">Linear Regression</span></a>
    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 1 ═══════════════════════════════ -->
  <div class="unit" id="u1">
    <div class="unit-header">
      <span class="unit-number">UNIT 1</span>
      <div class="unit-title">Descriptive Statistics</div>
    </div>
    <div class="unit-body">

      <!-- Introduction -->
      <div class="topic">
        <div class="topic-title">Introduction: Key Vocabulary</div>
        <div class="def-grid">
          <div class="def-item"><span class="def-term">Statistics</span><span class="def-desc">The science and art of collecting, analyzing, and drawing conclusions from data.</span></div>
          <div class="def-item"><span class="def-term">Individual</span><span class="def-desc">Each person, animal, or thing in a dataset.</span></div>
          <div class="def-item"><span class="def-term">Variable</span><span class="def-desc">A characteristic that takes different values for different individuals.</span></div>
          <div class="def-item"><span class="def-term">Categorical Variable</span><span class="def-desc">Places each individual into a group or category (e.g., gender, color).</span></div>
          <div class="def-item"><span class="def-term">Quantitative Variable</span><span class="def-desc">Takes numerical values that measure or count something (e.g., height, count of siblings).</span></div>
          <div class="def-item"><span class="def-term">Distribution</span><span class="def-desc">Describes what values a variable takes and how often it takes them.</span></div>
        </div>
      </div>

      <!-- Categorical Data -->
      <div class="topic">
        <div class="topic-title">Analyzing Categorical Data</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Displays</h4>
            <ul>
              <li><strong>Pie chart</strong> – shows proportion of whole for each category</li>
              <li><strong>Bar graph</strong> – compares frequencies or relative frequencies across categories</li>
              <li><strong>Side-by-side bar graph</strong> – compares distributions across two+ groups</li>
              <li><strong>Segmented bar graph</strong> – stacked to show proportion within groups</li>
            </ul>
            <div class="alert">
              <h5>⚠ Misleading Graphs</h5>
              <p>Beware of graphs with distorted scales. Never replace bar widths AND heights with pictures simultaneously.</p>
            </div>
          </div>
          <div class="card">
            <h4>Two-Way Tables — Three Types of Relative Frequency</h4>
            <ul>
              <li><strong>Marginal relative frequency</strong> – proportion in one variable (use row/column total ÷ table total)</li>
              <li><strong>Joint relative frequency</strong> – proportion with a specific value for both variables (cell ÷ table total)</li>
              <li><strong>Conditional relative frequency</strong> – proportion of one variable given a specific value of another (cell ÷ row or column total)</li>
            </ul>
            <div class="info">
              <h5>Association</h5>
              <p>Two variables are associated if knowing the value of one helps predict the other. Check using conditional relative frequencies — if the distributions differ across groups, an association exists.</p>
            </div>
          </div>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Bar Chart from Data List</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">Enter data in <span class="menu-path">Lists & Spreadsheet</span>. Name the column in the formula row (use 'name' for categorical).</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text"><span class="menu-path">Menu → Data → Quick Graph</span></span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text"><span class="menu-path">Menu → Plot Properties → Force Categorical X</span></span></div>
            <div class="calc-step"><span class="step-num">4</span><span class="step-text">Right-click in graph → <span class="menu-path">Bar Chart</span>. Trace over bars for details.</span></div>
          </div>
        </div>
      </div>

      <!-- Quantitative Data -->
      <div class="topic">
        <div class="topic-title">Analyzing Quantitative Data</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Graphical Displays</h4>
            <ul>
              <li><strong>Dotplot</strong> – displays individual values on a number line</li>
              <li><strong>Stemplot (stem-and-leaf)</strong> – separates each value into stem and one-digit leaf</li>
              <li><strong>Histogram</strong> – plots frequency or relative frequency in equal-width intervals</li>
              <li><strong>Boxplot</strong> – based on five-number summary; shows outliers with special symbols</li>
            </ul>
            <div class="alert">
              <h5>⚠ Remember</h5>
              <p>Histograms → quantitative data. Bar graphs → categorical data. Use relative frequencies when comparing datasets of different sizes.</p>
            </div>
          </div>
          <div class="card">
            <h4>SOCS — Describing Distributions</h4>
            <p>When describing any distribution of quantitative data, always address:</p>
            <br>
            <ul>
              <li><strong>Shape</strong> – symmetric, skewed left, skewed right; unimodal, bimodal; clusters/gaps</li>
              <li><strong>Outliers</strong> – observations that fall outside the overall pattern</li>
              <li><strong>Center</strong> – mean or median (typical value)</li>
              <li><strong>Spread (Variability)</strong> – range, IQR, or standard deviation</li>
            </ul>
            <div class="info">
              <h5>Comparing Distributions</h5>
              <p>Always compare Shape, Outliers, Center, and Spread — in context.</p>
            </div>
          </div>
        </div>

        <div class="topic-grid" style="margin-top:16px">
          <div class="card">
            <h4>Measures of Center</h4>
            <div class="formula-box">
              <span class="formula-label">Mean</span>
              <div class="formula">x̄ = (Σxᵢ) / n</div>
            </div>
            <p><strong>Median</strong> — the midpoint; half of observations are below, half above. Order all values and find the middle.</p>
            <div class="info">
              <h5>Resistance</h5>
              <p>The <strong>median is resistant</strong> to outliers and skewness. The <strong>mean is not resistant</strong> — it is pulled toward extreme values. Use mean + SD for symmetric distributions; median + IQR for skewed distributions.</p>
            </div>
          </div>
          <div class="card">
            <h4>Measures of Variability (Spread)</h4>
            <div class="formula-box">
              <span class="formula-label">Standard Deviation</span>
              <div class="formula">sₓ = √[Σ(xᵢ − x̄)² / (n−1)]</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">IQR (Interquartile Range)</span>
              <div class="formula">IQR = Q₃ − Q₁</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">1.5 × IQR Outlier Rule</span>
              <div class="formula">Outlier if: x &lt; Q₁ − 1.5·IQR<br>or: x &gt; Q₃ + 1.5·IQR</div>
            </div>
            <p style="font-size:0.84rem; margin-top:8px">IQR is resistant to outliers; standard deviation and range are NOT.</p>
          </div>
        </div>

        <div class="card card-full" style="margin-top:16px">
          <h4>Five-Number Summary & Boxplots</h4>
          <p>The five-number summary consists of: <strong>Minimum, Q₁, Median, Q₃, Maximum.</strong></p>
          <p style="margin-top:8px">A <strong>boxplot</strong> shows the box (from Q₁ to Q₃), median marked inside, and whiskers extending to the smallest/largest non-outlier values. Outliers are marked with a dot or asterisk. Boxplots are especially useful for comparing distributions side by side.</p>
        </div>

        <div class="calc-section" style="margin-top:16px">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Histogram, Boxplot & Summary Statistics</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">Enter data in named list (Lists & Spreadsheet). <span class="menu-path">Menu → Data → Quick Graph</span></span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Right-click → <span class="menu-path">Histogram</span> or <span class="menu-path">Box Plot</span>. Adjust bin width by dragging a bar.</span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text">For multiple boxplots: <span class="menu-path">Home → Add Data & Statistics</span>. Click to add x-variable, then right-click → Box Plot. Add another variable for comparison.</span></div>
            <div class="calc-step"><span class="step-num">4</span><span class="step-text">Summary stats: <span class="menu-path">Menu → Statistics → Stat Calculations → One-Variable Statistics</span>. Choose the list. Scroll for mean, sx, Q1, median, Q3, min, max.</span></div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 2 ═══════════════════════════════ -->
  <div class="unit" id="u2">
    <div class="unit-header">
      <span class="unit-number">UNIT 2</span>
      <div class="unit-title">Study Design</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Sampling & Surveys</div>
        <div class="def-grid">
          <div class="def-item"><span class="def-term">Census</span><span class="def-desc">Collects data from every individual in the population.</span></div>
          <div class="def-item"><span class="def-term">Sample Survey</span><span class="def-desc">Selects a sample to draw conclusions about the whole population.</span></div>
          <div class="def-item"><span class="def-term">SRS</span><span class="def-desc">Simple Random Sample — every possible sample of size n has equal probability of selection.</span></div>
          <div class="def-item"><span class="def-term">Stratified Random Sample</span><span class="def-desc">Divide population into strata (similar within), take SRS from each stratum. More precise than SRS when strata are homogeneous.</span></div>
          <div class="def-item"><span class="def-term">Cluster Sample</span><span class="def-desc">Divide into clusters (similar between), randomly select whole clusters. Saves time and money.</span></div>
          <div class="def-item"><span class="def-term">Convenience Sampling</span><span class="def-desc">Chooses easiest-to-reach individuals — leads to bias.</span></div>
          <div class="def-item"><span class="def-term">Voluntary Response</span><span class="def-desc">Individuals choose to respond — leads to bias (strong opinions over-represented).</span></div>
          <div class="def-item"><span class="def-term">Undercoverage</span><span class="def-desc">Some members of population are less likely/unable to be chosen.</span></div>
          <div class="def-item"><span class="def-term">Nonresponse</span><span class="def-desc">Selected individuals can't be contacted or refuse to answer — biggest problem in surveys.</span></div>
          <div class="def-item"><span class="def-term">Response Bias</span><span class="def-desc">Untruthful answers, poorly worded questions, interviewer effects.</span></div>
        </div>

        <!-- ── BIAS DEEP DIVE ── -->
        <div class="topic" style="margin-top:28px; padding-top:28px; border-top:1px solid var(--cream2)">
          <div class="topic-title">Types of Bias — Complete Breakdown</div>
          <p style="font-size:0.88rem; margin-bottom:16px; color:var(--muted)"><strong>Bias</strong> is a systematic tendency to over- or underestimate the true population value. Unlike random sampling variability, bias does NOT decrease when you increase sample size — you must fix the design.</p>

          <div class="topic-grid">
            <div class="card">
              <h4>Selection Bias (Sampling Bias)</h4>
              <p>The method of choosing the sample systematically favors certain individuals, so the sample is not representative of the population.</p>
              <br>
              <ul>
                <li><strong>Convenience sampling bias</strong> — only easy-to-reach individuals are selected (e.g., surveying friends, people at a mall). Overrepresents accessible groups.</li>
                <li><strong>Voluntary response bias</strong> — individuals self-select into the sample. People with extreme opinions are far more likely to respond, skewing results.</li>
                <li><strong>Undercoverage bias</strong> — some members of the population have a lower probability of being chosen (e.g., phone surveys miss people without phones). A subgroup is systematically excluded.</li>
              </ul>
              <div class="alert" style="margin-top:10px">
                <h5>⚠ Fix</h5>
                <p>Use a proper random sampling method (SRS, stratified, or cluster) so every member has a known, nonzero chance of selection.</p>
              </div>
            </div>

            <div class="card">
              <h4>Nonresponse Bias</h4>
              <p>Occurs <em>after</em> the sample is selected, when individuals who are chosen cannot be contacted or refuse to participate.</p>
              <br>
              <p>This is considered the <strong>single biggest problem</strong> in sample surveys. If nonrespondents differ systematically from respondents (e.g., busy high-earners refusing phone surveys), the results will be biased.</p>
              <br>
              <p><strong>Example:</strong> A political poll mails 1,000 surveys but only 200 respond — if enthusiastic supporters respond more than moderates, results skew toward one side.</p>
              <div class="alert" style="margin-top:10px">
                <h5>⚠ Fix</h5>
                <p>Follow up with nonrespondents; use multiple contact methods; keep surveys short and easy to complete.</p>
              </div>
            </div>

            <div class="card">
              <h4>Response Bias</h4>
              <p>Occurs when respondents give inaccurate or untruthful answers, regardless of how they were selected. The measurement process itself is flawed.</p>
              <br>
              <ul>
                <li><strong>Wording/question order bias</strong> — loaded, leading, or ambiguous question wording pushes respondents toward a particular answer ("Don't you agree that…?")</li>
                <li><strong>Social desirability bias</strong> — respondents give answers they think are socially acceptable rather than truthful (e.g., underreporting drug use, overstating exercise)</li>
                <li><strong>Interviewer bias</strong> — the interviewer's appearance, tone, or perceived expectations influence answers</li>
                <li><strong>Recall bias</strong> — respondents can't accurately remember past events or behaviors</li>
                <li><strong>Acquiescence bias</strong> — tendency to agree with statements regardless of their content</li>
              </ul>
              <div class="alert" style="margin-top:10px">
                <h5>⚠ Fix</h5>
                <p>Use neutral, clear, specific wording. Use anonymous surveys for sensitive topics. Pilot-test questions before full deployment.</p>
              </div>
            </div>

            <div class="card">
              <h4>Other Important Bias Types</h4>
              <ul>
                <li><strong>Confounding bias</strong> — a lurking variable is associated with both the explanatory and response variable, making it impossible to determine true cause and effect. Common in observational studies.</li>
                <li><strong>Placebo effect bias</strong> — subjects respond differently simply because they believe they are receiving treatment. Controlled with a blind or double-blind design.</li>
                <li><strong>Measurement/instrument bias</strong> — a faulty measurement tool or process systematically records incorrect values (e.g., a scale that reads 2 lbs heavy for everyone).</li>
                <li><strong>Publication bias</strong> — studies with statistically significant results are more likely to be published, creating a skewed picture of the evidence base.</li>
              </ul>
            </div>
          </div>

          <!-- Master Bias Comparison Table -->
          <table class="stats-table" style="margin-top:20px">
            <thead>
              <tr>
                <th>Bias Type</th>
                <th>When It Occurs</th>
                <th>Direction of Error</th>
                <th>How to Prevent</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>Convenience Sampling</strong></td>
                <td>Sample selection</td>
                <td>Unpredictable — depends on who is convenient</td>
                <td>Use random selection method</td>
              </tr>
              <tr>
                <td><strong>Voluntary Response</strong></td>
                <td>Sample selection</td>
                <td>Usually overestimates extreme opinions</td>
                <td>Use random selection; don't rely on self-selection</td>
              </tr>
              <tr>
                <td><strong>Undercoverage</strong></td>
                <td>Sample selection</td>
                <td>Depends on excluded group's characteristics</td>
                <td>Ensure complete sampling frame; use stratification</td>
              </tr>
              <tr>
                <td><strong>Nonresponse</strong></td>
                <td>After sample chosen</td>
                <td>Depends on how nonrespondents differ from respondents</td>
                <td>Follow-up contacts; incentives; short surveys</td>
              </tr>
              <tr>
                <td><strong>Response / Wording</strong></td>
                <td>Data collection</td>
                <td>Usually toward the "expected" or socially acceptable answer</td>
                <td>Neutral phrasing; anonymous surveys; pilot testing</td>
              </tr>
              <tr>
                <td><strong>Confounding</strong></td>
                <td>Study design</td>
                <td>Can inflate or hide a real effect</td>
                <td>Use experiments with random assignment; control variables</td>
              </tr>
            </tbody>
          </table>

          <div class="info" style="margin-top:16px">
            <h5>Key Principle: Bias vs. Variability</h5>
            <p><strong>Bias</strong> = consistent, systematic error in one direction. Increasing sample size does <em>not</em> fix bias — you must fix the design. <strong>Variability</strong> = random scatter around the true value. Increasing sample size <em>does</em> reduce variability. A large biased survey is still biased. A small well-designed random sample can be more trustworthy.</p>
          </div>
        </div>

        <div class="calc-section" style="margin-top:16px">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Generating Random Numbers & Samples</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">Single random number: <span class="menu-path">Home → Add Calculator → Menu → Statistics → Random → Number</span>. Press Enter repeatedly for new values.</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">List of random integers: <span class="menu-path">Home → Add Lists & Spreadsheet</span>. Name list, then type <span class="menu-path">=randint(low, high, #trials)</span> in the formula row.</span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text">Random sample from existing list: In the next list's formula cell, type <span class="menu-path">=randsamp(listname, #trials)</span>.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Experiments</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Key Vocabulary</h4>
            <ul>
              <li><strong>Observational study</strong> – gathers data without intervening; cannot show cause-and-effect</li>
              <li><strong>Experiment</strong> – imposes treatments; can establish causation</li>
              <li><strong>Explanatory variable</strong> – the variable that may cause a change (factor)</li>
              <li><strong>Response variable</strong> – the outcome measured</li>
              <li><strong>Confounding</strong> – two variables' effects on the response variable can't be separated</li>
              <li><strong>Experimental units / Subjects</strong> – the individuals in the experiment</li>
              <li><strong>Treatment</strong> – a specific combination of factor levels</li>
              <li><strong>Placebo / Control group</strong> – receives fake treatment; controls for placebo effect</li>
              <li><strong>Double-blind</strong> – neither subjects nor those measuring know who got which treatment</li>
              <li><strong>Single-blind</strong> – only one group knows</li>
            </ul>
          </div>
          <div class="card">
            <h4>Principles of Experimental Design</h4>
            <ul>
              <li><strong>Comparison</strong> – use two or more treatments</li>
              <li><strong>Random assignment</strong> – use chance to assign units to treatments; creates roughly equivalent groups</li>
              <li><strong>Control</strong> – keep other variables the same for all groups; reduces confounding</li>
              <li><strong>Replication</strong> – impose each treatment on enough units to distinguish treatment effects from chance</li>
            </ul>
            <hr class="section-divider">
            <p><strong>Completely randomized design:</strong> All units assigned to treatments by chance alone.</p>
            <p style="margin-top:8px"><strong>Randomized block design:</strong> Group similar units into blocks, then randomly assign within blocks. Reduces variability.</p>
            <p style="margin-top:8px"><strong>Matched pairs design:</strong> Special block design where each subject receives both treatments (in random order), OR pairs of similar subjects are used.</p>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Using Studies Wisely</div>
        <div class="two-col">
          <div class="card">
            <h4>Sampling Variability & Significance</h4>
            <ul>
              <li><strong>Sampling variability</strong> – different random samples give different estimates; reduce by increasing n</li>
              <li><strong>Statistically significant</strong> – observed results are too unusual to be explained by chance alone</li>
            </ul>
          </div>
          <div class="card">
            <h4>Scope of Inference</h4>
            <ul>
              <li><strong>Random selection</strong> → can generalize to the population</li>
              <li><strong>Random assignment</strong> → can infer cause-and-effect</li>
              <li>Causation without experiment requires: strong consistent association, clear explanation, ruling out lurking variables</li>
            </ul>
          </div>
        </div>
        <div class="info" style="margin-top:14px">
          <h5>Ethics</h5>
          <p>Studies involving humans require <strong>institutional review board</strong> approval. All participants must give <strong>informed consent</strong>. Data must be kept <strong>confidential</strong>.</p>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 3 ═══════════════════════════════ -->
  <div class="unit" id="u3">
    <div class="unit-header">
      <span class="unit-number">UNIT 3</span>
      <div class="unit-title">Probability & Random Variables</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Probability Fundamentals</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Core Rules</h4>
            <p><strong>Probability</strong> — long-run relative frequency; always between 0 and 1.</p>
            <p style="margin-top:8px"><strong>Law of Large Numbers:</strong> In many repetitions, the proportion of times an outcome occurs approaches its probability.</p>
            <div class="formula-box">
              <span class="formula-label">Equally likely outcomes</span>
              <div class="formula">P(A) = (# outcomes in A) / (total # outcomes)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Complement Rule</span>
              <div class="formula">P(Aᶜ) = 1 − P(A)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">General Addition Rule</span>
              <div class="formula">P(A ∪ B) = P(A) + P(B) − P(A ∩ B)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Mutually Exclusive Events</span>
              <div class="formula">P(A or B) = P(A) + P(B)</div>
            </div>
          </div>
          <div class="card">
            <h4>Conditional Probability & Independence</h4>
            <div class="formula-box">
              <span class="formula-label">Conditional Probability</span>
              <div class="formula">P(A|B) = P(A ∩ B) / P(B)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">General Multiplication Rule</span>
              <div class="formula">P(A ∩ B) = P(A) · P(B|A)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Independent Events</span>
              <div class="formula">P(A|B) = P(A)  [or P(B|A) = P(B)]<br>P(A ∩ B) = P(A) · P(B)</div>
            </div>
            <div class="info">
              <h5>Tools for Probability</h5>
              <p><strong>Two-way table</strong> and <strong>Venn diagram</strong> — display sample space for two events.<br><strong>Tree diagram</strong> — for multi-stage chance processes; great for conditional probability.</p>
            </div>
          </div>
        </div>

        <div class="card card-full" style="margin-top:16px">
          <h4>Simulation</h4>
          <p>To estimate probabilities using simulation:</p>
          <ol style="padding-left:18px; font-size:0.87rem; margin-top:8px; line-height:1.8">
            <li>Describe how to use a chance device to model one trial.</li>
            <li>State what you will record at the end of each trial.</li>
            <li>Perform many trials.</li>
            <li>Use the simulation results to answer the question.</li>
          </ol>
        </div>

        <!-- ── INDEPENDENCE DEEP DIVE ── -->
        <div class="topic" style="margin-top:28px; padding-top:28px; border-top:1px solid var(--cream2)">
          <div class="topic-title">Testing & Checking for Independence — Complete Guide</div>
          <p style="font-size:0.88rem; margin-bottom:16px; color:var(--muted)">Two events or variables are <strong>independent</strong> if knowing the outcome of one gives you <em>no information</em> about the probability of the other. There are multiple ways to check this depending on context.</p>

          <!-- Method 1: Formula check -->
          <div class="card card-full" style="margin-bottom:16px">
            <h4>Method 1 — The Multiplication Test (Most Direct)</h4>
            <p>Events A and B are independent if and only if:</p>
            <div class="formula-box">
              <span class="formula-label">Independence Check — Multiplication Rule</span>
              <div class="formula">P(A ∩ B) = P(A) · P(B)</div>
            </div>
            <p style="font-size:0.87rem; margin-top:8px"><strong>How to use it:</strong> Calculate P(A), P(B), and P(A ∩ B) separately from the data. If the product P(A) × P(B) equals P(A ∩ B), the events are independent. If they are not equal, the events are dependent (associated).</p>
            <div class="alert" style="margin-top:10px">
              <h5>⚠ Important Note</h5>
              <p>If P(A ∩ B) = 0 and P(A) &gt; 0 and P(B) &gt; 0, then A and B are <strong>mutually exclusive but NOT independent</strong>. Mutually exclusive events (no outcomes in common) are actually dependent — knowing A occurred tells you B did not occur!</p>
            </div>
          </div>

          <!-- Method 2: Conditional probability check -->
          <div class="two-col" style="margin-bottom:16px">
            <div class="card">
              <h4>Method 2 — The Conditional Probability Test</h4>
              <p>Events A and B are independent if knowing B occurred does NOT change the probability of A:</p>
              <div class="formula-box">
                <span class="formula-label">Three Equivalent Conditions</span>
                <div class="formula">P(A | B) = P(A)<br>P(B | A) = P(B)<br>P(A ∩ B) = P(A) · P(B)</div>
              </div>
              <p style="font-size:0.85rem; margin-top:8px">You only need to verify <em>one</em> of these — if one holds, all three hold. If one fails, the events are dependent.</p>
              <div class="info" style="margin-top:10px">
                <h5>Step-by-Step</h5>
                <p>1. Find P(A) from the overall totals.<br>2. Find P(A | B) — the proportion of B's that are also A.<br>3. Compare: if equal → independent; if different → dependent.</p>
              </div>
            </div>

            <div class="card">
              <h4>Method 3 — Two-Way Table Check</h4>
              <p>Given a two-way table, check independence by comparing <strong>conditional distributions</strong>:</p>
              <br>
              <ol style="padding-left:16px; font-size:0.87rem; line-height:1.9">
                <li>Calculate the conditional relative frequency of variable A for each value of variable B (each column or row).</li>
                <li>If all conditional distributions are the same → independent.</li>
                <li>If the conditional distributions differ across groups → dependent (associated).</li>
              </ol>
              <div class="formula-box" style="margin-top:10px">
                <span class="formula-label">Example Check</span>
                <div class="formula">P(A | B₁) = P(A | B₂) = P(A | B₃)?<br>If YES → A and B are independent.<br>If NO  → A and B are dependent.</div>
              </div>
            </div>
          </div>

          <!-- Worked Example -->
          <div class="card card-full" style="margin-bottom:16px; border: 2px solid var(--gold);">
            <h4>📋 Worked Example — Two-Way Table</h4>
            <p style="font-size:0.87rem; margin-bottom:14px">Suppose a survey of 200 students records whether they play a sport and whether they have a part-time job:</p>
            <table class="stats-table" style="margin-bottom:14px">
              <thead>
                <tr><th></th><th>Has Job</th><th>No Job</th><th>Total</th></tr>
              </thead>
              <tbody>
                <tr><td><strong>Plays Sport</strong></td><td>30</td><td>70</td><td>100</td></tr>
                <tr><td><strong>No Sport</strong></td><td>30</td><td>70</td><td>100</td></tr>
                <tr><td><strong>Total</strong></td><td>60</td><td>140</td><td>200</td></tr>
              </tbody>
            </table>
            <div class="two-col">
              <div>
                <p style="font-size:0.87rem"><strong>Step 1 — Find P(Has Job):</strong></p>
                <div class="formula-box"><div class="formula">P(Has Job) = 60/200 = 0.30</div></div>
                <p style="font-size:0.87rem; margin-top:10px"><strong>Step 2 — Find P(Has Job | Plays Sport):</strong></p>
                <div class="formula-box"><div class="formula">P(Has Job | Plays Sport) = 30/100 = 0.30</div></div>
              </div>
              <div>
                <p style="font-size:0.87rem"><strong>Step 3 — Compare:</strong></p>
                <div class="conditions">
                  <h5>✓ Conclusion</h5>
                  <ul>
                    <li>P(Has Job) = 0.30</li>
                    <li>P(Has Job | Plays Sport) = 0.30</li>
                    <li>These are equal → <strong>independent!</strong></li>
                    <li>Also verify: 60/200 × 100/200 = 0.30 × 0.50 = 0.15 = 30/200 ✓</li>
                  </ul>
                </div>
                <p style="font-size:0.84rem; margin-top:8px">Having a job and playing a sport are independent in this population — knowing whether a student plays a sport tells you nothing about whether they have a job.</p>
              </div>
            </div>
          </div>

          <!-- Worked Example 2: Dependent -->
          <div class="card card-full" style="margin-bottom:16px; border: 2px solid var(--red);">
            <h4>📋 Worked Example — When Events Are Dependent</h4>
            <p style="font-size:0.87rem; margin-bottom:14px">Now suppose the table looked like this instead:</p>
            <table class="stats-table" style="margin-bottom:14px">
              <thead>
                <tr><th></th><th>Has Job</th><th>No Job</th><th>Total</th></tr>
              </thead>
              <tbody>
                <tr><td><strong>Plays Sport</strong></td><td>10</td><td>90</td><td>100</td></tr>
                <tr><td><strong>No Sport</strong></td><td>50</td><td>50</td><td>100</td></tr>
                <tr><td><strong>Total</strong></td><td>60</td><td>140</td><td>200</td></tr>
              </tbody>
            </table>
            <div class="two-col">
              <div>
                <p style="font-size:0.87rem"><strong>P(Has Job) = 60/200 = 0.30</strong></p>
                <div class="formula-box"><div class="formula">P(Has Job | Plays Sport) = 10/100 = 0.10<br>P(Has Job | No Sport)   = 50/100 = 0.50</div></div>
              </div>
              <div>
                <div class="alert">
                  <h5>⚠ Conclusion: Dependent!</h5>
                  <p>P(Has Job | Plays Sport) = 0.10 ≠ P(Has Job) = 0.30. Knowing a student plays a sport changes the probability they have a job. The two variables are associated — students who play sports are much less likely to have a job.</p>
                </div>
                <p style="font-size:0.84rem; margin-top:8px">Also check: P(A)·P(B) = 0.30 × 0.50 = 0.15, but P(A∩B) = 10/200 = 0.05. Not equal → dependent.</p>
              </div>
            </div>
          </div>

          <!-- Summary of all methods -->
          <table class="stats-table">
            <thead>
              <tr><th>Method</th><th>What to Calculate</th><th>Conclude Independent If…</th><th>Best Used When…</th></tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>Multiplication Test</strong></td>
                <td>P(A), P(B), P(A ∩ B)</td>
                <td>P(A ∩ B) = P(A) · P(B)</td>
                <td>You have individual probabilities or a two-way table</td>
              </tr>
              <tr>
                <td><strong>Conditional Probability</strong></td>
                <td>P(A|B) and P(A)</td>
                <td>P(A|B) = P(A)</td>
                <td>You can compute conditional probabilities from a table or tree diagram</td>
              </tr>
              <tr>
                <td><strong>Conditional Distribution</strong></td>
                <td>Conditional distributions of A for each value of B</td>
                <td>All conditional distributions are identical</td>
                <td>You have a two-way table and want a visual/conceptual check</td>
              </tr>
              <tr>
                <td><strong>Chi-Square Test</strong> (Unit 7)</td>
                <td>χ² test statistic and P-value</td>
                <td>P-value ≥ α (fail to reject H₀ of independence)</td>
                <td>You want to formally test independence with a significance test</td>
              </tr>
            </tbody>
          </table>

          <div class="info" style="margin-top:16px">
            <h5>Independence of Random Variables vs. Events</h5>
            <p>Random variables X and Y are independent if knowing the value of one gives no information about the other. This is the assumption needed to add variances: σ²(X+Y) = σ²X + σ²Y. In practice, independence is usually stated in the problem context (e.g., "randomly selected independently") rather than something you must verify with a formula.</p>
          </div>
        </div>

      </div>

      <div class="topic">
        <div class="topic-title">Random Variables</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Discrete Random Variables</h4>
            <p>Has a fixed set of possible values with gaps between them. Probabilities must sum to 1; each ≥ 0.</p>
            <div class="formula-box">
              <span class="formula-label">Mean (Expected Value)</span>
              <div class="formula">μₓ = E(X) = Σ xᵢpᵢ</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Variance</span>
              <div class="formula">σ²ₓ = Σ (xᵢ − μₓ)² pᵢ</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Standard Deviation</span>
              <div class="formula">σₓ = √(σ²ₓ)</div>
            </div>
          </div>
          <div class="card">
            <h4>Continuous Random Variables</h4>
            <p>Can take any value in an interval. Probability distribution described by a <strong>density curve</strong> with area 1 underneath.</p>
            <p style="margin-top:8px">P(event) = area under the density curve over the event's values. P(X = any exact value) = 0.</p>
            <hr class="section-divider">
            <h4 style="margin-top:8px">Transforming Random Variables</h4>
            <div class="formula-box">
              <span class="formula-label">Add/subtract constant a</span>
              <div class="formula">μ(X±a) = μₓ ± a<br>σ(X±a) = σₓ  [shape unchanged]</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Multiply/divide by constant b</span>
              <div class="formula">μ(bX) = b·μₓ<br>σ(bX) = |b|·σₓ</div>
            </div>
          </div>
        </div>

        <div class="card card-full" style="margin-top:16px">
          <h4>Combining Random Variables (X and Y independent)</h4>
          <div class="two-col">
            <div class="formula-box">
              <span class="formula-label">Means always add/subtract</span>
              <div class="formula">μ(X+Y) = μₓ + μᵧ<br>μ(X−Y) = μₓ − μᵧ</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Variances always ADD (independent)</span>
              <div class="formula">σ²(X+Y) = σ²ₓ + σ²ᵧ<br>σ²(X−Y) = σ²ₓ + σ²ᵧ<br>σ(X±Y) = √(σ²ₓ + σ²ᵧ)</div>
            </div>
          </div>
          <div class="alert" style="margin-top:12px">
            <h5>⚠ Variances Always Add — Even for Differences!</h5>
            <p>The variance of X − Y is σ²ₓ + σ²ᵧ (not minus). The sum/difference of independent Normal random variables is also Normal.</p>
          </div>
        </div>

        <div class="topic" style="margin-top:24px; padding-top:24px; border-top:1px solid var(--cream2)">
          <div class="topic-title">Binomial & Geometric Distributions</div>
          <div class="topic-grid">
            <div class="card">
              <h4>Binomial Distribution — BINS</h4>
              <p><strong>B</strong>inary outcomes (success/failure)<br><strong>I</strong>ndependent trials<br><strong>N</strong>umber of trials is fixed (= n)<br><strong>S</strong>ame probability of success (= p) each trial</p>
              <div class="formula-box">
                <span class="formula-label">P(X = k) — exactly k successes</span>
                <div class="formula">P(X=k) = C(n,k) · pᵏ · (1−p)ⁿ⁻ᵏ</div>
              </div>
              <div class="formula-box">
                <span class="formula-label">Mean & Standard Deviation</span>
                <div class="formula">μₓ = np<br>σₓ = √(np(1−p))</div>
              </div>
              <div class="info">
                <h5>Normal Approximation</h5>
                <p>If np ≥ 10 AND n(1−p) ≥ 10, the binomial distribution is approximately Normal.</p>
              </div>
            </div>
            <div class="card">
              <h4>Geometric Distribution</h4>
              <p>Count the number of trials until the <strong>first success</strong>. Same BINS conditions but no fixed n.</p>
              <div class="formula-box">
                <span class="formula-label">P(first success on trial n)</span>
                <div class="formula">P(X=n) = (1−p)ⁿ⁻¹ · p</div>
              </div>
              <div class="formula-box">
                <span class="formula-label">Mean</span>
                <div class="formula">μₓ = 1/p</div>
              </div>
              <hr class="section-divider">
              <h4>Calc: Binomial/Geometric</h4>
              <p style="font-size:0.83rem">On TI-nspire: <strong>Menu → Probability → Distributions</strong></p>
              <ul style="font-size:0.83rem; padding-left:16px; margin-top:6px">
                <li><strong>BinomialPdf(n,p,k)</strong> → P(X = k)</li>
                <li><strong>BinomialCdf(n,p,low,high)</strong> → P(low ≤ X ≤ high)</li>
                <li>For P(X &gt; k): use 1 − BinomialCdf(n,p,0,k)</li>
                <li><strong>GeometricPdf(p,n)</strong> → P(1st success on trial n)</li>
                <li><strong>GeometricCdf(p,1,n)</strong> → P(1st success by trial n)</li>
                <li>P(1st success after trial n): 1 − GeometricCdf(p,1,n)</li>
              </ul>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 4 ═══════════════════════════════ -->
  <div class="unit" id="u4">
    <div class="unit-header">
      <span class="unit-number">UNIT 4</span>
      <div class="unit-title">Sampling Distributions</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Key Concepts</div>
        <div class="def-grid">
          <div class="def-item"><span class="def-term">Parameter</span><span class="def-desc">A number that describes a population (e.g., μ, p). Usually unknown.</span></div>
          <div class="def-item"><span class="def-term">Statistic</span><span class="def-desc">A number calculated from a sample used to estimate a parameter (e.g., x̄, p̂).</span></div>
          <div class="def-item"><span class="def-term">Sampling Distribution</span><span class="def-desc">Distribution of a statistic across all possible samples of the same size from the same population.</span></div>
          <div class="def-item"><span class="def-term">Unbiased Estimator</span><span class="def-desc">A statistic whose sampling distribution is centered at the true parameter value.</span></div>
          <div class="def-item"><span class="def-term">Variability</span><span class="def-desc">Spread of the sampling distribution. Larger n → less variability.</span></div>
        </div>
        <div class="info" style="margin-top:14px">
          <h5>Bias vs. Variability</h5>
          <p>To estimate a parameter well, choose a statistic with <strong>low (or no) bias</strong> AND <strong>minimum variability</strong>. Increasing sample size reduces variability but does not reduce bias.</p>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Sampling Distribution of p̂ (Sample Proportion)</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Properties</h4>
            <div class="formula-box">
              <span class="formula-label">Mean (unbiased)</span>
              <div class="formula">μ<sub>p̂</sub> = p</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Standard Deviation</span>
              <div class="formula">σ<sub>p̂</sub> = √(p(1−p)/n)<br><em>Use if n &lt; 0.10N (10% condition)</em></div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Shape — Large Counts Condition</span>
              <div class="formula">Approx. Normal if np ≥ 10 AND n(1−p) ≥ 10</div>
            </div>
          </div>
          <div class="card">
            <h4>Conditions</h4>
            <div class="conditions">
              <h5>✓ Check These Conditions</h5>
              <ul>
                <li><strong>Random:</strong> Data come from a random sample or randomized experiment.</li>
                <li><strong>10% condition:</strong> n &lt; 0.10N (sampling without replacement)</li>
                <li><strong>Large Counts:</strong> np ≥ 10 AND n(1−p) ≥ 10</li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Sampling Distribution of x̄ (Sample Mean)</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Properties</h4>
            <div class="formula-box">
              <span class="formula-label">Mean (unbiased)</span>
              <div class="formula">μ<sub>x̄</sub> = μ</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Standard Deviation</span>
              <div class="formula">σ<sub>x̄</sub> = σ/√n<br><em>Use if n &lt; 0.10N (10% condition)</em></div>
            </div>
          </div>
          <div class="card">
            <h4>Shape — Central Limit Theorem (CLT)</h4>
            <ul>
              <li>If population is <strong>Normal</strong>, sampling distribution of x̄ is exactly Normal for any n.</li>
              <li>If population is <strong>NOT Normal</strong>, the CLT states the sampling distribution of x̄ is approximately Normal when <strong>n ≥ 30</strong> (in most cases).</li>
              <li>If n &lt; 30 and shape unknown, use a graph to check for strong skewness or outliers.</li>
            </ul>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 5 ═══════════════════════════════ -->
  <div class="unit" id="u5">
    <div class="unit-header">
      <span class="unit-number">UNIT 5</span>
      <div class="unit-title">Confidence Intervals</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Confidence Interval Fundamentals</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Structure of a Confidence Interval</h4>
            <div class="formula-box">
              <span class="formula-label">General Form</span>
              <div class="formula">point estimate ± margin of error<br><br>statistic ± (critical value)(standard deviation of statistic)</div>
            </div>
            <p style="font-size:0.85rem; margin-top:10px">The <strong>confidence level C</strong> is the capture rate — if you use 95% CIs repeatedly, about 95% of them will capture the true parameter.</p>
          </div>
          <div class="card">
            <h4>Interpreting Confidence Intervals</h4>
            <div class="info">
              <h5>Correct Interpretation</h5>
              <p>"We are C% confident that the interval from ___ to ___ captures the true [parameter in context]."</p>
            </div>
            <div class="alert">
              <h5>⚠ Common Mistakes</h5>
              <p>Do NOT say: "There is a 95% probability that the parameter is in this interval." (The parameter is fixed — it either is or isn't in the interval.) Describe the parameter, not the statistic.</p>
            </div>
            <p style="font-size:0.84rem; margin-top:8px">Margin of error gets smaller as: C decreases OR n increases. The margin of error only accounts for <strong>chance variation</strong>, not nonresponse or undercoverage.</p>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">One-Sample z Interval for a Proportion <span class="tag tag-z">z</span><span class="tag tag-prop">proportion</span></div>
        <div class="conditions">
          <h5>✓ Conditions</h5>
          <ul>
            <li><strong>Random:</strong> Data from a random sample.</li>
            <li><strong>10%:</strong> n &lt; 0.10N (when sampling without replacement)</li>
            <li><strong>Large Counts:</strong> np̂ ≥ 10 AND n(1−p̂) ≥ 10</li>
          </ul>
        </div>
        <div class="formula-box">
          <span class="formula-label">One-Sample z Interval for p</span>
          <div class="formula">p̂ ± z* · √(p̂(1−p̂)/n)</div>
        </div>
        <div class="formula-box">
          <span class="formula-label">Standard Error of p̂</span>
          <div class="formula">SE<sub>p̂</sub> = √(p̂(1−p̂)/n)</div>
        </div>
        <div class="formula-box">
          <span class="formula-label">Required Sample Size for margin of error ME</span>
          <div class="formula">n ≥ (z*/ME)² · p̂(1−p̂)<br><em>If p̂ unknown, use p̂ = 0.5 (most conservative)</em></div>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">1-Prop z Interval</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Home → Add Calculator → Menu → Statistics → Confidence Intervals → 1-Prop z Interval</span></span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Enter Successes (x), n, and C Level (e.g., 0.95). Press OK.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">One-Sample t Interval for a Mean <span class="tag tag-t">t</span><span class="tag tag-mean">mean</span></div>
        <p style="font-size:0.88rem; margin-bottom:12px">In practice, σ is usually unknown, so we use sₓ (sample SD) and the <strong>t distribution</strong> with <strong>n−1 degrees of freedom</strong>.</p>
        <div class="conditions">
          <h5>✓ Conditions</h5>
          <ul>
            <li><strong>Random:</strong> Data from a random sample.</li>
            <li><strong>10%:</strong> n &lt; 0.10N</li>
            <li><strong>Normal/Large Sample:</strong> Population is Normal, OR n ≥ 30. If n &lt; 30 and shape unknown, graph the data — do not use t if there is strong skewness or outliers.</li>
          </ul>
        </div>
        <div class="formula-box">
          <span class="formula-label">One-Sample t Interval for μ</span>
          <div class="formula">x̄ ± t* · (sₓ/√n)   where df = n − 1</div>
        </div>
        <div class="info">
          <h5>z vs. t</h5>
          <p>Inference for <strong>proportions</strong> uses <strong>z</strong>. Inference for <strong>means</strong> uses <strong>t</strong> (because σ is unknown and must be estimated by sₓ).</p>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">t Interval for Mean</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Menu → Statistics → Confidence Intervals → t Interval</span></span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Choose Data Input Method: <strong>Stats</strong> (enter x̄, sx, n, C Level) or <strong>Data</strong> (choose list).</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">The Four-Step Process</div>
        <div class="four-step">
          <div class="step-card">
            <span class="step-letter">S</span>
            <span class="step-name">State</span>
            <span class="step-desc">Name the parameter you want to estimate and the confidence level.</span>
          </div>
          <div class="step-card">
            <span class="step-letter">P</span>
            <span class="step-name">Plan</span>
            <span class="step-desc">Identify the appropriate inference method and check all conditions.</span>
          </div>
          <div class="step-card">
            <span class="step-letter">D</span>
            <span class="step-name">Do</span>
            <span class="step-desc">If conditions are met, perform calculations to find the interval.</span>
          </div>
          <div class="step-card">
            <span class="step-letter">C</span>
            <span class="step-name">Conclude</span>
            <span class="step-desc">Interpret the interval in context. "We are C% confident that…"</span>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 6a ══════════════════════════════ -->
  <div class="unit" id="u6a">
    <div class="unit-header">
      <span class="unit-number">UNIT 6 · PART I</span>
      <div class="unit-title">Significance Tests — The Basics</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Hypothesis Testing Framework</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Hypotheses</h4>
            <div class="formula-box">
              <span class="formula-label">Null Hypothesis H₀</span>
              <div class="formula">H₀: parameter = null value<br><em>(claim we weigh evidence against; "no change")</em></div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Alternative Hypothesis Hₐ</span>
              <div class="formula">One-sided: parameter &lt; null value<br>One-sided: parameter &gt; null value<br>Two-sided: parameter ≠ null value</div>
            </div>
          </div>
          <div class="card">
            <h4>P-value & Conclusions</h4>
            <p><strong>P-value</strong> — probability of getting evidence as strong as or stronger than the observed evidence, assuming H₀ is true.</p>
            <div class="formula-box">
              <span class="formula-label">Decision Rules (significance level α)</span>
              <div class="formula">If P-value &lt; α: Reject H₀.<br>Conclude convincing evidence for Hₐ.<br><br>If P-value ≥ α: Fail to reject H₀.<br>Not convincing evidence for Hₐ.</div>
            </div>
            <div class="alert">
              <h5>⚠ Never "Accept H₀"</h5>
              <p>We only "fail to reject H₀" — absence of evidence is not evidence of absence.</p>
            </div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">One-Sample z Test for a Proportion <span class="tag tag-z">z</span><span class="tag tag-prop">proportion</span></div>
        <div class="conditions">
          <h5>✓ Conditions (Same as CI but use p₀)</h5>
          <ul>
            <li><strong>Random:</strong> Data from a random sample.</li>
            <li><strong>10%:</strong> n &lt; 0.10N</li>
            <li><strong>Large Counts:</strong> np₀ ≥ 10 AND n(1−p₀) ≥ 10  ← use p₀, not p̂!</li>
          </ul>
        </div>
        <div class="formula-box">
          <span class="formula-label">Standardized Test Statistic — 1-Sample z for p</span>
          <div class="formula">z = (p̂ − p₀) / √(p₀(1−p₀)/n)</div>
        </div>
        <p style="font-size:0.85rem; margin-top:8px">Find P-value from standard Normal distribution. A two-sided test at level α gives the same conclusion as a 100(1−α)% confidence interval.</p>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">1-Prop z Test</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → 1-Prop z Test</span></span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Enter P0 (null value), Successes (x), n, and alternate hypothesis direction. Press OK.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">One-Sample t Test for a Mean <span class="tag tag-t">t</span><span class="tag tag-mean">mean</span></div>
        <div class="conditions">
          <h5>✓ Conditions</h5>
          <ul>
            <li><strong>Random:</strong> Data from a random sample.</li>
            <li><strong>10%:</strong> n &lt; 0.10N</li>
            <li><strong>Normal/Large Sample:</strong> Population Normal, or n ≥ 30, or graph shows no strong skewness/outliers</li>
          </ul>
        </div>
        <div class="formula-box">
          <span class="formula-label">Standardized Test Statistic — 1-Sample t for μ</span>
          <div class="formula">t = (x̄ − μ₀) / (sₓ/√n)   df = n − 1</div>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">t Test for Mean</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → t Test</span></span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Choose <strong>Stats</strong> (enter μ₀, x̄, sx, n) or <strong>Data</strong> (choose list). Set alternate hypothesis. Check "Shade P Value" for a graph.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Errors & Power</div>
        <table class="stats-table">
          <thead>
            <tr><th>Decision</th><th>H₀ is TRUE</th><th>H₀ is FALSE (Hₐ is true)</th></tr>
          </thead>
          <tbody>
            <tr><td><strong>Reject H₀</strong></td><td style="color:var(--red)">TYPE I ERROR — P = α</td><td style="color:var(--green)">Correct Decision (Power)</td></tr>
            <tr><td><strong>Fail to Reject H₀</strong></td><td style="color:var(--green)">Correct Decision</td><td style="color:var(--red)">TYPE II ERROR — P = β</td></tr>
          </tbody>
        </table>
        <div class="two-col" style="margin-top:14px">
          <div class="card">
            <h4>Power of a Test</h4>
            <div class="formula-box">
              <span class="formula-label">Power</span>
              <div class="formula">Power = 1 − P(Type II error) = 1 − β</div>
            </div>
            <p style="font-size:0.84rem">Power = probability of finding convincing evidence for Hₐ when Hₐ is actually true.</p>
          </div>
          <div class="card">
            <h4>Increasing Power</h4>
            <ul>
              <li>Increase sample size n</li>
              <li>Increase significance level α</li>
              <li>Increase effect size (difference between null and true value)</li>
              <li>Reduce variability (blocking, controlling variables)</li>
            </ul>
          </div>
        </div>
        <div class="alert" style="margin-top:14px">
          <h5>⚠ P-hacking Warning</h5>
          <p>Running many tests will produce some statistically significant results by chance alone. A very small P-value with a large sample may not be practically important.</p>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 6b ══════════════════════════════ -->
  <div class="unit" id="u6b">
    <div class="unit-header">
      <span class="unit-number">UNIT 6 · PART II</span>
      <div class="unit-title">Comparing Two Populations or Groups</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Two-Sample z Procedures for Proportions <span class="tag tag-z">z</span><span class="tag tag-prop">2 proportions</span></div>
        <div class="conditions">
          <h5>✓ Conditions for p₁ − p₂</h5>
          <ul>
            <li><strong>Random:</strong> Two independent random samples or two groups in a randomized experiment</li>
            <li><strong>10%:</strong> n₁ &lt; 0.10N₁ and n₂ &lt; 0.10N₂</li>
            <li><strong>Large Counts:</strong> n₁p̂₁, n₁(1−p̂₁), n₂p̂₂, n₂(1−p̂₂) all ≥ 10</li>
          </ul>
        </div>
        <div class="two-col">
          <div class="formula-box">
            <span class="formula-label">2-Sample z Interval for p₁ − p₂</span>
            <div class="formula">(p̂₁ − p̂₂) ± z*·√(p̂₁(1−p̂₁)/n₁ + p̂₂(1−p̂₂)/n₂)</div>
          </div>
          <div class="formula-box">
            <span class="formula-label">2-Sample z Test for H₀: p₁ − p₂ = 0</span>
            <div class="formula">z = (p̂₁ − p̂₂) / √(p̂c(1−p̂c)(1/n₁ + 1/n₂))<br><br>p̂c = (x₁ + x₂)/(n₁ + n₂)  ← pooled proportion</div>
          </div>
        </div>
        <div class="alert">
          <h5>⚠ Pooled vs. Unpooled</h5>
          <p>Use the <strong>pooled proportion p̂c only for significance tests</strong> (when H₀: p₁ = p₂). For confidence intervals, use the separate p̂₁ and p̂₂.</p>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">2-Prop z Interval & Test</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">CI</span><span class="step-text"><span class="menu-path">Menu → Statistics → Confidence Intervals → 2-Prop z Interval</span>. Enter x1, n1, x2, n2, C Level.</span></div>
            <div class="calc-step"><span class="step-num">Test</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → 2-Prop z Test</span>. Enter x1, n1, x2, n2, set Hₐ direction.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Two-Sample t Procedures for Means <span class="tag tag-t">t</span><span class="tag tag-mean">2 means</span></div>
        <div class="conditions">
          <h5>✓ Conditions for μ₁ − μ₂</h5>
          <ul>
            <li><strong>Random:</strong> Two independent random samples or two groups in a randomized experiment</li>
            <li><strong>10%:</strong> n₁ &lt; 0.10N₁ and n₂ &lt; 0.10N₂</li>
            <li><strong>Normal/Large Sample:</strong> Both populations Normal, OR both n₁ ≥ 30 and n₂ ≥ 30, OR graph shows no strong skewness/outliers</li>
          </ul>
        </div>
        <div class="two-col">
          <div class="formula-box">
            <span class="formula-label">2-Sample t Interval for μ₁ − μ₂</span>
            <div class="formula">(x̄₁ − x̄₂) ± t*·√(s₁²/n₁ + s₂²/n₂)</div>
          </div>
          <div class="formula-box">
            <span class="formula-label">2-Sample t Test for H₀: μ₁ − μ₂ = 0</span>
            <div class="formula">t = (x̄₁ − x̄₂) / √(s₁²/n₁ + s₂²/n₂)</div>
          </div>
        </div>
        <div class="info">
          <h5>Degrees of Freedom</h5>
          <p>Option 1: Use technology (calculator gives the most accurate df). Option 2 (conservative): Use df = min(n₁−1, n₂−1).</p>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">2-Sample t Interval & Test</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">CI</span><span class="step-text"><span class="menu-path">Menu → Statistics → Confidence Intervals → 2-Sample t Interval</span>. Choose Stats or Data. Set Pooled = No.</span></div>
            <div class="calc-step"><span class="step-num">Test</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → 2-Sample t Test</span>. Choose Data or Stats. Set Hₐ, Pooled = No. "Shade P Value" for graph.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Paired Data (Matched Pairs) <span class="tag tag-t">t</span></div>
        <p style="font-size:0.88rem; margin-bottom:12px"><strong>Paired data</strong> result from recording two values of the same quantitative variable for each individual (or pair). To analyze: compute the difference for each pair, then perform a <strong>one-sample t procedure on the differences</strong>.</p>
        <div class="formula-box">
          <span class="formula-label">Paired t Interval</span>
          <div class="formula">x̄<sub>diff</sub> ± t* · (s<sub>diff</sub>/√n<sub>diff</sub>)   df = n<sub>diff</sub> − 1</div>
        </div>
        <div class="formula-box">
          <span class="formula-label">Paired t Test Statistic (H₀: μ<sub>diff</sub> = 0)</span>
          <div class="formula">t = x̄<sub>diff</sub> / (s<sub>diff</sub>/√n<sub>diff</sub>)</div>
        </div>
        <div class="alert">
          <h5>⚠ Paired vs. Two-Sample</h5>
          <p>Use <strong>paired t</strong> when data are collected in pairs or from the same individual. Use <strong>two-sample t</strong> when data come from two independent groups. Mixing these up is a common error.</p>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Matched Pairs</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">In Lists & Spreadsheet, create a third list: <span class="menu-path">=after − before</span> (the differences).</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Proceed with a <strong>1-Sample t Interval</strong> or <strong>1-Sample t Test</strong> using the difference list. Set μ₀ = 0 for the test.</span></div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 7 ═══════════════════════════════ -->
  <div class="unit" id="u7">
    <div class="unit-header">
      <span class="unit-number">UNIT 7</span>
      <div class="unit-title">Chi-Square Tests</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Chi-Square Statistic</div>
        <div class="formula-box">
          <span class="formula-label">χ² Test Statistic (all three chi-square tests)</span>
          <div class="formula">χ² = Σ (Observed count − Expected count)² / Expected count</div>
        </div>
        <p style="font-size:0.85rem; margin-top:8px">Large values of χ² are evidence against H₀. The P-value is the area to the <strong>right</strong> of χ² under the chi-square curve.</p>
        <div class="alert">
          <h5>⚠ Large Counts Condition for All Chi-Square Tests</h5>
          <p>All <strong>expected</strong> counts must be at least 5 (not observed counts).</p>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Chi-Square Goodness of Fit (GOF) <span class="tag tag-chi">χ²</span></div>
        <p style="font-size:0.87rem; margin-bottom:12px">Tests whether a categorical variable has a <strong>specified distribution</strong> in the population.</p>
        <div class="two-col">
          <div>
            <div class="formula-box">
              <span class="formula-label">Expected Count</span>
              <div class="formula">Expected = n × (proportion in H₀ category)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Degrees of Freedom</span>
              <div class="formula">df = number of categories − 1</div>
            </div>
            <div class="conditions">
              <h5>✓ Conditions</h5>
              <ul>
                <li><strong>Random:</strong> Random sample</li>
                <li><strong>10%:</strong> n &lt; 0.10N</li>
                <li><strong>Large Counts:</strong> All expected ≥ 5</li>
              </ul>
            </div>
          </div>
          <div class="card">
            <h4>Hypotheses</h4>
            <p><strong>H₀:</strong> The stated distribution of the categorical variable in the population is correct.</p>
            <p style="margin-top:8px"><strong>Hₐ:</strong> The categorical variable does not have the specified distribution.</p>
            <div class="info" style="margin-top:10px">
              <h5>Follow-Up Analysis</h5>
              <p>If significant, look at the largest contributions to χ² to identify which categories deviate most from expected.</p>
            </div>
          </div>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Chi-Square GOF Test</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">Enter observed counts in one list. Calculate and enter expected counts in another list.</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → χ² GOF</span>. Enter observed list, expected list, and df. "Shade P Value" for graph.</span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text">Scroll across the results column for the component list (contributions to χ²) for follow-up analysis.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Chi-Square Tests Using Two-Way Tables <span class="tag tag-chi">χ²</span></div>
        <div class="two-col">
          <div class="card">
            <h4>Test for Homogeneity</h4>
            <p>Compares the distribution of a single categorical variable across <strong>several populations or treatments</strong>.</p>
            <p style="margin-top:8px"><strong>H₀:</strong> There is no difference in the distribution of the categorical variable across all populations/treatments.</p>
            <p style="margin-top:8px"><strong>Condition:</strong> Data from independent random samples from each population (or groups in a randomized experiment).</p>
          </div>
          <div class="card">
            <h4>Test for Independence (Association)</h4>
            <p>Tests the association between <strong>two categorical variables</strong> for one population.</p>
            <p style="margin-top:8px"><strong>H₀:</strong> There is no association between the two categorical variables in the population (they are independent).</p>
            <p style="margin-top:8px"><strong>Condition:</strong> Data from a single random sample of one population.</p>
          </div>
        </div>
        <div class="formula-box" style="margin-top:14px">
          <span class="formula-label">Expected Count (when H₀ is true)</span>
          <div class="formula">Expected count = (row total × column total) / table total</div>
        </div>
        <div class="formula-box">
          <span class="formula-label">Degrees of Freedom — Two-Way Table</span>
          <div class="formula">df = (number of rows − 1)(number of columns − 1)</div>
        </div>
        <div class="conditions">
          <h5>✓ Conditions (Both Two-Way Tests)</h5>
          <ul>
            <li><strong>Random</strong></li>
            <li><strong>10%</strong> (for each sample when sampling without replacement)</li>
            <li><strong>Large Counts:</strong> All expected counts ≥ 5</li>
          </ul>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Chi-Square Two-Way Test</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Home → Add Calculator → Menu → Matrix & Vector → Create → Matrix</span>. Enter number of rows and columns. Type the observed counts into the matrix.</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">Press <span class="menu-path">Ctrl + Var</span> (sto→) to store as a matrix name (e.g., "obs").</span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → χ² 2-way Test</span>. Enter the matrix name. Press OK.</span></div>
            <div class="calc-step"><span class="step-num">4</span><span class="step-text">To see expected counts: type <span class="menu-path">stat.expmatrix</span> in the calculator. For components: type <span class="menu-path">stat.compmatrix</span>.</span></div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════════════════════ UNIT 8 ═══════════════════════════════ -->
  <div class="unit" id="u8">
    <div class="unit-header">
      <span class="unit-number">UNIT 8</span>
      <div class="unit-title">Linear Regression</div>
    </div>
    <div class="unit-body">

      <div class="topic">
        <div class="topic-title">Scatterplots & Correlation</div>
        <div class="topic-grid">
          <div class="card">
            <h4>Describing Scatterplots — DOFS</h4>
            <ul>
              <li><strong>Direction</strong> – positive, negative, or no association</li>
              <li><strong>Outliers</strong> – points that fall outside the overall pattern</li>
              <li><strong>Form</strong> – linear or nonlinear (curved)</li>
              <li><strong>Strength</strong> – how closely points follow the form</li>
            </ul>
            <div class="info" style="margin-top:10px">
              <h5>Explanatory vs. Response</h5>
              <p>Put the <strong>explanatory variable (x)</strong> on the horizontal axis and the <strong>response variable (y)</strong> on the vertical axis.</p>
            </div>
          </div>
          <div class="card">
            <h4>Correlation r</h4>
            <p>Measures the <strong>strength and direction</strong> of a linear relationship between two quantitative variables.</p>
            <ul style="margin-top:8px">
              <li>r is always between −1 and 1</li>
              <li>r &gt; 0 → positive association; r &lt; 0 → negative association</li>
              <li>r = ±1 only when all points fall exactly on a line</li>
              <li>r has no units; is not affected by changes in measurement scale</li>
            </ul>
            <div class="alert" style="margin-top:10px">
              <h5>⚠ Limitations of r</h5>
              <p>Correlation does NOT imply causation. r is not resistant to outliers. Use r only for linear relationships.</p>
            </div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Least-Squares Regression</div>
        <div class="topic-grid">
          <div class="card">
            <h4>The LSRL</h4>
            <div class="formula-box">
              <span class="formula-label">Regression Line</span>
              <div class="formula">ŷ = b₀ + b₁x</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">Slope b₁</span>
              <div class="formula">b₁ = r · (sᵧ/sₓ)</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">y-intercept b₀</span>
              <div class="formula">b₀ = ȳ − b₁x̄<br><em>Line always passes through (x̄, ȳ)</em></div>
            </div>
            <p style="font-size:0.84rem; margin-top:8px">The LSRL minimizes the sum of squared residuals (vertical distances from points to line).</p>
          </div>
          <div class="card">
            <h4>Key Quantities</h4>
            <div class="formula-box">
              <span class="formula-label">Residual</span>
              <div class="formula">residual = y − ŷ = actual − predicted</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">r² — Coefficient of Determination</span>
              <div class="formula">r² = fraction of variation in y explained by the linear relationship with x</div>
            </div>
            <div class="formula-box">
              <span class="formula-label">s — Standard Deviation of Residuals</span>
              <div class="formula">s = typical size of a prediction error</div>
            </div>
            <div class="alert">
              <h5>⚠ Avoid Extrapolation</h5>
              <p>Do not use a regression line to predict y for x values outside the range of the data used to build the model.</p>
            </div>
          </div>
        </div>
        <div class="card card-full" style="margin-top:16px">
          <h4>Interpreting Slope & Intercept — Template Phrases</h4>
          <p><strong>Slope b₁:</strong> "For each additional [one unit of x], the predicted [y] increases/decreases by [|b₁|] [units of y]."</p>
          <p style="margin-top:8px"><strong>Intercept b₀:</strong> "When [x] = 0, the predicted [y] is [b₀] [units]." (Only interpret if x = 0 is meaningful.)</p>
          <p style="margin-top:8px"><strong>r²:</strong> "About [r²]% of the variation in [y] is accounted for by the linear relationship with [x]."</p>
        </div>

        <div class="calc-section" style="margin-top:16px">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Scatterplot, LSRL & Residual Plot</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">1</span><span class="step-text">Enter x and y data in named lists. <span class="menu-path">Home → Add Data & Statistics</span>. Click to add x-variable, then y-variable.</span></div>
            <div class="calc-step"><span class="step-num">2</span><span class="step-text">For LSRL on graph: <span class="menu-path">Menu → Analyze → Regression → Show Linear (a+bx)</span>.</span></div>
            <div class="calc-step"><span class="step-num">3</span><span class="step-text">For r, r², and residuals via calculation: <span class="menu-path">Menu → Statistics → Stat Calculations → Linear Regression (a+bx)</span>. Enter x and y lists. Scroll down for r, r², residuals.</span></div>
            <div class="calc-step"><span class="step-num">4</span><span class="step-text">For residual plot: From scatterplot with LSRL shown, <span class="menu-path">Menu → Analyze → Residuals → Show Residual Plot</span>. Look for random scatter (no pattern) to confirm linear model.</span></div>
            <div class="calc-step"><span class="step-num">5</span><span class="step-text">Interpolate: <span class="menu-path">Menu → Analyze → Graph Trace</span>. Move pointer along the line.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Assessing Normality</div>
        <div class="two-col">
          <div class="card">
            <h4>Normal Probability Plot</h4>
            <p>If data are approximately Normal, the NPP should be roughly <strong>linear (straight)</strong>. Strong curves indicate non-normality.</p>
            <p style="margin-top:8px; font-size:0.84rem">TI-nspire: In Data & Statistics, right-click → <span style="color:var(--navy)">Normal Probability Plot</span>.</p>
          </div>
          <div class="card">
            <h4>Histogram + Normal PDF Overlay</h4>
            <p>Create a histogram, then <span style="color:var(--navy)"><strong>Menu → Analyze → Show Normal PDF</strong></span>. This overlays a normal curve based on x̄ and sₓ. Compare the shapes to judge normality.</p>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Inference for Regression <span class="tag tag-t">t</span></div>
        <p style="font-size:0.87rem; margin-bottom:12px">Use a sample regression line ŷ = b₀ + b₁x to estimate or test claims about the population (true) regression line: μᵧ = β₀ + β₁x.</p>
        <div class="conditions">
          <h5>✓ Conditions — LINER</h5>
          <ul>
            <li><strong>Linear:</strong> The true relationship between x and y is linear. (Check residual plot — should be random scatter.)</li>
            <li><strong>Independent:</strong> Individual observations are independent. Check 10% condition.</li>
            <li><strong>Normal:</strong> For any fixed x, the responses y vary Normally. Check NPP of residuals.</li>
            <li><strong>Equal SD:</strong> The standard deviation of y is the same for all values of x. Check residual plot — constant spread.</li>
            <li><strong>Random:</strong> Data from a random sample or randomized experiment.</li>
          </ul>
        </div>
        <div class="two-col">
          <div class="formula-box">
            <span class="formula-label">t Interval for Slope β₁</span>
            <div class="formula">b₁ ± t* · SE<sub>b₁</sub>   df = n − 2</div>
          </div>
          <div class="formula-box">
            <span class="formula-label">t Test for Slope (H₀: β₁ = 0)</span>
            <div class="formula">t = (b₁ − 0) / SE<sub>b₁</sub>   df = n − 2</div>
          </div>
        </div>
        <div class="info" style="margin-top:12px">
          <h5>Most Common Null Hypothesis</h5>
          <p>H₀: β₁ = 0 (no linear relationship between x and y in the population). Hₐ: β₁ ≠ 0 (two-sided) or β₁ &gt; 0 / β₁ &lt; 0 (one-sided).</p>
        </div>

        <div class="calc-section">
          <div class="calc-header">
            <span class="calc-badge">TI-nspire CX</span>
            <span class="calc-title">Inference for Regression</span>
          </div>
          <div class="calc-steps">
            <div class="calc-step"><span class="step-num">CI</span><span class="step-text"><span class="menu-path">Menu → Statistics → Confidence Intervals → Linear Reg t Intervals</span>. Enter x list, y list, C Level, interval = Slope. Scroll for SESlope, r, r², residuals.</span></div>
            <div class="calc-step"><span class="step-num">Test</span><span class="step-text"><span class="menu-path">Menu → Statistics → Stat Tests → Linear Reg t Test</span>. Enter x list, y list, set alternate hypothesis. Scroll for all results.</span></div>
          </div>
        </div>
      </div>

      <div class="topic">
        <div class="topic-title">Transforming to Achieve Linearity</div>
        <div class="two-col">
          <div class="card">
            <h4>Power Model: y = axᵖ</h4>
            <p>Take logarithm of both variables. A plot of <strong>log y vs. log x</strong> (or ln y vs. ln x) should be linear.</p>
            <p style="margin-top:8px">Option 1: Raise x to power p, then plot (xᵖ, y).<br>Option 2: Take pth root of y, then plot (x, ᵖ√y).</p>
          </div>
          <div class="card">
            <h4>Exponential Model: y = abˣ</h4>
            <p>Take logarithm of y only. A plot of <strong>log y vs. x</strong> (or ln y vs. x) should be linear.</p>
            <p style="margin-top:8px">Predicted values of y are multiplied by factor b for each 1-unit increase in x.</p>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- NORMAL DISTRIBUTION REFERENCE -->
  <div class="unit" id="normal-ref">
    <div class="unit-header">
      <span class="unit-number">REFERENCE</span>
      <div class="unit-title">Normal Distribution & Critical Values</div>
    </div>
    <div class="unit-body">
      <div class="topic">
        <div class="topic-title">Normal Distribution on TI-nspire CX</div>
        <div class="two-col">
          <div class="calc-section">
            <div class="calc-header">
              <span class="calc-badge">TI-nspire CX</span>
              <span class="calc-title">Area / Probability (Normal CDF)</span>
            </div>
            <div class="calc-steps">
              <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Menu → Statistics → Distributions → Normal Cdf</span></span></div>
              <div class="calc-step"><span class="step-num">2</span><span class="step-text">Enter Lower Bound, Upper Bound, μ (mean), σ (SD). Use −∞ = −1E99 for left tail.</span></div>
              <div class="calc-step"><span class="step-num">3</span><span class="step-text">For z-scores, leave μ = 0 and σ = 1. For raw values, input the actual μ and σ.</span></div>
              <div class="calc-step"><span class="step-num">4</span><span class="step-text">For a graph: perform the calculation in a <strong>Lists & Spreadsheet</strong> page (not Calculator) and check "Shade Area."</span></div>
            </div>
          </div>
          <div class="calc-section">
            <div class="calc-header">
              <span class="calc-badge">TI-nspire CX</span>
              <span class="calc-title">Inverse Normal (Percentile → Value)</span>
            </div>
            <div class="calc-steps">
              <div class="calc-step"><span class="step-num">1</span><span class="step-text"><span class="menu-path">Menu → Statistics → Distributions → Inverse Normal</span></span></div>
              <div class="calc-step"><span class="step-num">2</span><span class="step-text">Enter Area (probability measured from the <strong>extreme left</strong>), μ, and σ. Press OK.</span></div>
              <div class="calc-step"><span class="step-num">3</span><span class="step-text">For a critical value z*, find the area to the left: e.g., for 95% CI, area = 0.975 → z* ≈ 1.960.</span></div>
            </div>
          </div>
        </div>

        <div class="card card-full" style="margin-top:20px">
          <h4>Common Critical Values</h4>
          <table class="stats-table">
            <thead>
              <tr><th>Confidence Level</th><th>z* (proportions)</th><th>Significance Level α (two-sided)</th></tr>
            </thead>
            <tbody>
              <tr><td>90%</td><td>1.645</td><td>0.10</td></tr>
              <tr><td>95%</td><td>1.960</td><td>0.05</td></tr>
              <tr><td>99%</td><td>2.576</td><td>0.01</td></tr>
            </tbody>
          </table>
          <p style="font-size:0.84rem; margin-top:10px">For t* values: use the t distribution table (Table B) or technology with n−1 degrees of freedom. t* values are always larger than the corresponding z* values but approach z* as df → ∞.</p>
        </div>
      </div>

      <!-- Master Inference Decision Chart -->
      <div class="topic">
        <div class="topic-title">Master Inference Decision Guide</div>
        <table class="stats-table">
          <thead>
            <tr><th>Situation</th><th>Procedure</th><th>Test Statistic</th><th>Conditions</th></tr>
          </thead>
          <tbody>
            <tr>
              <td>One proportion p</td>
              <td><span class="tag tag-z">z</span> 1-Prop z</td>
              <td>z = (p̂ − p₀)/√(p₀(1−p₀)/n)</td>
              <td>Random, 10%, Large Counts (use p₀ for test, p̂ for CI)</td>
            </tr>
            <tr>
              <td>Two proportions p₁−p₂</td>
              <td><span class="tag tag-z">z</span> 2-Prop z</td>
              <td>z = (p̂₁−p̂₂)/√(p̂c(1−p̂c)(1/n₁+1/n₂))</td>
              <td>Random, 10%, Large Counts (use p̂c pooled for test)</td>
            </tr>
            <tr>
              <td>One mean μ (σ unknown)</td>
              <td><span class="tag tag-t">t</span> 1-Sample t</td>
              <td>t = (x̄ − μ₀)/(sₓ/√n), df = n−1</td>
              <td>Random, 10%, Normal/Large Sample</td>
            </tr>
            <tr>
              <td>Two means μ₁−μ₂ (independent)</td>
              <td><span class="tag tag-t">t</span> 2-Sample t</td>
              <td>t = (x̄₁−x̄₂)/√(s₁²/n₁+s₂²/n₂)</td>
              <td>Random, 10%, Normal/Large Sample (both groups)</td>
            </tr>
            <tr>
              <td>Paired data μ<sub>diff</sub></td>
              <td><span class="tag tag-t">t</span> Paired t</td>
              <td>t = x̄<sub>diff</sub>/(s<sub>diff</sub>/√n<sub>diff</sub>), df = n<sub>diff</sub>−1</td>
              <td>Random, 10%, Normal/Large Sample (on differences)</td>
            </tr>
            <tr>
              <td>Categorical distribution fit</td>
              <td><span class="tag tag-chi">χ²</span> GOF</td>
              <td>χ² = Σ(obs−exp)²/exp, df = k−1</td>
              <td>Random, 10%, Expected ≥ 5 all cells</td>
            </tr>
            <tr>
              <td>Homogeneity / Independence (2-way table)</td>
              <td><span class="tag tag-chi">χ²</span> Two-Way</td>
              <td>χ² = Σ(obs−exp)²/exp, df = (r−1)(c−1)</td>
              <td>Random, 10%, Expected ≥ 5 all cells</td>
            </tr>
            <tr>
              <td>Regression slope β₁</td>
              <td><span class="tag tag-t">t</span> Lin Reg t</td>
              <td>t = b₁/SE<sub>b₁</sub>, df = n−2</td>
              <td>LINER: Linear, Independent, Normal, Equal SD, Random</td>
            </tr>
          </tbody>
        </table>
      </div>

    </div>
  </div>

</div>

<button id="back-top" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button>

<script>
  // Show/hide back-to-top
  window.addEventListener('scroll', () => {
    document.getElementById('back-top').style.opacity = window.scrollY > 300 ? '1' : '0';
  });
  document.getElementById('back-top').style.opacity = '0';
  document.getElementById('back-top').style.transition = 'opacity 0.3s';
</script>


