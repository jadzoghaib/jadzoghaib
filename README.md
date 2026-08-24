# Jad Zoghaib

**Data scientist and AI product builder.** I work on operational and scientific problems where the answer has to end up as something a person can run. Recent work concentrates on clinical genomics and process intelligence: evidence provenance, root-cause analysis, and AI pipelines with human approval gates. Business and data-science background, so the work gets scoped around a decision rather than a metric.

**Open to** data science, applied AI / AI product, analytics engineering, and data & AI consulting roles.
**Based in** Barcelona, Spain. Open to remote and to GCC roles.

[![Portfolio](https://img.shields.io/badge/Portfolio-jadzoghaib.github.io-4F9CF9?style=for-the-badge&labelColor=0A0B10)](https://jadzoghaib.github.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-in%2Fjadzoghaib-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=0A0B10)](https://linkedin.com/in/jadzoghaib)

---

## Start here

Five projects, in the order I would open them.

### 1. Mendelea: an evidence timeline for reported genetic variants

[Code](https://github.com/jadzoghaib/mendelea)

A laboratory signs out a genetic variant, writes a report, and moves on. Years later the evidence underneath that report has changed and nothing tells them. Mendelea reconstructs what ClinVar asserted on any past date and reports what has moved since. It reports that the evidence moved and never asserts a classification. Research use only, not a medical device.

**The number I had to throw away.** Raw movement first read 67.1%. Almost all of it was a single ClinVar re-aggregation event that relabelled 5,843 variants in one nine-week window, which is the database changing how it aggregates rather than laboratories revising anything. True actionable movement is 7.2%. Telling a lab that 5,843 of its cases moved would have sent it re-reviewing thousands of files for nothing. `reports/policy.py` now detects that class of event automatically, and the adjustment is reported rather than quietly applied.

**Isolation enforced by reading the source.** A multi-tenant query once shipped with no tenant predicate, so a properly authenticated caller would have received every laboratory's data. A test now walks the AST of every source file and fails the build if any SQL naming a tenant-owned table omits `tenant_id`. That catches queries nobody thought to call.

Also worth a look: ingest pulls one gene out of a 19.1 MB ClinVar release over HTTP range requests, 98.1% saved, with BGZF and tabix readers written in pure Python because pysam does not build on Windows. The limitations register at the bottom of the README is the part I would read first.

`Python` `DuckDB` `bitemporal modelling` `ClinVar` `multi-tenancy`

### 2. Stride: a sponsorship marketplace priced on evidence

[Code](https://github.com/jadzoghaib/stride)

Sponsorship is priced on assertion. An athlete says they have reach, a brand takes the number on faith or pays an agency to guess, and nobody on either side of the table can decompose the price.

**What it does differently.** Marketability is computed from connected platforms through a versioned formula set, and every score carries its inputs, its coverage and its confidence. A sponsor who disagrees with a score can open it and see precisely which posts produced it. The commercial claim follows from the technical one: a marketplace whose prices are explainable lets both sides negotiate against evidence instead of reputation.

Athletes own their analytics, sponsors match campaign briefs against the athlete pool, clubs sell packages. First product draft, 35 tests, runs locally in two terminals with a self-seeding database.

`FastAPI` `React 18` `Supabase` `Python 3.11`

### 3. Locus: target and variant intelligence for drug discovery

**[Live console](https://jadzoghaib.github.io/genetic-variant-triage/)** · [Illustrated manual](https://jadzoghaib.github.io/genetic-variant-triage/manual.html) · [Code](https://github.com/jadzoghaib/genetic-variant-triage)

Two linked questions over one ontology. Which variants in a gene look misclassified, by reconciling AlphaMissense predictions against ClinVar's clinical assertions on AlphaFold structure and grading how much structural evidence actually backs each call. And whether a target is worth pursuing, by assembling genetic evidence, structural readiness, binding-site tractability and clinical activity into one dossier where every fact resolves back to the retrieval that produced it.

**The constraint it is built around.** It surfaces candidates for expert review and never asserts a clinical classification. That is enforced in code, not just stated: a test fails if any review outcome reads as a clinical call. Rebuilt from source weekly, with 218 tests across core rules, governance and the exported site.

`Python` `DuckDB` `AlphaFold` `AlphaMissense` `ClinVar` `Open Targets` `3Dmol.js`

### 4. ProcessLens: purchase-to-pay process intelligence

**[Live demo](https://jadzoghaib.github.io/processlens/)** · [Code](https://github.com/jadzoghaib/processlens) · [Methodology](https://github.com/jadzoghaib/processlens/blob/main/METHODOLOGY.md)

A Celonis-style cockpit over the BPI Challenge 2019 event log: 1,595,923 events, 251,734 cases, €1.56B of observed spend, with cross-filtered process maps and drill-downs to individual case traces.

**What the analysis found.** Median order-to-pay is 77 days and the invoice-to-payment leg owns most of it (42d median, 97d at p90). 22% of cases pass through a manual payment-block release, covering €397M of spend. 13,881 distinct process variants, which says the process is under-standardised rather than slow in one place. The pandas ETL that computes every number ships in the same repo and the artifacts regenerate byte for byte from the raw log.

`React 19` `TypeScript` `pandas` `process mining`

### 5. Aegis: SOC alert triage copilot

[Code](https://github.com/jadzoghaib/aegis-soc-triage) · **[Documentation hub](https://jadzoghaib.github.io/aegis-soc-triage/)**

Multi-source alert ingestion, threat-intel enrichment with an offline fallback, incident correlation, dual-classifier severity triage, and containment that a human has to approve. Every stage is a visible workflow rather than a black box, which is the point: an analyst can see why an alert was escalated and stop it before anything is contained.

The documentation hub carries an interactive threat manual mapping 14 techniques to MITRE ATT&CK, each with a clickable architecture diagram, plus the six workflow specs and the incident lifecycle.

`n8n` `FastAPI` `SQLite` `MITRE ATT&CK`

---

## Also worth opening

| Project | What it does | Stack |
|---|---|---|
| **[Batch Investigation Console](https://jadzoghaib-batch-traceability-root-cause-studio-for--app-zrys7k.streamlit.app/)** · [code](https://github.com/jadzoghaib/Batch-Traceability-Root-Cause-Studio-for-Pharma-Manufacturing) | Root-cause analysis across 1,005 real pharmaceutical production batches. 22 of 44 candidate drivers reverse their correlation sign between pooled and within-cohort analysis, so a standard pooled correlation chart sends the investigator after the wrong condition. Batches are scored only against the control limits that existed at the time of manufacture; scoring with hindsight flips the verdict on 394 of them | `Python` `Streamlit` `random forest` |
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
| [My Match Olympics](https://ioc-nil-monetization-platform-dpm.vercel.app) · [code](https://github.com/jadzoghaib/IOC-NIL-Monetization-Platform_DPM) | Three-sided fan-economy concept for the Olympic Games: fans discover athletes by personality match, athletes run content and sponsorship offers from one studio, sponsors scout by sport, country and audience fit. Independent student project, not affiliated with the IOC | `React` `TypeScript` |
| [Boardroom Simulator](https://github.com/jadzoghaib/Boardroom_Simulator_PDAI) | Eight-quarter startup simulation: quarterly events across six departments, LLM advisor chats, five fundraising stages, rival dynamics, and an ML success predictor scored at board reviews | `Python` `LLM` |
| [Hamlet Data Viz](https://github.com/jadzoghaib/R_Hamlet_DataVizClub) | Word frequency, sentiment arcs and character networks across the play | `R` `ggplot2` `NLP` |

</details>

---

## How I build

Most of these follow the same shape. Frame the decision first, get the data honest before modelling it, keep the uncertainty visible instead of collapsing it into a single score, and ship a running interface rather than a notebook. Where a pipeline makes a call that is hard to undo, a person approves it. Every one of these repos has a limitations section, and it is usually the section I would want read.

**Tools I actually use:** Python, SQL, pandas, scikit-learn, DuckDB, TypeScript/React, FastAPI, n8n, Streamlit, AWS (SageMaker, ECS), Docker, R.

## Currently building

[**Mendelea**](https://github.com/jadzoghaib/mendelea), the variant evidence timeline above, and [**Stride**](https://github.com/jadzoghaib/stride).

---

Happy to talk through any of these in detail. The fastest way to reach me is [LinkedIn](https://linkedin.com/in/jadzoghaib).
