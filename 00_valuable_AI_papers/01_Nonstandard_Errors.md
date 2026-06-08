### Paper link: arxiv.org/abs/2603.16744

# Nonstandard Errors in AI Agents

**Ruijiang Gao · Steven Chong Xiao**
Naveen Jindal School of Management, University of Texas at Dallas
ruijiang.gao@utdallas.edu · steven.xiao@utdallas.edu

*arXiv:2603.16744v2 [cs.AI] 19 Mar 2026*

---

## Abstract

We study whether state-of-the-art AI coding agents, given the same data and research question, produce the same empirical results. Deploying 150 autonomous Claude Code agents to independently test six hypotheses about market quality trends in NYSE TAQ data for SPY (2015–2024), we find that AI agents exhibit sizable nonstandard errors (NSEs), that is, uncertainty from agent-to-agent variation in analytical choices, analogous to those documented among human researchers. AI agents diverge substantially on measure choice (e.g., autocorrelation vs. variance ratio, dollar vs. share volume). Different model families (Sonnet 4.6 vs. Opus 4.6) exhibit stable "empirical styles," reflecting systematic differences in methodological preferences. In a three-stage feedback protocol, AI peer review (written critiques) has minimal effect on dispersion, whereas exposure to top-rated exemplar papers reduces the interquartile range of estimates by 80–99% within converging measure families. Convergence occurs both through within-family estimation tightening and through agents switching measure families entirely, but convergence reflects imitation rather than understanding. These findings have implications for the growing use of AI in automated policy evaluation and empirical research.

**Keywords:** Nonstandard errors, AI agents

---

## 1 Introduction

The deployment of artificial intelligence in empirical research is accelerating rapidly. AI agents now automate tasks ranging from data collection and coding to statistical estimation and report writing (Lu et al., 2024). Projects such as Autonomous Policy Evaluation (APE; Social Catalyst Lab, 2026) deploy AI to produce end-to-end economics research papers, raising a fundamental question: if we ask different AI agents to analyze the same data and test the same hypothesis, will they produce the same result?

The concern is well motivated. A large literature documents that "researcher degrees of freedom" (Simmons et al., 2011) introduce substantial variation into empirical findings. Silberzahn et al. (2018) show that 29 teams analyzing the same soccer data reach divergent conclusions about whether dark-skinned players receive more red cards. Botvinik-Nezer et al. (2020) find that 70 neuroimaging teams testing nine hypotheses on the same fMRI data produce highly variable results. Menkveld et al. (2024) document that 164 research teams, given the same data and hypotheses about market microstructure, produce estimates with an interquartile range (IQR) comparable in magnitude to the standard error of any individual estimate. They use the term nonstandard errors (NSE) to describe this additional uncertainty arising from researcher-to-researcher variation in analytical choices in the "evidence-generating process" (EGP).

A natural question is whether AI agents, which lack the idiosyncratic training and institutional pressures that shape human researchers' choices, would exhibit similar variation. On one hand, AI agents drawing on the same foundation model might converge to a single "best" approach, eliminating NSE. On the other hand, the stochasticity inherent in language model sampling, combined with the underspecification of most empirical tasks (Steegen et al., 2016), could produce meaningful variation even among identically initialized agents.

We address this question by replicating the Menkveld et al. (2024) experimental design with AI agents. We deploy 150 autonomous Claude Code agents (100 Sonnet 4.6, 50 Opus 4.6) to independently test six hypotheses about market quality trends in SPY using NYSE TAQ millisecond data (2015–2024). Each agent operates as a fully autonomous researcher: it reads instructions, explores the data, constructs measures, estimates trends, writes a 2,000–4,000-word research report, and produces code, figures, and structured results. The entire pipeline, from data to deliverables, runs fully autonomously without human intervention. We conduct a three-stage feedback protocol that mimics a fully automated AI research society: Stage 1 (independent analysis), Stage 2 (AI peer review with written feedback), and Stage 3 (exposure to the five highest-rated exemplar papers). We analyze the dynamics of AI NSE in these stages.

**Key findings:**

First, we find that AI agents exhibit sizable nonstandard errors. The effect can range from negative to positive, insignificant to significant, and small to large. For example, for the market efficiency hypothesis (H1), the IQR of effect size estimates across agents is 2.43%/yr, with estimates ranging from −0.74%/yr to +1.7%/yr. For the hypothesis on trading volume (H4), the IQR is 10.69%/yr, driven entirely by agents choosing different volume measures (dollar volume at approximately +6%/yr vs. share volume at approximately −5%/yr). For price impact (H6), the IQR is 10.34%/yr, reflecting a split between trade-level price impact and Amihud illiquidity ratio measures (Amihud, 2002).

Second, the structure of AI NSE is distinctive. All 150 agents independently choose regression with a linear time trend as the estimation paradigm, split between level specifications (56%) and log specifications (44%). No agent uses relative changes (period-over-period ratios) or first differences, which are common in human choices. AI NSE is therefore concentrated almost entirely in measure-choice forks rather than in estimation-paradigm forks.

Third, different model families exhibit stable "empirical styles." Sonnet 4.6 agents overwhelmingly prefer autocorrelation measures for market efficiency (87%), level OLS, and daily frequency. Opus 4.6 agents universally choose variance ratio measures (100%), prefer log OLS, and use monthly frequency 28% of the time.

Fourth, AI peer review has no effect on reducing dispersion: the IQR is essentially unchanged from S1 to S2. In contrast, exposure to top papers triggers dramatic convergence. For converging measure families, the IQR collapses by 80–99% from S1 to S3. However, for two hypotheses (H1 and H5), dispersion increases as exemplar papers introduce new methodological options that agents adopt inconsistently.

