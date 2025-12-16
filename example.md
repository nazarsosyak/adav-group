---
title: "The Story"
permalink: /story/
layout: default
---

## **Part I: Market Segmentation**

Before accusing any individual stock of driving a crisis, we must first
identify *when* the market itself entered abnormal regimes.

We therefore begin with the only element the market cannot conceal:  
**the aggregate return timeline**, segmented into statistically homogeneous periods.

<div class="plot-container" style="text-align: center; margin: 2rem 0;">
  <iframe
    src="{{ '/assets/plots/segmentation.html' | relative_url }}"
    loading="lazy"
    style="width:100%; height:480px; border:none;">
  </iframe>

  <p class="plot-caption" style="margin-top: 0.75rem; font-size: 0.95rem; color: #555;">
    <strong>Figure 1 — Market return segmentation over time.</strong><br>
    Weekly mean market returns with detected regime segments shown as background shading.
    Each colored region corresponds to a period of statistically similar market behavior.
  </p>
</div>
This segmentation reveals several extended periods of abnormal market dynamics,
characterized by persistently negative returns and increased volatility.
Notably, the most severe segments coincide with well-known systemic crises,
including the dot-com bubble burst, the 2008 financial crisis, and the COVID-19 shock.

These periods serve as our **outbreak windows** in the subsequent analysis.
Rather than analyzing the full timeline uniformly, we focus on these segments
to study how financial contagion emerges, propagates, and eventually dissipates.

### What we did

We segmented the market timeline into consecutive regimes using **dynamic programming**.
The segmentation groups periods with **similar average market returns**, allowing us
to detect **structural changes in market behavior** without relying on predefined crisis dates.

**Table 1 — Major crisis periods identified by market segmentation.**

| Crisis episode            | Start date | End date   | Duration (weeks) | Cumulative market return | Interpretation |
|---------------------------|------------|------------|------------------|--------------------------|----------------|
| Dot-com bubble burst      | 2000-09-08 | 2000-10-20 | 6                | **−19.49%**              | Tech-driven systemic correction |
| Subprime financial crisis | 2008-10-03 | 2008-10-24 | 3                | **−22.02%**              | Global banking and credit collapse |
| COVID-19 market shock     | 2020-02-21 | 2020-04-10 | 7                | **−22.90%**              | Exogenous shock and synchronized sell-off |

These regimes correspond to well-known systemic crises and validate the segmentation approach.
Despite differences in duration, all three periods exhibit sharp cumulative losses,
highlighting moments of extreme market stress.

In the remainder of this project, we focus on these segments as **financial outbreak windows**,
within which we study contagion dynamics, transmission pathways, and network-level amplification effects.

All identified crisis periods exhibit cumulative losses exceeding 19%, confirming their systemic severity
and justifying their use as outbreak windows in the subsequent contagion analysis.

---

## **Part II: Choose a case file**

<div class="segment-row">

  <button class="segment-card is-active"
       type="button"
       data-target="panel-dotcom"
       data-bg="#F5F6FC"
       data-accent="#2E357A"
       aria-selected="true">
    <img src="{{ '/assets/images/internet.png' | relative_url }}" alt="Dot-com Bubble">
    <div class="segment-title">Dot-com Bubble</div>
  </button>

  <button class="segment-card"
       type="button"
       data-target="panel-subprime"
       data-bg="#F4FBF6"
       data-accent="#1F6B3A"
       aria-selected="false">
    <img src="{{ '/assets/images/subprime.png' | relative_url }}" alt="Subprime Crisis">
    <div class="segment-title">Subprime Crisis</div>
  </button>

  <button class="segment-card"
       type="button"
       data-target="panel-covid"
       data-bg="#FDFDF8"
       data-accent="#6A5F12"
       aria-selected="false">
    <img src="{{ '/assets/images/covid.png' | relative_url }}" alt="COVID Outbreak">
    <div class="segment-title">COVID Outbreak</div>
  </button>

</div>

---

