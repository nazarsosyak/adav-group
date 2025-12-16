---
title: "The Story"
permalink: /story/
layout: default
---

## **Part I: Market Segmentation**

Before we accuse anyone, we need a crime scene.

So we start with the only thing the market can’t hide: the timeline.

<div class="full-width-plot">
  <iframe
    src="{{ '/assets/plots/segmentation.html' | relative_url }}"
    loading="lazy"></iframe>
</div>

### What we did

We segmented the market timeline into consecutive regimes using dynamic programming.
Periods are grouped by **similar average returns**, revealing structural regime changes.

| Period name               | Start date | End date   | Duration (weeks) | Cumulative return |
| ------------------------- | ---------- | ---------- | ---------------- | ----------------- |
| Dot-com bubble burst      | 2000-09-08 | 2000-10-20 | 6                | **−19.49%**       |
| Subprime financial crisis | 2008-10-03 | 2008-10-24 | 3                | **−22.02%**       |
| COVID-19 market shock     | 2020-02-21 | 2020-04-10 | 7                | **−22.90%**       |

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

    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}"></iframe>
    </div>

    <p>
      The market yields negative daily returns approximately x% of the time. In order to obtain a cumulative return of x% over the whole period, negative returns must therefore carry a stronger weight than positive ones. To understand what is happening behind the scenes, we put our immunological framework to the test. The objective is to identify the patient zero, or the first entity that contracted the “virus” and ignited the epidemic. The algorithm is also designed to detect super-spreaders, meaning entities that, once contaminated, exhibit an abnormally high transmission rate, as well as entities that are sick or at risk. An entity is labeled sick if its daily return crosses the −5% threshold and if its cumulative return over the entire period falls below −20%. Entities at risk are those that maintain strong connections, either through correlation or causal exposure, with sick entities. Over time, entities may recover and are then labeled recovered, while those unaffected throughout the episode remain healthy.
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

      <p>
        The timeline highlights how early losses in technology rapidly contaminate adjacent sectors.
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
/* Panel switching + per-panel theming (bg + accent)
   + Run analysis button logic */
document.addEventListener("DOMContentLoaded", () => {
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

  // wire panel clicks
  buttons.forEach(btn => {
    btn.addEventListener("click", () => showPanel(btn.dataset.target, btn));
  });

  // initial theme (from the active button)
  const active = document.querySelector(".segment-card.is-active") || buttons[0];
  if (active) showPanel(active.dataset.target, active);

  // wire run analysis buttons
  const runButtons = Array.from(document.querySelectorAll(".run-analysis-btn"));

  runButtons.forEach((btn) => {
    btn.addEventListener("click", () => {
      const runSel = btn.getAttribute("data-run");
      const overlaySel = btn.getAttribute("data-overlay");

      const out = runSel ? document.querySelector(runSel) : null;
      const overlay = overlaySel ? document.querySelector(overlaySel) : null;

      if (!out || !overlay) return;

      overlay.hidden = false;

      const statusEl = overlay.querySelector(".analysis-status");
      const steps = [
        "Initializing…",
        "Loading data…",
        "Reconstructing network…",
        "Detecting patient zero…",
        "Scoring super-spreaders…",
        "Finalizing…"
      ];

      let i = 0;
      if (statusEl) statusEl.textContent = steps[i];

      const timer = setInterval(() => {
        i += 1;

        if (i < steps.length) {
          if (statusEl) statusEl.textContent = steps[i];
          return;
        }

        clearInterval(timer);

        overlay.hidden = true;
        out.classList.remove("is-locked");
        out.style.display = "block";

        // optional: don't re-run
        btn.disabled = true;
      }, 550);
    });
  });
});
</script>