---

## 2 Related Work

### 2.1 Automated Research with AI Agents

AI systems are increasingly deployed not merely as tools for researchers but as autonomous researchers themselves. Lu et al. (2024) introduce the AI Scientist, a system that autonomously generates hypotheses, designs experiments, runs code, and writes full scientific papers at a cost of less than $15 per paper. Project APE (Social Catalyst Lab, 2026) deploys AI agents for end-to-end economics policy evaluation. These systems raise a fundamental question that existing work has not addressed: how reliable are the empirical estimates they produce?

In concurrent and independent work, Huang et al. (2026) run 158 instances of GPT-5.2 on the #fincap dataset from Menkveld et al. (2024) and find that AI agents concentrate on a narrow set of analysis paths. Our study differs in three important ways. First, our agents are fully autonomous tool-using systems (Claude Code) that interactively explore data, write and debug code, and produce complete research reports. Second, we implement a three-stage feedback protocol. Third, we deploy two model families (Sonnet and Opus) within the same architecture, enabling decomposition of AI NSE into within-model stochasticity and between-model "empirical style" components.

### 2.2 Nonstandard Errors in Social Science

A growing literature documents that researcher-to-researcher variation in analytical choices introduces substantial uncertainty into empirical findings. Silberzahn et al. (2018) recruit 29 teams to analyze the same soccer data and find conclusions ranging from a significant positive to a significant negative effect. Botvinik-Nezer et al. (2020) scale to 70 neuroimaging teams testing nine hypotheses on the same fMRI data. Breznau et al. (2022) study 73 teams analyzing identical cross-country survey data on immigration attitudes, finding that observable team characteristics explain only 4% of the variability in results, with the remaining 96% attributable to undocumented analytical choices.

Menkveld et al. (2024) formalize this phenomenon as "nonstandard errors" (NSE) and conduct the largest such study to date, with 164 research teams and 34 peer evaluators testing six hypotheses on EURO STOXX 50 futures data. The multiverse analysis framework of Steegen et al. (2016) provides a complementary single-researcher approach.

A critical gap in this literature is that all existing many-analyst studies use human researchers, leaving open whether the observed variation reflects irreducible task ambiguity or idiosyncratic human factors. Our study addresses this gap by replacing human researchers with AI agents, thereby isolating the variation attributable to task underspecification.

### 2.3 LLM Behavioral Research

A parallel literature investigates the behavioral properties of LLMs as computational models of human decision-making. Horton et al. (2023) propose treating LLMs as "Homo silicus": simulated economic agents that can be endowed with preferences and information. Argyle et al. (2023) demonstrate "algorithmic fidelity," showing that GPT-3, when conditioned on sociodemographic backstories, generates response distributions that closely match real survey data from diverse human subpopulations.

This work also reveals systematic biases. Perez et al. (2023) and Sharma et al. (2024) document sycophancy: the tendency of LLMs to conform to a user's stated opinion even when incorrect. Our findings suggest it has a direct analog in research methodology: when AI agents see exemplar papers in Stage 3, they engage in wholesale imitation rather than independent evaluation.

---

## 3 Experimental Design

### 3.1 The #AIcap Project

We design the #AIcap project as an AI analog of the #fincap crowdsourced research project in Menkveld et al. (2024). Where #fincap recruited 164 human research teams, we deploy 150 AI coding agents. Each agent receives identical instructions and access to the same dataset, and independently produces a research report with quantitative estimates.

**AI agents.** Each agent is an instance of Claude Code (Anthropic), a command-line AI coding agent that can read files, write code, execute programs, inspect outputs, and iteratively refine its analysis. We use two model variants: 100 agents run Sonnet 4.6 (`claude-sonnet-4-6`) and 50 agents run Opus 4.6 (`claude-opus-4-6`). Both models use default sampling parameters (temperature = 1.0). Each agent has a budget cap of $20, 40 GB RAM, and 6 CPUs.

**Data.** The dataset comprises NYSE TAQ millisecond trade and quote data for the SPDR S&P 500 ETF Trust (SPY) from January 2, 2015, through December 31, 2024. The data spans 2,516 trading days, approximately 66 GB, and over 7 billion rows. Agents access the data as read-only Parquet files mounted in a Singularity container.

**Hypotheses.** Agents test six hypotheses about market quality trends over the sample period (2015–2024), each with the null of no change:

- **H1:** "Assuming that informationally-efficient prices follow a random walk, did market efficiency change over time?"
- **H2:** "The quoted bid-ask spread is the difference between the best ask and the best bid price. It is a standard measure of trading cost. Did the quoted bid-ask spread change over time?"
- **H3:** "The realized spread could be thought of as the gross-profit component of the spread as earned by the liquidity provider. It compares the trade price to the midpoint some time after the trade. Did the realized bid-ask spread change over time?"
- **H4:** "Did daily trading volume change over time?"
- **H5:** "Intraday price volatility captures the magnitude of price fluctuations within a trading day. Did intraday volatility change over time?"
- **H6:** "Price impact measures how much prices move in response to trading activity. It captures the information content of trades and the depth of the market. Did the price impact of trades change over time?"

Note that H2 and H3 provide explicit definitions of the measure, while H1, H4, and H6 leave the specific operationalization to the agent. We refer to H1, H4, and H6 as **abstract hypotheses** because they describe the concept at a level of abstraction that admits multiple valid measures.

**Deliverables.** Each agent produces: (i) a structured CSV with effect size, standard error, t-statistic, and direction for each hypothesis; (ii) a research report of 2,000–4,000 words; (iii) all analysis code with reproduction instructions; and (iv) figures.

