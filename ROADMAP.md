# Research Roadmap — Trust Me, I'm an Agent
### A Security Measurement of Permission and Privilege Exposure in Open-Source LLM Agents

> **Document purpose.** This roadmap is the single source of truth for the project plan. It merges (a) the conceptual 16-step methodology that defines the paper's storyline with (b) an 8-phase execution plan that defines what gets built when. Read the steps for *what* is being done; read the phase tags for *when*.

---

## 1. Project Title and Research Questions

**Title.** Trust Me, I'm an Agent: A Security Measurement of Permission and Privilege Exposure in Open-Source LLM Agents.

| ID | Research Question |
| --- | --- |
| **RQ1** | What permissions and privileges do open-source LLM agents require in practice during setup and runtime? |
| **RQ2** | How can we detect anomalous, excessive, or undocumented permissions in open-source LLM agents? |
| **RQ3** | How can we quantify and mitigate the security risks of unintended or unauthorized permission access in LLM agents? |

**One-line pitch.** Before any attack happens, what authority do open-source LLM agents ask users to grant — and is that authority documented, necessary, and consistent with least-privilege principles?

---

## 2. Phase Index

| Phase | Title | Status | Target window |
| --- | --- | --- | --- |
| **P0** | Pilot + foundation | ✅ Complete | — |
| **P1** | Manual verification of pilot findings | 🔄 In progress | weeks 1–2 |
| **P2** | Audit framework tool-building | Pending | weeks 3–8 |
| **P3** | Corpus enrichment and sampling | Pending | weeks 9–10 |
| **P4** | Scale-up audit | Pending | weeks 11–18 |
| **P5** | Risk-score model + CVE backtest | Pending | weeks 19–22 |
| **P6** | Anomaly-detection framework | Pending | weeks 23–25 |
| **P7** | Mitigation artefacts | Pending | weeks 26–28 |
| **P8** | Manuscript drafting and submission | Pending | weeks 29–36 |

---

## 3. Sixteen-Step Methodology (Paper Backbone)

Each step is annotated with the execution **phase** that delivers it, its **dependencies**, the concrete **deliverable**, and the current **status**.

---

### Step 1 — Define the scope

**Phase: P0 (done).** No dependencies.

Include projects that (a) use an LLM as part of decision-making, (b) use tools, APIs, files, browsers, shell, databases, or local services, (c) support autonomous or semi-autonomous actions, and (d) ship runnable open-source code on GitHub.

Exclude projects that are only simple chatbots without tool use, pure model-training or fine-tuning repositories, prompt collections, and closed-source applications.

**Deliverable.** Scope statement in README §1.
**Status.** ✅ Complete.

---

### Step 2 — Position the gap

**Phase: P0 (done).** Depends on Step 1.

> Prior work studies vulnerabilities, prompt-injection attacks, and advisory-level security risks in LLM systems. Little is known about the baseline permission and privilege surface that open-source LLM agents require before any attack happens. Our contribution is to measure declared, statically inferred, and runtime-observed permissions in open-source LLM agents at corpus scale.

Closest prior work and how it differs:

| Venue | Paper | Difference from this study |
| --- | --- | --- |
| USENIX Security 2025 | *Make Agent Defeat Agent* (AgentFuzz) | Taint-style vulnerability detection, not corpus-level permission measurement. |
| arXiv 2025 | *Progent: Programmable Privilege Control for LLM Agents* | Runtime privilege control, not measurement of declared vs runtime gaps. |
| IEEE S&P 2026 | *Investigating the Impact of Dark Patterns on LLM-Based Web Agents* | Agent behavior under adversarial UI, not permission surfaces. |
| IEEE S&P 2026 | *When AI Meets the Web: Prompt Injection in Third-Party AI Chatbot Plugins* | Plugin-side prompt injection, not whole-repository audits. |
| NDSS 2026 (LAST-X) | *Towards Automating Data Access Permissions in AI Agents* | Permission prediction and control, not repository-level measurement. |

**Deliverable.** Related-work table in README §8 and in paper §3.
**Status.** ✅ Complete.

---

### Step 3 — Build the repository dataset

**Phase: P0 (done) and P3 (enrichment).** Depends on Step 1.

Two corpus snapshots, both HTTP-verified live and fully disjoint:

| Snapshot | File | Size |
| --- | --- | ---: |
| v1 | `repos_1000_live_unique.json` | 1,000 |
| v2 | `repos_1000_set2_live_unique.json` | 1,000 |
| **Total** | | **2,000** |