<div class="case-panels">

  <!-- ===================================================== -->
  <!-- DOTCOM -->
  <!-- ===================================================== -->

  <section id="panel-dotcom" class="case-panel is-visible">
    <h3>Case File: Dot-com Bubble</h3>

    <div class="panel-intro">
      <img src="{{ '/assets/images/internetintro.png' | relative_url }}" alt="Dot-com Bubble intro">
    </div>


    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}"></iframe>
    </div>

    <p>
      The market yields negative daily returns approximately 77% of the time. In order to match the cumulative return of -19.49% over the whole period, negative returns must therefore carry a stronger weight than positive ones. To understand what is happening behind the scenes, we put our immunological framework to the test. The objective is to identify the patient zero, or the first entity that contracted the “virus” and ignited the epidemic. The algorithm is also designed to detect super-spreaders, meaning entities that, once contaminated, exhibit an abnormally high transmission rate, as well as entities that are sick or at risk. An entity is labeled sick if its daily return crosses the −5% threshold and if its cumulative return over the entire period falls below −20%. Entities at risk are those that maintain strong connections, either through correlation or causal exposure, with sick entities. Over time, entities may recover and are then labeled recovered, while those unaffected throughout the episode remain healthy.
    </p>

    <p>
      You can press the <span class="text-accent">red button</span> below to initiate the analysis.
    </p>

    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#dotcom-output"
         data-overlay="#dotcom-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <div id="dotcom-overlay" class="analysis-overlay" hidden>
      <div class="analysis-modal">
        <div class="spinner"></div>
        <div class="analysis-title">Running outbreak analysis…</div>
        <div class="analysis-status">Initializing…</div>
      </div>
    </div>


    <div id="dotcom-output" class="analysis-output is-locked">
      <div class="plot-frame plot-frame--first">
          <iframe
            src="{{ '/assets/plots/ppi_3d_internet.html' | relative_url }}"
            loading="lazy"
            title="Dot-com 3D plot"></iframe>
        </div>
        
      <p>
        Two interactive plots for the network have been generated below. Patient zero has been identified as entity <span class="text-accent">ROST</span>:
      </p>

      <p>
        <span class="text-accent">Ross Stores is an american company specializing in hard-discount hypermarkets.</span>
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/internet' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        Network reconstruction reveals super-spreaders that amplify contagion through correlation.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/internet' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>
    </div>
  </section>

  <!-- ===================================================== -->
  <!-- SUBPRIME -->
  <!-- ===================================================== -->

  <section id="panel-subprime" class="case-panel">
    <h3>Case File: Subprime Crisis</h3>

    <div class="panel-intro">
      <img src="{{ '/assets/images/subprimeintro.png' | relative_url }}" alt="Subprime Crisis intro">
    </div>

    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}"></iframe>
    </div>

    <p>
      Credit stress does not stay local.  
      This regime is short but brutal, propagating through financial exposure.
    </p>

    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#subprime-output"
         data-overlay="#subprime-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <div id="subprime-overlay" class="analysis-overlay" hidden>
      <div class="analysis-modal">
        <div class="spinner"></div>
        <div class="analysis-title">Running outbreak analysis…</div>
        <div class="analysis-status">Initializing…</div>
      </div>
    </div>

    <div id="subprime-output" class="analysis-output is-locked">

      <div class="plot-frame plot-frame--first">
          <iframe
            src="{{ '/assets/plots/ppi_2008.html' | relative_url }}"
            loading="lazy"
            title="Subprime 3D plot"></iframe>
        </div>
        
      <p>
        Losses propagate through tightly coupled financial institutions.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/subprime' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        The network exposes institutions acting as systemic amplifiers.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/subprime' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>
    </div>
  </section>

  <!-- ===================================================== -->
  <!-- COVID -->
  <!-- ===================================================== -->

  <section id="panel-covid" class="case-panel">
    <h3>Case File: COVID-19</h3>

    <div class="panel-intro">
      <img src="{{ '/assets/images/covidintro.png' | relative_url }}" alt="COVID-19 intro">
    </div>

    
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}"></iframe>
    </div>

    <p>
      A fast global transmission with extreme co-movement.
    </p>

    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#covid-output"
         data-overlay="#covid-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <div id="covid-overlay" class="analysis-overlay" hidden>
      <div class="analysis-modal">
        <div class="spinner"></div>
        <div class="analysis-title">Running outbreak analysis…</div>
        <div class="analysis-status">Initializing…</div>
      </div>
    </div>

    <div id="covid-output" class="analysis-output is-locked">
    
      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/plots/ppi_3d_covid.html' | relative_url }}"
          loading="lazy"
          title="COVID 3D plot"></iframe>
      </div>

      <p>
        The timeline shows synchronized global drawdowns.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/covid' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        The network confirms market-wide immune system failure.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/covid' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>
    </div>
  </section>

</div>