**Isolation.** Agents run inside Singularity containers with filesystem isolation. They cannot communicate with each other or see other agents' outputs. Variation across agents arises solely from the stochasticity of the language model's sampling process.

### 3.2 Three-Stage Feedback Protocol

Following Menkveld et al. (2024), we implement a staged feedback protocol:

- **Stage 1 (Independent analysis).** Each agent independently analyzes the data and produces its deliverables.
- **Stage 2 (Peer review).** Each agent receives anonymized written evaluations from two AI peer evaluators (one Sonnet, one Opus) rating its Stage 1 report on a 0–10 scale per hypothesis, with detailed written feedback. The agent then revises its report and results.
- **Stage 3 (Top papers).** Each agent receives the five highest-rated anonymized Stage 2 reports and may revise its analysis one final time.

### 3.3 Effect Size Normalization

We develop a conversion pipeline to normalize all effect sizes to a common unit: percentage change per year (%/yr) relative to the mean level of the measure. For each agent, an Opus conversion agent classifies the model as log or level, detects any pre-scaling, computes the time-series mean of the dependent variable, and converts level-model effect sizes via:

> effect size_%/yr = (effect size / mean_y) × 100

**Cost.** The total API cost for the experiment is $1,558 across 450 agent-stage runs, with a median cost of $3.17 per agent for Stage 1, $1.90 for Stage 2, and $2.87 for Stage 3. The median wall-clock time is 53 minutes for S1, 27 minutes for S2, and 25 minutes for S3. By comparison, Menkveld et al. (2024) estimate approximately 27 person-years of effort from their 164 human teams, which would cost approximately $2.7 million at a $100,000 annual salary.

---

## 4 AI Nonstandard Errors Exist and Are Structured

### 4.1 NSE Is Sizable

Table 1 reports the distribution of Stage 1 effect size estimates (%/yr) across 150 agents for each hypothesis.

**Table 1: Stage 1 effect size distribution (%/yr) across 150 AI agents**

| Hyp | N | Q10 | Q25 | Median | Q75 | Q90 | IQR | IDR |
|-----|---|-----|-----|--------|-----|-----|-----|-----|
| H1 | 150 | −1.65 | −0.74 | −0.06 | 1.70 | 2.86 | 2.43 | 4.51 |
| H2 | 150 | −6.74 | −6.63 | −6.21 | −6.21 | −6.19 | 0.43 | 0.55 |
| H3 | 150 | 1.17 | 2.33 | 4.75 | 7.61 | 9.21 | 5.28 | 8.05 |
| H4 | 150 | −4.71 | −4.60 | 5.84 | 6.09 | 6.09 | 10.69 | 10.80 |
| H5 | 150 | 2.98 | 3.00 | 3.08 | 3.54 | 3.67 | 0.54 | 0.69 |
| H6 | 150 | −14.97 | −13.23 | −10.31 | −2.89 | −1.35 | 10.34 | 13.62 |

*Notes: Effect sizes are expressed as percentage change per year (%/yr) relative to the measure's mean level. IQR = Q75 − Q25; IDR = Q90 − Q10. All estimates are from Stage 1 (independent analysis, before any feedback).*

The estimates reveal a clear pattern of heterogeneity. For H2 (quoted spread), agents are near-unanimous: all 150 find that spreads decreased, with a median of −6.21%/yr and an IQR of only 0.43. In contrast, for H4 (volume), the distribution is sharply bimodal in S1: 90 agents using dollar volume find approximately +6.1%/yr growth, while 60 agents using share volume find approximately −4.6%/yr decline.

### 4.2 AI NSE Is Driven by Measure Choice

A key structural feature of AI NSE is its concentration in discrete measure-choice forks. Table 2 reports the IQR after stratifying H1 and H4 by measure family.

**Table 2: Stratified Stage 1 NSE: H1 and H4 by measure family**

| Hypothesis | N | Median | IQR | IDR |
|------------|---|--------|-----|-----|
| H1: autocorrelation | 87 | −0.33 | 2.73 | 7.40 |
| H1: variance ratio | 63 | −0.05 | 1.45 | 2.70 |
| H2 (all) | 150 | −6.21 | 0.43 | 0.55 |
| H3 (all) | 150 | 4.75 | 5.28 | 8.05 |
| H4: dollar volume | 90 | 6.09 | 0.25 | 0.82 |
| H4: share volume | 60 | −4.60 | 0.11 | 0.55 |
| H5 (all) | 150 | 3.08 | 0.54 | 0.69 |
| H6: price impact | 84 | −13.03 | 2.59 | 5.33 |
| H6: Amihud | 60 | −2.75 | 1.35 | 5.65 |
| H6: Kyle λ | 6 | 3.00 | 6.98 | — |

We decompose AI NSE into three distinct sources:

1. **Hypothesis abstraction:** the research question admits multiple valid operationalizations (e.g., "market efficiency" can be measured via autocorrelation or variance ratio; "trading volume" can mean dollar or share volume; "price impact" can be trade-level or Amihud). This affects H1, H4, and H6.
2. **Specification-choice variation:** agents agree on the construct and measure but differ in functional form (log vs. level regression), frequency (daily vs. monthly), or estimation details. This affects H2, H3, and H5.

**Table 3: Sources of AI NSE by hypothesis (Stage 1)**

