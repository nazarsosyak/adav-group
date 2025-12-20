---
title: "The Story"
permalink: /story/
layout: default
---

## **Part I: Market Segmentation**

Before accusing any individual stock of driving a crisis, we must first
identify *when* the market itself entered abnormal regimes.

We therefore begin with the only element the market cannot conceal:  
**the timeline**.

<div class="plot-container" style="text-align: center; margin: 2rem 0;">
  <iframe
    src="{{ '/assets/plots/segmentation.html' | relative_url }}"
    loading="lazy"
    style="width:100%; height:480px; border:none;">
  </iframe>
</div>

In the figure above, the timeline was segmented with respect to periods that exhibit similar weekly returns using dynamic programming (50 segments). Notably, the most severe segments coincide with well-known systemic crises,
including the **dot-com bubble burst**, the **2008 financial crisis**, and the **COVID-19 shock**.

These periods serve as our **outbreak windows** in the following analysis.
We will focus on these segments
to study how financial contagion emerges, propagates, and eventually dissipates.


**Major crisis periods identified by market segmentation.**

| Crisis episode            | Start date | End date   | Duration (weeks) | Cumulative market return | Interpretation |
|---------------------------|------------|------------|------------------|--------------------------|----------------|
| Dot-com bubble burst      | 2000-09-08 | 2000-10-20 | 6                | **−19.49%**              | Huge correction after the internet hype |
| Subprime financial crisis | 2008-10-03 | 2008-10-24 | 3                | **−22.02%**              | Banking and credit collapse |
| COVID-19 market shock     | 2020-02-21 | 2020-04-10 | 7                | **−22.90%**              | Global shutdown |

All identified crisis periods exhibit cumulative losses exceeding 19%, confirming their systemic severity
and justifying their use as outbreak windows in the subsequent contagion analysis.

---

## **Part II: Definition of contagion dynamics**

### The Main Immunology Pipeline

Before analysis, it is important to be clear on how the algorithm functions:

Three key dimensions must be introduced first.
These dimensions are jointly used to evaluate the state and systemic relevance of each market entity.

1. **Network centrality:** We measure how embedded each asset is within the market network. Centrality reflects how strongly a node is connected to others through correlation, mutual information, and causal exposure.
2. **Temporal leadership:** Timing matters. Assets that exhibit abnormal stress **early** in the outbreak window carry more explanatory power than late movers. Early infection combined with strong connectivity raises suspicion regarding a possible triggering role (i.e. **patient zero**).
3. **Reproduction number (R₀):** Inspired by epidemiological concepts, this metric quantifies the effective contagion pressure exerted by a **distressed node** on the rest of the network. Higher values indicate nodes with a greater capacity to transmit and amplify market stress through interconnected pathways. 

Together, these three dimensions define the
**Pandemic Potential Index** (**PPI**),
a composite score that captures an entity’s ability to
**initiate**, **amplify** or **propagate**
financial stress within the market. This helps us find **super-spreaders** in the network.

For each case, we used **50 representative tickers** for the sake of visualization. All the tickers are accessible through the **Ticker Dictonary** on the right of the page, providing insightful information about every single one of them.

### Infection state classification
    
In parallel, each entity is assigned a health state based on its return dynamics
over the outbreak window.

1. An entity is labeled **directly sick** if its daily return crosses the **−5% threshold**.
2. Entities that maintain strong connections with sick nodes (through correlation or causal exposure) are classified as **sick by contagion**.
3. Over time, entities may **recover** if their daily returns are positive for three consecutive days.
4. Those that never meet the infection criteria remain **healthy**.

In each case file, we apply the same investigative procedure:
we examine market behavior during the outbreak window,
reconstruct the underlying interaction network,
and identify key roles such as patient zero, super-spreaders, and high-risk entities.

### Select a case file

