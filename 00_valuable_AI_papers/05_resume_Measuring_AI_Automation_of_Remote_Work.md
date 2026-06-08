# "Remote Labor Index: Measuring AI Automation of Remote Work" - Summary

**Paper link:** [arxiv.org/abs/2510.26787](https://arxiv.org/abs/2510.26787)

---

## Authors & Affiliation
- **Mantas Mazeika, Alice Gatti, Cristina Menghini, et al.** — Center for AI Safety (CAIS)
- **Udari Madhushani Sehwag, Shivam Singhal, et al.** — Scale AI
- **Dan Hendrycks** (Senior Author) — CAIS

---

## Context & Experiment
- Introduces **Remote Labor Index (RLI)**: first standardized benchmark measuring AI's capability to automate real-world remote work
- **240 projects** across **23 categories** from Upwork taxonomy (game dev, architecture, CAD, video, graphic design, audio, etc.)
- Projects sourced from **real freelance platforms** with actual economic transactions
- Each project includes: project brief, input files, and **human gold-standard deliverable**
- Evaluated **6 frontier AI agents**: ChatGPT agent, GPT-5, Claude Sonnet 4.5, Grok 4, Gemini 2.5 Pro, Manus
- Rigorous **manual evaluation** by human annotators (94.4% inter-annotator agreement)

---

## Key Findings

### Finding 1: AI Agents Perform Near the Floor
- **Best-performing agent (Manus): 2.5% automation rate**
- All agents automate <3% of tasks
- Stark gap between progress on knowledge benchmarks and real economically valuable work

### Finding 2: Most Remote Work Remains Far Beyond AI Capabilities
| Agent | Automation Rate |
|-------|-----------------|
| Manus | 2.5% |
| Grok 4 | 2.1% |
| Sonnet 4.5 | 2.1% |
| GPT-5 | 1.7% |
| ChatGPT agent | 1.3% |
| Gemini 2.5 Pro | 0.8% |

### Finding 3: Common Failure Modes
- **Poor quality (45.6%)**: Work doesn't meet professional standards
- **Incomplete deliverables (35.7%)**: Missing components, truncated videos
- **Corrupted files (17.6%)**: Empty or unusable formats
- **Inconsistencies (14.8%)**: Visual appearance changes across renderings

### Finding 4: Where AI Succeeds
- Audio editing/mixing/production tasks
- Image generation (ads, logos)
- Report writing
- Interactive data visualization code
- Simple web visualizations

### Finding 5: Elo Scores Show Steady Progress
- While absolute performance is low, **relative improvement is measurable**
- Newer frontier models achieve higher Elo scores than older ones
- Human baseline Elo fixed at 1,000; all AI agents significantly below

### Finding 6: RLI Reflects Real Labor Market Complexity
- Average completion time matches real Upwork distribution
- Previous benchmarks focus on software/research/writing (well-covered in pretraining)
- RLI includes design, operations, marketing, admin, audio-video production

---

## Conclusions & Implications

- **AI agents are far from capable of autonomously handling diverse remote labor demands**
- Performance on knowledge/reasoning benchmarks does NOT translate to economically valuable work completion
- RLI provides **empirical foundation for monitoring AI automation trajectory**
- Total value of completing all RLI projects: **$143,991** — AI agents currently capture almost none
- Unlike task-specific automation (calculators), AI is being developed to automate **general human intelligence**
- Stakeholders (policymakers, researchers, public) need empirical grounding for navigating AI-driven labor automation
- The gap between AI benchmark performance and real-world work capability is substantial