| Hyp | Overall IQR | Dominant source | Within-source IQR |
|-----|-------------|-----------------|-------------------|
| H1 | 2.43 | Hypothesis abstraction (AC vs VR) + sub-forks | AC: 2.74, VR: 1.45. Within AC subcells: 0.02–0.34 |
| H2 | 0.43 | Specification (log vs level OLS) | Level: 0.003. Log: 0.11 |
| H3 | 5.28 | Specification (trade weighting) | Equal-wtd: 3.26. Vol-wtd: 2.04. Dollar-wtd: 1.26 |
| H4 | 10.69 | Hypothesis abstraction (dollar vs share volume) | Dollar: 0.25. Share: 0.11 |
| H5 | 0.54 | Specification (log vs level OLS) | Level: 0.005. Log: 0.12 |
| H6 | 10.34 | Hypothesis abstraction (price impact vs Amihud vs Kyle λ) | Price impact: 2.59. Amihud: 1.35 |

### 4.3 Paradigm Uniformity

All 150 agents independently choose to estimate trends by regressing the measure on a time trend via OLS. The variation is confined to:

- **Functional form:** level OLS (56%) vs. log OLS (44%)
- **Standard error correction:** HAC/Newey-West (80%), robust/HC3 (11%), none (9%)
- **Frequency:** daily (86%), monthly (13%), annual (1 agent)

This contrasts with human teams in Menkveld et al. (2024), where 35% use regression with a linear time trend, 58% use relative changes (period-over-period ratios), and 6% use log-differences. The relative-change paradigm, which is the most common among humans, is entirely absent among AI agents.

### 4.4 Model-Specific Empirical Styles

Different model families exhibit systematic methodological preferences that we term "empirical styles."

**Table 4: Model-specific empirical styles (Stage 1)**

| Hypothesis | Fork | Sonnet 4.6 (N=100) | Opus 4.6 (N=50) | Test |
|------------|------|-------------------|-----------------|------|
| H1 | Autocorrelation | 87% | 0% | 10.97*** |
| H1 | Variance ratio | 13% | 100% | |
| H1 | Level OLS | 96% | 36% | |
| H1 | Log OLS | 4% | 64% | |
| H2 | Level OLS | 90% | 14% | 37.64*** |
| H2 | Log OLS | 10% | 86% | |
| H3 | Level OLS | 99% | 62% | 15.19*** |
| H3 | Log OLS | 1% | 38% | |
| H3 | Equal-weighted | 79% | 18% | |
| H3 | Volume/dollar-weighted | 20% | 76% | |
| H4 | Dollar volume | 50% | 80% | 7.17*** |
| H4 | Share volume | 50% | 20% | |
| H5 | Level OLS | 69% | 12% | 10.01*** |
| H5 | Log OLS | 31% | 88% | |
| H6 | Price impact | 47% | 74% | 12.62*** |
| H6 | Amihud | 47% | 26% | |
| All | Daily frequency | 93% | 72% | χ²=14.31*** |
| All | Monthly frequency | 6% | 28% | |

*Notes: *** denotes p < 0.001. All six hypotheses reject distributional equality.*

The most pronounced difference is in H1 (market efficiency): 87% of Sonnet agents choose autocorrelation measures, while 100% of Opus agents choose variance ratio measures. A consistent pattern emerges: Opus strongly prefers log OLS, while Sonnet prefers level OLS.

---

## 5 Feedback Effects

### 5.1 Peer Review Has Minimal Effect

**Table 5: IQR convergence across stages**

| Hyp | S1 IQR | S2 IQR | S3 IQR | S1→S2 | S2→S3 | S1→S3 |
|-----|--------|--------|--------|--------|--------|--------|
| H1 | 2.43 | 2.69 | 5.68 | +10.7% | +111.1% | +133.6% |
| H2 | 0.43 | 0.43 | 0.01 | +0.2% | −98.1% | −98.1% |
| H3 | 5.28 | 5.56 | 3.01 | +5.4% | −46.0% | −43.0% |
| H4 | 10.69 | 10.69 | 10.69 | +0.0% | +0.0% | +0.0% |
| H5 | 0.54 | 0.54 | 0.96 | +0.2% | +78.1% | +78.4% |
| H6 | 10.34 | 10.44 | 2.09 | +1.0% | −80.0% | −79.8% |

From S1 to S2 (peer review), the IQR is essentially unchanged for most hypotheses. On average, AI peer review does not reduce estimate dispersion.

Importantly, the absence of IQR reduction does not mean agents ignore the feedback. Between S1 and S2, 42% of agents change their measure name, 29% change their model specification, and 44% change their effect size by more than 0.5%/yr. The issue is that these changes are *undirected*: agents move toward and away from the cross-agent median in roughly equal proportions. Peer review generates movement but not convergence.

This contrasts with Menkveld et al. (2024), where convergence is distributed roughly evenly across all four stages. The difference may reflect how human researchers and AI agents process feedback. Human researchers can evaluate a critique's merit and make targeted adjustments. AI agents appear to treat feedback as a prompt for wholesale revision, sometimes switching measures entirely rather than refining their existing approach.

### 5.2 Top Papers Drive Dramatic Convergence

From S1 to S3 (the combined effect of peer review and top-paper exposure), the IQR declines substantially for four of six hypotheses:

- **H2:** −98% (IQR from 0.43 to 0.008)
- **H6:** −80% (IQR from 10.34 to 2.09)
- **H3:** −43% (IQR from 5.28 to 3.01; marginally significant, p = 0.076)
- **H4 (dollar volume):** −97% (stratified IQR from 0.25 to 0.007)

Nearly all of this convergence occurs in the S2-to-S3 transition (top papers), not the S1-to-S2 transition (peer review). Agents shift their methodology to match the top papers. For H6, the fraction using trade-level price impact rises from 56% (S1) to 99% (S3), while Amihud illiquidity nearly disappears.

