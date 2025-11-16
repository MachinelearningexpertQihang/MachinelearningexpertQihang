<!-- index.html - interactive portfolio page for Qihang (Kyle) Chen -->

<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Qihang (Kyle) Chen — Data Scientist</title>
  <style>
    :root{
      --bg:#f5f7f8;
      --card:#ffffff;
      --text:#0f1720;
      --muted:#6b7280;
      --accent:#0b7285; /* chosen professional teal */
      --glass: rgba(255,255,255,0.6);
    }
    [data-theme="dark"]{
      --bg:#071016;
      --card:#0b1320;
      --text:#e6eef6;
      --muted:#98a3ad;
      --accent:#12b0c8;
      --glass: rgba(10,18,24,0.6);
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial}
    body{background:linear-gradient(180deg,var(--bg),#e9eef0);color:var(--text);padding:28px}
    .container{max-width:980px;margin:0 auto}
    header{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px}
    .hero{display:flex;gap:20px;align-items:center}
    .avatar{width:84px;height:84px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#074b5a)}
    h1{margin:0;font-size:22px}
    p.lead{margin:4px 0;color:var(--muted)}

```
.controls{display:flex;gap:10px;align-items:center}
.btn{background:var(--card);border:1px solid rgba(0,0,0,0.05);padding:8px 12px;border-radius:8px;cursor:pointer}
.btn:active{transform:translateY(1px)}

main{display:grid;grid-template-columns:1fr 320px;gap:20px}
.card{background:var(--card);border-radius:12px;padding:16px;box-shadow:0 6px 18px rgba(2,6,23,0.06)}
.projects .project{margin-bottom:12px}
details summary{cursor:pointer;padding:8px;border-radius:8px}

/* animated stat tiles */
.stats{display:flex;gap:10px;flex-wrap:wrap}
.stat{flex:1;min-width:140px;padding:12px;border-radius:10px;background:linear-gradient(180deg,var(--glass),transparent);border:1px solid rgba(0,0,0,0.04)}
.stat strong{display:block;font-size:18px}
.stat small{color:var(--muted)}

/* contribution graph iframe */
.graph{width:100%;height:160px;border-radius:8px;border:0}

/* clicker game */
.game{display:flex;flex-direction:column;gap:10px;align-items:center}
.score{font-size:28px;font-weight:700}
.clicker{width:160px;height:160px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;border:2px solid rgba(0,0,0,0.06);cursor:pointer}
footer{margin-top:18px;color:var(--muted);font-size:13px}

@media (max-width:880px){main{grid-template-columns:1fr;}}
```

  </style>
</head>
<body>
  <div class="container" id="page">
    <header>
      <div class="hero">
        <div class="avatar" aria-hidden></div>
        <div>
          <h1>Qihang (Kyle) Chen</h1>
          <p class="lead">MS in Business Analytics — Carnegie Mellon University. Building cloud-native data platforms and ML systems.</p>
        </div>
      </div>

```
  <div class="controls">
    <button class="btn" id="themeToggle">Toggle theme</button>
    <a class="btn" href="./index.html" download="kyle-portfolio.html">Download</a>
  </div>
</header>

<main>
  <section>
    <div class="card">
      <h2>Featured projects</h2>
      <div class="projects">
        <div class="project">
          <details>
            <summary><strong>User Behavior Funnel Analytics Platform</strong> — 30s</summary>
            <div style="margin-top:10px">
              <p>Built an e-commerce funnel analytics platform for 8,000 users. Converted JSONL to Parquet using AWS Glue and partitioned by event_type to accelerate queries by 70% and reduce storage cost by 87%. Athena analysis identified a 35% drop between "Add to Cart" and "Checkout"; email channel conversion exceeded Facebook ads by 28%. Delivered QuickSight dashboards for self-service analysis.</p>
              <details>
                <summary>Technical notes (1-minute)</summary>
                <ul>
                  <li>Parquet chosen for columnar reads — ~10x speedup on aggregations.</li>
                  <li>Partitioned by <code>event_type</code> for common event-centric queries.</li>
                  <li>Query cost on Athena reduced from $0.013 to $0.0015 per query via partition pruning.</li>
                </ul>
              </details>
            </div>
          </details>
        </div>

        <div class="project">
          <details>
            <summary><strong>Real-time Esports Analytics System</strong> — 30s</summary>
            <div style="margin-top:10px">
              <p>Designed a real-time analytics pipeline with five independent consumers. Enabled Kinesis Enhanced Fan-Out to deliver per-consumer 2MB/s throughput, reducing latency from 5s to 200ms. Components include Lambda/DynamoDB leaderboard, SageMaker predictions, anomaly detection, and batch archiving via Firehose.</p>
              <details>
                <summary>Technical notes (1-minute)</summary>
                <ul>
                  <li>Decoupled consumers for reliability and scaling.</li>
                  <li>Firehose used for cost-effective batch S3 archival vs per-record writes.</li>
                </ul>
              </details>
            </div>
          </details>
        </div>

        <!-- Add other projects similarly -->
      </div>
    </div>

    <div class="card" style="margin-top:12px">
      <h2>Animated stats</h2>
      <div class="stats" id="statTiles">
        <div class="stat" aria-hidden>
          <strong id="projectsCount">0</strong>
          <small>Projects</small>
        </div>
        <div class="stat">
          <!-- GitHub readme stats image (replace USERNAME) -->
          <img src="https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_USERNAME&show_icons=true&count_private=true&hide_title=true&include_all_commits=true" alt="github stats" style="width:100%;border-radius:8px" />
        </div>
        <div class="stat">
          <!-- compact trophy placeholder using shields.io — adjust as needed -->
          <img src="https://github-profile-trophy.vercel.app/?username=YOUR_GITHUB_USERNAME&theme=matrix&no-frame=true" alt="trophies" style="width:100%;border-radius:8px" />
        </div>
      </div>

      <p style="margin-top:10px;color:var(--muted)">Contribution graph below updates automatically from GitHub.</p>
      <iframe class="graph" src="https://ghchart.rshah.org/YOUR_GITHUB_USERNAME" title="contribution graph"></iframe>
    </div>

    <div class="card" style="margin-top:12px">
      <h2>Interactive demo — Clicker game</h2>
      <div class="game">
        <div class="score" id="score">0</div>
        <div class="clicker" id="clicker">Click</div>
        <div style="display:flex;gap:8px">
          <button class="btn" id="upgrade">Upgrade (+1 per click) — cost 20</button>
          <button class="btn" id="reset">Reset</button>
        </div>
        <small style="color:var(--muted)">A lightweight example you can extend into a memory game or leaderboard.</small>
      </div>
    </div>
  </section>

  <aside>
    <div class="card">
      <h3>Contact</h3>
      <p style="margin:6px 0;color:var(--muted)">Carnegie Mellon University — MS Business Analytics</p>
      <p><a href="mailto:your_email@example.com">your_email@example.com</a></p>
    </div>

    <div class="card" style="margin-top:12px">
      <h3>Quick links</h3>
      <ul style="margin:6px 0 0 18px;color:var(--muted)">
        <li><a href="#">Portfolio</a></li>
        <li><a href="#">Resume</a></li>
        <li><a href="#">Repositories</a></li>
      </ul>
    </div>
  </aside>
</main>

<footer>
  <div class="container">
    <p>Generated portfolio HTML — customize GitHub usernames and email in the source. Host via GitHub Pages for live interaction.</p>
  </div>
</footer>
```

  </div>

  <script>
    (function(){
      // theme handling
      const root = document.documentElement;
      const toggle = document.getElementById('themeToggle');
      const saved = localStorage.getItem('theme');
      if(saved==='dark') document.documentElement.setAttribute('data-theme','dark');
      function switchTheme(){
        const active = document.documentElement.getAttribute('data-theme');
        if(active==='dark'){document.documentElement.removeAttribute('data-theme');localStorage.setItem('theme','light');}
        else {document.documentElement.setAttribute('data-theme','dark');localStorage.setItem('theme','dark');}
      }
      toggle.addEventListener('click',switchTheme);

      // simple animated stat counter
      const projectsCount = document.getElementById('projectsCount');
      const target = 5; // set to number of highlighted projects
      let current = 0;
      const inc = Math.ceil(target/30);
      const counter = setInterval(()=>{
        current += inc;
        if(current>=target){current=target;clearInterval(counter)}
        projectsCount.textContent = current;
      },40);

      // Clicker game logic
      let score=0;
      let perClick=1;
      const scoreEl = document.getElementById('score');
      const clicker = document.getElementById('clicker');
      const upgradeBtn = document.getElementById('upgrade');
      const resetBtn = document.getElementById('reset');

      function updateScore(){scoreEl.textContent = score}
      clicker.addEventListener('click',()=>{score += perClick; updateScore();})
      upgradeBtn.addEventListener('click',()=>{
        const cost = 20;
        if(score>=cost){score -= cost; perClick += 1; upgradeBtn.textContent = `Upgrade (+${perClick} per click) — cost ${cost}`; updateScore();}
        else{alert('Not enough points');}
      })
      resetBtn.addEventListener('click',()=>{score=0;perClick=1;upgradeBtn.textContent='Upgrade (+1 per click) — cost 20';updateScore();})

      // accessibility: allow Enter to click
      clicker.tabIndex = 0;
      clicker.addEventListener('keydown', (e)=>{ if(e.key === 'Enter') clicker.click(); })

    })()
  </script>

</body>
</html>


