# "Nonstandard Errors in AI Agents" - Summary

**Paper link:** [arxiv.org/abs/2603.16744]

---

## Authors & Affiliation
- **Ruijiang Gao & Steven Chong Xiao** — University of Texas at Dallas (Naveen Jindal School of Management)

---

## Experiment Context
- Deployed **150 autonomous Claude Code agents** (100 Sonnet 4.6 + 50 Opus 4.6) to test **6 market quality hypotheses** on NYSE TAQ data for SPY (2015–2024)
- Replicates the **Menkveld et al. (2024)** crowdsourced research design, replacing 164 human teams with AI agents
- **Three-stage protocol**: independent analysis → AI peer review → exposure to top 5 papers
- Total cost: **$1,558** (~$3/agent) vs. estimated **$2.7M** for human teams

---

## Key Findings
- **AI agents exhibit substantial nonstandard errors (NSE)** — same data/question → widely varying results (positive to negative, significant to insignificant)
- **Variation is structured, not random**: concentrated in **measure-choice forks** (e.g., autocorrelation vs. variance ratio; dollar vs. share volume)
- Different **model families have distinct "empirical styles"**: Sonnet prefers autocorrelation (87%), Opus universally chooses variance ratio (100%)
- All 150 agents chose **linear regression**; no agent used relative changes or first differences (common human choices)
- **AI peer review had NO effect** on reducing dispersion
- **Exemplar exposure dramatically reduced IQR by 80–99%**, but convergence = **imitation, not understanding**
- Exemplars can also **increase** dispersion by introducing new methods agents adopt inconsistently

---

## Conclusions
- **A single AI estimate should NOT be trusted** — the "which measure" fork alone can flip conclusions
- **Multiverse analysis** (running multiple measure/specification variants) should be standard practice
- AI agents encode **stable methodological biases** that vary by model family
- Critical implications for **automated policy evaluation** and AI-generated research reliability
