---
title: "The Story"
permalink: /story/
layout: default
---


## Part I: Market Segmentation

Before we accuse a stock, we need a crime scene.

So we start with the only thing the market can’t hide: the timeline.

<div class="full-width-plot">
  <iframe
    src="{{ '/assets/plots/segmentation.html' | relative_url }}"
    loading="lazy"></iframe>
</div>

After thorough investigation, 4 key periods stand out and will be analyzed:

| Period name               | Start date   | End date     | Duration (weeks) | Cumulative return |
|--------------------------|--------------|--------------|------------------|-------------------|
| Collapse of the USSR     | 1991-12-20   | 1992-01-10   | 4                | **+17.16%**       |
| Dot-com bubble burst     | 2000-09-08   | 2000-10-13   | 6                | **−19.49%**       |
| Subprime financial crisis| 2008-10-03   | 2008-10-17   | 3                | **−22.02%**       |
| COVID-19 market shock    | 2020-02-21   | 2020-04-03   | 7                | **−22.90%**       |



<div class="segment-row">

  <button class="segment-card is-active" data-target="panel-ussr" type="button">
    <img src="{{ '/assets/images/ussr.jpg' | relative_url }}" alt="Collapse of the USSR">
    <div class="segment-title">Collapse of the USSR</div>
  </button>

  <button class="segment-card" data-target="panel-dotcom" type="button">
    <img src="{{ '/assets/images/internet.png' | relative_url }}" alt="Dotcom Bubble">
    <div class="segment-title">Dotcom Bubble</div>
  </button>

  <button class="segment-card" data-target="panel-subprime" type="button">
    <img src="{{ '/assets/images/subprime.jpg' | relative_url }}" alt="Subprime Crisis">
    <div class="segment-title">Subprime Crisis</div>
  </button>

  <button class="segment-card" data-target="panel-covid" type="button">
    <img src="{{ '/assets/images/covid.jpg' | relative_url }}" alt="Covid Outbreak">
    <div class="segment-title">Covid Outbreak</div>
  </button>

</div>

<!-- Panels (only one is visible at a time) -->
<div class="case-panels">

  <section id="panel-ussr" class="case-panel is-visible">
    <h3>Collapse of the USSR — regime change shock</h3>
    <p>We start here: the market shifts tone, volatility rises, and correlations begin to rewire.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_1991.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-dotcom" class="case-panel">
    <h3>Dot-com bubble — fever in tech</h3>
    <p>Speculation peaks, then immunity fails: tech drags everything down through network links.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-subprime" class="case-panel">
    <h3>Subprime — systemic infection</h3>
    <p>Credit stress spreads across sectors. This is where “local symptoms” become systemic.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-covid" class="case-panel">
    <h3>COVID — synchronized shock</h3>
    <p>A fast global transmission: sudden drawdowns and extreme co-movement.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

</div>

<script>
(function () {
  const cards = document.querySelectorAll(".segment-card");
  const panels = document.querySelectorAll(".case-panel");

  function showPanel(id) {
    panels.forEach(p => {
      if (p.id === id) {
        p.classList.add("is-visible");
      } else {
        p.classList.remove("is-visible");
      }
    });
  }

  cards.forEach(card => {
    card.addEventListener("click", () => {
      cards.forEach(c => c.classList.remove("is-active"));
      card.classList.add("is-active");
      showPanel(card.dataset.target);
    });
  });
})();
</script>