Filters applied: not archived, not a fork, at least two stars, reachable on snapshot date.

Per-record fields captured: `owner_repo`, `url`, `description`, `language`, `stars`, `pushed_at`, `created_at`, `archived`, `license`, `source_query`, `from_github_search`, `http_status_on_check`, `redirected_to`.

**P3 enrichment will add.** Cluster labels per agent type (coding agent, RAG, multi-agent, browser agent, finance agent, etc.), a runnability heuristic (0–3 score based on presence of Dockerfile, dependency files, entry point), and a stratified sample selection.

**Deliverable.** Final `corpus_sampled.json` with cluster labels and chosen sample.
**Status.** ✅ Raw corpus complete; sampling pending P3.

---

### Step 4 — Define the permission taxonomy

**Phase: P0 (done).** Depends on Step 1.

Fifteen permission categories, each with explicit evidence criteria:

| Category | Example evidence |
| --- | --- |
| Secrets / Credentials | API keys, tokens, on-disk credential files |
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

**Deliverable.** `taxonomy/permissions.yaml` with category, evidence patterns, default risk weight.
**Status.** ✅ Defined; YAML serialisation deferred to P2.

---

### Step 5 — Extract declared permissions

**Phase: P1 (manual on pilots), P2 (automated extractor), P4 (scale).** Depends on Steps 3 and 4.

Inspect README, installation guide, `.env.example`, Dockerfile, `config.yaml`, documentation folder, setup scripts, requirements files, and package files. Record per repository:

```json
{
  "repo": "owner/example-agent",
  "commit": "abc1234",
  "declared_api_keys": ["OPENAI_API_KEY"],
  "declared_filesystem": ["workspace/"],
  "declared_network": ["OpenAI", "SerpAPI"],
  "declared_database": [],
  "declared_local_server": "FastAPI port 8000",
  "declared_shell": true,
  "declared_evidence": [
    {"permission": "OPENAI_API_KEY", "source_file": "README.md",
     "line_numbers": "12", "evidence_text": "..."}
  ]
}
```

**Deliverable.** `framework/declared_extractor.py` plus per-repo `declared.json`.
**Status.** P1 manual extraction in progress on AgentCraft; automation pending P2.

---

### Step 6 — Static code analysis

**Phase: P1 (manual on pilots), P2 (automated scanner), P4 (scale).** Depends on Steps 3 and 4.

Search for: environment-variable patterns (`os.getenv`, `process.env`); API client imports; file-access primitives (`open`, `readFile`, `writeFile`); shell/process invocations (`subprocess`, `os.system`, `exec`, `eval`, `ProcessBuilder`); network clients (`requests`, `fetch`, `axios`, `socket`); local server frameworks (Flask, FastAPI, Gradio, Streamlit); browser automation (Selenium, Playwright); database clients; cloud SDKs; wallet/web3 primitives; CORS settings; exposed ports.

```json
{
  "repo": "owner/example-agent",
  "commit": "abc1234",
  "static_secrets": ["OPENAI_API_KEY", "SERPAPI_API_KEY"],
  "static_filesystem_read": true,
  "static_filesystem_write": true,
  "static_shell": true,
  "static_network": ["api.openai.com", "serpapi.com"],
  "static_local_server": ["0.0.0.0:8000"],
  "static_high_risk": ["shell_execution", "open_cors"],
  "static_evidence": [
    {"permission": "shell_execution", "source_file": "src/agent.py",
     "line_numbers": "42-58", "code_snippet": "...", "risk_explanation": "..."}
  ]
}
```

Every claim **must** carry `source_file`, `line_numbers`, and a code snippet so the finding is independently verifiable.

**Deliverable.** `framework/static_scanner.py` plus per-repo `static.json`.
**Status.** P1 manual scan in progress on AgentCraft; automation pending P2.

---

### Step 7 — Sandboxed runtime analysis

**Phase: P2 (sandbox harness), P4 (scale).** Depends on Step 6.

Sandbox configuration:

- Isolated Docker container or VM.
- No real personal files, no real API keys, no host-home-directory mount.
- Dummy secrets only (e.g., `OPENAI_API_KEY=dummy_openai_key`).
- Restricted network with egress logging via `mitmproxy` or iptables.
- File-activity log via `auditd` / `inotify`.
- Port and process-tree capture.

