---
title: "The Story"
permalink: /story/
layout: default
---

## Part I: Market Segmentation

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

| Period name                | Start date   | End date     | Duration (weeks) | Cumulative return |
|---------------------------|--------------|--------------|------------------|-------------------|
| Dot-com bubble burst      | 2000-09-08   | 2000-10-20   | 6                | **−19.49%**       |
| Subprime financial crisis | 2008-10-03   | 2008-10-24   | 3                | **−22.02%**       |
| COVID-19 market shock     | 2020-02-21   | 2020-04-10   | 7                | **−22.90%**       |

---

## Choose a case file

<div class="segment-row">

  <button class="segment-card is-active"
        data-target="panel-dotcom"
        data-bg="#F5F6FC"
        data-accent="#2E357A"
        aria-selected="true">
    <img src="{{ '/assets/images/internet.png' | relative_url }}">
    <div class="segment-title">Dot-com Bubble</div>
  </button>

  <button class="segment-card"
        data-target="panel-subprime"
        data-bg="#F4FBF6"
        data-accent="#1F6B3A"
        aria-selected="false">
    <img src="{{ '/assets/images/subprime.png' | relative_url }}">
    <div class="segment-title">Subprime Crisis</div>
  </button>

  <button class="segment-card"
        data-target="panel-covid"
        data-bg="#FDFDF8"
        data-accent="#6A5F12"
        aria-selected="false">
    <img src="{{ '/assets/images/covid.png' | relative_url }}">
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
Speculation peaks, then confidence collapses.  
Technology firms are hit first, before correlations spike and drag the rest of the market with them.
</p>

<button class="run-analysis-btn img-button"
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

<section id="panel-subprime" class="case-panel" hidden>

<h3>Case File: Subprime Crisis</h3>

<div class="plot-frame">
  <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}"></iframe>
</div>

<p>
Credit stress does not stay local.  
This regime is short but brutal, propagating through financial exposure.
</p>

<button class="run-analysis-btn img-button"
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

<section id="panel-covid" class="case-panel" hidden>

<h3>Case File: COVID-19</h3>

<div class="plot-frame">
  <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}"></iframe>
</div>

<p>
A fast global transmission with extreme co-movement.
</p>

<button class="run-analysis-btn img-button"
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
(() => {

  const statusTexts = [
    "Finding patient zero…",
    "Tracing contagion links…",
    "Identifying super-spreaders…",
    "Finalizing network…",
    "Analysis complete."
  ];

  document.querySelectorAll(".run-analysis-btn").forEach(btn => {
    btn.addEventListener("click", () => {

      const output  = document.querySelector(btn.dataset.run);
      const overlay = document.querySelector(btn.dataset.overlay);
      const status  = overlay.querySelector(".analysis-status");

      overlay.hidden = false;
      btn.disabled = true;

      let i = 0;
      const interval = setInterval(() => {
        status.textContent = statusTexts[i % statusTexts.length];
        i++;
      }, 900);

      setTimeout(() => {
        clearInterval(interval);
        overlay.hidden = true;
        output.classList.remove("is-locked");
      }, 4200);
    });
  });

})();
</script>
