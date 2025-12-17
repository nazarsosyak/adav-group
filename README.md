## **Who Infected the Market?**

**Ever wondered which stock took your wallet down the drain?**  
**Looking for someone to blame for your life savings disappearing?**

Markets rarely collapse in a single blow. They deteriorate through **chains of exposure**:
correlations tighten, sector linkages transmit stress, and hidden dependencies turn local shocks
into systemic events.

This datastory treats financial markets as a **living network**, where shocks behave like pathogens
and risk spreads through interaction channels. Our goal is not prediction, but **forensic understanding**:
reconstruct the outbreak, identify the main transmission routes, and explain how the system fails.

---

### **The idea**

Markets don’t collapse all at once. A crisis leaves traces.  
They spread.

A sudden price shock rarely stays local. It travels through correlations, sector linkages, and hidden dependencies, infecting stocks that were never directly exposed to the original event.

This project treats financial markets as a **living system**, where shocks behave like pathogens and risk propagates through a complex network.

we can investigate questions that resemble outbreak response:

- Where did the stress appear first?
- Which entities amplified it?
- Through which paths did it spread?
- When did the market stop containing it?

---

### **Research questions**

This investigation is guided the following research questions:

> **How do market shocks propagate?**
> Through which channels do shocks spread, and how do individual stocks and sectors react as the disturbance unfolds?

> **Can we identify a patient zero?**
> Is it possible to trace major market events back to an initial source, and distinguish between early carriers, super-spreaders, and secondary infections?

> **What are the dynamics of financial contagion?**
> How fast does risk propagate, how concentrated is the spread, and when does it become systemic?

> **Does the market have an immune system?**
> How does the market absorb, dampen or amplify shocks, and under what conditions does this defense mechanism fail?


---

### **Our objective**

We treat each crisis episode as a **case file** and aim to:

- identify the most probable **patient zero**,
- detect **super-spreaders** and amplification hubs,
- reconstruct the **propagation timeline** and dominant transmission paths,
- assess whether the outbreak remains **localized** or becomes **system-wide**.

---

### **How it works**

Using a large stock-level dataset, we reconstruct financial outbreaks step by step.  
Each post in this blog is a **case file**, documenting:

- early warning signals  
- transmission paths across stocks and sectors  
- super-spreader behavior  
- moments where the market’s immune system failed  

The goal is not prediction, but **forensic understanding**.

---

### **How the investigation works**

We analyze a stock-level dataset and reconstruct financial outbreaks step by step.
Each case file combines:
- an outbreak window extracted from the market timeline,
- interactive visualizations of network structure and evolution,
- role identification (patient zero, super-spreaders, at-risk entities),
- and sector-level mapping to interpret systemic risk.

The companion notebook contains the full implementation and computations;
this website focuses on **visual storytelling and interpretability**.

---

### **Investigation workflow**

Our workflow mirrors a real outbreak response:

1. **Market segmentation**  
   We scan the full return timeline to detect **critical regimes** where abnormal market behavior emerges.

2. **Case isolation**  
   Once a regime is flagged, we isolate it and analyze it as a **contained financial outbreak**.

3. **Network reconstruction**  
   Inside the outbreak window, we build dynamic interaction networks to identify:
   - the probable **patient zero**,
   - **super-spreaders**,
   - and dominant **propagation paths**.

4. **Sector mapping**  
   Finally, we project contagion onto sectors to detect:
   - **critical sectors** that amplify contagion,
   - **sector-to-sector transmission** patterns,
   - and whether the episode becomes **system-wide**.

---

**Welcome to the investigation.**  
Start with **The Story** to follow the analysis from the first signal to the full outbreak reconstruction.
<a class="btn-primary" href="{{ '/story/' | relative_url }}">Start the data story →</a>