Observed and recorded: required secrets, file reads and writes, contacted network domains, opened ports and bind addresses, CORS posture, subprocess launches, browser-automation initialisation, database connection attempts, wallet or private-key requests, runtime blockers.

```json
{
  "repo": "owner/example-agent",
  "commit": "abc1234",
  "runtime_status": "partial",
  "runtime_required_secrets": ["OPENAI_API_KEY"],
  "runtime_outbound_domains": ["api.openai.com"],
  "runtime_file_writes": ["logs/", "workspace/output.py"],
  "runtime_open_ports": ["8000"],
  "runtime_bind_addresses": ["0.0.0.0:8000"],
  "runtime_cors_behavior": "allow_origins=['*'], allow_credentials=true",
  "runtime_shell_observed": false,
  "runtime_blocker": "missing OPENAI_API_KEY"
}
```

This is the hardest sub-system and the strongest contribution.

**Deliverable.** `framework/runtime_sandbox/` Docker harness plus per-repo `runtime.json`.
**Status.** Pending P2.

---

### Step 8 — Compare declared, static, and runtime permissions

**Phase: P2 (triangulator), P4 (scale).** Depends on Steps 5, 6, 7.

Each permission per repository receives one of seven classification labels:

| Label | Meaning |
| --- | --- |
| Declared + Used | Documented and observed at runtime. |
| Declared + Not Used | Documented but not observed. |
| Undeclared + Used | Not documented but used at runtime. **Primary anomaly signal.** |
| Static Only | Present in code but not triggered at runtime. |
| High-Risk Used | Shell, wallet, cloud, database, or broad file access exercised. |
| Runtime Blocker | Could not run due to missing key, environment, or dependency. |
| Declared + Not Present | Docs claim an artefact (e.g., Docker stack) that does not exist. |

**Deliverable.** `framework/triangulator.py` plus per-repo `triangulation.json`.
**Status.** Pending P2.

---

### Step 9 — Define permission anomaly rules

**Phase: P0 (rules drafted), P6 (codification).** Depends on Step 8.

A permission is anomalous if it is used at runtime but not documented, high-risk but unnecessary for the stated function, broader than required, inherited from a framework but not needed by the application, enabled by default without user warning, exposed through a local service with weak configuration, or contacts external services not mentioned in the documentation.

| Agent type | Expected permission | Possible anomaly |
| --- | --- | --- |
| Chat assistant | LLM API key | Shell execution |
| RAG application | File read, vector DB | Open CORS + public-bind server |
| Coding agent | Shell, file write | Full home-directory access |
| Web agent | Browser / network | Local `.env` file read |
| Crypto agent | Wallet key | Signing enabled by default |

**Deliverable.** `taxonomy/anomaly_rules.yaml` codifying ten anomaly classes derived from the AgentCraft audit.
**Status.** Rules drafted; YAML serialisation pending P6.

---

### Step 10 — Build the anomaly-detection framework

**Phase: P6.** Depends on Steps 8 and 9.

Hybrid detector with three layers:

**Rule-based detection.** Direct checks: if `shell_execution = true` and README does not mention shell, flag; if local server binds to `0.0.0.0` and docs do not warn, flag; if private key required and no security warning present, flag; if file write exists but documentation claims read-only behavior, flag.

**Statistical detection.** Cluster each repository by agent type (Step 3). For each cluster, compute mean and standard deviation of every permission category. Flag any repository more than two standard deviations beyond its cluster mean.

**Functionality-permission matching.** Use an LLM to classify the repository's stated purpose from the README, then compare to its permission set. Flag mismatches: "summarise PDFs" should not require wallet signing; "personal finance assistant" should not require broad filesystem write; "coding agent" may need shell but should document it.

The combined verdict aggregates rule confidence into a final Low / Medium / High / Critical label.

**Deliverable.** `framework/anomaly_detector.py` plus a verdict file per repo.
**Status.** Pending P6.

---

### Step 11 — Create a permission risk score *(with empirical validation)*

**Phase: P5.** Depends on Step 8.

Two-stage construction:

**Stage A — scoring rubric.** Each of six dimensions scored 0–10 with explicit anchor points; equal weights, capped at 100.

| Factor | 0 (low) | 5 (mid) | 10 (high) |
| --- | --- | --- | --- |
| Sensitivity | Public API only | One vendor key | Private key, cloud token |
| Scope | Project folder only | Project + outputs dir | Full filesystem |
| Runtime exposure | Local only | Local + one external API | External network, multiple endpoints |
| Autonomy | User confirms each action | Some auto-actions | Fully autonomous |
| Documentation gap | Fully declared | Partial gap | Undocumented |
| Data sensitivity | Logs only | App data | Personal files, credentials |