You may now select one of the following crisis episodes to open its corresponding case file.
Each case file presents a focused and comparable analysis of market behavior
during that outbreak.

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
    <h1><span class="text-accent"><strong>Case File: Dot-com Bubble</strong></span></h1>

    <div class="panel-intro">
      <img src="{{ '/assets/images/internetintro.png' | relative_url }}" alt="Dot-com Bubble intro">
    </div>

    <p>
      At the turn of the millennium, markets were drunk on promises.
      Anything with a website and a “.com” suffix
      was treated as the future of civilization. Valuations detached from fundamentals,
      and skepticism quietly exited the room.
      Then reality pushed back when the internet bubble burst.
    
    </p>
      
      <p>
      The plot below shows the mean daily market return during the identified outbreak window.
      </p>



    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2000.html' | relative_url }}"></iframe>
    </div>

    <p>
      During this period, the market records negative daily returns on nearly <strong>77% of trading days</strong>, cumulating to a <strong>−19.49%</strong> loss over the entire window.<br><br>
      
      To grasp what's really happening here we shall analyze the internal structure of the market and track
      how stress appears, spreads, and concentrates at the entity level.
    </p>

    <p>
      You can press the <span class="text-accent"><strong>RED BUTTON</strong></span> below to initiate the analysis.
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
      <hr class="analysis-separator">
      
      <h3 class="text-accent">Patient zero has been identified as entity <strong>BIIB</strong>.</h3>
      

      <p>
        Now that a patient zero has been identified, we might want to understand how the outbreak unfolded.
        It is interesting to understand the
        relative roles played by all assets during the crisis.
      </p>
      
      <p>
        The 3D plot below places every stock in the market inside a common
        <strong>contagion space</strong>.
        Each point represents an entity, positioned according to three dimensions:
        reproduction index, centrality and temporal leadership (all normalized). These values are the mean values over the entire timeframe.
      </p>


      <div class="plot-frame plot-frame--first">
          <iframe
            src="{{ '/assets/plots/ppi_3d_internet.html' | relative_url }}"
            loading="lazy"
            title="Dot-com 3D plot"></iframe>
        </div>

      <p>
        To move from this static snapshot to a dynamic view,
        we now follow how the outbreak unfolds over time.
        The timeline below tracks the daily evolution of asset states,
        showing when entities become infected, recover, or remain resilient. The slider bar can be used to scroll over the timeline.
      </p>


      <div class="img-slider"
           data-folder="{{ '/assets/internet' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        Finally, we reconstruct the underlying interaction network.
        This network reveals the channels through which stress propagates,
        highlighting super-spreaders that amplify contagion through correlation. The arrows represent the transfer of information, combining causality and correlation between the nodes of the network. Here again the slider bar can be used in the same manner.
      </p>


      <div class="img-slider"
           data-folder="{{ '/assets/internet' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>

      <h3 class="text-accent">Discussion</h3>
      <p>
        BLABLABLA
      </p>

      <h2 class="text-accent">Cluster membership</h2>

      <p>
        The clusters shown in the 3D plot below emerge directly from how individual stocks behave during the outbreak window.
      </p>
      
      <p>
        Each stock is represented as a point in a three-dimensional space defined by
        (i) the <strong>fraction of days spent sick</strong>,
        (ii) the <strong>average time needed to recover</strong> after a stress event,
        and (iii) the <strong>fraction of days spent in a healthy state</strong>.
        Stocks that occupy nearby positions in this space exhibit similar recovery dynamics. The clustering algorithm groups stocks solely based on this behavioral similarity.
      </p>
    
      
      <p>
        The envelopes drawn around each group indicate the range of behaviors covered by a cluster.
        Clusters that lie far apart in the plot correspond to fundamentally different ways in which market stress
        propagates and dissipates during the crisis.
      </p>

      
      <div class="cluster-legend" style="display:flex; flex-wrap:wrap; gap:.55rem; margin:.35rem 0 1rem;">
        <span class="cl-pill" data-cl="0" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:orange; display:inline-block;"></span>
          <strong>Cluster 0</strong>: orange group (with blue points)
        </span>
      
        <span class="cl-pill" data-cl="1" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#1f77b4; display:inline-block;"></span>
          <strong>Cluster 1</strong>: blue group (with orange points)
        </span>
      
        <span class="cl-pill" data-cl="2" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:hotpink; display:inline-block;"></span>
          <strong>Cluster 2</strong>: pink group (with green points)
        </span>
      
        <span class="cl-pill" data-cl="3" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#2ca02c; display:inline-block;"></span>
          <strong>Cluster 3</strong>: green group (with purple points)
        </span>
      </div>
      
      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/plots/immune_phenotypes_3d_dot-com.html' | relative_url }}"
          loading="lazy"
          title="Immune phenotypes: Dot-com">
        </iframe>
      </div>

      <div class="cluster-widget" data-period="dotcom"></div>

      Each cluster can be intepreted in the following manner:<br>
        - Tickers belonging to <strong>cluster 0</strong> take longer to recover and are sick for a longer time period.<br>
        - Tickers belonging to <strong>cluster 1</strong> on the other hand recover fast and are healthy more than they are sick.<br>
        - Tickers belonging to <strong>cluster 2</strong> stay pretty much healthy most of the time, with a wide range of recovery times.<br>
        - Tickers belonging to <strong>cluster 3</strong> are in a state of contagion or recovry most of the time.<br><br>

      This classification helps us understand the role of each stock in the outbreak.

      <h2 class="text-accent"><strong>Part III: Sectorial Analysis</strong></h2>

      <p>Maybe we have been looking at the problem from a wrong angle. What if the epidemic was actually caused by an entire sector of activity? This is what this section aims to explore.<br><br>
      We will reuse the algorithm, but this time, over the different sectors of the market. Below is a non-exhaustive bubble map of each sector and the 20 largest stocks they contain.
      </p>

      <div class="plot-container" style="margin:2rem 0;">
        <iframe
          src="{{ '/assets/plots/sector_bubblemap.html' | relative_url }}"
          loading="lazy"
          style="width:100%; height:620px; border:none;">
        </iframe>
      </div>

      <p>
        Similarly as before, we display all sectors on a reproduction index-- temporal leadership--centrality map and the resulting PPI index. 
      </p>


      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/internet/sector/ppi_3d_analysis.html' | relative_url }}"
          loading="lazy"
          title="Sector-to-sector 3D">
        </iframe>
      </div>

      <h3 class="text-accent">
        For the case of the dot-com bubble burst, the sectorial patient zero is <strong>Utilities</strong>.
      </h3>
      <p>
        The timeline below tracks how sector-level health evolves over time.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/internet/sector' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        We then reconstruct the network of inter-sector interactions.
        This network reveals how stress is transmitted across sectors,
        identifying which sectors act as conduits that amplify
        or dampen systemic risk.
      </p>
      
      <div class="img-slider"
           data-folder="{{ '/assets/internet/sector' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>
      <h3 class="text-accent">Discussion</h3>
          <p>
            BLABLABLA
          </p>

    </div>
  </section>

  <!-- ===================================================== -->
  <!-- SUBPRIME -->
  <!-- ===================================================== -->

  <section id="panel-subprime" class="case-panel">
    <h1><span class="text-accent"><strong>Case File: Subprime Crisis</strong></span></h1>

    <div class="panel-intro">
      <img src="{{ '/assets/images/subprimeintro.png' | relative_url }}" alt="Subprime Crisis intro">
    </div>

    <p>
      In October 2008, the financial system stopped trusting itself.
      Years of hidden leverage, opaque balance sheets
      and mispriced risk surfaced almost simultaneously.
      What had been framed as a localized housing issue
      suddenly revealed deep fractures at the core of global finance.
      This outbreak is widely regarded as one of the most severe market upsets in modern history.
      </p>
      
      <p>
      From the daily market returns below, large negative swings are compressed into a short time span,
      punctuated by sharp but short-lasting rebounds.
      Unlike the dot-com episode, here losses arrive in strong bursts.
      </p>


    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2008.html' | relative_url }}"></iframe>
    </div>

    <p> 
      Here the market records negative daily returns on <strong>80% of trading days</strong>, with a cumulative loss of <strong>−22.02%</strong> over this time period.<br><br>
    </p>
    <p>
      Press <span class="text-accent"><strong>RED BUTTON</strong></span> below and see what happens.
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
      <hr class="analysis-separator">
      <h3 class="text-accent">
        Patient zero has been identified as entity <strong>GS</strong> (use helper dictionary on the right of your screen for more information on the company).
      </h3>

      <p>
        Now that the problematic stock has been identified, we might want to understand how the outbreak unfolded.
        It is interesting to understand the
        relative roles played by all assets during the crisis.
      </p>
      
      <p>
        The 3D plot below places every stock in the market inside a common
        <strong>contagion space</strong>.
        Each point represents an entity, positioned according to three dimensions:
        how early it exhibits stress, how central it is within the market network,
        and how strongly it tends to transmit that stress to others. These values are the mean values over the entire timeframe.
      </p>
      
      <div class="plot-frame plot-frame--first">
          <iframe
            src="{{ '/assets/plots/ppi_2008.html' | relative_url }}"
            loading="lazy"
            title="Subprime 3D plot"></iframe>
        </div>

      <p>
        To move from this static snapshot to a dynamic view,
        we now follow how the outbreak unfolds over time.
        The timeline below tracks the daily evolution of asset states,
        showing when entities become infected, recover, or remain resilient. The slider bar can be used to scroll over the timeline.
      </p>
        

      <div class="img-slider"
           data-folder="{{ '/assets/subprime' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        Finally, we reconstruct the underlying interaction network.
        This network reveals the channels through which stress propagates,
        highlighting super-spreaders that amplify contagion through correlation. The arrows represent the transfer of information, combining causality and correlation between the nodes of the network. Here again the slider bar can be used in the same manner.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/subprime' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>

      <h2 class="text-accent">Cluster membership</h2>

      <p>
        The clusters shown in the 3D plot below emerge directly from how individual stocks behave during the outbreak window.
      </p>
      
      <p>
        Each stock is represented as a point in a three-dimensional space defined by
        (i) the <strong>fraction of days spent sick</strong>,
        (ii) the <strong>average time needed to recover</strong> after a stress event,
        and (iii) the <strong>fraction of days spent in a healthy state</strong>.
        Stocks that occupy nearby positions in this space exhibit similar stress-recovery dynamics.
      </p>
      
      <p>
        The clustering algorithm groups stocks solely based on this behavioral similarity.
        As a result, stocks in the same cluster may belong to different sectors or have very different business models.
        What unites them is not what they do, but <strong>how they react to market stress</strong>.
      </p>
      
      <p>
        The translucent envelopes drawn around each group indicate the range of behaviors covered by a cluster.
        Clusters that lie far apart in the plot correspond to fundamentally different ways in which market stress
        propagates and dissipates during the crisis.
      </p>
      
      <div class="cluster-legend" style="display:flex; flex-wrap:wrap; gap:.55rem; margin:.35rem 0 1rem;">
        <span class="cl-pill" data-cl="0" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:orange; display:inline-block;"></span>
          <strong>Cluster 0</strong>: orange group (with blue points)
        </span>
      
        <span class="cl-pill" data-cl="1" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#1f77b4; display:inline-block;"></span>
          <strong>Cluster 1</strong>: blue group (with orange points)
        </span>
      
        <span class="cl-pill" data-cl="2" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:hotpink; display:inline-block;"></span>
          <strong>Cluster 2</strong>: pink group (with green points)
        </span>
      
        <span class="cl-pill" data-cl="3" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#2ca02c; display:inline-block;"></span>
          <strong>Cluster 3</strong>: green group (with purple points)
        </span>
      </div>

      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/plots/immune_phenotypes_3d_subprime.html' | relative_url }}"
          loading="lazy"
          title="Immune phenotypes: Subprime">
        </iframe>
      </div>

      <div class="cluster-widget" data-period="subprime"></div>
      
      <h2 class="text-accent"><strong>Part III: Sectorial Analysis</strong></h2>

      <p>Maybe we have been looking at the problem from a wrong angle. What if the epidemic was actually caused by an entire sector of activity? This is what this section aims to do.<br><br>
      We will reuse the algorithm, but this time, over the different sectors of the market. Below is a non-exhaustive bubble map of each sector and the 20 largest stocks they contain.
      </p>

      <div class="plot-container" style="margin:2rem 0;">
        <iframe
          src="{{ '/assets/plots/sector_bubblemap.html' | relative_url }}"
          loading="lazy"
          style="width:100%; height:620px; border:none;">
        </iframe>
      </div>
      
      <h3 class="text-accent">
        The patient zero in this case is the <strong>Real Estate Sector</strong>, which totally makes sense in this context! This is a great sign.
      </h3>
      
      <p>
        We can use the same reasoning as for individual tickers but this time we apply it to our newly defined sectors.
      </p>

      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/subprime/sector/ppi_3d_analysis.html' | relative_url }}"
          loading="lazy"
          title="Sector-to-sector 3D">
        </iframe>
      </div>

      <p>
        The timeline below tracks how sector-level health evolves over time.
        It shows when stress concentrates within specific sectors
        and whether contagion remains localized or spills over
        into the rest of the economy.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/subprime/sector' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        We then reconstruct the network of inter-sector interactions.
        This network reveals how stress is transmitted across sectors,
        identifying which sectors act as conduits that amplify
        or dampen systemic risk.
      </p>
      
      <div class="img-slider"
           data-folder="{{ '/assets/subprime/sector' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>

      
      <p>
      This sector-level perspective reveals that systemic risk is not solely driven
      by individual assets, but by the structure of inter-sector dependencies. 
      </p>
      

    </div>
  </section>

  <!-- ===================================================== -->
  <!-- COVID -->
  <!-- ===================================================== -->

  <section id="panel-covid" class="case-panel">
    <h1><span class="text-accent"><strong>Case File: COVID-19</strong></span></h1>

    <div class="panel-intro">
      <img src="{{ '/assets/images/covidintro.png' | relative_url }}" alt="COVID-19 intro">
    </div>

    <p>
      The COVID-19 crisis did not originate inside the market as economic activity was frozen by policy decisions,
      supply chains fractured overnight
      and uncertainty replaced all prior narratives. Public places were shutdown, international trade was disrupted and 
      </p>
      
      <p>
      The return series below captures this instability.
      Violent oscillations dominate the window:
      deep drawdowns followed by sharp rebounds,
      often within days of each other.
      These swings reflect a market struggling to price
      an evolving situation in real time,
      as information, fear, and intervention collide.
      Rather than settling into a single direction,
      the system oscillates under stress.
      </p>


    
    <div class="plot-frame">
      <iframe src="{{ '/assets/plots/daily_mean_return_2020.html' | relative_url }}"></iframe>
    </div>

    <p> 
      In this scenario, the market records negative daily returns on roughly <strong>53% of trading days</strong>, with a cumulative loss of <strong>−22.90%</strong>, meaning the negative days carry a much stronger weight than the positive return days. The analysis using our pipeline will give proper insight into the COVID-19 Crisis.<br><br>
    </p>

    <p>
      You can press the <span class="text-accent"><strong>RED BUTTON</strong></span> below to proceed with the analysis.
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
      <hr class="analysis-separator">
      <p>
      Patient zero has been identified as entity <span class="text-accent"><strong>GILD</strong></span> (use helper dictionary on the right of your screen for more information on the company).
      </p>
      
      <p>
        Now that the problematic stock has been identified, we might want to understand how the outbreak unfolded.
        It is interesting to understand the
        relative roles played by all assets during the crisis.
      </p>
      
      <p>
        The 3D plot below places every stock in the market inside a common
        <strong>contagion space</strong>.
        Each point represents an entity, positioned according to three dimensions:
        how early it exhibits stress, how central it is within the market network,
        and how strongly it tends to transmit that stress to others. These values are the mean values over the entire timeframe.
      </p>
      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/plots/ppi_3d_covid.html' | relative_url }}"
          loading="lazy"
          title="COVID 3D plot"></iframe>
      </div>

      <p>
        To move from this static snapshot to a dynamic view,
        we now follow how the outbreak unfolds over time.
        The timeline below tracks the daily evolution of asset states,
        showing when entities become infected, recover, or remain resilient. The slider bar can be used to scroll over the timeline.
      </p>
     

      <div class="img-slider"
           data-folder="{{ '/assets/covid' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        Finally, we reconstruct the underlying interaction network.
        This network reveals the channels through which stress propagates,
        highlighting super-spreaders that amplify contagion through correlation. The arrows represent the transfer of information, combining causality and correlation between the nodes of the network. Here again the slider bar can be used in the same manner.
      </p>

      <div class="img-slider"
           data-folder="{{ '/assets/covid' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>

      <h2 class="text-accent">Cluster membership</h2>

      <p>
        The clusters shown in the 3D plot below emerge directly from how individual stocks behave during the outbreak window.
      </p>
      
      <p>
        Each stock is represented as a point in a three-dimensional space defined by
        (i) the <strong>fraction of days spent sick</strong>,
        (ii) the <strong>average time needed to recover</strong> after a stress event,
        and (iii) the <strong>fraction of days spent in a healthy state</strong>.
        Stocks that occupy nearby positions in this space exhibit similar stress-recovery dynamics.
      </p>
      
      <p>
        The clustering algorithm groups stocks solely based on this behavioral similarity.
        As a result, stocks in the same cluster may belong to different sectors or have very different business models.
        What unites them is not what they do, but <strong>how they react to market stress</strong>.
      </p>
      
      <p>
        The translucent envelopes drawn around each group indicate the range of behaviors covered by a cluster.
        Clusters that lie far apart in the plot correspond to fundamentally different ways in which market stress
        propagates and dissipates during the crisis.
      </p>
      
      <div class="cluster-legend" style="display:flex; flex-wrap:wrap; gap:.55rem; margin:.35rem 0 1rem;">
        <span class="cl-pill" data-cl="0" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:orange; display:inline-block;"></span>
          <strong>Cluster 0</strong>: orange group (with blue points)
        </span>
      
        <span class="cl-pill" data-cl="1" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#1f77b4; display:inline-block;"></span>
          <strong>Cluster 1</strong>: blue group (with orange points)
        </span>
      
        <span class="cl-pill" data-cl="2" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:hotpink; display:inline-block;"></span>
          <strong>Cluster 2</strong>: pink group (with green points)
        </span>
      
        <span class="cl-pill" data-cl="3" style="display:inline-flex; align-items:center; gap:.45rem; padding:.35rem .6rem; border-radius:999px; border:1px solid rgba(0,0,0,.12); background:rgba(255,255,255,.75);">
          <span style="width:12px; height:12px; border-radius:50%; background:#2ca02c; display:inline-block;"></span>
          <strong>Cluster 3</strong>: green group (with purple points)
        </span>
      </div>

      
      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/plots/immune_phenotypes_3d_covid.html' | relative_url }}"
          loading="lazy"
          title="Immune phenotypes: COVID">
        </iframe>
      </div>

      <div class="cluster-widget" data-period="covid"></div>

      <h2 class="text-accent"><strong>Part III: Sectoral Analysis</strong></h2>
      <p>
        Up to this point, the analysis has focused on individual assets.
        However it is bold to assume that only one entity is responsible for a market shutdown as these epidemics often propagate through <strong>entire sectors</strong>.
      </p>
      
      <p>
        In this section, we shift the level of observation from assets to sectors.
        Each sector is treated as an aggregated entity whose health reflects
        the combined behavior of its constituent stocks during the outbreak window. Below is a non-exhaustive bubble map of each sector and the 20 largest stocks they contain.
      </p>

      <div class="plot-container" style="margin:2rem 0;">
        <iframe
          src="{{ '/assets/plots/sector_bubblemap.html' | relative_url }}"
          loading="lazy"
          style="width:100%; height:620px; border:none;">
        </iframe>
      </div>

      <h3 class="text-accent">
        The patient zero in this case is <strong>Consumer Staples</strong>.
      </h3>
      
      <p>
        The 3D plot below positions sectors in a contagion space analogous to the one
        used for individual assets.
        It captures how early sectoral stress emerges, how central each sector is
        within the market structure, and how strongly stress propagates from one
        sector to another.
      </p>
      
      <p>
        This change in scale allows us to distinguish between crises driven by
        a small number of influential sectors and those that spread broadly across
        the economic landscape.
      </p>

      <div class="plot-frame plot-frame--first">
        <iframe
          src="{{ '/assets/covid/sector/ppi_3d_analysis.html' | relative_url }}"
          loading="lazy"
          title="Sector-to-sector 3D">
        </iframe>
      </div>

      <p>
        The timeline below tracks how sector-level health evolves over time.
        It shows when stress concentrates within specific sectors
        and whether contagion remains localized or spills over
        into the rest of the economy.
      </p>


      <div class="img-slider"
           data-folder="{{ '/assets/covid/sector' | relative_url }}"
           data-prefix="timeline_"
           data-pad="4">
      </div>

      <p>
        We then reconstruct the network of inter-sector interactions.
        This network reveals how stress is transmitted across sectors,
        identifying which sectors act as conduits that amplify
        or dampen systemic risk.
      </p>

      
      <div class="img-slider"
           data-folder="{{ '/assets/covid/sector' | relative_url }}"
           data-prefix="network_"
           data-pad="4">
      </div>
      


    </div>
  </section>

