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

| Period name               | Start date | End date   | Duration (weeks) | Cumulative return |
| ------------------------- | ---------- | ---------- | ---------------- | ----------------- |
| Dot-com bubble burst      | 2000-09-08 | 2000-10-20 | 6                | **−19.49%**       |
| Subprime financial crisis | 2008-10-03 | 2008-10-24 | 3                | **−22.02%**       |
| COVID-19 market shock     | 2020-02-21 | 2020-04-10 | 7                | **−22.90%**       |

---

## Choose a case file

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

    <!-- Button directly under the first plot -->
    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#dotcom-output"
         data-overlay="#dotcom-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <p>
      Speculation peaks, then confidence collapses.  
      Technology firms are hit first, before correlations spike and drag the rest of the market with them.
    </p>

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

    <!-- Button directly under the first plot -->
    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#subprime-output"
         data-overlay="#subprime-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <p>
      Credit stress does not stay local.  
      This regime is short but brutal, propagating through financial exposure.
    </p>

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

    <!-- Button directly under the first plot -->
    <button class="run-analysis-btn img-button"
         type="button"
         data-run="#covid-output"
         data-overlay="#covid-overlay">
      <img src="{{ '/assets/images/redbutton.png' | relative_url }}" alt="Run analysis">
    </button>

    <p>
      A fast global transmission with extreme co-movement.
    </p>

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

  /* =========================
     IMAGE SLIDER (BUILD + INIT)
     ========================= */

  function padNum(n, width) {
    const s = String(n);
    return s.length >= width ? s : ("0".repeat(width - s.length) + s);
  }

  function imageExists(url) {
    return new Promise(resolve => {
      const img = new Image();
      img.onload = () => resolve(true);
      img.onerror = () => resolve(false);
      img.src = url;
    });
  }

  function ensureSliderSkeleton(root) {
    // If the slider div is empty, build the UI inside it.
    if (root.querySelector(".img-slider-range")) return;

    root.innerHTML = `
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="Slider frame" loading="lazy">
    `;
  }

  async function initOneSlider(root) {
    ensureSliderSkeleton(root);

    const folder = root.dataset.folder;
    const prefix = root.dataset.prefix || "";
    const ext    = root.dataset.ext || "png";
    const pad    = parseInt(root.dataset.pad || "4", 10);
    const start  = parseInt(root.dataset.start || "0", 10);

    const rangeEl = root.querySelector(".img-slider-range");
    const imgEl   = root.querySelector(".img-slider-img");
    const idxEl   = root.querySelector(".img-slider-idx");

    function urlFor(i){
      return `${folder}/${prefix}${padNum(i, pad)}.${ext}`;
    }

    // probe frames to find last
    let last = start;

    if (!(await imageExists(urlFor(start)))) {
      // hide slider if folder/prefix doesn't exist
      root.style.display = "none";
      return;
    }

    while (await imageExists(urlFor(last + 1))) {
      last += 1;
      if (last - start > 2000) break;
    }

    rangeEl.min = String(start);
    rangeEl.max = String(last);
    rangeEl.value = String(start);

    function render(i){
      imgEl.src = urlFor(i);
      idxEl.textContent = String(i);
    }

    render(start);
    rangeEl.addEventListener("input", () => render(parseInt(rangeEl.value, 10)));
  }

  function initSlidersWithin(scopeEl) {
    const nodes = scopeEl.querySelectorAll(".img-slider");
    nodes.forEach(slider => {
      if (!slider.dataset._inited) {
        slider.dataset._inited = "1";
        initOneSlider(slider);
      }
    });
  }

  /* =========================
     PANEL SWITCHING (SEGMENT CARDS)
     ========================= */
  const body = document.documentElement; // easier for CSS vars
  const cards = Array.from(document.querySelectorAll(".segment-card"));
  const panels = Array.from(document.querySelectorAll(".case-panel"));

  function showPanel(targetId, bg, accent) {
    // theme variables
    if (bg) body.style.setProperty("--page-bg", bg);
    if (accent) body.style.setProperty("--content-accent", accent);

    // panels
    panels.forEach(p => {
      const isTarget = p.id === targetId;
      p.classList.toggle("is-visible", isTarget);
    });

    // cards
    cards.forEach(c => {
      const isTarget = c.dataset.target === targetId;
      c.classList.toggle("is-active", isTarget);
      c.setAttribute("aria-selected", isTarget ? "true" : "false");
    });
  }

  cards.forEach(card => {
    card.addEventListener("click", () => {
      showPanel(card.dataset.target, card.dataset.bg, card.dataset.accent);
    });
  });

  /* Ensure initial theme matches active card (on page load) */
  const initial = cards.find(c => c.classList.contains("is-active")) || cards[0];
  if (initial) showPanel(initial.dataset.target, initial.dataset.bg, initial.dataset.accent);

  /* =========================
     RUN ANALYSIS BUTTON (REVEAL LOCKED OUTPUT)
     ========================= */
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

        // IMPORTANT: now that output is visible, build+init sliders inside it
        initSlidersWithin(output);

      }, 4200);
    });
  });

})();
</script>