**Stage B — empirical validation via CVE backtest.** Check out the *pre-fix* commit of each of the following CVEs, run the audit framework, compute the risk score, and correlate against CVSS severity:

- LangChain — CVE-2025-68664 *"LangGrinch"* (CVSS 9.3)
- Langflow — CVE-2025-3248
- mcp-remote — CVE-2025-6514 (CVSS 9.6)
- LangGraph — CVE-2026-27794
- Microsoft Semantic Kernel — CVE-2026-25592 and CVE-2026-26030 (CVSS 9.9)
- AutoGPT — documented Docker escape via README content

**Success criterion.** Spearman ρ ≥ 0.6 between pre-fix risk score and CVSS severity across the backtest set.

**Fallback.** If ρ is too low, drop the 0–100 score and report a categorical Low / Medium / High / Critical verdict instead.

**Deliverable.** `framework/risk_score.py` plus `validation/cve_backtest.csv`.
**Status.** Pending P5.

---

### Step 12 — Propose mitigation artefacts

**Phase: P7.** Depends on Steps 9, 10, 11.

Three concrete artefacts, none of which need to be a full product.

**Agent permission manifest.** A standardised `agent-permissions.yml` declaring required secrets, filesystem scopes, allowed outbound domains, shell flag, and server bind configuration. Example:

```yaml
agent_permissions:
  secrets: [OPENAI_API_KEY]
  filesystem:
    read:  [./workspace]
    write: [./outputs]
  network:
    outbound: [api.openai.com]
  shell:
    enabled: false
  local_server:
    port: 8000
    bind: 127.0.0.1
```

**Permission scanner.** A `trustme-scan` CLI tool that scans a repository and emits:

```
Security Permission Report
- Declared permissions:     5
- Static inferred:          9
- Runtime observed:         6
- Undocumented runtime:     3
- High-risk permissions:    2
- Risk score:               74/100
```

**Sandbox policy templates.** Docker, Bubblewrap, and Firejail templates that enforce least-privilege defaults: deny shell, restrict filesystem to project folder, whitelist outbound domains, bind local servers to `127.0.0.1`, block private-key access without explicit approval, require user confirmation before sensitive actions.

**Deliverable.** `mitigation/` directory containing the manifest spec, the CLI tool, and the policy templates.
**Status.** Pending P7.

---

### Step 13 — Validation plan *(with concrete numbers)*

**Phase: P4 (during scale audit), P5 (during risk-score work), P8 (during write-up).** Cross-cutting.

| Validation | Target |
| --- | --- |
| Manual hand-validation of a stratified sample | 100 repositories drawn at random across agent-type clusters |
| Two independent annotators | Cohen's κ ≥ 0.7 on permission labels |
| Precision and recall of `static_scanner.py` per category | Reported per category, table in paper §6 |
| Precision and recall of `runtime_sandbox/` evidence vs declared | Reported in paper §7 |
| Case studies of high-risk examples | 3–5 representative repositories described in paper §10 |
| Risk-score Spearman ρ vs CVSS | ≥ 0.6 on the CVE backtest |

**Deliverable.** `validation/` directory with annotator-disagreement logs, per-category precision/recall tables, and the CVE backtest workbook.
**Status.** Pending; design locked.

---

### Step 14 — Expected findings to look for

**Phase: P8 (analysis).** Depends on Steps 8–11.

The paper becomes strong if results include:

- Many agents require API keys but do not clearly explain their scope.
- Some agents open local servers with insecure defaults.
- Some agents statically include shell or file-write permissions that are not documented.
- Some agents contact third-party services not mentioned in the README.
- Framework templates introduce permissions that application developers may not realise they have inherited.
- High-risk permissions such as wallet keys, cloud tokens, or shell execution are not consistently documented.
- Runtime blockers are common, making safe evaluation of the ecosystem difficult.

The key is to find findings beyond *"agents need permissions"* — the paper rests on demonstrating **undocumented, excessive, or unnecessary authority**.

**Status.** Hypothesis form; verification awaits P4 results.

---

### Step 15 — Paper structure

**Phase: P8.**