</div>

---
## **Part IV: Crisis Signatures**

Up to this point, each crisis has been examined in isolation through its
own case file. We now take a step back and ask a broader question:

> **Do different crises stress the market through the same underlying mechanisms, or through fundamentally different ones?**

To answer this, we compress each crisis into a **latent market signature**
using **Principal Component Analysis (PCA)** applied to the immune phenotype
features introduced earlier.

Rather than focusing on individual assets, PCA extracts the **dominant
collective mode** that explains how the market behaves *as a system* during
each outbreak.

Each crisis is therefore summarized by:
- its **dominant PCA mode (PC1)**, capturing the main direction of market stress,
- the **fraction of variance explained** by that mode, measuring how synchronized
  the market becomes,
- and the **feature loadings** defining the underlying crisis mechanism.

<div id="signature-controls" class="signature-controls">
  <label for="pc-select"><strong>Select component:</strong></label>
  <select id="pc-select">
    <option value="PC1" selected>PC1 - dominant market stress mode</option>
    <option value="PC2">PC2 - secondary market mode</option>
  </select>
</div>

<div id="signature-plot" class="signature-plot"></div>

<p class="signature-caption">
  <strong>Figure X: Crisis signature comparison.</strong><br>
  Each node represents a crisis period. The vertical position and size of a node
  reflect the fraction of variance explained by the selected PCA component:
  larger and higher nodes indicate more synchronized, low-dimensional market
  behavior. Hovering over a node reveals the standardized feature loadings that
  define the corresponding crisis mechanism. Positive loadings indicate features
  that intensify the crisis mode, while negative loadings indicate stabilizing or
  opposing effects.
