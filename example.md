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

We segmented the market timeline into consecutive regimes using dynamic programming:  
periods are grouped by **similar average returns**, so we can spot when the market changes states.

From that full timeline, **four regimes stand out** as unusually violent, meaningful, or historically interpretable.

| Period name                | Start date   | End date     | Duration (weeks) | Cumulative return |
|---------------------------|--------------|--------------|------------------|-------------------|
| Collapse of the USSR      | 1991-12-20   | 1992-01-10   | 4                | **+17.16%**       |
| Dot-com bubble burst      | 2000-09-08   | 2000-10-13   | 6                | **−19.49%**       |
| Subprime financial crisis | 2008-10-03   | 2008-10-17   | 3                | **−22.02%**       |
| COVID-19 market shock     | 2020-02-21   | 2020-04-03   | 7                | **−22.90%**       |

---

### Choose a case file

Pick one regime below.  
When you click a card, you access the **case study content** of this very period.  

<div class="segment-row">

  <button class="segment-card is-active"
        data-target="panel-ussr"
        data-bg="#FFF5F6"
        data-accent="#8C1D2C"
        aria-selected="true">
    <img src="{{ '/assets/images/ussr.png' | relative_url }}" alt="Collapse of the USSR">
    <div class="segment-title">Collapse of the USSR</div>
  </button>

  <button class="segment-card"
        data-target="panel-dotcom"
        data-bg="#F5F6FC"
        data-accent="#2E357A">
    <img src="{{ '/assets/images/internet.png' | relative_url }}" alt="Dot-com Bubble">
    <div class="segment-title">Dot-com Bubble</div>
  </button>

  <button class="segment-card"
        data-target="panel-subprime"
        data-bg="#F4FBF6"
        data-accent="#1F6B3A">
    <img src="{{ '/assets/images/subprime.png' | relative_url }}" alt="Subprime Crisis">
    <div class="segment-title">Subprime Crisis</div>
  </button>

  <button class="segment-card"
        data-target="panel-covid"
        data-bg="#FDFDF8"
        data-accent="#6A5F12">
    <img src="{{ '/assets/images/covid.png' | relative_url }}" alt="COVID Outbreak">
    <div class="segment-title">COVID Outbreak</div>
  </button>

</div>

<!-- Case file container -->
<div class="case-panels" id="case-files" aria-live="polite">

  <section id="panel-ussr" class="case-panel is-visible">
    <h3>Case File: USSR collapse — regime change shock</h3>
    <p>
      This is our first “clean” anomaly: the market tone shifts quickly, volatility rises,
      and the return distribution stops behaving like the previous regime.
      Think of it as a sudden mutation in the environment.
    </p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_1991.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-dotcom" class="case-panel" hidden>
    <h3>Case File: Dot-com burst — fever in tech</h3>
    <p>
      Speculation peaks, then confidence collapses. This is a classic “contagion amplifier” period:
      one sector gets hit first, then correlations spike and pull the rest of the market into the outbreak.
    </p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-subprime" class="case-panel" hidden>
    <h3>Case File: Subprime — systemic infection</h3>
    <p>
      Credit stress doesn’t stay local. This regime is short but brutal:
      shocks propagate through financial exposure and sector links,
      turning “symptoms” into a system-wide condition.
    </p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-covid" class="case-panel" hidden>
    <h3>Case File: COVID — synchronized shock</h3>
    <p>
      A fast global transmission: abrupt drawdowns, violent reversals, and extreme co-movement.
      If the market had an immune system, this is the moment it got overwhelmed.
    </p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

</div>

<script>
(function () {
  const cards  = [...document.querySelectorAll(".segment-card")];
  const panels = [...document.querySelectorAll(".case-panel")];

  function setTheme(bg, accent) {
    const body = document.querySelector("body.site-body");
    if (!body) return;

    requestAnimationFrame(() => {
      body.style.setProperty("--page-bg", bg || "#ffffff");
      body.style.setProperty("--content-accent", accent || "#2aa36b");
    });
  }

  function showPanel(id) {
    const current = panels.find(p => p.classList.contains("is-visible"));
    const next = document.getElementById(id);
    if (!next || current === next) return;

    if (current) {
      current.classList.remove("is-visible");
      setTimeout(() => current.hidden = true, 220);
    }

    next.hidden = false;
    requestAnimationFrame(() => next.classList.add("is-visible"));
  }

  cards.forEach(card => {
    card.addEventListener("click", () => {
      cards.forEach(c => c.classList.remove("is-active"));
      card.classList.add("is-active");

      setTheme(card.dataset.bg, card.dataset.accent);
      showPanel(card.dataset.target);
    });
  });

  const active = document.querySelector(".segment-card.is-active") || cards[0];
  if (active) setTheme(active.dataset.bg, active.dataset.accent);
})();
</script>

