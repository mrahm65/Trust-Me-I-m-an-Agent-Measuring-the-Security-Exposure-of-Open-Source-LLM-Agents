# Trust Me, I'm an Agent — Measuring the Security Exposure of Open-Source LLM Agents

Companion data for the security measurement study. Contains the curated, deduplicated, HTTP-verified corpus of open-source LLM-agent repositories used to bound the study population.

## Contents

- **`repos_1000_live_unique.json`** — Primary corpus of **1,000 live, unique LLM-agent repositories**.
  - **563** repos from the initial V1 + V2 inventories, HTTP-verified live on 2026-06-13.
  - **437** additional repos sourced from the GitHub Search API across 17 topic queries (`topic:llm-agent`, `topic:ai-agent`, `topic:autogen`, `topic:langgraph`, `topic:crewai`, `topic:agentic`, `topic:multi-agent`, `topic:browser-use`, `topic:mcp-server`, etc.) and keyword queries.
  - Per-record fields: `owner_repo`, `url`, `description`, `language`, `stars`, `pushed_at`, `created_at`, `archived`, `license`, `source_query`, `from_github_search`, `in_v1`, `in_v2`, `http_status_on_check`, `redirected_to`.
  - Selection criteria for new repos: not archived, not a fork, ≥2 stars, ranked by most-recently-pushed first.

- **`repo_health_check.json`** / **`repo_health_check.csv`** — Per-URL HTTP health snapshot of the original V1 + V2 inventory (607 unique URLs). Records HTTP status, redirect targets, and source-list membership. Used to derive the 563-repo live subset.

## Methodology

The corpus combines:

1. **V1 + V2 inventories** — multi-agent research across GitHub, Hugging Face, GitLab, Kaggle, company OSS portals, and academic repositories. Scope restricted to individually coded, runnable agents (not use cases, papers, or benchmarks). 607 unique URLs collected; **44 returned HTTP 404 and were excluded**; 21 returned 200 with a redirect to a renamed owner/repo; the remaining 563 are confirmed live.
2. **GitHub Search expansion** — 17 GitHub topic queries plus keyword queries to broaden language and framework coverage. Filters: not archived, not a fork, ≥2 stars. Sorted by most-recently-pushed, top 437 selected to bring the corpus to 1,000.

## Caveats

- "Live" means the GitHub page responded HTTP 200 on 2026-06-13. It does **not** mean the repository builds, runs, has executable agent code, or is non-trivial. Runtime-pilot filtering belongs to a later stage of the study.
- The V1/V2 segment lacks the rich metadata (stars, language, last-push timestamp) carried by the GitHub-Search segment, because the V1/V2 health check used `curl -I` rather than the GitHub API.

## Citation

If you use this corpus, please cite as:

> Trust Me, I'm an Agent: A Security Measurement of Permission and Privilege Exposure in Open-Source LLM Agents. Corpus snapshot v1.0, 2026-06-13.