</p>

### What this comparison reveals

The crisis signatures highlight clear structural differences between major market shocks.

The **dot-com bubble** emerges as the most synchronized episode. Its dominant PCA mode
explains a larger fraction of the variance than in the other crises (roughly 57% of the variance is explained by this dominant mode), indicating that
market behavior collapsed onto a **single prevailing stress mechanism**.
This mode is driven by a sharp rise in sick assets and longer recovery times, while
the fraction of healthy assets contributes in the opposite direction. In this sense,
the dot-com crisis reflects a broad erosion of market health concentrated along
one dominant dimension.

The **subprime crisis** displays a less concentrated structure.
Its lower explained variance suggests a more **heterogeneous propagation of stress**,
consistent with a crisis originating within specific financial institutions and
spreading through tightly connected parts of the system rather than affecting all
assets uniformly.

The **COVID-19 shock**, while severe in magnitude, is characterized by a dominant mode
that explains even less variance. This indicates that market stress unfolded through
**multiple concurrent channels**, reflecting an abrupt shock impacting
assets and sectors in uneven ways.

Overall, these signatures show that crises with similar aggregate losses can differ
substantially in their internal dynamics. PCA reveals that each episode is governed
by a distinct latent stress structure, shaping how quickly, how broadly, and how
uniformly financial contagion spreads through the market.

