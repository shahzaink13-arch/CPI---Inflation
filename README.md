<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>India CPI Inflation — Case Study README</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --saffron: #FF6B00;
    --saffron-light: #FF9A45;
    --green: #138808;
    --green-light: #2CC84D;
    --blue: #1565C0;
    --blue-light: #42A5F5;
    --gold: #F5C518;
    --red: #C62828;
    --white: #FAFAFA;
    --dark: #0D1117;
    --card-bg: #161B22;
    --border: rgba(255,255,255,0.08);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  .hero {
    position: relative;
    padding: 80px 40px 60px;
    text-align: center;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(255,107,0,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 50% 40% at 10% 80%, rgba(19,136,8,0.15) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 90% 80%, rgba(21,101,192,0.15) 0%, transparent 60%);
    z-index: 0;
  }
  .hero-flag {
    display: flex;
    justify-content: center;
    gap: 0;
    margin-bottom: 28px;
    position: relative; z-index: 1;
  }
  .flag-stripe { width: 12px; height: 56px; border-radius: 3px; }
  .flag-stripe:nth-child(1) { background: var(--saffron); }
  .flag-stripe:nth-child(2) { background: white; }
  .flag-stripe:nth-child(3) { background: var(--green); }

  .hero-eyebrow {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--saffron-light);
    margin-bottom: 16px;
    position: relative; z-index: 1;
  }
  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.2rem, 5vw, 3.6rem);
    font-weight: 800;
    line-height: 1.1;
    position: relative; z-index: 1;
    margin-bottom: 20px;
  }
  .hero h1 span.saffron { color: var(--saffron); }
  .hero h1 span.green   { color: var(--green-light); }
  .hero h1 span.blue    { color: var(--blue-light); }

  .hero-sub {
    font-size: 16px;
    color: rgba(255,255,255,0.6);
    max-width: 620px;
    margin: 0 auto 36px;
    position: relative; z-index: 1;
  }

  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    position: relative; z-index: 1;
  }
  .badge {
    padding: 6px 16px;
    border-radius: 999px;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.5px;
    border: 1px solid;
  }
  .badge-saffron { background: rgba(255,107,0,0.12); border-color: var(--saffron); color: var(--saffron-light); }
  .badge-green   { background: rgba(19,136,8,0.12);  border-color: var(--green);   color: var(--green-light); }
  .badge-blue    { background: rgba(21,101,192,0.12); border-color: var(--blue-light); color: var(--blue-light); }
  .badge-gold    { background: rgba(245,197,24,0.12); border-color: var(--gold);    color: var(--gold); }

  .divider { display: flex; height: 4px; width: 100%; }
  .divider span:nth-child(1) { flex: 1; background: var(--saffron); }
  .divider span:nth-child(2) { flex: 1; background: white; }
  .divider span:nth-child(3) { flex: 1; background: var(--green); }

  .container { max-width: 980px; margin: 0 auto; padding: 60px 40px; }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-title .icon {
    width: 36px; height: 36px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }
  .icon-saffron { background: rgba(255,107,0,0.18); }
  .icon-green   { background: rgba(19,136,8,0.18); }
  .icon-blue    { background: rgba(21,101,192,0.18); }
  .icon-gold    { background: rgba(245,197,24,0.18); }
  .icon-red     { background: rgba(198,40,40,0.18); }

  .card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px;
    margin-bottom: 16px;
  }

  .kpi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 14px;
    margin-bottom: 40px;
  }
  .kpi-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px 18px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .kpi-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
  }
  .kpi-card.c-saffron::before { background: var(--saffron); }
  .kpi-card.c-green::before   { background: var(--green-light); }
  .kpi-card.c-blue::before    { background: var(--blue-light); }
  .kpi-card.c-gold::before    { background: var(--gold); }
  .kpi-card.c-red::before     { background: var(--red); }
  .kpi-card.c-white::before   { background: white; }

  .kpi-value {
    font-family: 'Syne', sans-serif;
    font-size: 1.7rem;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 8px;
  }
  .kpi-card.c-saffron .kpi-value { color: var(--saffron); }
  .kpi-card.c-green   .kpi-value { color: var(--green-light); }
  .kpi-card.c-blue    .kpi-value { color: var(--blue-light); }
  .kpi-card.c-gold    .kpi-value { color: var(--gold); }
  .kpi-card.c-red     .kpi-value { color: #EF5350; }
  .kpi-card.c-white   .kpi-value { color: white; }
  .kpi-label { font-size: 11px; color: rgba(255,255,255,0.5); letter-spacing: 0.5px; text-transform: uppercase; }

  .sheets-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 14px;
    margin-bottom: 40px;
  }
  .sheet-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    display: flex;
    gap: 14px;
    align-items: flex-start;
  }
  .sheet-num { font-family: 'Syne', sans-serif; font-size: 1.4rem; font-weight: 800; line-height: 1; min-width: 32px; opacity: 0.3; }
  .sheet-info h4 { font-family: 'Syne', sans-serif; font-size: 0.95rem; font-weight: 600; margin-bottom: 6px; color: white; }
  .sheet-info p  { font-size: 12.5px; color: rgba(255,255,255,0.5); line-height: 1.5; }

  .analysis-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 14px;
    margin-bottom: 40px;
  }
  .analysis-card { background: var(--card-bg); border: 1px solid var(--border); border-radius: 14px; padding: 22px; }
  .analysis-card h4 { font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 700; margin-bottom: 10px; display: flex; align-items: center; gap: 8px; }
  .dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
  .dot-saffron { background: var(--saffron); }
  .dot-green   { background: var(--green-light); }
  .dot-blue    { background: var(--blue-light); }
  .dot-gold    { background: var(--gold); }
  .dot-red     { background: #EF5350; }
  .analysis-card p { font-size: 13px; color: rgba(255,255,255,0.55); line-height: 1.65; }

  .tech-row { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 40px; }
  .tech-pill {
    display: flex; align-items: center; gap: 8px;
    padding: 10px 18px;
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 999px;
    font-size: 13px; font-weight: 500;
  }
  .tech-pill .dot { width: 7px; height: 7px; }

  .tree {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 28px;
    font-family: 'Courier New', monospace;
    font-size: 13px;
    line-height: 1.9;
    margin-bottom: 40px;
    color: rgba(255,255,255,0.7);
  }
  .tree .folder { color: var(--gold); font-weight: bold; }
  .tree .file   { color: var(--green-light); }
  .tree .sheet  { color: var(--blue-light); }

  .insight-list { list-style: none; margin-bottom: 40px; }
  .insight-list li {
    display: flex; gap: 14px; align-items: flex-start;
    padding: 14px 0;
    border-bottom: 1px solid var(--border);
    font-size: 14px; color: rgba(255,255,255,0.7);
  }
  .insight-list li:last-child { border-bottom: none; }
  .insight-list li .num { font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 800; color: var(--saffron); min-width: 24px; }

  .footer {
    text-align: center; padding: 40px;
    border-top: 1px solid var(--border);
    color: rgba(255,255,255,0.35); font-size: 13px;
  }

  .section { margin-bottom: 56px; }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .hero > * { animation: fadeUp 0.6s ease both; }
  .hero .hero-eyebrow { animation-delay: 0.1s; }
  .hero h1            { animation-delay: 0.2s; }
  .hero .hero-sub     { animation-delay: 0.3s; }
  .hero .badge-row    { animation-delay: 0.4s; }
</style>
</head>
<body>

<div class="hero">
  <div class="hero-flag">
    <span class="flag-stripe"></span>
    <span style="width:6px"></span>
    <span class="flag-stripe"></span>
    <span style="width:6px"></span>
    <span class="flag-stripe"></span>
  </div>
  <p class="hero-eyebrow">📊 Data Analysis Case Study</p>
  <h1>
    <span class="saffron">India</span> CPI<br>
    <span class="green">Inflation</span> <span class="blue">Analysis</span>
  </h1>
  <p class="hero-sub">
    A comprehensive Excel-based case study examining Consumer Price Index trends,
    sectoral breakdowns, oil price correlations, and COVID-19 impact on inflation
    across Rural, Urban, and Combined segments in India.
  </p>
  <div class="badge-row">
    <span class="badge badge-saffron">📅 2013 – 2023</span>
    <span class="badge badge-green">🌾 Rural + Urban</span>
    <span class="badge badge-blue">📈 7 Analysis Sheets</span>
    <span class="badge badge-gold">🛢️ Oil Price Trends</span>
    <span class="badge badge-green">🦠 COVID Impact</span>
  </div>
</div>

<div class="divider"><span></span><span></span><span></span></div>

<div class="container">

  <div class="section">
    <div class="section-title"><div class="icon icon-saffron">📌</div>At a Glance</div>
    <div class="kpi-grid">
      <div class="kpi-card c-saffron"><div class="kpi-value">2013</div><div class="kpi-label">Data Start Year</div></div>
      <div class="kpi-card c-blue"><div class="kpi-value">2023</div><div class="kpi-label">Data End Year</div></div>
      <div class="kpi-card c-green"><div class="kpi-value">27+</div><div class="kpi-label">CPI Categories</div></div>
      <div class="kpi-card c-gold"><div class="kpi-value">3</div><div class="kpi-label">Sectors Tracked</div></div>
      <div class="kpi-card c-red"><div class="kpi-value">7</div><div class="kpi-label">Analysis Sheets</div></div>
      <div class="kpi-card c-white"><div class="kpi-value">44%</div><div class="kpi-label">Food's CPI Weight</div></div>
    </div>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-green">🧭</div>Project Overview</div>
    <div class="card">
      <p style="color:rgba(255,255,255,0.7); margin-bottom:14px;">
        This case study analyzes India's <strong style="color:white">Consumer Price Index (CPI)</strong> data from
        <strong style="color:var(--saffron)">January 2013</strong> to <strong style="color:var(--saffron)">2023</strong>,
        tracking inflation across 27+ product categories including Food, Clothing, Housing, Fuel, Health, Transport, and Education.
      </p>
      <p style="color:rgba(255,255,255,0.7); margin-bottom:14px;">
        The dataset is split across <strong style="color:white">Rural</strong>, <strong style="color:white">Urban</strong>,
        and <strong style="color:white">Rural+Urban</strong> sectors. The study addresses sectoral CPI weights,
        year-over-year trends, oil price correlations, and the COVID-19 inflation impact.
      </p>
      <p style="color:rgba(255,255,255,0.55); font-size:13px;">
        📁 File: <code style="color:var(--blue-light)">CaseStudy_India_CPI_Inflation.xlsx</code>
      </p>
    </div>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-blue">📋</div>Workbook Structure — 7 Sheets</div>
    <div class="sheets-grid">
      <div class="sheet-card"><div class="sheet-num">01</div><div class="sheet-info"><h4>CPI_Inflation</h4><p>Raw CPI data with Sector, Year, Month, Original Classification, CPI Value and Classified Category columns.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">02</div><div class="sheet-info"><h4>Main</h4><p>Wide-format pivot with all 27 product categories as columns, broken by Sector, Year, and Month.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">03</div><div class="sheet-info"><h4>Sector Wise Allocation</h4><p>Identifies which broad category contributes most to CPI. Food leads at ~44% weight.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">04</div><div class="sheet-info"><h4>Y-O-Y Trend in CPI</h4><p>Year-over-Year CPI trend for Rural + Urban from 2013 onwards tracking General Index movement.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">05</div><div class="sheet-info"><h4>MoM Growth</h4><p>Month-over-Month growth for Vegetables, Fruits, Pulses, and Milk from June 2022 to May 2023.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">06</div><div class="sheet-info"><h4>Oil Price Trends</h4><p>Correlation analysis between oil price fluctuations and Fuel & Transport CPI categories.</p></div></div>
      <div class="sheet-card"><div class="sheet-num">07</div><div class="sheet-info"><h4>Inflation %</h4><p>CPI inflation % before and after COVID-19, focusing on Healthcare, Food, and Essential Services.</p></div></div>
    </div>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-gold">🔍</div>Key Analyses Performed</div>
    <div class="analysis-grid">
      <div class="analysis-card"><h4><span class="dot dot-saffron"></span>Sector Allocation in CPI</h4><p>Food dominates at ~44%, followed by Luxury (14.8%), Clothing (11.1%), and Housing (7.4%).</p></div>
      <div class="analysis-card"><h4><span class="dot dot-blue"></span>Year-over-Year CPI Trend</h4><p>General Index tracked for Rural, Urban, Combined from 2013–2023 with notable acceleration post-2020.</p></div>
      <div class="analysis-card"><h4><span class="dot dot-green"></span>Month-over-Month Growth</h4><p>MoM growth for Vegetables, Fruits, Pulses, Milk during June 2022 – May 2023 to capture seasonal volatility.</p></div>
      <div class="analysis-card"><h4><span class="dot dot-gold"></span>Oil Price Correlation</h4><p>CORREL between imported oil prices and Fuel & Transport CPI to find which tracks oil prices most strongly.</p></div>
      <div class="analysis-card"><h4><span class="dot dot-red"></span>COVID-19 Inflation Impact</h4><p>Pre vs post-COVID inflation % for Healthcare, Food & Beverages, and Household Goods. Healthcare spiked sharply.</p></div>
      <div class="analysis-card"><h4><span class="dot dot-saffron"></span>Time Intelligence</h4><p>CPI values broken down by YTD, QTD, and MTD periods for granular trend comparison across years.</p></div>
    </div>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-red">💡</div>Key Findings & Insights</div>
    <ul class="insight-list">
      <li><span class="num">01</span><span>🌾 <strong style="color:white">Food & Beverages</strong> has the highest CPI basket weight at ~44%, making it the biggest inflation driver in India.</span></li>
      <li><span class="num">02</span><span>📈 CPI showed a <strong style="color:white">consistent upward trend from 2013 to 2023</strong> with Rural CPI slightly outpacing Urban in early years.</span></li>
      <li><span class="num">03</span><span>🛢️ <strong style="color:white">Fuel & Light</strong> and <strong style="color:white">Transport & Communication</strong> showed strong positive correlation with imported oil price fluctuations.</span></li>
      <li><span class="num">04</span><span>🦠 Post-COVID (2020+), <strong style="color:white">Healthcare and Household goods</strong> inflation accelerated significantly vs pre-COVID baselines.</span></li>
      <li><span class="num">05</span><span>🥬 <strong style="color:white">Vegetables</strong> showed the highest month-over-month volatility among perishables in the 2022–2023 period.</span></li>
      <li><span class="num">06</span><span>🏙️ <strong style="color:white">Urban CPI</strong> was generally lower than Rural CPI for food categories, reflecting better supply chain infrastructure.</span></li>
    </ul>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-blue">🛠️</div>Tools & Technologies</div>
    <div class="tech-row">
      <div class="tech-pill"><span class="dot dot-green"></span> Microsoft Excel</div>
      <div class="tech-pill"><span class="dot dot-saffron"></span> Pivot Tables</div>
      <div class="tech-pill"><span class="dot dot-blue"></span> CORREL Formula</div>
      <div class="tech-pill"><span class="dot dot-gold"></span> Data Validation</div>
      <div class="tech-pill"><span class="dot dot-red"></span> Conditional Formatting</div>
      <div class="tech-pill"><span class="dot dot-green"></span> Charts & Graphs</div>
      <div class="tech-pill"><span class="dot dot-blue"></span> Power Query (ETL)</div>
      <div class="tech-pill"><span class="dot dot-saffron"></span> Statistical Analysis</div>
    </div>
  </div>

  <div class="section">
    <div class="section-title"><div class="icon icon-gold">📂</div>File Structure</div>
    <div class="tree">
      <div><span class="folder">📁 India-CPI-Inflation-CaseStudy/</span></div>
      <div>&nbsp;&nbsp;├── <span class="file">📊 CaseStudy_India_CPI_Inflation.xlsx</span></div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 1:</span> CPI_Inflation &nbsp;&nbsp;&nbsp;← Raw data</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 2:</span> Main &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;← Wide pivot</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 3:</span> Sector wise allocation</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 4:</span> Y-O-Y trend in CPI</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 5:</span> MoM Growth</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── <span class="sheet">Sheet 6:</span> Oil Price Trends</div>
      <div>&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── <span class="sheet">Sheet 7:</span> Inflation %</div>
      <div>&nbsp;&nbsp;└── <span class="file">📄 README.html</span></div>
    </div>
  </div>

</div>

<div class="divider"><span></span><span></span><span></span></div>

<div class="footer">
  <p style="margin-bottom:8px;">🇮🇳 &nbsp; India CPI Inflation Case Study &nbsp;•&nbsp; Data Analysis Project</p>
  <p>Built with ❤️ using Microsoft Excel &nbsp;|&nbsp; Data: Ministry of Statistics & Programme Implementation (MoSPI), India</p>
</div>

</body>
</html>
