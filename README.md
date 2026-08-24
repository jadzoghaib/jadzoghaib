# Jad Zoghaib

**Data scientist and AI product builder.** I work on operational and scientific problems where the answer has to end up as something a person can run: process intelligence, root-cause analysis, and AI pipelines with human approval gates. Business and data-science background, so the work gets scoped around a decision rather than a metric.

**Open to** data science, applied AI / AI product, analytics engineering, and data & AI consulting roles.
**Based across** Lebanon, UAE / GCC, and Europe. Open to remote.

[![Portfolio](https://img.shields.io/badge/Portfolio-jadzoghaib.github.io-4F9CF9?style=for-the-badge&labelColor=0A0B10)](https://jadzoghaib.github.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-in%2Fjadzoghaib-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=0A0B10)](https://linkedin.com/in/jadzoghaib)

---

## Start here

Three projects that show the whole range: the business framing, the analysis, and the working tool. Each one runs live in a browser.

### 1. ProcessLens: purchase-to-pay process intelligence

**[Live demo](https://jadzoghaib.github.io/processlens/)** · [Code](https://github.com/jadzoghaib/processlens) · [Methodology](https://github.com/jadzoghaib/processlens/blob/main/METHODOLOGY.md)

A Celonis-style cockpit over the BPI Challenge 2019 purchase-to-pay event log: 1,595,923 events, 251,734 cases, €1.56B of observed spend. Cross-filtered process maps, throughput funnels, conformance checks, and drill-downs to individual case traces.

**What the analysis found.** Median order-to-pay is 77 days, and the invoice-to-payment leg owns most of it (42d median, 97d at p90). 22% of cases pass through a manual payment-block release, covering €397M of spend. 13,881 distinct process variants, which says the process is under-standardised rather than slow in one place.

**Why it holds up.** The pandas ETL that computes every number ships in the same repo, the artifacts regenerate byte for byte from the raw log, and every metric definition is written down.

`React 19` `TypeScript` `pandas` `process mining`

### 2. Batch Investigation Console: root-cause analysis for pharma manufacturing

**[Live demo](https://jadzoghaib-batch-traceability-root-cause-studio-for--app-zrys7k.streamlit.app/)** · [Code](https://github.com/jadzoghaib/Batch-Traceability-Root-Cause-Studio-for-Pharma-Manufacturing)

Traces tablet quality back to incoming raw-material attributes and in-process compression conditions across 1,005 real production batches.

**The finding that shaped the product.** 22 of 44 candidate drivers *reverse their correlation sign* between pooled and within-product analysis. Product identity alone explains 85% of hardness variance. A standard pooled "top correlations" chart would send a quality investigator after exactly the wrong condition, so every comparison in the tool is scoped to a structurally comparable cohort instead.

**Two more decisions worth reading.** Batches are scored only against the control limits that existed at the moment of manufacture; scoring with hindsight instead flips the verdict on 394 of 1,005 batches. And evidence stays in three separate tiers (descriptive, association, model) rather than being fused into one confidence score, with a driver promoted only when two tiers agree.

`Python` `Streamlit` `pandas` `random forest` `root-cause analysis`

### 3. Locus: target and variant intelligence for drug discovery

**[Live console](https://jadzoghaib.github.io/genetic-variant-triage/)** · [Illustrated manual](https://jadzoghaib.github.io/genetic-variant-triage/manual.html) · [Code](https://github.com/jadzoghaib/genetic-variant-triage)

Two linked questions over one ontology. Which variants in a gene look misclassified, by reconciling AlphaMissense predictions against ClinVar's clinical assertions on AlphaFold structure and grading how much structural evidence actually backs each call. And whether a target is worth pursuing, by assembling genetic evidence, structural readiness, binding-site tractability and clinical activity into one dossier where every fact resolves back to the retrieval that produced it.

**The constraint it is built around.** It surfaces candidates for expert review and never asserts a clinical classification. That is enforced in code, not just stated: a test fails if any review outcome reads as a clinical call. Rebuilt from source weekly, with 218 tests across core rules, governance, and the exported site.

`Python` `DuckDB` `AlphaFold` `AlphaMissense` `ClinVar` `Open Targets` `3Dmol.js`

---

## Also worth opening

| Project | What it does | Stack |
|---|---|---|
| **[Aegis: SOC triage copilot](https://github.com/jadzoghaib/aegis-soc-triage)** · [docs hub](https://jadzoghaib.github.io/aegis-soc-triage/) | Alert ingestion, threat-intel enrichment, incident correlation, dual-classifier severity triage, and human-gated containment. Every stage is a visible workflow, and 14 techniques are mapped to MITRE ATT&CK in the interactive manual | `n8n` `FastAPI` `SQLite` `MITRE ATT&CK` |
| **[Supply Chain Sentinel](https://github.com/jadzoghaib/supply-chain-sentinel)** | Autonomous supplier-risk watch: GDELT ingestion, LLM risk analysis, scheduled per-supplier sweeps, geospatial impact scoring, approval-gated client advisories | `FastAPI` `n8n` `GDELT` `LLM` |
| **[CineMatch](https://movie-rec-sys-lovat.vercel.app)** · [code](https://github.com/jadzoghaib/Movie-RecSys) | MovieLens recommender with several algorithms behind one registry-driven interface: add a model and it appears in the API, the evaluation harness and the UI. Taste map, discovery slider, metrics lab | `Next.js` `FastAPI` `recommenders` |
| **[TeamMatch](https://google-talent-project-matching-reco.vercel.app)** · [code](https://github.com/jadzoghaib/Google-Talent-Project-Matching-Recommender-System) | Staffs a whole pipeline at once rather than ranking one match: matrix factorization plus content and personality scoring, feeding a cohesion-aware portfolio optimizer over 800 engineers and 300 projects | `TypeScript` `recommenders` `optimization` |

<details>
<summary><b>Everything else, by industry</b></summary>

<br>

**Life sciences**

| Project | What it does | Stack |
|---|---|---|
| [EnzySelect](https://enzyselect.streamlit.app/) · [code](https://github.com/jadzoghaib/enzyselect) | Prioritises candidate enzymes for PET plastic degradation against operating conditions and a testing budget, with transparent decomposable scoring and real AlphaFold/UniProt anchors. Educational prototype on a synthetic candidate set, and it says so on every screen | `Python` `Streamlit` `AlphaFold` `UniProt` |
| [Breast Cancer Detection](https://github.com/jadzoghaib/CC_Breast_Cancer_Detection) | Cloud-deployed containerised ML classifier | `Python` `AWS` `scikit-learn` |

**Finance**

| Project | What it does | Stack |
|---|---|---|
| [Sabadell Capstone](https://github.com/jadzoghaib/Sabadell_Capstone) | ESADE capstone with Banc Sabadell: XGBoost against LLM reasoned-decision engines for credit default, covering prompt-caching economics, SHAP against natural-language rationales, confidence-gated hybrid routing, and RAG over precedent loans | `Python` `XGBoost` `LLM` `RAG` |
| [Credit Default Prediction](https://github.com/jadzoghaib/DS-Finance-Credit-Default-) | Credit decisions on 25,000 applications, built around a deliberate target-leakage trap: one field reproduces the label at 99%. Excluded on principle, with an honest 0.86 out-of-fold accuracy reported instead | `Python` `scikit-learn` |

**Operations and energy**

| Project | What it does | Stack |
|---|---|---|
| [OilShield](https://github.com/jadzoghaib/oilshield) | Strategic stress-testing console for oil and gas portfolios: build a company from typed assets, shape a 36-month Brent scenario, watch break-evens, liquidity headroom and shut-in economics recompute. Revenues float with price while fixed costs keep running, and that asymmetry is the product | `Python` `Streamlit` `Plotly` |
| [Hotel Overbooking Tool](https://jadzoghaib-hotel-booking-ai2-app-my01c0.streamlit.app/) · [code](https://github.com/jadzoghaib/Hotel_Booking_AI2) | Cancellation prediction turned into a decision tool: given a caller requesting a room at a full hotel, accept or reject, weighing predicted cancellation risk against the cost of walking a confirmed guest | `Python` `scikit-learn` `Streamlit` |
| [GroceryAI](https://github.com/jadzoghaib/Grocery-Shopping-Optimizer-PDAI26) | Nutrition and grocery app: meal planning, LLM shopping-list generation against real Mercadona supermarket data, a fridge-to-recipe engine, and a multi-agent basket debate | `FastAPI` `LangGraph` `Groq` |

**HR, sports and media**

| Project | What it does | Stack |
|---|---|---|
| [TalentFlow](https://github.com/jadzoghaib/talentflow) | Hiring funnel on the TeamMatch engine: LLM profile extraction, cold-start match scoring, recruiter review gates that resume paused workflows, and weekly calibration | `Node 24` `n8n` `LLM` |
| [Stride](https://github.com/jadzoghaib/stride) | Athlete and club monetisation platform: evidence-based marketability analytics, sponsor campaign matching with fully decomposable scoring, and a deal pipeline that runs end to end | `FastAPI` `React` `Supabase` |
| [My Match Olympics](https://ioc-nil-monetization-platform-dpm.vercel.app) · [code](https://github.com/jadzoghaib/IOC-NIL-Monetization-Platform_DPM) | Three-sided fan-economy concept for the Olympic Games: fans discover athletes by personality match, athletes run content and sponsorship offers from one studio, sponsors scout by sport, country and audience fit. Independent student project, not affiliated with the IOC | `React` `TypeScript` |
| [Boardroom Simulator](https://github.com/jadzoghaib/Boardroom_Simulator_PDAI) | Eight-quarter startup simulation: quarterly events across six departments, LLM advisor chats, five fundraising stages, rival dynamics, and an ML success predictor scored at board reviews | `Python` `LLM` |
| [Hamlet Data Viz](https://github.com/jadzoghaib/R_Hamlet_DataVizClub) | Word frequency, sentiment arcs and character networks across the play | `R` `ggplot2` `NLP` |

</details>

---

## How I build

Most of these follow the same shape. Frame the decision first, get the data honest before modelling it, keep the uncertainty visible instead of collapsing it into a single score, and ship a running interface rather than a notebook. Where a pipeline makes a call that is hard to undo, a person approves it.

**Tools I actually use:** Python, SQL, pandas, scikit-learn, TypeScript/React, FastAPI, DuckDB, n8n, Streamlit, AWS (SageMaker, ECS), Docker, R.

## Currently building

[**Stride**](https://github.com/jadzoghaib/stride), a sponsorship marketplace for athletes and clubs, built around marketability analytics a sponsor can actually audit.

---

Happy to talk through any of these in detail. The fastest way to reach me is [LinkedIn](https://linkedin.com/in/jadzoghaib).