## **Part V: Systemic Risk Radar**

Another way to compare these three crises is to look at how different they can be in terms of liquidity exchanges, volatility, causality between the nodes, how large the mean contagion index is, and how much the market goes down. The plot below gives a clear picture of what is happening in these three time periods.


<div class="plot-frame plot-frame--first">
  <iframe
    src="{{ '/assets/plots/systemic_risk_radar.html' | relative_url }}"
    loading="lazy"
    title="Systemic Risk Radar for the three periods.">
  </iframe>
</div>

We can easily assess that overall, the <strong>Subprime Financial Crisis</strong> had the strongest impact market-wise, as basically all the indices are higher than any of the other two crises. On the other hand, the COVID-19 epidemic and the dot-com bubble burst have lower causality and contagion dynamics, respectively. A lower causality for the COVID-19 period hereby confirms the results obtained with PCA, as we previously found that this period did not have one distinct stress structure but the outbreak rather unfolded through multiple channels. There was not necessarily causality between different nodes or sectors of the network as they did not react to stress in the same way.

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
<script src="https://cdn.plot.ly/plotly-2.27.0.min.js"></script>
<script>
(async function buildCrisisSignature() {

  const FILES = {
    "Dot-com (2000)": "{{ '/assets/data/pca_signature_dot-com_2000.csv' | relative_url }}",
    "Subprime (2008)": "{{ '/assets/data/pca_signature_subprime_2008.csv' | relative_url }}",
    "COVID (2020)": "{{ '/assets/data/pca_signature_covid_2020.csv' | relative_url }}"
  };

  const FEATURES = [
    "sick_frac",
    "mean_recovery_days",
    "health_frac",
    "mean_sick_return"
  ];

  async function loadCSV(url) {
    const text = await fetch(url).then(r => r.text());
    const rows = text.trim().split("\n").map(r => r.split(","));
    const header = rows.shift();
    return rows.map(r =>
      Object.fromEntries(r.map((v, i) => [header[i], v]))
    );
  }

  function extractSignature(rows, pc) {
    const ev = parseFloat(rows[0][`explained_var_${pc}`]);
    const loadings = FEATURES.map(f => ({
      feature: f,
      value: parseFloat(rows[0][`loading_${pc}_${f}`])
    }));
    return { ev, loadings };
  }

  function render(pc) {
    Promise.all(
      Object.entries(FILES).map(async ([name, url]) => {
        const rows = await loadCSV(url);
        const sig = extractSignature(rows, pc);
        return { name, ...sig };
      })
    ).then(crises => {

      const trace = {
        type: "scatter",
        mode: "markers+text",
        x: crises.map((_, i) => i),
        y: crises.map(c => c.ev),
        text: crises.map(c => c.name),
        textposition: "top center",
        marker: {
          size: crises.map(c => 40 + 200 * c.ev),
          color: "#2E357A",
          opacity: 0.85
        },
        hovertemplate: crises.map(c =>
          `<b>${c.name}</b><br>` +
          `Explained variance: ${(100*c.ev).toFixed(1)}%<br>` +
          c.loadings.map(l =>
            `${l.feature}: ${(+l.value).toFixed(2)}`
          ).join("<br>")
        )
      };

      Plotly.newPlot("signature-plot", [trace], {
        title: `Crisis signatures - ${pc}`,
        template: "plotly_white",
        xaxis: { visible: false },
        yaxis: {
          title: "Explained variance",
          tickformat: ".0%"
        },
        margin: { l: 60, r: 30, t: 70, b: 40 }
      });
    });
  }

  document.getElementById("pc-select").addEventListener("change", e => {
    render(e.target.value);
  });

  render("PC1");

})();
</script>

