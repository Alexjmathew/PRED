
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --pm-bg: #0a0e14;
    --pm-surface: #111722;
    --pm-border: rgba(255,255,255,0.07);
    --pm-accent: #00e5a0;
    --pm-accent2: #3b82f6;
    --pm-accent3: #f59e0b;
    --pm-text: #e8edf5;
    --pm-muted: #6b7a90;
    --pm-syne: 'Syne', sans-serif;
    --pm-mono: 'Space Mono', monospace;
  }

  body { background: transparent; }

  .readme-wrap {
    font-family: var(--pm-syne);
    background: var(--pm-bg);
    color: var(--pm-text);
    border-radius: 16px;
    overflow: hidden;
    border: 1px solid var(--pm-border);
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    padding: 52px 48px 44px;
    background: linear-gradient(135deg, #0a0e14 0%, #0f1a2e 50%, #0a1a12 100%);
    overflow: hidden;
  }

  .hero-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,160,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,160,0.04) 1px, transparent 1px);
    background-size: 32px 32px;
  }

  .hero-glow {
    position: absolute;
    width: 400px; height: 400px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,229,160,0.12) 0%, transparent 70%);
    top: -100px; right: -80px;
    pointer-events: none;
  }

  .hero-glow2 {
    position: absolute;
    width: 300px; height: 300px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(59,130,246,0.08) 0%, transparent 70%);
    bottom: -80px; left: 40px;
    pointer-events: none;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    font-family: var(--pm-mono);
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--pm-accent);
    background: rgba(0,229,160,0.08);
    border: 1px solid rgba(0,229,160,0.2);
    padding: 5px 12px;
    border-radius: 4px;
    margin-bottom: 20px;
  }

  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--pm-accent);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  .hero h1 {
    font-family: var(--pm-syne);
    font-size: 36px;
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    color: #fff;
    margin-bottom: 14px;
    position: relative;
  }

  .hero h1 span {
    color: var(--pm-accent);
  }

  .hero-sub {
    font-family: var(--pm-mono);
    font-size: 12px;
    color: var(--pm-muted);
    line-height: 1.7;
    max-width: 560px;
    position: relative;
  }

  .hero-tags {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-top: 28px;
    position: relative;
  }

  .tag {
    font-family: var(--pm-mono);
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 3px;
    letter-spacing: 0.05em;
  }

  .tag-blue { background: rgba(59,130,246,0.12); color: #60a5fa; border: 1px solid rgba(59,130,246,0.2); }
  .tag-amber { background: rgba(245,158,11,0.1); color: #fbbf24; border: 1px solid rgba(245,158,11,0.2); }
  .tag-green { background: rgba(0,229,160,0.08); color: var(--pm-accent); border: 1px solid rgba(0,229,160,0.2); }

  /* ── TOC STRIP ── */
  .toc-strip {
    display: flex;
    border-bottom: 1px solid var(--pm-border);
    background: var(--pm-surface);
    overflow: hidden;
  }

  .toc-item {
    flex: 1;
    padding: 14px 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    border-right: 1px solid var(--pm-border);
    transition: background 0.2s;
    position: relative;
  }

  .toc-item:last-child { border-right: none; }

  .toc-item:hover { background: rgba(0,229,160,0.04); }

  .toc-item.active::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: var(--pm-accent);
  }

  .toc-num {
    font-family: var(--pm-mono);
    font-size: 10px;
    color: var(--pm-accent);
    opacity: 0.6;
    min-width: 20px;
  }

  .toc-label {
    font-size: 12px;
    font-weight: 600;
    color: var(--pm-muted);
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  .toc-item.active .toc-label { color: var(--pm-text); }

  /* ── CONTENT PANELS ── */
  .content-area {
    padding: 0;
  }

  .section {
    display: none;
    padding: 40px 48px;
    animation: fadeIn 0.3s ease;
    border-bottom: 1px solid var(--pm-border);
  }

  .section.active { display: block; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(6px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section-eyebrow {
    font-family: var(--pm-mono);
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--pm-accent);
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .section-eyebrow::after {
    content: '';
    flex: 1;
    height: 1px;
    max-width: 40px;
    background: rgba(0,229,160,0.3);
  }

  .section-title {
    font-size: 22px;
    font-weight: 800;
    color: #fff;
    margin-bottom: 20px;
    line-height: 1.2;
  }

  /* overview cards */
  .overview-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 28px;
  }

  .ov-card {
    background: var(--pm-surface);
    border: 1px solid var(--pm-border);
    border-radius: 10px;
    padding: 20px 22px;
    position: relative;
    overflow: hidden;
  }

  .ov-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
  }

  .ov-card.green::before { background: var(--pm-accent); }
  .ov-card.blue::before { background: var(--pm-accent2); }
  .ov-card.amber::before { background: var(--pm-accent3); }
  .ov-card.red::before { background: #ef4444; }

  .ov-card-icon {
    font-size: 22px;
    margin-bottom: 10px;
  }

  .ov-card-title {
    font-size: 11px;
    font-family: var(--pm-mono);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--pm-muted);
    margin-bottom: 6px;
  }

  .ov-card-val {
    font-size: 15px;
    font-weight: 700;
    color: #fff;
    line-height: 1.4;
  }

  .prose {
    font-family: var(--pm-mono);
    font-size: 12px;
    color: var(--pm-muted);
    line-height: 1.9;
  }

  .prose strong { color: var(--pm-text); font-weight: 700; }

  /* problem statement */
  .task-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 24px;
  }

  .task-card {
    background: var(--pm-surface);
    border: 1px solid var(--pm-border);
    border-radius: 10px;
    padding: 22px;
  }

  .task-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 14px;
  }

  .task-pill {
    font-family: var(--pm-mono);
    font-size: 9px;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    padding: 3px 8px;
    border-radius: 3px;
  }

  .pill-reg { background: rgba(0,229,160,0.1); color: var(--pm-accent); border: 1px solid rgba(0,229,160,0.2); }
  .pill-cls { background: rgba(59,130,246,0.1); color: #60a5fa; border: 1px solid rgba(59,130,246,0.2); }

  .task-name {
    font-size: 13px;
    font-weight: 700;
    color: #fff;
  }

  .task-desc {
    font-family: var(--pm-mono);
    font-size: 11px;
    color: var(--pm-muted);
    line-height: 1.8;
  }

  .benefits {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-top: 24px;
  }

  .benefit {
    background: rgba(0,229,160,0.04);
    border: 1px solid rgba(0,229,160,0.1);
    border-radius: 8px;
    padding: 14px 16px;
    text-align: center;
  }

  .benefit-icon { font-size: 20px; margin-bottom: 8px; }

  .benefit-text {
    font-family: var(--pm-mono);
    font-size: 10px;
    color: var(--pm-muted);
    letter-spacing: 0.03em;
    line-height: 1.6;
  }

  /* dataset */
  .ds-table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 24px;
    font-family: var(--pm-mono);
    font-size: 11px;
  }

  .ds-table th {
    text-align: left;
    padding: 10px 14px;
    font-size: 9px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--pm-muted);
    background: rgba(255,255,255,0.03);
    border-bottom: 1px solid var(--pm-border);
  }

  .ds-table td {
    padding: 11px 14px;
    border-bottom: 1px solid var(--pm-border);
    color: var(--pm-text);
    vertical-align: top;
  }

  .ds-table tr:last-child td { border-bottom: none; }

  .ds-table tr:hover td { background: rgba(255,255,255,0.02); }

  .ds-table td:first-child {
    color: var(--pm-accent);
    white-space: nowrap;
  }

  .subsets {
    display: flex;
    gap: 10px;
    margin-bottom: 24px;
  }

  .subset-chip {
    background: var(--pm-surface);
    border: 1px solid var(--pm-border);
    border-radius: 8px;
    padding: 12px 16px;
    flex: 1;
    text-align: center;
  }

  .subset-name {
    font-family: var(--pm-mono);
    font-size: 13px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 4px;
  }

  .subset-desc {
    font-family: var(--pm-mono);
    font-size: 9px;
    color: var(--pm-muted);
    letter-spacing: 0.05em;
  }

  .subset-chip:nth-child(1) .subset-name { color: var(--pm-accent); }
  .subset-chip:nth-child(2) .subset-name { color: var(--pm-accent2); }
  .subset-chip:nth-child(3) .subset-name { color: var(--pm-accent3); }
  .subset-chip:nth-child(4) .subset-name { color: #f87171; }

  .code-block {
    background: #070a0f;
    border: 1px solid var(--pm-border);
    border-radius: 8px;
    padding: 16px 20px;
    font-family: var(--pm-mono);
    font-size: 11px;
    color: #7dd3a8;
    line-height: 1.8;
    overflow-x: auto;
  }

  .code-block .comment { color: var(--pm-muted); }
  .code-block .key { color: #60a5fa; }
  .code-block .val { color: #fbbf24; }

  /* footer bar */
  .footer-bar {
    background: var(--pm-surface);
    border-top: 1px solid var(--pm-border);
    padding: 14px 48px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .footer-left {
    font-family: var(--pm-mono);
    font-size: 10px;
    color: var(--pm-muted);
  }

  .footer-left span { color: var(--pm-accent); }

  .footer-links {
    display: flex;
    gap: 20px;
  }

  .footer-link {
    font-family: var(--pm-mono);
    font-size: 10px;
    color: var(--pm-muted);
    text-decoration: none;
    letter-spacing: 0.05em;
    cursor: pointer;
    transition: color 0.2s;
  }

  .footer-link:hover { color: var(--pm-text); }
</style>

<h2 class="sr-only" style="position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0,0,0,0)">Predictive Maintenance README — Overview, Problem Statement, and Dataset sections</h2>

<div class="readme-wrap">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-grid"></div>
    <div class="hero-glow"></div>
    <div class="hero-glow2"></div>

    <div class="hero-badge">ML · Industrial IoT · Predictive Maintenance</div>

    <h1>Predict Failures<br><span>Before They Happen</span></h1>

    <p class="hero-sub">
      Sensor-driven RUL estimation for turbofan jet engines using the NASA CMAPSS dataset.
      Stop reacting to failures — start anticipating them.
    </p>

    <div class="hero-tags">
      <span class="tag tag-blue">Scikit-learn</span>
      <span class="tag tag-amber">XGBoost</span>
      <span class="tag tag-green">Pandas</span>
      <span class="tag tag-blue">NASA CMAPSS</span>
      <span class="tag tag-green">Python 3.9+</span>
    </div>
  </div>

  <!-- TOC STRIP -->
  <div class="toc-strip">
    <div class="toc-item active" onclick="showSection('overview', this)">
      <span class="toc-num">01</span>
      <span class="toc-label">Overview</span>
    </div>
    <div class="toc-item" onclick="showSection('problem', this)">
      <span class="toc-num">02</span>
      <span class="toc-label">Problem Statement</span>
    </div>
    <div class="toc-item" onclick="showSection('dataset', this)">
      <span class="toc-num">03</span>
      <span class="toc-label">Dataset</span>
    </div>
  </div>

  <!-- CONTENT -->
  <div class="content-area">

    <!-- OVERVIEW -->
    <div id="sec-overview" class="section active">
      <div class="section-eyebrow">01 / overview</div>
      <div class="section-title">What this project does</div>

      <div class="overview-grid">
        <div class="ov-card green">
          <div class="ov-card-icon">🛡️</div>
          <div class="ov-card-title">Goal</div>
          <div class="ov-card-val">Predict remaining useful life of engines before failure</div>
        </div>
        <div class="ov-card blue">
          <div class="ov-card-icon">📡</div>
          <div class="ov-card-title">Input</div>
          <div class="ov-card-val">21 sensor streams + 3 operational settings per cycle</div>
        </div>
        <div class="ov-card amber">
          <div class="ov-card-icon">⚙️</div>
          <div class="ov-card-title">Output</div>
          <div class="ov-card-val">RUL in cycles — or binary alert within threshold window</div>
        </div>
        <div class="ov-card red">
          <div class="ov-card-icon">💸</div>
          <div class="ov-card-title">Stakes</div>
          <div class="ov-card-val">Unplanned downtime costs billions annually across industries</div>
        </div>
      </div>

      <p class="prose">
        This project applies machine learning to <strong>multivariate time-series sensor data</strong>
        from jet engines to estimate how many operational cycles remain before failure.
        Given a sequence of readings from an engine's operational history, the model
        learns degradation patterns and outputs a <strong>Remaining Useful Life (RUL)</strong> prediction —
        enabling maintenance teams to act <strong>before</strong> failure, not after.
      </p>
    </div>

    <!-- PROBLEM STATEMENT -->
    <div id="sec-problem" class="section">
      <div class="section-eyebrow">02 / problem statement</div>
      <div class="section-title">Two ways to frame the problem</div>

      <div class="task-row">
        <div class="task-card">
          <div class="task-header">
            <span class="task-pill pill-reg">Regression</span>
            <span class="task-name">Predict exact RUL</span>
          </div>
          <p class="task-desc">
            Given sensor readings up to cycle <em>t</em>, predict the exact number of cycles
            remaining before engine failure. Output is a continuous value minimized with RMSE.
          </p>
        </div>
        <div class="task-card">
          <div class="task-header">
            <span class="task-pill pill-cls">Classification</span>
            <span class="task-name">Predict failure window</span>
          </div>
          <p class="task-desc">
            Classify whether an engine will fail within a defined threshold window —
            typically the next 30 cycles. Binary label: <em>1 = imminent failure</em>.
          </p>
        </div>
      </div>

      <div class="benefits">
        <div class="benefit">
          <div class="benefit-icon">🗓️</div>
          <p class="benefit-text">Schedule maintenance proactively, not reactively</p>
        </div>
        <div class="benefit">
          <div class="benefit-icon">📉</div>
          <p class="benefit-text">Reduce unplanned downtime and repair costs</p>
        </div>
        <div class="benefit">
          <div class="benefit-icon">🔩</div>
          <p class="benefit-text">Extend asset lifetime and improve safety</p>
        </div>
      </div>
    </div>

    <!-- DATASET -->
    <div id="sec-dataset" class="section">
      <div class="section-eyebrow">03 / dataset</div>
      <div class="section-title">NASA CMAPSS — Turbofan Engine Dataset</div>

      <div class="subsets">
        <div class="subset-chip">
          <div class="subset-name">FD001</div>
          <div class="subset-desc">1 condition · HPC fault</div>
        </div>
        <div class="subset-chip">
          <div class="subset-name">FD002</div>
          <div class="subset-desc">6 conditions · HPC fault</div>
        </div>
        <div class="subset-chip">
          <div class="subset-name">FD003</div>
          <div class="subset-desc">1 condition · Fan fault</div>
        </div>
        <div class="subset-chip">
          <div class="subset-name">FD004</div>
          <div class="subset-desc">6 conditions · Fan fault</div>
        </div>
      </div>

      <table class="ds-table">
        <thead>
          <tr>
            <th>Property</th>
            <th>Details</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Source</td>
            <td>NASA Prognostics Center of Excellence</td>
          </tr>
          <tr>
            <td>Features</td>
            <td>3 operational settings + 21 sensor measurements per cycle</td>
          </tr>
          <tr>
            <td>Target</td>
            <td>Remaining Useful Life (RUL) in operational cycles</td>
          </tr>
          <tr>
            <td>Format</td>
            <td>Space-delimited .txt files — train, test, RUL ground truth</td>
          </tr>
          <tr>
            <td>Engines</td>
            <td>100–260 per subset, each run to failure</td>
          </tr>
        </tbody>
      </table>

      <div class="code-block">
        <span class="comment"># File structure</span><br>
        data/<br>
        &nbsp;&nbsp;├── <span class="key">train_FD001.txt</span> &nbsp;<span class="comment"> # run-to-failure sequences</span><br>
        &nbsp;&nbsp;├── <span class="key">test_FD001.txt</span> &nbsp;&nbsp;<span class="comment"> # partial sequences (predict at last cycle)</span><br>
        &nbsp;&nbsp;└── <span class="key">RUL_FD001.txt</span> &nbsp;&nbsp;<span class="comment"> # ground truth RUL for test engines</span>
      </div>
    </div>

  </div>

  <!-- FOOTER -->
  <div class="footer-bar">
    <div class="footer-left">Built with <span>Scikit-learn · XGBoost · Pandas</span></div>
    <div class="footer-links">
      <span class="footer-link">MIT License</span>
      <span class="footer-link">Saxena et al., 2008</span>
    </div>
  </div>

</div>

<script>
function showSection(id, el) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.toc-item').forEach(t => t.classList.remove('active'));
  document.getElementById('sec-' + id).classList.add('active');
  el.classList.add('active');
}
</script>
