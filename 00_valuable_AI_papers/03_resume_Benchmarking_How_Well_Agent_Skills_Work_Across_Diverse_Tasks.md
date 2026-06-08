# "SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks" - Summary

**Paper link:** [arxiv.org/abs/2602.12670](https://arxiv.org/abs/2602.12670)

---

## Authors & Affiliation
- **Xiangyi Li, Yimin Liu, Wenbo Chen, Shenghan Zheng, et al.** — BenchFlow, Ohio State University, Amazon, Dartmouth College, Stanford University, UC Davis, CMU, UC Berkeley, Princeton, and others (multi-institutional collaboration)

---

## Context & Experiment
- **First benchmark treating Agent Skills as first-class evaluation artifacts**
- Skills = structured packages of procedural knowledge (instructions, code templates, resources) that augment LLM agents at inference time
- **84 tasks across 11 domains**: Software Engineering, Healthcare, Manufacturing, Finance, Cybersecurity, Robotics, etc.
- Evaluated **7 agent-model configurations** across **7,308 trajectories**
- Three conditions tested: **No Skills**, **Curated Skills**, and **Self-Generated Skills**
- Agent harnesses: Claude Code, Gemini CLI, Codex CLI
- Models: GPT-5.2, Claude Opus 4.5/4.6, Claude Sonnet 4.5, Claude Haiku 4.5, Gemini 3 Pro/Flash

---

## Key Findings

### Finding 1: Curated Skills Provide Substantial but Variable Benefit
- **+16.2 percentage points** average improvement across all configurations
- High variance by configuration: range +13.6pp to +23.3pp

### Finding 2: Best Performance
- **Gemini CLI + Gemini 3 Flash** achieved maximum pass rate (48.7%)
- Claude Code + Opus 4.5 showed highest improvement (+23.3pp)

### Finding 3: Self-Generated Skills Provide Negligible/Negative Benefit
- **–1.3pp average** compared to no-Skills baseline
- Models cannot reliably author the procedural knowledge they benefit from consuming

### Finding 4: Skills Benefit Varies Widely Across Domains
- **Healthcare: +51.9pp** (largest gain)
- **Manufacturing: +41.9pp**
- **Software Engineering: +4.5pp** (smallest gain — models already have strong priors)
- 16 of 84 tasks showed **negative Skills deltas**

### Finding 5: Optimal Skills Quantity is 2–3
- 2–3 Skills: +18.6pp improvement
- 4+ Skills: only +5.9pp (diminishing returns, cognitive overhead)

### Finding 6: Focused Skills Outperform Comprehensive Documentation
- Detailed/Compact Skills: +17-19pp
- Comprehensive Skills: **–2.9pp** (hurts performance)

### Finding 7: Smaller Model + Skills Can Match Larger Model Without
- Claude Haiku 4.5 with Skills (27.7%) exceeded Opus 4.5 without Skills (22.0%)

---

## Conclusions
- **Skills efficacy is context-dependent**, not universal — motivates paired evaluation as standard practice
- **Less is more**: focused, stepwise guidance with working examples beats exhaustive documentation
- **Human-curated domain expertise is essential** — models cannot self-generate effective procedural knowledge
- Skills are most helpful for **domains with specialized workflows underrepresented in pretraining**
- **Skills can partially compensate for model scale limitations** on procedural tasks
- Harness implementation significantly affects Skills utilization — some harnesses acknowledge but ignore Skills