<script>
document.addEventListener("DOMContentLoaded", () => {

  // -------------------------
  // DATA (your cluster memberships)
  // -------------------------
  const CLUSTERS = {
    dotcom: {
      label: "Dot-com (2000)",
      groups: {
        0: ["AAPL","AMAT","AMZN","BKNG","KLAC","MCHP","MU","TXN"],
        1: ["ADBE","ADI","GILD","GS","ILMN","NVDA","PEP","QCOM","REGN"],
        2: ["BA","BIIB","CAT","CSCO","MSFT","ORLY","ROST","SNPS"],
        3: ["ADSK","AMD","AMGN","COST","INTC","INTU","ISRG","JPM","LRCX","VRTX"],
      }
    },
    subprime: {
      label: "Subprime (2008)",
      groups: {
        0: ["COST","GILD","GOOG","MCHP","MDLZ","ORLY","PEP","QCOM","SNPS","VRTX"],
        1: ["ADBE","AMZN","BIIB","BKNG","CSCO","ILMN","ISRG","MU","NFLX","ROST","TXN"],
        2: ["AAPL","ADI","AMAT","AMGN","BA","CVX","INTC","INTU","WMT","XOM"],
        3: ["ADSK","AMD","CAT","CRM","GS","JPM","KLAC","LRCX","MSFT","NVDA","REGN","SBUX"],
      }
    },
    covid: {
      label: "COVID (2020)",
      groups: {
        0: ["AMZN","CAT","CRWD","NFLX","ORLY","PEP","SNPS","VRTX"],
        1: ["AAPL","ADBE","AMGN","BIIB","COST","CRM","FTNT","GILD","GOOG","INTC","INTU","MDLZ","MSFT","QCOM","REGN","WMT"],
        2: ["ADSK","AMAT","AMD","BA","BKNG","CSCO","ILMN","ISRG","LRCX","MCHP","MU","NVDA","PYPL","TXN"],
        3: ["ADI","AVGO","CVX","GS","JPM","KLAC","PANW","ROST","SBUX","TSLA","XOM"],
      }
    }
  };

  function flatten(groups) {
    const out = [];
    for (const [cl, arr] of Object.entries(groups)) {
      arr.forEach(t => out.push({ ticker: t, cluster: +cl }));
    }
    return out.sort((a,b) => a.ticker.localeCompare(b.ticker));
  }

  function buildWidget(el) {
    const key = el.getAttribute("data-period");
    const meta = CLUSTERS[key];
    if (!meta) return;

    const all = flatten(meta.groups);

    // DOM
    el.innerHTML = `
      <div class="cw-top">
        <div>
          <div class="cw-title">Interactive directory - ${meta.label}</div>
          <div class="cw-sub">Here you can check to which cluster every stock belongs, and reciprocally which stocks are contained in every cluster.</div>
        </div>

        <div class="cw-controls">
          <input class="cw-search" type="text" placeholder="Search ticker (e.g., AAPL)" aria-label="Search ticker">
          <button class="cw-btn is-active" data-filter="all" type="button">All</button>
          <button class="cw-btn" data-filter="0" type="button">Cluster 0</button>
          <button class="cw-btn" data-filter="1" type="button">Cluster 1</button>
          <button class="cw-btn" data-filter="2" type="button">Cluster 2</button>
          <button class="cw-btn" data-filter="3" type="button">Cluster 3</button>
        </div>
      </div>

      <div class="cw-grid" aria-live="polite"></div>

      <div class="cw-footer">
        <div class="cw-kv">
          <span>Selected:</span>
          <span class="cw-pill" data-selected>None</span>
        </div>
      </div>
    `;

    const grid = el.querySelector(".cw-grid");
    const search = el.querySelector(".cw-search");
    const btns = Array.from(el.querySelectorAll(".cw-btn"));
    const selectedPill = el.querySelector("[data-selected]");

    let activeFilter = "all";
    let activeQuery = "";
    let selectedTicker = null;

    function render() {
      const q = activeQuery.trim().toUpperCase();

      const visible = all.filter(d => {
        const okFilter = (activeFilter === "all") || (String(d.cluster) === activeFilter);
        const okQuery = !q || d.ticker.includes(q);
        return okFilter && okQuery;
      });

      grid.innerHTML = "";
      visible.forEach(d => {
        const chip = document.createElement("div");
        chip.className = "cw-chip";
        chip.textContent = d.ticker;
        chip.setAttribute("data-cl", String(d.cluster));
        chip.setAttribute("role", "button");
        chip.setAttribute("tabindex", "0");
        if (selectedTicker === d.ticker) chip.classList.add("is-hit");

        const pick = () => {
          selectedTicker = d.ticker;
          selectedPill.textContent = `${d.ticker} : Cluster ${d.cluster}`;
          render(); // re-render to update highlight
        };

        chip.addEventListener("click", pick);
        chip.addEventListener("keydown", (e) => {
          if (e.key === "Enter" || e.key === " ") { e.preventDefault(); pick(); }
        });

        grid.appendChild(chip);
      });

      if (!selectedTicker) selectedPill.textContent = "None";
    }

    btns.forEach(b => {
      b.addEventListener("click", () => {
        btns.forEach(x => x.classList.toggle("is-active", x === b));
        activeFilter = b.getAttribute("data-filter") || "all";
        render();
      });
    });

    search.addEventListener("input", () => {
      activeQuery = search.value || "";
      render();
    });

    render();
  }

  // Build all widgets on page
  document.querySelectorAll(".cluster-widget").forEach(buildWidget);

});
</script>
<aside id="ticker-dictionary" class="ticker-dict">
  <button id="td-close" class="td-close" type="button" aria-label="Hide ticker helper">×</button>

  <div class="td-head">
    <div class="td-title">Ticker dictionary</div>
    <div class="td-sub">Click a ticker to see what the company does.</div>
  </div>

  <input
    id="td-search"
    class="td-search"
    type="text"
    placeholder="Search ticker (e.g. MSFT)"
    aria-label="Search ticker"
  />

  <div id="td-list" class="td-list"></div>

  <div id="td-card" class="td-card" hidden>
    <div class="td-ticker" id="td-ticker">—</div>
    <div class="td-desc" id="td-desc">—</div>
    <div class="td-links" id="td-links"></div>
  </div>
