# Trust Me, I'm an Agent
### A Security Measurement of Permission and Privilege Exposure in Open-Source LLM Agents

> **Status — Research preview, work-in-progress.**
> This repository accompanies an ongoing security-measurement study.
> Pilot results and preliminary findings are included for transparency; final results pending manual verification.

---

## 1. Overview

Open-source LLM-agent repositories increasingly request broad authority from users — API keys, filesystem access, network egress, local servers, shell execution, browser automation, database access, and sometimes root-level operating-system operations. Yet very little is known about the **baseline permission surface** these agents demand from users *before any attack happens*.

This project measures that surface. For a corpus of 1,000 live, unique open-source LLM-agent repositories, we compare three layers of permission evidence:

1. **Declared permissions** — what the README, configuration files, and setup scripts say the agent needs.
2. **Static permissions** — what the source code can actually do, derived from grep / AST analysis.
3. **Runtime permissions** — what the agent actually does when executed inside a sandbox.

The most important finding category is **Undeclared + Used**: behavior reachable at runtime that the documentation never mentions. This is where the security and privacy risk lives, and existing work does not measure it at corpus scale.

---

## 2. Research Questions

| ID | Question |
| --- | --- |
| **RQ1** | What permissions and privileges do open-source LLM agents require in practice during setup and runtime? |
| **RQ2** | How can we detect anomalous, excessive, or undocumented permissions in open-source LLM agents? |
| **RQ3** | How can we quantify and mitigate the security risks of unintended or unauthorized permission access in LLM agents? |

---

## 3. Methodology — Three-Layer Triangulation

```
┌────────────────────┐    ┌────────────────────┐    ┌────────────────────┐
│  Layer 1: Declared │    │   Layer 2: Static  │    │  Layer 3: Runtime  │
│  README, .env.exa- │    │  Source code grep  │    │  Sandboxed exec    │
│  mple, Dockerfile, │    │  + AST analysis    │    │  with dummy keys,  │
│  config.yml, docs  │    │  for permission    │    │  monitored network │
│                    │    │  patterns          │    │  and filesystem    │
└─────────┬──────────┘    └─────────┬──────────┘    └─────────┬──────────┘
          │                         │                         │
          └─────────────────────────┴─────────────────────────┘
                                    │
                                    ▼
                       Triangulation + Anomaly Detection
                                    │
                                    ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │  Permission classification:                                       │
   │  Declared+Used  |  Declared+Not Used  |  Undeclared+Used         │
   │  Static Only    |  High-Risk Used     |  Runtime Blocker         │
   │  Declared+Not Present (docs claim, repo missing artefact)         │
   └──────────────────────────────────────────────────────────────────┘
```

The most consequential class is **Undeclared + Used** — behavior reachable at runtime that the README never mentions. This is the gap our framework targets.

---

## 4. Permission Taxonomy

The audit framework classifies findings into 15 permission categories:

| Category | Example evidence |
| --- | --- |
| Secrets / Credentials | API keys (OpenAI, Anthropic, Polygon), tokens, on-disk credential files |
| Filesystem Read | `open()`, `FileReader`, path traversal, secrets-file reads |
| Filesystem Write | logs, generated code, credential duplication, cache files |
| Network Access | outbound HTTP/TCP to non-localhost hosts, API base URLs |
| Local Server Exposure | FastAPI, Flask, Streamlit, Gradio, `0.0.0.0` bindings, open CORS |
| Shell / Process Execution | `subprocess`, `os.system`, `exec`, `eval`, `ProcessBuilder`, `sudo` |
| Browser Automation | Selenium, Playwright, `browser-use`, WebSurferAgent |
| Database Access | JDBC, SQLAlchemy, MongoDB, Redis, Chroma, Pinecone |
| Cloud Access | AWS, GCP, Azure SDKs, cloud functions |
| Communication Access | email, Slack, Discord, Twilio |
| Device / Browser Permissions | microphone, camera, geolocation, notifications |
| Blockchain / Wallet | web3, eth_account, private keys, RPC URLs |
| Docker / System Runtime | Dockerfile, compose, `chown`, sudoers, host volumes |
| Financial / Market Data API | Polygon, Yahoo Finance, market data SDKs |
| Telemetry / Logging / Monitoring | Sentry, PostHog, LangSmith, DataDog, custom telemetry endpoints |

---

## 5. Repository Contents

| Path | Purpose |
| --- | --- |
| `repos_1000_live_unique.json` | Primary corpus — 1,000 live, unique open-source LLM-agent repositories with metadata. |
| `repo_health_check.json` / `.csv` | HTTP-status snapshot of the original V1+V2 inventory (607 unique URLs); records 200/404/redirect outcomes. |
| `pilots/` | Per-repo permission-audit reports (Markdown + structured JSON). One subfolder per audited repo. *Pilot audits are currently AI-assisted and pending manual verification.* |
| `taxonomy/` | Machine-readable permission taxonomy and anomaly rules. |
| `framework/` | Audit scripts, JSON schemas, sandbox templates. *(In development.)* |
| `docs/` | Methodology notes, ethics / responsible-disclosure protocol, related-work summary. |
| `README.md` | This document. |