| § | Section | Source |
| --- | --- | --- |
| 1 | Introduction | Step 2 framing; "before any attack happens" |
| 2 | Motivation example | One verified case study (AgentCraft after P1) |
| 3 | Related work | Step 2 table, expanded |
| 4 | Permission taxonomy | Step 4 |
| 5 | Dataset collection | Step 3 + P3 sampling |
| 6 | Methodology | Steps 5, 6, 7 |
| 7 | RQ1 results | Step 8 outputs from P4 |
| 8 | RQ2 results | Step 10 anomaly framework verdicts |
| 9 | RQ3 results | Step 11 risk-score validation + Step 12 mitigation |
| 10 | Case studies | 3–5 representative repositories |
| 11 | Ethics and responsible disclosure | 90-day embargo, sandbox-only execution |
| 12 | Discussion and limitations | Runtime blockers, sampling bias, sandbox-escape risk |
| 13 | Conclusion | One-line pitch restated |

---

### Step 16 — Timeline (execution-phase mapping)

| Month | Phase | Activities |
| --- | --- | --- |
| 1 | P1 | Manual verification of four pilots (AgentCraft → MACRec → financial-agent → AG2); freeze verified results. |
| 2 | P2 (start) | Build `declared_extractor.py`, `static_scanner.py`; draft JSON schema. |
| 3 | P2 (end) + P3 | Finish sandbox harness; validate framework against P1 verified pilots; enrich corpus, cluster, sample. |
| 4 | P4 (start) | Static + declared pass over the static-only subset (≈500 repos). |
| 5 | P4 (mid) | Runtime pass over the runnable subset (≈150 repos); log Runtime Blockers. |
| 6 | P4 (end) + P5 | Triangulation results; design risk score; run CVE backtest. |
| 7 | P6 + P7 | Anomaly detector; mitigation artefacts. |
| 8 | P8 (start) | Manuscript first draft. |
| 9 | P8 (end) | Manuscript polish; figures and tables; ethics and responsible-disclosure section; submission. |

**Target venues, ordered by realism.**

1. ACSAC 2027 (December 2026 submission window).
2. EuroS&P 2027 (October 2026 submission).
3. USENIX Security 2027 (February 2027 cycle 2).
4. IEEE S&P 2027 (only if Step 11 backtest produces strong ρ and corpus scales to 1,500+ audited repos).

---

## 4. Critical-Path Risks

| Risk | Phase | Mitigation |
| --- | --- | --- |
| P1 verification skipped or rushed | P1 | Single most important phase. Block all later phases on a clean P1 sign-off. |
| Runtime sandbox harder than expected | P2 / P4 | Pre-declare "Runtime Blocker frequency" as a finding; report static-only results for blocked repos. |
| CVE backtest produces weak ρ | P5 | Fall back to categorical verdict instead of 0–100 score. |
| Inter-annotator agreement < 0.7 | P4 / P5 | Refine the rubric with explicit anchor points; re-annotate the disagreed cases. |
| Manuscript scope creep | P8 | Lock the three RQs before writing begins; do not add a fourth RQ mid-draft. |
| Coordinated-disclosure timing | P4 onwards | File GHSA reports as findings emerge; respect the 90-day embargo before public disclosure in the paper. |

---

## 5. Final Roadmap Summary

> Collect repositories → define permission taxonomy → extract declared permissions → infer static permissions → observe runtime permissions → compare gaps → detect anomalies → quantify risk → propose mitigation → validate → publish.

| RQ | Output |
| --- | --- |
| **RQ1** | Permission taxonomy + dataset of real agent permissions (Steps 1–7). |
| **RQ2** | Anomaly and documentation-gap detection framework (Steps 8–10). |
| **RQ3** | Empirically validated risk score + mitigation artefacts (Steps 11–12). |
| **Cross-cutting** | Validation plan, paper structure, ethics protocol (Steps 13–16). |

---

## 6. Next Direction — This Week

1. **Phase 1 kicks off with AgentCraft.** Clone `wrxck/AgentCraft` at commit `edf9ec4`, open `verification_log.md`, and walk through each ANM-01 through ANM-08 finding by hand, recording every grep command and every file/line opened.
2. **Send Dai the AgentCraft verification report** within four days — a one-page summary noting which findings were confirmed, which were refined, and which (if any) were retracted.
3. **Offer the screenshare Dai mentioned** around the verification walkthrough, to end the AI-credibility question permanently.
4. **In parallel, scaffold P2 directory structure** in the GitHub repo (`framework/`, `taxonomy/`, `validation/`, `mitigation/`, `pilots/`, `docs/`) so the workspace is ready when verification finishes.