<script>
document.addEventListener("DOMContentLoaded", () => {

  /* =========================
     IMAGE SLIDER BUILDER
     ========================= */

  function padNum(n, pad) {
    return String(n).padStart(pad, "0");
  }

  async function detectMaxFrame(folder, prefix, pad) {
    const tryLoad = (src) =>
      new Promise((resolve) => {
        const img = new Image();
        img.onload = () => resolve(true);
        img.onerror = () => resolve(false);
        img.src = src;
      });

    let i = 1;
    const CAP = 500;

    while (i <= CAP) {
      const src = `${folder}/${prefix}${padNum(i, pad)}.png`;
      const ok = await tryLoad(src);
      if (!ok) return Math.max(1, i - 1);
      i += 1;
    }
    return CAP;
  }

  async function initOneSlider(el) {
    if (el.dataset.ready === "true") return;

    const folder = el.getAttribute("data-folder");
    const prefix = el.getAttribute("data-prefix") || "";
    const pad = parseInt(el.getAttribute("data-pad") || "4", 10);

    if (!folder) return;
    el.dataset.ready = "true";

    const top = document.createElement("div");
    top.className = "img-slider-top";

    const range = document.createElement("input");
    range.type = "range";
    range.min = "1";
    range.value = "1";
    range.className = "img-slider-range";

    const label = document.createElement("div");
    label.className = "img-slider-label";
    label.textContent = "Frame 1";

    top.appendChild(range);
    top.appendChild(label);

    const img = document.createElement("img");
    img.className = "img-slider-img";

    el.appendChild(top);
    el.appendChild(img);

    const maxFrame = await detectMaxFrame(folder, prefix, pad);
    range.max = String(maxFrame);

    function update() {
      const i = parseInt(range.value, 10);
      img.src = `${folder}/${prefix}${padNum(i, pad)}.png`;
      label.textContent = `Frame ${i} / ${maxFrame}`;
    }

    range.addEventListener("input", update);
    update();
  }

  async function initSliders(root = document) {
    const sliders = Array.from(root.querySelectorAll(".img-slider"));
    for (const el of sliders) {
      // eslint-disable-next-line no-await-in-loop
      await initOneSlider(el);
    }
  }

  /* =========================
     PANEL SWITCHING + THEMING
     ========================= */

  const buttons = Array.from(document.querySelectorAll(".segment-card"));
  const panels  = Array.from(document.querySelectorAll(".case-panel"));

  function applyTheme(bg, accent) {
    document.documentElement.style.setProperty("--page-bg", bg);
    document.documentElement.style.setProperty("--content-accent", accent);
    document.documentElement.style.setProperty("--panel-bg", bg);
    document.documentElement.style.setProperty("--panel-accent", accent);
  }

  function showPanel(targetId, btn) {
    buttons.forEach(b => {
      b.classList.toggle("is-active", b === btn);
      b.setAttribute("aria-selected", b === btn ? "true" : "false");
    });

    panels.forEach(p => p.classList.remove("is-visible"));
    const panel = document.getElementById(targetId);
    if (panel) panel.classList.add("is-visible");

    const bg = btn.getAttribute("data-bg") || "#ffffff";
    const accent = btn.getAttribute("data-accent") || "#2aa36b";
    applyTheme(bg, accent);
  }

  buttons.forEach(btn => {
    btn.addEventListener("click", () => showPanel(btn.dataset.target, btn));
  });

  const active = document.querySelector(".segment-card.is-active") || buttons[0];
  if (active) showPanel(active.dataset.target, active);

  /* =========================
     RUN ANALYSIS BUTTON LOGIC
     ========================= */

  const runButtons = Array.from(document.querySelectorAll(".run-analysis-btn"));

  runButtons.forEach((btn) => {
    btn.addEventListener("click", () => {
      const runSel = btn.getAttribute("data-run");
      const overlaySel = btn.getAttribute("data-overlay");

      const out = runSel ? document.querySelector(runSel) : null;
      const overlay = overlaySel ? document.querySelector(overlaySel) : null;

      if (!out || !overlay) return;

      btn.classList.add("is-pressed", "is-rippling");
      setTimeout(() => btn.classList.remove("is-rippling"), 600);

      overlay.classList.add("is-open");
      overlay.style.setProperty("--prog", "0");

      const statusEl = overlay.querySelector(".analysis-status");
      const steps = [
        { txt: "Initializing…",            p: 12 },
        { txt: "Loading data…",            p: 28 },
        { txt: "Reconstructing network…",  p: 52 },
        { txt: "Detecting patient zero…",  p: 73 },
        { txt: "Scoring super-spreaders…", p: 90 },
        { txt: "Finalizing…",              p: 100 }
      ];

      let i = 0;
      if (statusEl) statusEl.textContent = steps[i].txt;
      overlay.style.setProperty("--prog", String(steps[i].p));

      const tick = () => {
        i += 1;

        if (i < steps.length) {
          if (statusEl) statusEl.textContent = steps[i].txt;
          overlay.style.setProperty("--prog", String(steps[i].p));
          setTimeout(tick, 520);
          return;
        }

        overlay.classList.remove("is-open");

        out.classList.remove("is-locked");
        out.style.display = "block";

        initSliders(out).then(() => {
          out.querySelectorAll(".img-slider-img").forEach((img) => {
            if (img.complete) img.classList.add("is-loaded");
            else img.addEventListener("load", () => img.classList.add("is-loaded"), { once: true });
          });
        });

        btn.classList.remove("is-pressed");
        btn.disabled = true;
      };

      setTimeout(tick, 520);
    });
  });

  // ALSO build sliders immediately
  initSliders();

});
</script>

