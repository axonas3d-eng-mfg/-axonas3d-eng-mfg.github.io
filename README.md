# -axonas3d-eng-mfg.github.io<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Axonas — Get a Quote</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --red: #cc2b2b;
    --red-dim: rgba(204,43,43,0.12);
    --red-border: rgba(204,43,43,0.3);
    --bg: #0d0d0f;
    --bg2: #141418;
    --bg3: #1a1a20;
    --border: rgba(255,255,255,0.08);
    --text: #f0f0f0;
    --muted: rgba(255,255,255,0.4);
    --mono: 'DM Mono', monospace;
    --sans: 'DM Sans', sans-serif;
    --display: 'Bebas Neue', sans-serif;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
    z-index: 0;
  }

  /* Nav */
  nav {
    position: relative;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 48px;
    border-bottom: 1px solid var(--border);
    background: rgba(13,13,15,0.9);
    backdrop-filter: blur(12px);
  }

  .nav-brand {
    font-family: var(--display);
    font-size: 28px;
    letter-spacing: 0.08em;
    color: var(--text);
  }
  .nav-brand span { color: var(--red); }

  .nav-tag {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* Main layout */
  main {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  .page-title {
    font-family: var(--display);
    font-size: 64px;
    letter-spacing: 0.04em;
    line-height: 0.95;
    margin-bottom: 12px;
  }
  .page-title em { font-style: normal; color: var(--red); }

  .page-sub {
    font-size: 15px;
    font-weight: 300;
    color: var(--muted);
    margin-bottom: 48px;
    line-height: 1.6;
  }

  /* Steps progress */
  .steps-bar {
    display: flex;
    align-items: center;
    gap: 0;
    margin-bottom: 48px;
  }

  .step-pill {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 8px 18px;
    border: 1px solid var(--border);
    border-radius: 100px;
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    transition: all 0.3s;
    cursor: default;
  }
  .step-pill.active {
    border-color: var(--red-border);
    background: var(--red-dim);
    color: var(--text);
  }
  .step-pill.done {
    border-color: rgba(255,255,255,0.15);
    color: rgba(255,255,255,0.6);
  }
  .step-num {
    width: 20px; height: 20px;
    border-radius: 50%;
    background: rgba(255,255,255,0.08);
    display: flex; align-items: center; justify-content: center;
    font-size: 10px; font-weight: 500;
  }
  .step-pill.active .step-num { background: var(--red); color: #fff; }
  .step-pill.done .step-num { background: rgba(255,255,255,0.2); }

  .step-connector {
    flex: 1;
    height: 1px;
    background: var(--border);
    max-width: 32px;
  }

  /* Panels */
  .panel {
    display: none;
    animation: fadeIn 0.3s ease;
  }
  .panel.active { display: block; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Upload zone */
  .upload-zone {
    border: 1.5px dashed rgba(255,255,255,0.15);
    border-radius: 12px;
    padding: 64px 40px;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
    position: relative;
    background: var(--bg2);
  }
  .upload-zone:hover, .upload-zone.drag-over {
    border-color: var(--red);
    background: var(--red-dim);
  }
  .upload-zone input[type="file"] {
    position: absolute; inset: 0; opacity: 0; cursor: pointer; width: 100%; height: 100%;
  }

  .upload-icon {
    width: 56px; height: 56px;
    margin: 0 auto 20px;
    background: rgba(255,255,255,0.05);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
  }
  .upload-icon svg { width: 28px; height: 28px; stroke: var(--muted); fill: none; stroke-width: 1.5; }

  .upload-title {
    font-size: 18px; font-weight: 500; margin-bottom: 8px;
  }
  .upload-sub {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.1em;
    color: var(--muted);
    text-transform: uppercase;
  }

  .file-info {
    display: none;
    margin-top: 20px;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 20px;
    text-align: left;
    align-items: center;
    gap: 14px;
  }
  .file-info.visible { display: flex; }
  .file-name { font-size: 14px; font-weight: 500; flex: 1; }
  .file-size { font-family: var(--mono); font-size: 11px; color: var(--muted); }
  .file-remove {
    width: 24px; height: 24px;
    background: rgba(255,255,255,0.06);
    border: none; border-radius: 50%; color: var(--muted);
    cursor: pointer; display: flex; align-items: center; justify-content: center;
    font-size: 14px;
  }

  /* Config grid */
  .config-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 24px;
  }

  .field-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .field-group.full { grid-column: 1 / -1; }

  label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.18em;
    color: var(--muted);
    text-transform: uppercase;
  }

  select, input[type="text"], input[type="email"], input[type="number"], textarea {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 12px 14px;
    color: var(--text);
    font-family: var(--sans);
    font-size: 14px;
    outline: none;
    transition: border-color 0.2s;
    width: 100%;
    appearance: none;
    -webkit-appearance: none;
  }
  select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23666' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 14px center; padding-right: 36px; }
  select:focus, input:focus, textarea:focus { border-color: rgba(204,43,43,0.5); }
  textarea { resize: vertical; min-height: 90px; }

  /* Quantity stepper */
  .qty-wrap {
    display: flex;
    align-items: center;
    gap: 0;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    overflow: hidden;
  }
  .qty-btn {
    width: 40px; height: 44px;
    background: none; border: none;
    color: var(--muted); font-size: 20px; cursor: pointer;
    transition: background 0.15s;
    flex-shrink: 0;
  }
  .qty-btn:hover { background: rgba(255,255,255,0.06); color: var(--text); }
  .qty-input {
    border: none !important;
    text-align: center;
    background: transparent !important;
    width: 60px;
    border-radius: 0 !important;
  }

  /* Price estimate */
  .price-bar {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 18px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 24px;
  }
  .price-label { font-family: var(--mono); font-size: 11px; color: var(--muted); letter-spacing: 0.12em; text-transform: uppercase; }
  .price-val { font-family: var(--display); font-size: 36px; letter-spacing: 0.05em; color: var(--text); }
  .price-val span { color: var(--red); font-size: 22px; }
  .price-note { font-size: 11px; color: var(--muted); margin-top: 2px; }

  /* Buttons */
  .btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 14px 28px;
    border-radius: 6px;
    font-family: var(--mono);
    font-size: 12px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    transition: all 0.2s;
    font-weight: 500;
  }
  .btn-primary {
    background: var(--red);
    color: #fff;
  }
  .btn-primary:hover { background: #b52424; }
  .btn-outline {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--muted);
  }
  .btn-outline:hover { border-color: rgba(255,255,255,0.25); color: var(--text); }

  .btn-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 8px;
  }

  /* Summary panel */
  .summary-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    margin-bottom: 24px;
  }
  .summary-head {
    padding: 18px 24px;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; justify-content: space-between;
  }
  .summary-head-title { font-family: var(--mono); font-size: 11px; letter-spacing: 0.15em; text-transform: uppercase; color: var(--muted); }
  .summary-rows { padding: 8px 0; }
  .summary-row {
    display: flex; justify-content: space-between; align-items: center;
    padding: 10px 24px;
    font-size: 14px;
  }
  .summary-row + .summary-row { border-top: 1px solid rgba(255,255,255,0.04); }
  .summary-key { color: var(--muted); font-size: 13px; }
  .summary-val { font-weight: 500; }
  .summary-total {
    border-top: 1px solid var(--border);
    padding: 16px 24px;
    display: flex; justify-content: space-between; align-items: center;
  }
  .total-label { font-family: var(--mono); font-size: 11px; letter-spacing: 0.15em; text-transform: uppercase; color: var(--muted); }
  .total-val { font-family: var(--display); font-size: 32px; color: var(--text); }

  /* Success screen */
  .success-screen {
    text-align: center;
    padding: 60px 20px;
  }
  .success-icon {
    width: 72px; height: 72px;
    border-radius: 50%;
    background: rgba(34,197,94,0.1);
    border: 1px solid rgba(34,197,94,0.25);
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 28px;
  }
  .success-icon svg { width: 32px; height: 32px; stroke: #22c55e; fill: none; stroke-width: 2; }
  .success-title { font-family: var(--display); font-size: 52px; margin-bottom: 14px; }
  .success-msg { font-size: 15px; color: var(--muted); line-height: 1.7; max-width: 420px; margin: 0 auto; }

  /* Accent bar left */
  .accent-bar {
    position: fixed;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(to bottom, var(--red) 0%, var(--red) 30%, transparent 100%);
    z-index: 100;
  }

  @media (max-width: 600px) {
    nav { padding: 16px 20px; }
    main { padding: 36px 16px 60px; }
    .page-title { font-size: 44px; }
    .config-grid { grid-template-columns: 1fr; }
    .steps-bar { gap: 4px; }
    .step-pill { padding: 7px 12px; font-size: 10px; }
    .step-connector { max-width: 16px; }
  }
</style>
</head>
<body>
<div class="accent-bar"></div>

<nav>
  <div class="nav-brand">AX<span>O</span>NAS</div>
  <div class="nav-tag">// 3D Manufacturing Studio</div>
</nav>

<main>
  <h1 class="page-title">Get your <em>quote</em><br>instantly.</h1>
  <p class="page-sub">Upload your CAD file, configure your print settings, and confirm — we'll get in touch to finalize your order.</p>

  <!-- Steps bar -->
  <div class="steps-bar">
    <div class="step-pill active" id="spill-1">
      <span class="step-num">1</span> Upload file
    </div>
    <div class="step-connector"></div>
    <div class="step-pill" id="spill-2">
      <span class="step-num">2</span> Configure
    </div>
    <div class="step-connector"></div>
    <div class="step-pill" id="spill-3">
      <span class="step-num">3</span> Confirm
    </div>
    <div class="step-connector"></div>
    <div class="step-pill" id="spill-4">
      <span class="step-num">4</span> Done
    </div>
  </div>

  <!-- Panel 1: Upload -->
  <div class="panel active" id="panel-1">
    <div class="upload-zone" id="uploadZone">
      <input type="file" id="fileInput" accept=".stl,.obj,.step,.stp,.3mf,.iges,.igs">
      <div class="upload-icon">
        <svg viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
      </div>
      <div class="upload-title">Drop your file here</div>
      <div class="upload-sub">STL · OBJ · STEP · 3MF · IGES &nbsp;—&nbsp; Max 100MB</div>
    </div>

    <div class="file-info" id="fileInfo">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1.5"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
      <span class="file-name" id="fileName">—</span>
      <span class="file-size" id="fileSize">—</span>
      <button class="file-remove" onclick="removeFile()">✕</button>
    </div>

    <div class="btn-row" style="margin-top:28px; justify-content:flex-end;">
      <button class="btn btn-primary" onclick="goTo(2)" id="nextBtn1" disabled>
        Continue <span style="font-size:16px;">→</span>
      </button>
    </div>
  </div>

  <!-- Panel 2: Configure -->
  <div class="panel" id="panel-2">
    <div class="config-grid">
      <div class="field-group">
        <label>Print technology</label>
        <select id="tech" onchange="updatePrice()">
          <option value="fdm">FDM — Fused Deposition</option>
          <option value="msla">MSLA — Resin (high detail)</option>
        </select>
      </div>

      <div class="field-group">
        <label>Material</label>
        <select id="material" onchange="updatePrice()">
          <option value="pla">PLA (standard)</option>
          <option value="petg">PETG (tough)</option>
          <option value="abs">ABS (heat resistant)</option>
          <option value="tpu">TPU (flexible)</option>
          <option value="asa">ASA (outdoor)</option>
          <option value="resin_std">Standard resin</option>
          <option value="resin_eng">Engineering resin</option>
          <option value="resin_cast">Castable resin (jewelry)</option>
        </select>
      </div>

      <div class="field-group">
        <label>Layer height / resolution</label>
        <select id="resolution" onchange="updatePrice()">
          <option value="draft">Draft — 0.3mm (fast)</option>
          <option value="standard" selected>Standard — 0.2mm</option>
          <option value="fine">Fine — 0.1mm</option>
          <option value="ultra">Ultra — 0.05mm (MSLA only)</option>
        </select>
      </div>

      <div class="field-group">
        <label>Infill density</label>
        <select id="infill" onchange="updatePrice()">
          <option value="15">15% — Lightweight</option>
          <option value="30" selected>30% — Standard</option>
          <option value="50">50% — Durable</option>
          <option value="100">100% — Solid</option>
        </select>
      </div>

      <div class="field-group">
        <label>Quantity</label>
        <div class="qty-wrap">
          <button class="qty-btn" onclick="changeQty(-1)">−</button>
          <input class="qty-input" type="number" id="qty" value="1" min="1" max="100" onchange="updatePrice()">
          <button class="qty-btn" onclick="changeQty(1)">+</button>
        </div>
      </div>

      <div class="field-group">
        <label>Post-processing</label>
        <select id="post" onchange="updatePrice()">
          <option value="none">None</option>
          <option value="sanding">Sanding & smoothing</option>
          <option value="painting">Sanding + painting</option>
          <option value="support">Support removal only</option>
        </select>
      </div>

      <div class="field-group full">
        <label>Special notes (optional)</label>
        <textarea id="notes" placeholder="Color preference, tolerance requirements, assembly needs..."></textarea>
      </div>
    </div>

    <div class="price-bar">
      <div>
        <div class="price-label">Estimated total</div>
        <div class="price-note">Final price confirmed after review</div>
      </div>
      <div style="text-align:right;">
        <div class="price-val"><span>$</span><span id="priceDisplay">18</span></div>
      </div>
    </div>

    <div class="btn-row">
      <button class="btn btn-outline" onclick="goTo(1)">← Back</button>
      <button class="btn btn-primary" onclick="goTo(3)">Review order →</button>
    </div>
  </div>

  <!-- Panel 3: Confirm -->
  <div class="panel" id="panel-3">
    <div class="summary-card">
      <div class="summary-head">
        <span class="summary-head-title">Order summary</span>
        <button style="background:none;border:none;color:var(--muted);cursor:pointer;font-size:12px;font-family:var(--mono);letter-spacing:0.1em;" onclick="goTo(2)">EDIT</button>
      </div>
      <div class="summary-rows" id="summaryRows"></div>
      <div class="summary-total">
        <span class="total-label">Estimated total</span>
        <span class="total-val" id="summaryTotal">$18</span>
      </div>
    </div>

    <div class="config-grid">
      <div class="field-group">
        <label>Your name</label>
        <input type="text" id="contactName" placeholder="Jane Smith">
      </div>
      <div class="field-group">
        <label>Email address</label>
        <input type="email" id="contactEmail" placeholder="jane@university.edu">
      </div>
      <div class="field-group full">
        <label>Phone (optional)</label>
        <input type="text" id="contactPhone" placeholder="+1 (555) 000-0000">
      </div>
    </div>

    <div class="btn-row">
      <button class="btn btn-outline" onclick="goTo(2)">← Back</button>
      <button class="btn btn-primary" onclick="submitOrder()">Confirm order →</button>
    </div>
  </div>

  <!-- Panel 4: Success -->
  <div class="panel" id="panel-4">
    <div class="success-screen">
      <div class="success-icon">
        <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
      </div>
      <h2 class="success-title">Order received.</h2>
      <p class="success-msg">We've got your file and specs. The Axonas team will review your order and reach out within <strong>24 hours</strong> to confirm details and payment.</p>
      <p class="success-msg" style="margin-top:16px; font-family:var(--mono); font-size:12px; color:rgba(255,255,255,0.25); letter-spacing:0.1em;">
        FDM · MSLA · Prototyping · Jewelry
      </p>
    </div>
  </div>
</main>

<script>
  let uploadedFile = null;

  // Pricing engine
  const basePrices = {
    fdm: 8, msla: 14
  };
  const materialMult = {
    pla: 1, petg: 1.2, abs: 1.25, tpu: 1.4, asa: 1.3,
    resin_std: 1, resin_eng: 1.6, resin_cast: 2.2
  };
  const resMult = { draft: 0.8, standard: 1, fine: 1.3, ultra: 1.6 };
  const infillMult = { 15: 0.85, 30: 1, 50: 1.2, 100: 1.5 };
  const postAdd = { none: 0, sanding: 6, painting: 14, support: 3 };
  const materialNames = {
    pla:'PLA',petg:'PETG',abs:'ABS',tpu:'TPU (Flexible)',asa:'ASA',
    resin_std:'Standard Resin',resin_eng:'Engineering Resin',resin_cast:'Castable Resin'
  };
  const resNames = { draft:'Draft 0.3mm', standard:'Standard 0.2mm', fine:'Fine 0.1mm', ultra:'Ultra 0.05mm' };
  const postNames = { none:'None', sanding:'Sanding & smoothing', painting:'Sanding + painting', support:'Support removal' };

  function getPrice() {
    const tech = document.getElementById('tech').value;
    const mat = document.getElementById('material').value;
    const res = document.getElementById('resolution').value;
    const inf = document.getElementById('infill').value;
    const qty = parseInt(document.getElementById('qty').value) || 1;
    const post = document.getElementById('post').value;
    let price = basePrices[tech] * (materialMult[mat]||1) * (resMult[res]||1) * (infillMult[inf]||1) * qty;
    price += postAdd[post] || 0;
    return Math.round(price);
  }

  function updatePrice() {
    document.getElementById('priceDisplay').textContent = getPrice();
    buildSummary();
  }

  function buildSummary() {
    const tech = document.getElementById('tech').value;
    const mat = document.getElementById('material').value;
    const res = document.getElementById('resolution').value;
    const inf = document.getElementById('infill').value;
    const qty = document.getElementById('qty').value;
    const post = document.getElementById('post').value;
    const notes = document.getElementById('notes').value;

    const rows = [
      ['File', document.getElementById('fileName').textContent || '—'],
      ['Technology', tech === 'fdm' ? 'FDM' : 'MSLA Resin'],
      ['Material', materialNames[mat]||mat],
      ['Resolution', resNames[res]||res],
      ['Infill', inf + '%'],
      ['Quantity', qty + ' unit(s)'],
      ['Post-processing', postNames[post]||post],
    ];
    if (notes) rows.push(['Notes', notes]);

    const html = rows.map(([k,v]) =>
      `<div class="summary-row"><span class="summary-key">${k}</span><span class="summary-val">${v}</span></div>`
    ).join('');
    document.getElementById('summaryRows').innerHTML = html;
    document.getElementById('summaryTotal').textContent = '$' + getPrice();
  }

  function goTo(step) {
    for (let i = 1; i <= 4; i++) {
      document.getElementById('panel-' + i).classList.toggle('active', i === step);
      const pill = document.getElementById('spill-' + i);
      pill.classList.remove('active', 'done');
      if (i === step) pill.classList.add('active');
      else if (i < step) pill.classList.add('done');
    }
    if (step === 3) buildSummary();
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  function changeQty(delta) {
    const el = document.getElementById('qty');
    el.value = Math.max(1, Math.min(100, parseInt(el.value||1) + delta));
    updatePrice();
  }

  function removeFile() {
    uploadedFile = null;
    document.getElementById('fileInfo').classList.remove('visible');
    document.getElementById('nextBtn1').disabled = true;
    document.getElementById('fileInput').value = '';
  }

  function handleFile(file) {
    if (!file) return;
    uploadedFile = file;
    document.getElementById('fileName').textContent = file.name;
    document.getElementById('fileSize').textContent = (file.size / 1024 / 1024).toFixed(2) + ' MB';
    document.getElementById('fileInfo').classList.add('visible');
    document.getElementById('nextBtn1').disabled = false;
  }

  document.getElementById('fileInput').addEventListener('change', e => handleFile(e.target.files[0]));

  const zone = document.getElementById('uploadZone');
  zone.addEventListener('dragover', e => { e.preventDefault(); zone.classList.add('drag-over'); });
  zone.addEventListener('dragleave', () => zone.classList.remove('drag-over'));
  zone.addEventListener('drop', e => {
    e.preventDefault();
    zone.classList.remove('drag-over');
    handleFile(e.dataTransfer.files[0]);
  });

  function submitOrder() {
    const name = document.getElementById('contactName').value.trim();
    const email = document.getElementById('contactEmail').value.trim();
    if (!name || !email) { alert('Please enter your name and email.'); return; }
    goTo(4);
  }

  updatePrice();
</script>
</body>
</html>