### 5.3 Stratified Convergence

**Table 6: Stratified IQR convergence across stages**

**Panel A: All agents (S1 and S3 populations may differ)**

| Family | N_S1 | N_S3 | S1 IQR | S3 IQR | ΔIQR |
|--------|------|------|--------|--------|------|
| H1: autocorrelation | 87 | 25 | 2.74 | 0.13 | −95.4% |
| H1: variance ratio | 63 | 125 | 1.45 | 5.51 | +281.5% |
| H4: dollar volume | 90 | 45 | 0.25 | 0.007 | −97.0% |
| H4: share volume | 60 | 88 | 0.11 | 0.001 | −99.3% |

**Panel B: Stayers only (same agents in S1 and S3)**

| Family | N | S1 IQR | S3 IQR | ΔIQR | p-value |
|--------|---|--------|--------|------|---------|
| H1: AC stayers | 25 | 7.16 | 0.13 | −98.3% | 0.002 |
| H1: VR stayers | 63 | 1.45 | 2.50 | +73.2% | 0.090 |
| H2 | 150 | 0.43 | 0.008 | −98.1% | 0.005 |
| H3 | 150 | 5.28 | 3.01 | −43.0% | 0.074 |
| H5 | 150 | 0.54 | 0.96 | +78.4% | <0.001 |
| H6 | 150 | 10.34 | 2.09 | −79.8% | <0.001 |
| Menkveld (human, S1→S4) | 164 | — | — | −47.2% | <0.005 |

Within converging measure families, AI convergence from S1 to S3 ranges from −80% to −99%. Convergence operates through two distinct mechanisms: (1) within-family estimation tightening, and (2) measure-family migration (e.g., 62 of 87 autocorrelation agents switch to variance ratio by S3).

### 5.4 Divergence Cases

Not all hypotheses converge. H1:variance ratio IQR increases by 282% from S1 to S3. Two of the five top papers use signed variance ratio deviation (VR(5) − 1) and find a positive trend. Agents that previously used autocorrelation switch to variance ratio but implement it inconsistently: some use |VR − 1| (absolute), finding near-zero trends; others use the signed version, finding approximately +5.5%/yr. The top papers created a new measure-choice fork rather than resolving an existing one.

### 5.5 Measure Switching and Hypothesis Ambiguity

For H4, where the five top papers are split (2 share volume, 2 dollar volume, 1 number of trades), 91% of agents switch their volume measure between S1 and S3. The transition matrix is striking: 78 of 90 dollar-volume agents switch to share volume, while simultaneously 41 of 60 share-volume agents switch to dollar volume — producing a near-random shuffle of family membership. Only 14 of 150 agents (9%) retain their original measure.

This wholesale measure switching is economically irrational. An agent that chose dollar volume in S1 because it measures capital flows has no analytical reason to switch to share volume in S3 merely because a top-rated paper used share volume. The switch reflects **imitation without understanding**: agents copy the exemplar's measure choice without evaluating whether it is economically superior to their own.

---

## 6 Multiverse Analysis

### 6.1 Fork Taxonomy

**Table 7: Methodology fork taxonomy (Stage 1, 150 agents)**

| Category | Fork | Distribution |
|----------|------|--------------|
| **Measure** | H1 measure family | autocorrelation 58%, variance ratio 42% |
| | H1 abs vs. signed | absolute 73%, signed 27% |
| | H4 measure family | dollar volume 60%, share volume 40% |
| | H6 measure type | price impact 56%, Amihud 40%, Kyle λ 4% |
| **Estimation** | Functional form | level OLS 56%, log OLS 44% |
| | SE correction | HAC 59%, NW 21%, robust/HC3 11%, none 9% |
| | Frequency | daily 86%, monthly 13%, annual 1% |
| | NW lag length | ranges from 2 to 252 (median 10) |
| **Data** | Trading hours | RTH 9:30–16:00 (100%) |
| | Outlier treatment | none (85%), winsorize (7%), clip/trim (8%) |
| | Odd-lot inclusion | include 49%, exclude 17%, unknown 34% |
| | Trade subsampling | none (97%), 5k–50k trades/day (3%) |

### 6.2 Which Forks Matter Most?

**Table 8: Variance decomposition: Which forks explain AI NSE?**

| Hypothesis | Fork | R² | F-stat | Sig. |
|------------|------|----|--------|------|
| H1: Efficiency | abs or signed | 0.165 | 29.3 | *** |
| | measure family | 0.165 | 29.1 | *** |
| | llm (Sonnet/Opus) | 0.132 | 22.5 | *** |
| | scale (log/level) | 0.085 | 4.5 | *** |
| H2: Quoted Spread | scale (log/level) | 0.882 | 1110.8 | *** |
| | llm (Sonnet/Opus) | 0.446 | 119.0 | *** |
| | se correction | 0.095 | 5.1 | *** |
| H3: Realized Spread | trade weighting | 0.145 | 8.2 | *** |
| | scale (log/level) | 0.027 | 4.1 | ** |
| | llm (Sonnet/Opus) | 0.021 | 3.1 | * |
| H4: Volume | measure family | 0.954 | 3069.5 | *** |
| | llm (Sonnet/Opus) | 0.085 | 13.8 | *** |
| | scale (log/level) | 0.054 | 8.5 | *** |
| H5: Volatility | scale (log/level) | 0.205 | 38.2 | *** |
| | se correction | 0.023 | 1.1 | |
| H6: Price Impact | h6 measure type | 0.623 | 121.6 | *** |
| | trade weighting | 0.478 | 33.2 | *** |
| | scale (log/level) | 0.356 | 81.8 | *** |
| | llm (Sonnet/Opus) | 0.065 | 10.3 | *** |