</aside>

<button id="td-toggle" class="td-toggle" type="button"
        aria-controls="ticker-dictionary" aria-expanded="true">
  ?
</button>


<script>
document.addEventListener("DOMContentLoaded", () => {

  /* ======================================
     TICKER DATA — EXACT ANALYSIS UNIVERSE
     ====================================== */

  const TICKER_INFO = {
    AAPL:"Apple designs consumer electronics and software, including the iPhone, Mac, iPad, and digital services.",
    MSFT:"Microsoft develops operating systems, enterprise software, and cloud services such as Windows, Office, and Azure.",
    AMZN:"Amazon operates a global e-commerce platform and Amazon Web Services (AWS).",
    GOOG:"Alphabet, through Google, provides internet services including Search, YouTube, Android, and cloud computing.",
    JPM:"JPMorgan Chase is a global financial institution offering banking and asset management services.",
    GS:"Goldman Sachs is an investment bank focused on advisory, trading, and asset management.",
    XOM:"Exxon Mobil is an integrated oil and gas company active in exploration, refining, and chemicals.",
    CVX:"Chevron is a multinational energy company engaged in oil and gas production.",
    BA:"Boeing designs and manufactures commercial airplanes and defense systems.",
    CAT:"Caterpillar produces heavy machinery for construction, mining, and industrial use.",
    WMT:"Walmart operates global retail stores and e-commerce platforms.",
    META:"Meta Platforms develops social media products including Facebook, Instagram, and WhatsApp.",
    TSLA:"Tesla designs electric vehicles, battery systems, and energy storage solutions.",
    NVDA:"NVIDIA develops graphics processing units and AI computing platforms.",
    NFLX:"Netflix is a streaming entertainment company producing and distributing video content.",
    ADBE:"Adobe develops software for digital media creation and document management.",
    CRM:"Salesforce provides cloud-based customer relationship management software.",
    INTC:"Intel designs and manufactures semiconductor processors for PCs and servers.",
    AMD:"AMD designs processors and graphics chips used in computing and gaming.",
    CSCO:"Cisco develops networking hardware, software, and cybersecurity solutions.",
    AVGO:"Broadcom designs semiconductor and infrastructure software solutions.",
    QCOM:"Qualcomm develops wireless communication chips and communication technologies.",
    TXN:"Texas Instruments designs analog and embedded semiconductor products.",
    AMAT:"Applied Materials supplies equipment used in semiconductor manufacturing.",
    MU:"Micron Technology produces memory and storage products.",
    LRCX:"Lam Research develops equipment for semiconductor fabrication.",
    KLAC:"KLA produces inspection and process control systems for chip manufacturing.",
    PYPL:"PayPal operates digital payment platforms for online transactions.",
    BKNG:"Booking Holdings operates online travel and accommodation platforms.",
    PEP:"PepsiCo produces beverages and snack food products.",
    COST:"Costco operates membership-based warehouse retail stores.",
    SBUX:"Starbucks operates a global chain of coffeehouses.",
    ADI:"Analog Devices designs analog and mixed-signal semiconductor products.",
    MCHP:"Microchip Technology produces microcontrollers and embedded control products.",
    MDLZ:"Mondelez International produces packaged snack and food products.",
    GILD:"Gilead Sciences develops antiviral and oncology pharmaceutical products.",
    VRTX:"Vertex Pharmaceuticals develops treatments for genetic diseases.",
    REGN:"Regeneron Pharmaceuticals develops biotechnology-based medicines.",
    AMGN:"Amgen develops therapies for serious diseases.",
    BIIB:"Biogen develops treatments for neurological disorders.",
    ISRG:"Intuitive Surgical develops robotic-assisted surgical systems.",
    ILMN:"Illumina develops genetic sequencing technologies.",
    PANW:"Palo Alto Networks provides cybersecurity solutions.",
    CRWD:"CrowdStrike develops cloud-based endpoint cybersecurity solutions.",
    FTNT:"Fortinet provides network security products.",
    ADSK:"Autodesk develops design and engineering software.",
    SNPS:"Synopsys provides electronic design automation software.",
    INTU:"Intuit develops financial and accounting software.",
    ORLY:"O’Reilly Automotive operates retail stores for automotive parts.",
    ROST:"Ross Stores operates off-price retail apparel and home goods stores."
  };

  /* ======================================
     BUILD UI
     ====================================== */

  const listEl = document.getElementById("td-list");
  const cardEl = document.getElementById("td-card");
  const tEl = document.getElementById("td-ticker");
  const dEl = document.getElementById("td-desc");
  const linksEl = document.getElementById("td-links");
  const searchEl = document.getElementById("td-search");

  const tickers = Object.keys(TICKER_INFO).sort();

  function renderList(filter=""){
    const q = filter.toUpperCase();
    listEl.innerHTML = "";

    tickers
      .filter(t => !q || t.includes(q))
      .forEach(t => {
        const chip = document.createElement("div");
        chip.className = "td-chip";
        chip.textContent = t;
        chip.onclick = () => show(t);
        listEl.appendChild(chip);
      });
  }

  function show(ticker){
    tEl.textContent = ticker;
    dEl.textContent = TICKER_INFO[ticker];
    linksEl.innerHTML =
      `<a href="https://www.google.com/search?q=${ticker}+company" target="_blank">Search</a>`;
    cardEl.hidden = false;
  }

  searchEl.addEventListener("input", () => renderList(searchEl.value));
  renderList();

});
</script>

<script>
document.addEventListener("DOMContentLoaded", () => {
  const panel = document.getElementById("ticker-dictionary");
  const toggle = document.getElementById("td-toggle");
  const closeBtn = document.getElementById("td-close");

  if (!panel || !toggle || !closeBtn) return;

  function openPanel(){
    panel.classList.remove("is-collapsed");
    toggle.classList.add("is-hidden");
    toggle.setAttribute("aria-expanded", "true");
  }

  function closePanel(){
    panel.classList.add("is-collapsed");
    toggle.classList.remove("is-hidden");
    toggle.setAttribute("aria-expanded", "false");
  }

  closeBtn.addEventListener("click", closePanel);
  toggle.addEventListener("click", openPanel);

  // start OPEN
  openPanel();
});
</script>


