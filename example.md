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

After thorough investigation, 4 key periods can be picked out:

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
      <iframe src="{{ '/assets/plots/seg_ussr.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-dotcom" class="case-panel">
    <h3>Dot-com bubble — fever in tech</h3>
    <p>Speculation peaks, then immunity fails: tech drags everything down through network links.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/seg_dotcom.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-subprime" class="case-panel">
    <h3>Subprime — systemic infection</h3>
    <p>Credit stress spreads across sectors. This is where “local symptoms” become systemic.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/seg_subprime.html' | relative_url }}" loading="lazy"></iframe>
    </div>
  </section>

  <section id="panel-covid" class="case-panel">
    <h3>COVID — synchronized shock</h3>
    <p>A fast global transmission: sudden drawdowns and extreme co-movement.</p>
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/seg_covid.html' | relative_url }}" loading="lazy"></iframe>
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