*Notes: ***, **, * denote significance at 1%, 5%, 10%.*

For H4 (volume), the measure family fork alone explains 95.4% of all cross-agent variation. For H2 (quoted spread), the scale fork explains 88.2%. For H1, the LLM backbone (Sonnet vs. Opus) explains 13.2% of variance.

---

## 7 Discussion

### 7.1 Structure of AI NSE in Context

**Table 9: AI NSE in context: comparison with Menkveld et al. (2024)**

| Property | Human (Menkveld et al., 2024) | AI (this paper) |
|----------|-------------------------------|-----------------|
| Paradigm diversity | High (linear trend 35%, relative changes 58%, log-diff 6%) | Low (level regression 56%, log regression 44%; no relative changes) |
| Measure diversity | Moderate | High (model-dependent) |
| Jensen's inequality | Major source of outliers | Absent |
| Feedback response | Gradual, each stage contributes | Binary: exemplars work, critiques do not |
| PE quality → NSE | Higher quality → −33% IQR | Significant for H4, H6; not for H1, H2, H5 |
| Convergence S1→S3/S4 | −47% IQR (4 stages) | −80% to −99% stratified (3 stages) |

AI NSE is concentrated in measure-choice forks with near-zero within-family variation, whereas Menkveld et al. (2024) find that human NSE is additionally driven by estimation-paradigm diversity.

An important distinction emerges between two types of cross-agent variation. The first is variation from different but defensible analytical choices applied to the same well-defined construct. The second is **hypothesis abstraction**: variation arising because the hypothesis itself admits multiple valid interpretations. For the three abstract hypotheses (H1, H4, H6), much of the cross-agent variation reflects hypothesis abstraction rather than analytical disagreement.

### 7.2 AI NSE as a Lower Bound on Human NSE

An important implication of our findings is that AI NSE potentially provides a lower bound on the nonstandard errors that would arise among human researchers facing the same task. The argument is as follows. AI agents share a common training corpus, a common architecture, and common instruction-following behavior. The only sources of variation are sampling stochasticity and model-family differences. Human researchers, by contrast, bring idiosyncratic graduate training, institutional norms, disciplinary preferences, career incentives, and varying levels of domain expertise.

Every fork that AI agents disagree on reflects genuine ambiguity in the research question rather than any deficiency in the analyst. Human researchers may additionally disagree on forks where AI agents show limited diversity (such as the relative-change paradigm), suggesting that AI NSE provides a plausible lower bound.

This framing reinterprets AI NSE not as a deficiency but as a diagnostic. The measure-choice forks that AI agents cannot resolve reveal irreducible ambiguity in the research question itself. This perspective suggests a practical use for AI agents: deploying a multiverse of AI agents as a **pre-registration diagnostic** to estimate the minimum NSE for a given research design before committing human effort.

### 7.3 Implications for Automated Policy Evaluation

Projects such as APE (Social Catalyst Lab, 2026) deploy AI agents to produce end-to-end economics research. Our findings suggest that the credibility of AI-generated empirical results depends critically on which measure-choice forks the agent happens to take, and different model families have different stable preferences. A single AI-generated estimate should not be treated as ground truth.

We recommend **multiverse analysis** (Steegen et al., 2016) as a standard complement to AI-generated estimates: running the same analysis with multiple measure definitions, model specifications, and agent configurations to reveal the full distribution of plausible results.

### 7.4 Implications for AI-Assisted Research

For researchers using AI as coding assistants, our findings highlight that the tool's defaults encode methodological preferences. A researcher using Sonnet would likely see autocorrelation-based efficiency measures; the same researcher using Opus would see variance ratio measures. Reporting the LLM model version is necessary but insufficient for reproducibility, as the same model at different temperature draws produces different fork choices.

### 7.5 AI NSE as Learned Uncertainty, Not Error

The term "nonstandard errors" frames analytical variation as a problem to be eliminated. We argue for a more nuanced interpretation: much of the variation we observe reflects inherent uncertainty in social science research design that AI agents have learned from the research literature itself.

During pre-training, large language models process millions of academic papers spanning decades of methodological debate. When different agent runs select different measures, they are sampling from the empirical distribution of defensible analytical choices as represented in the training corpus. In this view, AI NSE is not a deficiency of the model but a faithful reflection of the methodological uncertainty that the social science literature itself contains.

We therefore recommend that **AI NSE be preserved rather than eliminated** in models intended for research use. The variation across runs is informative: it reveals which aspects of a research question are well-specified and which are underspecified. Deployed as a multiverse tool, AI agents can provide a rapid, low-cost assessment of the inherent uncertainty in a research design.

### 7.6 Limitations

**Trade direction classification.** The realized spread (H3) and price impact (H6) measures require classifying each trade as buyer- or seller-initiated. For SPY, where trades occur at sub-millisecond frequency and the spread is often 1 cent, tick-test classification is known to perform poorly. No agent validates classification accuracy.

**Effective spread decomposition.** In the standard microstructure framework, the effective spread decomposes approximately into realized spread plus price impact: H2 ≈ H3 + H6. No agent verifies this internal consistency condition.

**Top paper selection and evaluator bias.** The five exemplar papers shown in Stage 3 are selected by AI peer evaluation scores. If AI evaluators systematically prefer certain measure choices (e.g., Opus evaluators preferring variance ratio), the top paper selection may propagate evaluator preferences rather than reflect genuine quality.

**External validity.** We examine a single, extremely liquid asset (SPY) in a single domain (market microstructure). Whether AI NSE patterns generalize to other empirical domains remains an open question.