---

## 6. Corpus — 1,000 Live LLM-Agent Repositories

The primary corpus is `repos_1000_live_unique.json`.

**Composition.** 1,000 unique repositories, all HTTP-verified live on the snapshot date.

| Source | Count |
| ---: | ---: |
| V1 + V2 curated inventory (HTTP-verified live) | 563 |
| GitHub Search expansion (topic + keyword queries) | 437 |
| **Total** | **1,000** |

**Filters applied:** not archived, not a fork, ≥ 2 stars, reachable on the snapshot date.

**Per-record fields.** `owner_repo`, `url`, `description`, `language`, `stars`, `pushed_at`, `created_at`, `archived`, `license`, `source_query`, `from_github_search`, `in_v1`, `in_v2`, `http_status_on_check`, `redirected_to`.

**Provenance of the V1 + V2 segment.** Multi-agent research across GitHub, Hugging Face, GitLab, Kaggle, company OSS portals, and academic repositories. 607 unique URLs collected initially. After HTTP verification: **44 returned HTTP 404 and were excluded** (some were AI-hallucinated repository names); 21 returned 200 with a redirect to a renamed owner; the remaining **563 are confirmed live**.

**Provenance of the GitHub-Search segment.** 17 GitHub topic queries (`topic:llm-agent`, `topic:ai-agent`, `topic:autogen`, `topic:langgraph`, `topic:crewai`, `topic:agentic`, `topic:multi-agent`, `topic:browser-use`, `topic:mcp-server`, etc.) plus keyword queries (e.g., `"llm agent" language:python stars:>30`). Ranked by most-recently-pushed first. Top 437 selected.

### Caveats

- *"Live"* means the GitHub page responded HTTP 200 on the snapshot date. It does **not** mean the repository builds, runs, has executable agent code, or is non-trivial. Runtime-pilot filtering belongs to a later stage of the study.
- The V1/V2 segment lacks the rich metadata (stars, language, last-push timestamp) carried by the GitHub-Search segment, because the V1/V2 health check used `curl -I` rather than the GitHub API. A metadata-enrichment pass is planned.

---

## 7. Preliminary Pilot Results

> **Honesty note.** Pilot audits below were produced with substantial AI assistance for first-pass static analysis. Findings are anchored in real public repositories at named commit hashes, and every claim cites a file path and line number. However, every line-number citation will be **manually re-verified** before being used as a final result. Treat this section as a preliminary, workflow-based draft, not as final verified evidence.

Four open-source agent repositories have been audited end-to-end as the initial pilot.

| Repository | Risk classification | Representative findings |
| --- | --- | --- |
| **ag2ai/ag2** | High | `exec(code)` in `captainagent/tool_retriever.py:212,282`; Agent-to-Agent network server; Jupyter kernel gateway spawned as a subprocess; SQLite-based conversation logging; browser automation via Selenium WebDriver, `WebSurferAgent`, and `browser-use`; nine-plus API key providers — several undocumented as security-relevant. |
| **virattt/financial-agent** | Medium | FastAPI server with `allow_origins=['*']` and `allow_credentials=True` (High, Undeclared + Used); `0.0.0.0:8000` bind; LangSmith telemetry via transitive `langchain-core`. None disclosed in the README. |
| **wzf2000/MACRec** | Critical | `eval(init_args.main + 'Task')()` in `main.py:21` (arbitrary code execution from a CLI argument); `subprocess.call('mkdir ' + dir, shell=True)` in `amazon.py:30,35` (shell command injection); `exec(...)` in `rank_metric.py:26`. None documented. |
| **wrxck/AgentCraft** | High (Critical-on-trigger) | `sudo -n -u claude … claude --dangerously-skip-permissions` per LLM call in `ClaudeClient.java:41-50,119-138`; `chown -R claude:claude` in `AgentManager.java:329-333`; undocumented `/minecraft/fleet-secrets.env` read; per-agent duplication of long-lived Claude credentials; silent outbound calls to Mojang APIs; README claims a three-service Docker Compose stack that is not present in the repository. |

**Early pattern.** Every one of the four pilots exposes undocumented system-level capabilities — shell execution, `eval` / `exec` use, open CORS policies, public-interface server bindings, third-party telemetry, or root-level operating-system operations. Two of four reach the **Critical** severity tier.

**Independent corroboration of the problem class.** Recent CVEs on this exact surface confirm that the issues are not theoretical:

