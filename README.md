# Trust Me, I'm an Agent — Measuring the Security Exposure of Open-Source LLM Agents

Companion data for the security measurement study. Contains two snapshots of the curated agent inventory used to bound the study population.

## Contents

- **V1/** — Initial inventory (June 11, 2026). 236 repository records totaling 1,000+ individually coded agents across 8 sections. Includes:
  - `1000-ai-agents-list.md` / `.pdf` — human-readable master list
  - `1000-ai-agents-list.json` — structured records (id, section, repo URL, agent count, description)
  - Per-track research reports (collections, galleries, multi-agent systems, domain-specific, additional sources)
  - `plan.md` — research methodology
- **V2/** — Expanded inventory (June 12, 2026). Adds hackathon, international community, and new-domain sources. Includes:
  - `1000-ai-agents-list-v2.md` / `.pdf` — updated master list
  - `unique_ai_agent_repos.json` / `.md` — deduplicated repository set
  - Additional research tracks: hackathon agents, international community, agent implementations, new domain agents
  - `plan-v2.md` — updated methodology

## Methodology

Multi-agent parallel research across GitHub, Hugging Face, GitLab, Kaggle, company open-source portals, and academic repositories. Scope is restricted to individually coded, runnable agents (not use cases, papers, or benchmarks).