---

## 8 Conclusion

This paper documents that state-of-the-art AI coding agents exhibit sizable nonstandard errors. When given the same research question and dataset, different agent runs produce widely varying estimates of key market quality measures for SPY. The variation is not random noise but structured: it arises from specific methodological forks (e.g., autocorrelation vs. variance ratio for market efficiency) that are stable across runs and model families.

AI peer review (S2) is surprisingly ineffective at reducing the NSE in AI agents as it fails to resolve the underlying methodological forks and may encourage agents to explore different methodological paths. When exposed to exemplar papers, AI agents converge through two mechanisms: within-family estimation tightening (IQR reductions of 80–99% in converging families) and cross-family migration. However, exemplar exposure can also increase dispersion when top papers introduce new methodological options that agents adopt inconsistently.

**Practical implications:**

1. A single AI estimate should not be trusted as definitive, since the "which measure" fork alone can flip conclusions.
2. AI peer review is ineffective at reducing NSE, while exemplar-based calibration is far more powerful but can backfire.
3. Different model families encode different methodological "styles" that persist across runs.
4. Multiverse analysis should be standard practice when deploying AI agents for empirical research.

**Data and code availability.** All agent outputs, converted results, and analysis scripts are available at https://github.com/ruijiang81/AI_NSE/. The underlying NYSE TAQ data can be accessed through Wharton Research Data Services.

---

## References

Amihud, Y. (2002). Illiquidity and stock returns: Cross-section and time-series effects. *Journal of Financial Markets*, 5(1):31–56.

Argyle, L. P., Busby, E. C., Fulda, N., Gubler, J. R., Rytting, C., and Wingate, D. (2023). Out of one, many: Using language models to simulate human samples. *Political Analysis*, 31(3):337–351.

Bessembinder, H. and Kaufman, H. M. (1997). A comparison of trade execution costs for NYSE and NASDAQ-listed stocks. *Journal of Financial and Quantitative Analysis*, 32(3):287–310.

Botvinik-Nezer, R., et al. (2020). Variability in the analysis of a single neuroimaging dataset by many teams. *Nature*, 582(7810):84–88.

Breznau, N., et al. (2022). Observing many researchers using the same data and hypothesis reveals a hidden universe of uncertainty. *Proceedings of the National Academy of Sciences*, 119(44):e2203150119.

Brodeur, A., Cook, N., and Heyes, A. (2020). Methods matter: p-hacking and publication bias in causal analysis in economics. *American Economic Review*, 110(11):3634–3660.

Harvey, C. R., Liu, Y., and Zhu, H. (2016). … and the cross-section of expected returns. *The Review of Financial Studies*, 29(1):5–68.

Horton, J. J., Filippas, A., and Manning, B. (2023). Large language models as simulated economic agents: What can we learn from homo silicus? Working Paper 31122, National Bureau of Economic Research.

Huang, W., Menkveld, A. J., and Yu, S. (2026). AI "errors". Working paper, Bank for International Settlements, Vrije Universiteit Amsterdam, and Singapore Management University.

Lee, C. M. C. and Ready, M. J. (1991). Inferring trade direction from intraday data. *The Journal of Finance*, 46(2):733–746.

Lo, A. W. and MacKinlay, A. C. (1988). Stock market prices do not follow random walks: Evidence from a simple specification test. *The Review of Financial Studies*, 1(1):41–66.

Lu, C., et al. (2024). The AI scientist: Towards fully automated open-ended scientific discovery. *arXiv preprint arXiv:2408.06292*.

Menkveld, A. J., et al. (2024). Nonstandard errors. *The Journal of Finance*, 79(3):2339–2390.

Perez, E., et al. (2023). Discovering language model behaviors with model-written evaluations. In *Findings of ACL 2023*, pages 13387–13434.

Sharma, M., et al. (2024). Towards understanding sycophancy in language models. In *Proceedings of ICLR 2024*.

Silberzahn, R., et al. (2018). Many analysts, one data set: Making transparent how variations in analytic choices affect results. *Advances in Methods and Practices in Psychological Science*, 1(3):337–356.

Simmons, J. P., Nelson, L. D., and Simonsohn, U. (2011). False-positive psychology: Undisclosed flexibility in data collection and analysis allows presenting anything as significant. *Psychological Science*, 22(11):1359–1366.

Social Catalyst Lab (2026). Project APE: Autonomous policy evaluation. University of Zurich, Department of Economics.

Steegen, S., Tuerlinckx, F., Gelman, A., and Vanpaemel, W. (2016). Increasing transparency through a multiverse analysis. *Perspectives on Psychological Science*, 11(5):702–712.

Zhang, X., et al. (2025). The invisible hand: Unveiling provider bias in large language models for code generation. In *Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics*, pages 21376–21403.

---

## Appendix A: Agent Instructions

### A.1 Cost, Running Time, and Turns

**Table 10: Cost, running time, and turns per agent-stage**

| | Mean | Median | Min | Max |
|--|------|--------|-----|-----|
| **API cost ($ per agent-stage)** | | | | |
| Sonnet S1 | 3.54 | 2.85 | 1.30 | 14.03 |
| Sonnet S2 | 2.13 | 1.58 | 0.69 | 13.63 |
| Sonnet S3 | 3.12 | 2.56 | 1.27 | 10.52 |
| Opus S1 | 5.59 | 4.19 | 1.83 | 18.70 |
| Opus S2 | 3.21 | 2.57 | 1.31 | 19.05 |
| Opus S3 | 4.75 | 3.56 | 1.44 | 20.03 |
| **Wall-clock time (minutes per agent-stage)** | | | | |
| S1 | 60 | 53 | 21 | 119 |
| S2 | 31 | 27 | 6 | 98 |
| S3 | 31 | 25 | 6 | 110 |
| **Number of turns per agent-stage** | | | | |
| S1 | 82 | 66 | 37 | 387 |
| S2 | 54 | 44 | 26 | 388 |
| S3 | 58 | 51 | 30 | 278 |
| **Totals** | | | | |
| Total API cost | $1,558 (S1: $634, S2: $374, S3: $550) | | | |
| Total wall time | ~122 min/agent × 150 agents ÷ 12 parallel = ~25 hours | | | |

