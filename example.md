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
| Dot-com bubble burst      | 2000-09-08   | 2000-10-20   | 6                | **−19.49%**       |
| Subprime financial crisis | 2008-10-03   | 2008-10-24   | 3                | **−22.02%**       |
| COVID-19 market shock     | 2020-02-21   | 2020-04-10   | 7                | **−22.90%**       |

---

### **Choose a case file**

Pick one regime below.  
When you click a card, you access the **case study content** of this very period.  

<div class="segment-row">

  <button class="segment-card is-active"
        data-target="panel-dotcom"
        data-bg="#F5F6FC"
        data-accent="#2E357A"
        aria-selected="true">
    <img src="{{ '/assets/images/internet.png' | relative_url }}" alt="Dot-com Bubble">
    <div class="segment-title">Dot-com Bubble</div>
  </button>

  <button class="segment-card"
        data-target="panel-subprime"
        data-bg="#F4FBF6"
        data-accent="#1F6B3A"
        aria-selected="false">
    <img src="{{ '/assets/images/subprime.png' | relative_url }}" alt="Subprime Crisis">
    <div class="segment-title">Subprime Crisis</div>
  </button>

  <button class="segment-card"
        data-target="panel-covid"
        data-bg="#FDFDF8"
        data-accent="#6A5F12"
        aria-selected="false">
    <img src="{{ '/assets/images/covid.png' | relative_url }}" alt="COVID Outbreak">
    <div class="segment-title">COVID Outbreak</div>
  </button>

</div>

<!-- Case file container -->
<div class="case-panels" id="case-files" aria-live="polite">

  <!-- DOTCOM (visible by default) -->
  <section id="panel-dotcom" class="case-panel is-visible">
    <h3>Case File: Dot-com burst</h3>

    <!-- 1) Daily returns plot -->
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}" loading="lazy"></iframe>
    </div>

    <!-- 2) Text -->
    <p>
      Speculation peaks, then confidence collapses.
      One sector gets hit first, then correlations spike and pull the rest of the market into the outbreak.
    </p>

    <!-- 3) Timeline slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/internet' | relative_url }}"
         data-prefix="timeline_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="Dot-com timeline frame" loading="lazy">
    </div>

    <!-- 4) Text -->
    <p>
      The timeline view shows how quickly the shock intensifies and how persistent it becomes across consecutive days.
    </p>

    <!-- 5) Network slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/internet' | relative_url }}"
         data-prefix="network_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="Dot-com network frame" loading="lazy">
    </div>
  </section>

  <!-- SUBPRIME -->
  <section id="panel-subprime" class="case-panel" hidden>
    <h3>Case File: Subprime Crisis</h3>

    <!-- 1) Daily returns plot -->
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}" loading="lazy"></iframe>
    </div>

    <!-- 2) Text -->
    <p>
      Credit stress doesn’t stay local. This regime is short but brutal:
      shocks propagate through financial exposure and sector links,
      turning symptoms into a system-wide condition.
    </p>

    <!-- 3) Timeline slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/subprime' | relative_url }}"
         data-prefix="timeline_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="Subprime timeline frame" loading="lazy">
    </div>

    <!-- 4) Text -->
    <p>
      Sliding through the timeline reveals how the set of “infected” assets expands day by day, even when the trigger remains concentrated.
    </p>

    <!-- 5) Network slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/subprime' | relative_url }}"
         data-prefix="network_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="Subprime network frame" loading="lazy">
    </div>
  </section>

  <!-- COVID -->
  <section id="panel-covid" class="case-panel" hidden>
    <h3>Case File: COVID</h3>

    <!-- 1) Daily returns plot -->
    <p>
      Let's first zoom-in on the timeline and have a glance at the daily return of the market:
    </p>
    
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}" loading="lazy"></iframe>
    </div>

    <p>
      The market yields negative daily returns approximately 57% of the time... In order to have a cumulative return of -22.90% over the whole period the negative returns would have to carry a stronger weight compared to the positive returns. Let's try to understand what is happening behind the scenes. We have to put our immunoligical tool to the test for this one. It should be able to identify who the patient-zero is, meaning which is the first entity that contracted the so-called "virus" and that sparked the flame of this epidemic. The algorithm should also be able to pick out the super-spreaders, in other words the entities that, once contaminated, have an abnormally high transmission rate, as well as "sick" or "at risk" of getting stick entities. An entity is called "sick" if its daily returns cross the -5% threshold and if their cumulative return over the entire period is below -20%. The ones "at risk" of getting sick are the ones that have strong connections, be it strong correlation or causal link with "sick" entities. In the end, entities can recover from the virus and are labelled "recovered". The unaffected entities are labelled "healthy". You can press the big red button below to start the analysis.
    </p>

    <!-- 2) Text -->
    <p>
      A fast global transmission: abrupt drawdowns, violent reversals, and extreme co-movement.
      If the market had an immune system, this is the moment it got overwhelmed.
    </p>

    <!-- 3) Timeline slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/covid' | relative_url }}"
         data-prefix="timeline_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="COVID timeline frame" loading="lazy">
    </div>

    <!-- 4) Text -->
    <p>
      The timeline captures the synchronized nature of the shock: many assets move together, leaving fewer “safe” pockets.
    </p>

    <!-- 5) Network slider -->
    <div class="img-slider"
         data-folder="{{ '/assets/covid' | relative_url }}"
         data-prefix="network_"
         data-ext="png"
         data-pad="4"
         data-start="0">
      <div class="img-slider-top">
        <input class="img-slider-range" type="range" min="0" max="0" step="1" value="0">
        <div class="img-slider-label">Frame: <span class="img-slider-idx">0</span></div>
      </div>
      <img class="img-slider-img" alt="COVID network frame" loading="lazy">
    </div>
  </section>

</div>

<script>
(function () {

  // ---------------------------
  // Image slider init
  // ---------------------------
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

  async function initOneSlider(root) {
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

    let last = start;

    if (!(await imageExists(urlFor(start)))) {
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

  document.querySelectorAll(".img-slider").forEach(slider => {
    initOneSlider(slider);
  });

  // ---------------------------
  // Case switching + theming
  // ---------------------------
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
      cards.forEach(c => {
        c.classList.remove("is-active");
        c.setAttribute("aria-selected", "false");
      });
      card.classList.add("is-active");
      card.setAttribute("aria-selected", "true");

      setTheme(card.dataset.bg, card.dataset.accent);
      showPanel(card.dataset.target);
    });
  });

  const active = document.querySelector(".segment-card.is-active") || cards[0];
  if (active) setTheme(active.dataset.bg, active.dataset.accent);

})();
</script>