- LangChain — CVE-2025-68664 *"LangGrinch"* (CVSS 9.3), serialization injection → secret extraction.
- Langflow — CVE-2025-3248, unauthenticated decorator-payload remote code execution.
- mcp-remote — CVE-2025-6514 (CVSS 9.6), arbitrary OS command execution via untrusted MCP server.
- Microsoft Semantic Kernel — CVE-2026-25592 and CVE-2026-26030 (CVSS 9.9), prompt injection → host-level RCE.

---

## 8. Related Work

Closely related accepted work at the top-four security venues:

| Venue | Paper | What it does | What it does *not* do |
| --- | --- | --- | --- |
| USENIX Security 2025 | *Make Agent Defeat Agent* (AgentFuzz) | Taint-style vulnerability detection in LLM agents. | Repository-level permission measurement. |
| arXiv 2025 | *Progent: Programmable Privilege Control for LLM Agents* | Runtime privilege control. | Measurement of declared vs runtime gaps. |
| IEEE S&P 2026 | *Investigating the Impact of Dark Patterns on LLM-Based Web Agents* | Agent decision-making under adversarial UI. | Permission-surface measurement. |
| IEEE S&P 2026 | *When AI Meets the Web: Prompt Injection in Third-Party AI Chatbot Plugins* | Plugin-side prompt injection. | Whole-repository permission audit. |
| NDSS 2026 LAST-X workshop | *Towards Automating Data Access Permissions in AI Agents* | Permission prediction and control. | Repository-level measurement. |

Adjacent work outside the top-four venues — *You Told Me to Do It* (instructional-text leakage), *Security in the Wild* (AIware 2025), *LLM-Enabled OSS in the Wild* (FSE 2026), *Agent Skills in the Wild*, *Agent Audit* — either analyses attacks and advisories after the fact, or operates at the single-skill layer rather than at whole-repository scale.

To the best of our knowledge, **no prior work performs declared-vs-static-vs-runtime triangulation across a corpus of open-source LLM-agent repositories**.

---

## 9. Roadmap

| Phase | Deliverable |
| --- | --- |
| **Pilot (done)** | 4-repo AI-assisted audit, framework validation on AgentCraft. |
| **Manual verification (in progress)** | Re-verify every file/line citation in the pilot audits by hand; freeze the verified results. |
| **Corpus enrichment** | GitHub-API metadata pass on the V1/V2 segment (stars, language, last-push, archived flag). |
| **Scale-up audit** | Apply the framework across a larger sample drawn from the 1,000-repo corpus, including minimal-permission baseline repositories. |
| **Risk-score model** | Per-repository risk score; validated by CVE backtest against LangChain CVE-2025-68664, Langflow CVE-2025-3248, mcp-remote CVE-2025-6514, and Semantic Kernel CVE-2026-25592 / -26030. |
| **Anomaly framework** | Rule-based + statistical-outlier + functionality-permission-matching detection framework. |
| **Mitigation artefacts** | Permission manifest specification, permission scanner, sandbox-policy templates. |
| **Manuscript** | Measurement study on permission transparency and over-privilege in open-source LLM agents. |

---

## 10. Ethics and Responsible Disclosure

- All audited repositories are publicly available on GitHub.
- All execution is performed inside isolated sandboxes with dummy credentials. No real API keys, no real personal files, no host-home-directory mounts.
- Findings of severity **High** or **Critical** in still-maintained repositories are reported to the maintainers via GitHub Security Advisories with a 90-day embargo before public disclosure in any publication.
- The corpus contains links to public repositories only; no private code, private credentials, or personal data is collected, redistributed, or analysed.

---

## 11. Citation

If you use this corpus or the audit framework, please cite as:

```bibtex
@misc{trustmeagent2026,
  title  = {Trust Me, I'm an Agent: A Security Measurement of Permission
            and Privilege Exposure in Open-Source LLM Agents},
  note   = {Corpus snapshot v1.0, 2026-06-13},
  year   = {2026},
  url    = {https://github.com/mrahm65/Trust-Me-I-m-an-Agent-Measuring-the-Security-Exposure-of-Open-Source-LLM-Agents}
}
```

---

## 12. License

License **TBD**. The corpus catalogues *links* to public repositories along with publicly available metadata. Each linked repository is governed by its own license; this project does not redistribute their source code.

---

## 13. Acknowledgments and Contact

This work is conducted under the supervision of the project lead. AI tools have been used throughout the workflow for first-pass static analysis, drafting, and corpus collection; the research direction, framing, permission taxonomy, repository selection, interpretation of findings, and final verification are the author's own.

**Maintainer:** Saidur Rahman (`saidur@eub.edu.bd`)
**Repository:** https://github.com/mrahm65/Trust-Me-I-m-an-Agent-Measuring-the-Security-Exposure-of-Open-Source-LLM-Agents