### A.2 System Setup and Pipeline

**Infrastructure.** All experiments run on a shared HPC cluster managed by SLURM. Each agent is submitted as an array task, with up to 12 agents running in parallel on a single compute node (40 GB RAM, 6 CPUs per agent). No GPU is used; all computation is CPU-based.

**Container isolation.** Each agent runs inside a Singularity container containing Python 3.12, the Claude Code CLI, and standard scientific Python packages. The container enforces filesystem isolation: each agent has a private read-write workspace, read-only access to the shared TAQ data directory, and no access to other agents' workspaces.

**Three-stage pipeline:**
1. **Stage 1:** Each agent receives an environment specification, research instructions, and read-only access to the TAQ data. It independently produces a structured results file, a research report, analysis code, and figures.
2. **Peer evaluation:** Two AI evaluators (one Sonnet, one Opus) read each agent's Stage 1 report and produce per-hypothesis ratings (0–10) and written feedback.
3. **Stage 2:** Each agent receives its two anonymized peer evaluations and revises its analysis.
4. **Top paper selection:** The five agents with the highest average Stage 2 peer evaluation scores are selected. Their anonymized reports and results are distributed to all agents.
5. **Stage 3:** Each agent receives the five top papers and may revise its analysis one final time.

### A.3 Agent Instructions

#### A.3.1 Assignment

You are expected to write a research report (2,000–4,000 words). For each of the six hypotheses listed below, you should:

1. Propose a statistical measure, briefly motivate it, and present the formula to calculate it.
2. For this measure, estimate the average per-year change in percentage points, based on the full sample. Test it against the null of no change.
3. Report this estimate along with its standard error and the direction of the effect.
4. Briefly discuss your result.

All results are in percentage points per year (e.g., a 1.234% annual decline is reported as −1.234, not −0.01234).

#### A.3.2 Hypotheses

**H1: Market Efficiency.** Assuming that informationally-efficient prices follow a random walk, did market efficiency change over time?
*Null hypothesis 1: Market efficiency has not changed over the sample period (2015–2024).*

**H2: Quoted Bid-Ask Spread.** The quoted bid-ask spread is the difference between the best ask and the best bid price. It is a standard measure of trading cost. Did the quoted bid-ask spread change over time?
*Null hypothesis 2: The quoted bid-ask spread has not changed over the sample period (2015–2024).*

**H3: Realized Bid-Ask Spread.** The realized spread could be thought of as the gross-profit component of the spread as earned by the liquidity provider. It compares the trade price to the midpoint some time after the trade. Did the realized bid-ask spread change over time?
*Null hypothesis 3: The realized bid-ask spread has not changed over the sample period (2015–2024).*

**H4: Trading Volume.** Did daily trading volume change over time?
*Null hypothesis 4: Daily trading volume has not changed over the sample period (2015–2024).*

**H5: Intraday Volatility.** Intraday price volatility captures the magnitude of price fluctuations within a trading day. Did intraday volatility change over time?
*Null hypothesis 5: Intraday volatility has not changed over the sample period (2015–2024).*

**H6: Price Impact of Trades.** Price impact measures how much prices move in response to trading activity. It captures the information content of trades and the depth of the market. Did the price impact of trades change over time?
*Null hypothesis 6: The price impact of trades has not changed over the sample period (2015–2024).*

---

## Appendix B: Does AI Peer Evaluation Quality Predict NSE?

Menkveld et al. (2024) find that higher peer evaluation (PE) ratings are associated with lower NSE: a one-standard-deviation increase in PE rating reduces the IQR by 33%. We test whether a similar relationship holds for AI agents.

**Table 11: PE rating vs. NSE: Spearman correlation and IQR by rating tercile (Stage 1)**

| Hyp | Spearman r | p-value | Low-rated IQR | Mid-rated IQR | High-rated IQR |
|-----|------------|---------|---------------|---------------|----------------|
| H1 | −0.040 | 0.628 | 2.45 | 2.31 | 1.09 |
| H2 | +0.125 | 0.127 | 0.06 | 0.53 | 0.38 |
| H3 | −0.189 | 0.021** | 5.83 | 3.81 | 3.18 |
| H4 | −0.325 | <0.001*** | 10.60 | 10.70 | 0.82 |
| H5 | −0.099 | 0.229 | 0.54 | 0.54 | 0.48 |
| H6 | −0.601 | <0.001*** | 5.77 | 11.88 | 2.44 |

*Notes: Spearman r is the rank correlation between per-hypothesis PE rating and |effect size − median|. Negative r means higher-rated agents are closer to the median. **, *** denote p < 0.05, p < 0.01.*

The relationship between PE quality and NSE is significant only for hypotheses with measure-choice ambiguity: H4 (r = −0.325, p < 0.001) and H6 (r = −0.601, p < 0.001). For well-specified hypotheses (H2, H5), PE ratings do not predict deviation because there is little deviation to predict. This contrasts with Menkveld et al. (2024), where PE quality predicts NSE across all six hypotheses.