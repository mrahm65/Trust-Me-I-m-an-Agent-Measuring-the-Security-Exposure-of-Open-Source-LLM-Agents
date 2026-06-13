# Additional and Lesser-Known Sources of Individually Coded AI Agents

## Comprehensive Research Report

---

## 1. HUGGING FACE SPACES/COLLECTIONS

### 1.1 Hugging Face Spaces as Agent Tools
- **URL**: https://huggingface.co/spaces (300,000+ Spaces)
- **Source Type**: HuggingFace
- **Agent Count**: 300,000+ Spaces, many agent-compatible
- **Description**: Every Gradio Space exposes an `agents.md` endpoint that coding agents (Claude Code, Codex, OpenCode, Pi) can call directly. Spaces can be chained - e.g., image generation -> 3D model creation. Each Space is a runnable agent with its own API.

### 1.2 smolagents Framework + Gallery
- **URL**: https://huggingface.co/spaces/davidberenstein1957/smolagents-and-tools
- **Source Type**: HuggingFace
- **Agent Count**: 100+ community agents
- **Description**: Gallery of live previews for community-created smolagents. The Hugging Face Agents Course teaches building agents with smolagents and publishing them as runnable Spaces.

### 1.3 TinyCodeAgent (Hugging Face Space)
- **URL**: https://github.com/askbudi/TinyCodeAgent
- **Source Type**: HuggingFace Space / GitHub
- **Agent Count**: 1 agent (template)
- **Description**: Self-building, self-debugging Python agent that runs in the cloud. Built on TinyAgent framework with Gradio integration. Uses Qwen/Qwen3-235B-A22B.

### 1.4 Hugging Face Agents Course - Student Projects
- **URL**: https://huggingface.co/spaces/orbulat/Unit4_Final/tree/main
- **Source Type**: HuggingFace Spaces
- **Agent Count**: 1000+ student projects
- **Description**: Students build and publish agents as Hugging Face Spaces as part of the Agents Course. Each Space is a runnable agent.

---

## 2. KAGGLE NOTEBOOKS

### 2.1 Kaggle AI Agents Intensive Course
- **URL**: https://www.kaggle.com/code/kaggle5daysofai/day-4b-agent-evaluation
- **Source Type**: Kaggle
- **Agent Count**: 11,000+ capstone submissions
- **Description**: 5-day AI Agents Intensive with Google. 3.3M views on course notebooks. 160,000+ learners. Students build agents in Kaggle Notebooks with runnable code.

### 2.2 Kaggle 5-Day GenAI Course - Agent Notebooks
- **URL**: https://github.com/saroshfarhan/AI_Agent
- **Source Type**: Kaggle / GitHub
- **Agent Count**: Course-based (dozens of examples)
- **Description**: Hands-on notebooks demonstrating agent creation, sequential/parallel workflows, memory systems, and human-in-the-loop patterns.

### 2.3 Kaggle Competition - AI Agent Capstone
- **URL**: https://www.kaggle.com/competitions/agents-intensive-capstone-project
- **Source Type**: Kaggle Competition
- **Agent Count**: 11,000+ submissions
- **Description**: Capstone competition where participants build functional AI agents in Kaggle Notebooks.

### 2.4 Kaggle Notebooks for MLAgentBench
- **URL**: Referenced in GitTaskBench paper
- **Source Type**: Kaggle
- **Agent Count**: Multiple research notebooks
- **Description**: Researchers run agent experiments on Kaggle with free GPU access for climate cooperation simulations.

---

## 3. GITLAB

### 3.1 GitLab AI Catalog
- **URL**: https://docs.gitlab.com/user/duo_agent_platform/agents/
- **Source Type**: GitLab
- **Agent Count**: 600+ agents from hackathon + foundational agents
- **Description**: Central repository for discovering, creating, and sharing agents. Three types: Foundational (pre-built), Custom (user-defined), and External (Claude Code, Codex, Amazon Q, Gemini).

### 3.2 GitLab AI Hackathon 2026 - 600+ Entries
- **URL**: https://about.gitlab.com/blog/gitlab-ai-hackathon-2026-meet-the-winners/
- **Source Type**: GitLab / Hackathon
- **Agent Count**: 600+ agents and flows submitted
- **Description**: Nearly 7,000 developers built 600+ agents. Winners include SecurityMonkey, Compliance Sentinel, Carbon Tracker, RepoWarden, and MR Compliance Auditor.

### 3.3 GitLab External Agents
- **URL**: https://docs.gitlab.com/user/duo_agent_platform/agents/external/
- **Source Type**: GitLab
- **Agent Count**: 4 managed external agents (Claude Code, Codex, Amazon Q, Gemini)
- **Description**: GitLab-managed external agents that can be triggered from issues, merge requests, and epics.

### 3.4 GitLab.org AI Skills
- **URL**: https://gitlab.com/gitlab-org/ai/skills
- **Source Type**: GitLab
- **Agent Count**: Growing collection of reusable skills
- **Description**: Reusable agent skills for GitLab projects - structured prompt files for AI coding assistants.

---

## 4. COMPANY/LAB OPEN SOURCE

### 4.1 IBM

#### IBM/Agentics
- **URL**: https://github.com/IBM/Agentics
- **Source Type**: Company (IBM)
- **Agent Count**: 1 framework
- **Description**: Python framework that transforms LLM computation into functional code with typed transductions. Includes 6 notebooks for different concepts.

#### IBM SWE-Agent
- **URL**: Referenced at IBM TechXchange
- **Source Type**: Company (IBM)
- **Agent Count**: 1 agent (Mixture of Agents paradigm)
- **Description**: Open-source SWE agent achieving 23.7% on SWE-bench using only open-source models (LLaMa 3.1, Mistral, Granite).

### 4.2 Amazon/AWS

#### Amazon Bedrock Agent Samples
- **URL**: https://github.com/awslabs/amazon-bedrock-agent-samples
- **Source Type**: Company (AWS)
- **Agent Count**: 25+ agent examples
- **Description**: Jupyter notebooks and code scripts for Amazon Bedrock Agents. Includes multi-agent collaboration examples (DevOps, Energy, Mortgage, Portfolio, Real Estate, Startup Advisor, Support, Trip Planner, etc.)

#### Amazon Bedrock AgentCore Samples
- **URL**: https://github.com/awslabs/agentcore-samples
- **Source Type**: Company (AWS)
- **Agent Count**: 15+ end-to-end samples + feature deep dives
- **Description**: Production-ready samples for AgentCore - Python/TypeScript getting-started, feature examples (Runtime, Gateway, Identity, Memory, Tools, Observability, Evaluation, Policy), and infrastructure-as-code templates.

#### AWS Dynamic Text-to-SQL with Bedrock Agent
- **URL**: https://github.com/aws-samples/sample-Dynamic-Text-to-SQL-with-Amazon-Bedrock-Agent
- **Source Type**: Company (AWS)
- **Agent Count**: 1 agent
- **Description**: CDK-based deployment of a Bedrock Agent for Athena database queries.

#### AWS Bedrock Deep Researcher
- **URL**: https://github.com/aws-samples/sample-bedrock-deep-researcher
- **Source Type**: Company (AWS)
- **Agent Count**: 1 agent (research workflow)
- **Description**: Streamlit app using Bedrock, LangGraph, and LangChain for automated article/report generation.

### 4.3 NVIDIA

#### NVIDIA NeMo Agent Toolkit
- **URL**: https://github.com/NVIDIA/NeMo-Agent-Toolkit
- **Source Type**: Company (NVIDIA)
- **Agent Count**: Toolkit with multiple integrations
- **Description**: Open-source agent tools and skills for Physical AI. Supports Google ADK, Microsoft AutoGen, CrewAI, Dynamo, FastAPI, LangChain, LlamaIndex, MCP, Semantic Kernel.

#### NVIDIA Physical AI Skills
- **URL**: https://skills.sh + GitHub
- **Source Type**: Company (NVIDIA)
- **Agent Count**: 10+ agent skills
- **Description**: Agent skills for synthetic data generation (Neural Reconstruction, Video Augmentation, Defect Image Generation). Available as Physical AI Launchables on NVIDIA Brev.

### 4.4 Google

#### Google Agent Development Kit (ADK)
- **URL**: https://github.com/google/adk-docs
- **Source Type**: Company (Google)
- **Agent Count**: SDK + sample collection
- **Description**: Open-source, code-first toolkit for building agents. Multi-language (Python, TypeScript, Go, Java, Kotlin). Includes adk-samples repo with practical examples.

#### Google ADK Bot (GitHub triage)
- **URL**: https://github.com/Ashutosh0x/adk-bot (community) + google/adk-js
- **Source Type**: Company (Google) + Community
- **Agent Count**: 2+ reference implementations
- **Description**: ADK-powered GitHub bot for PR triage, issue labeling, and review. Uses Gemini.

#### Google Gemini CLI GitHub Actions
- **URL**: Referenced in analyticsindiamag
- **Source Type**: Company (Google)
- **Agent Count**: 3 default workflows
- **Description**: Open-source AI agent for automating dev tasks - issue triage, PR review, on-demand collaboration.

### 4.5 Microsoft

#### Microsoft Agent Framework
- **URL**: https://github.com/microsoft/agent-framework
- **Source Type**: Company (Microsoft)
- **Agent Count**: Framework + starter kits
- **Description**: Open-source multi-language framework (.NET/Python) for production-grade agents. Unifies Semantic Kernel + AutoGen. Supports MCP, A2A, OpenAPI.

#### Microsoft AI Agents for Beginners
- **URL**: https://github.com/microsoft/ai-agents-for-beginners
- **Source Type**: Company (Microsoft)
- **Agent Count**: 12+ lessons with code samples
- **Description**: 12-lesson course with code samples for each lesson. Multi-language support (50+ languages).

#### Microsoft Agent Governance Toolkit
- **URL**: https://github.com/microsoft/agent-governance-toolkit
- **Source Type**: Company (Microsoft)
- **Agent Count**: 1 toolkit
- **Description**: Governance toolkit for AI agents with policy enforcement, identity, trust, audit. 8 language SDKs (Python, TypeScript, Rust, Go, .NET, etc.)

#### Microsoft AutoGen
- **URL**: https://github.com/microsoft/autogen
- **Source Type**: Company (Microsoft)
- **Agent Count**: Research framework
- **Description**: Programming framework for agentic AI. Now in maintenance mode as development moves to Microsoft Agent Framework.

#### Microsoft 365 Agents SDK
- **URL**: https://github.com/microsoft/agents
- **Source Type**: Company (Microsoft)
- **Agent Count**: SDK for building M365 agents
- **Description**: SDK for building agents that work across Microsoft 365 Copilot, Teams, web, and other surfaces.

#### Agents League Contest
- **URL**: https://github.com/microsoft/agentsleague
- **Source Type**: Company (Microsoft) / Competition
- **Agent Count**: Competition-based (100s of entries)
- **Description**: 2-week AI developer challenge with live coding battles. Three tracks: Creative Apps, Reasoning Agents, Enterprise Agents.

#### Microsoft AI Agents Hackathon 2025
- **URL**: https://github.com/microsoft/AI_Agents_Hackathon
- **Source Type**: Company (Microsoft) / Hackathon
- **Agent Count**: Competition with 1000s of participants
- **Description**: Free 3-week virtual hackathon with 20+ expert sessions. Covers Semantic Kernel, Autogen, Azure AI Agents SDK, M365 Agents SDK.

#### Azure AI Dev Days Hackathon
- **URL**: https://github.com/Azure/AI-Dev-Days-Hackathon
- **Source Type**: Company (Microsoft) / Hackathon
- **Agent Count**: Competition-based
- **Description**: 5-week global challenge to build AI agents, agentic DevOps workflows. $80,000+ in prizes.

### 4.6 Alibaba

#### OpenTiny Tiny Agent
- **URL**: https://github.com/opentiny/tiny-agent
- **Source Type**: Company (Alibaba/OpenTiny)
- **Agent Count**: 1 prototype
- **Description**: WebMCP Agent Prototype Project. Agent with MCP protocol support for web interactions.

### 4.7 Baidu

#### Baidu Map + DeepSeek Agent
- **URL**: https://github.com/leng-2024/agent-with-mcp
- **Source Type**: Community (using Baidu API)
- **Agent Count**: 1 agent
- **Description**: Location search and route planning Agent using Baidu Map API + DeepSeek API + MCP tools.

### 4.8 Oracle

#### Oracle Select AI Pre-Built Agents
- **URL**: Referenced on Oracle blog
- **Source Type**: Company (Oracle)
- **Agent Count**: 8 pre-built agents
- **Description**: Collection of AI-driven workflow helpers: NL2SQL Data Retrieval, Autonomous AI DB Provisioning, Database Inspect, Insight Agent for Jira, Cloud Repository Connector, OCI Network LB Agent, OCI Object Storage Agent, OCI Vault Agent.

### 4.9 SAP

#### SAP AI SDK Samples (TechEd 2025)
- **URL**: https://github.com/SAP-samples/teched2025-AI160
- **Source Type**: Company (SAP)
- **Agent Count**: 1 reference implementation (JS + Java)
- **Description**: AI-powered Purchase Order Management Agent using SAP S/4HANA and SAP AI Core. Available in LangGraph (JS) and Spring AI (Java).

#### SAP Agent Builder Lab
- **URL**: https://github.com/SAP-samples/teched2025-AI165
- **Source Type**: Company (SAP)
- **Agent Count**: 1 lab preview
- **Description**: Agent Builder in Joule Studio - build custom agents with A2A protocol support.

### 4.10 Apache

#### Apache Flink Agents
- **URL**: https://github.com/apache/flink-agents
- **Source Type**: Foundation (Apache)
- **Agent Count**: 1 framework
- **Description**: Agentic AI framework based on Apache Flink. Java + Python support. Weekly community sync.

### 4.11 Linux Foundation

#### Agentic AI Foundation (AAIF)
- **URL**: https://github.com/aaif
- **Source Type**: Foundation (Linux Foundation)
- **Agent Count**: 3 founding projects + ecosystem
- **Description**: Neutral home for agent standards. Founding contributions: Anthropic's MCP, Block's goose, OpenAI's AGENTS.md. 60,000+ projects using AGENTS.md.

#### AgentGateway
- **URL**: https://github.com/agentgateway/agentgateway
- **Source Type**: Foundation (Linux Foundation)
- **Agent Count**: 1 gateway (connects many agents)
- **Description**: AI-native proxy for agent connectivity. Supports A2A and MCP protocols.

---

## 5. RESEARCH LAB RELEASES

### 5.1 Princeton/Stanford (SWE-agent team)

#### SWE-agent
- **URL**: https://github.com/SWE-agent/SWE-agent
- **Source Type**: Research Lab
- **Agent Count**: 1 agent + ecosystem
- **Description**: Software engineering agent that automatically solves GitHub issues. NeurIPS 2024. 19.5k stars.

#### mini-swe-agent
- **URL**: https://github.com/SWE-agent/mini-swe-agent
- **Source Type**: Research Lab
- **Agent Count**: 1 minimal agent
- **Description**: 100-line AI agent that achieves >74% on SWE-bench verified. Supports all models via LiteLLM/OpenRouter.

#### SWE-bench
- **URL**: https://github.com/SWE-agent/SWE-bench
- **Source Type**: Research Lab / Benchmark
- **Agent Count**: Benchmark (500+ verified tasks)
- **Description**: Benchmark for evaluating AI systems on real-world GitHub issues.

### 5.2 MIT

#### MIT Agentic AI Curriculum
- **URL**: Referenced on X/Twitter
- **Source Type**: Research Lab (MIT)
- **Agent Count**: Course materials
- **Description**: $2,500 agentic AI curriculum released on GitHub at no cost. 15,000 people previously paid for it.

### 5.3 Allen Institute for AI (AI2)

#### Panda (Plan-and-Act Agent)
- **URL**: https://github.com/allenai/panda
- **Source Type**: Research Lab (AI2)
- **Agent Count**: 1 autonomous research agent
- **Description**: Autonomous scientific discovery agent. Plan-do outer loop, act-reflect inner loop. Customizable for research tasks.

#### AI2 Agent Baselines
- **URL**: https://github.com/allenai/agent-baselines
- **Source Type**: Research Lab (AI2)
- **Agent Count**: Multiple baseline agents
- **Description**: Baseline implementations of agents as reported in AstaBench. Each solver has its own environment.

#### SUPER Benchmark
- **URL**: https://github.com/allenai/super-benchmark
- **Source Type**: Research Lab (AI2)
- **Agent Count**: 3 agent implementations
- **Description**: Evaluating agents on setting up and executing ML/NLP tasks from research repos. 45 Expert + 152 Masked + 602 AutoGen tasks.

#### Paper Finder Agent
- **URL**: https://github.com/allenai/asta-paper-finder
- **Source Type**: Research Lab (AI2)
- **Agent Count**: 1 agent
- **Description**: Paper-seeking agent for locating sets of papers by content and metadata. Multiple workflows for different intents.

### 5.4 Tsinghua University

#### AgentBench
- **URL**: https://github.com/THUDM/AgentBench
- **Source Type**: Research Lab (Tsinghua)
- **Agent Count**: 8 environments
- **Description**: First comprehensive benchmark evaluating LLMs as agents across 8 diverse environments (OS, Database, Web Shopping, etc.)

### 5.5 MILA

#### Climate Cooperation Competition
- **URL**: https://github.com/mila-iqia/climate-cooperation-competition
- **Source Type**: Research Lab (MILA)
- **Agent Count**: Competition with agent submissions
- **Description**: AI for Global Climate Cooperation - agent-based model with RL agents. Free GPU on Kaggle.

---

## 6. AGENT BENCHMARKS/EVALUATIONS (often include agent implementations)

### 6.1 AgentBench (Tsinghua)
- **URL**: https://github.com/THUDM/AgentBench
- **Source Type**: Benchmark
- **Agent Count**: 8 environments
- **Description**: Comprehensive benchmark across 8 environments: OS, Database, Web Shopping, Home, Digital Card Game, Web browsing, Knowledge Graph.

### 6.2 SWE-bench (Princeton/Stanford)
- **URL**: https://github.com/SWE-agent/SWE-bench
- **Source Type**: Benchmark
- **Agent Count**: 500+ verified GitHub issues
- **Description**: Industry-standard benchmark for evaluating agents on real-world GitHub issue resolution.

### 6.3 GitTaskBench
- **URL**: Referenced in arxiv paper (anonymous GitHub)
- **Source Type**: Benchmark
- **Agent Count**: 54 tasks across 18 repos
- **Description**: Evaluates agents on real-world tasks using code repositories. 7 domains, 24 subdomains. Includes OpenHands, SWE-Agent, Aider baselines.

### 6.4 WildClawBench
- **URL**: https://github.com/InternLM/WildClawBench
- **Source Type**: Benchmark
- **Agent Count**: 60 tasks, 4 agent harnesses
- **Description**: In-the-wild benchmark with 60 original tasks. Tests agency, multimodal, long-horizon, coding, safety.

### 6.5 AI Agent Benchmark Compendium
- **URL**: https://github.com/philschmid/ai-agent-benchmark-compendium
- **Source Type**: Benchmark Collection
- **Agent Count**: 50+ benchmarks catalogued
- **Description**: Compendium of benchmarks categorized into Function Calling, General Assistant, Coding, and Computer Interaction.

### 6.6 AgentEvals (LangChain)
- **URL**: https://github.com/langchain-ai/agentevals
- **Source Type**: Evaluation Framework
- **Agent Count**: Framework (N/A)
- **Description**: Readymade evaluators for agent trajectories - trajectory match, LLM-as-judge, graph trajectory evaluation.

### 6.7 Agent Skills Leaderboard
- **URL**: https://github.com/jaychempan/Agent-Skills-Leaderboard
- **Source Type**: Leaderboard / Discovery
- **Agent Count**: 4500+ repos tracked
- **Description**: Five boards: Agent Skills (500+), MCP Servers (1500+), Prompt Library (1100+), AI Frameworks (1200+), Auto Research (100+). Updated daily.

### 6.8 AI Agent Benchmark (User-Reported)
- **URL**: https://github.com/murataslan1/ai-agent-benchmark
- **Source Type**: Benchmark Comparison
- **Agent Count**: 80+ agents compared
- **Description**: Comparison of 80+ AI coding agents with SWE-Bench scores, pricing, and real user experiences.

### 6.9 Cua-Bench
- **URL**: https://github.com/trycua/cua (cua-bench subpackage)
- **Source Type**: Benchmark
- **Agent Count**: Multiple benchmark tasks
- **Description**: Benchmarks for computer-use agents on OSWorld, ScreenSpot, Windows Arena, and custom tasks.

---

## 7. AGENT COMPETITIONS/HACKATHONS

### 7.1 GitLab AI Hackathon 2026
- **URL**: https://about.gitlab.com/blog/gitlab-ai-hackathon-2026-meet-the-winners/
- **Source Type**: Hackathon
- **Agent Count**: 600+ agents/flows
- **Description**: 7,000 developers, $65,000 prizes. 19 judges. 6 honorable mentions with detailed projects.

### 7.2 Microsoft AI Agents Hackathon 2025
- **URL**: https://github.com/microsoft/AI_Agents_Hackathon
- **Source Type**: Hackathon
- **Agent Count**: 1000s of participants
- **Description**: Free 3-week virtual hackathon. 20+ expert sessions. Cash prizes.

### 7.3 Microsoft Agents League
- **URL**: https://github.com/microsoft/agentsleague
- **Source Type**: Competition
- **Agent Count**: Competition-based (100s)
- **Description**: 2-week developer challenge with live coding battles. 3 tracks. $500/track winner.

### 7.4 AI Agents Global Challenge
- **URL**: https://aiagentschallenge.com/
- **Source Type**: Competition
- **Agent Count**: Competition entries
- **Description**: $1M prize pool. Challenge: build productive AI agents for enterprise applications.

### 7.5 Reply Challenges - AI Agent Challenge
- **URL**: https://challenges.reply.com/challenges/ai-agent/home
- **Source Type**: Competition
- **Agent Count**: Team-based (2-4 members)
- **Description**: 6-hour team competition. Design multi-agent system for fraud detection. EUR 2,500 per team member for winner.

### 7.6 Agentic AI Challenge (Hong Kong)
- **URL**: https://iabhongkong.com/aichallenge
- **Source Type**: Competition
- **Agent Count**: Competition entries
- **Description**: Multi-category competition. HK$10,000 for champion.

### 7.7 Agent.ai Challenge (DEV Community)
- **URL**: https://dev.to/challenges/agentai
- **Source Type**: Competition
- **Agent Count**: Community submissions
- **Description**: Build agents with Agent.ai Builder. $10,000 prize pool. 3 prompts/challenges.

### 7.8 Merck Innovation Cup - AI Agent Competition
- **URL**: https://www.merckgroup.com/en/research/open-innovation/innovation-cup/ai-agent.html
- **Source Type**: Competition
- **Agent Count**: Research teams
- **Description**: Solve 1 of 3 research challenges with AI agent. 10,000 euro prize. Registration June 2026.

---

## 8. SPECIFIC KNOWN COLLECTIONS

### 8.1 Agent Laboratory
- **URL**: https://github.com/SamuelSchmidgall/AgentLaboratory
- **Source Type**: Research Tool
- **Agent Count**: 5 specialized agents (Professor, PhD Student, Postdoc, SW Engineer, ML Engineer)
- **Description**: End-to-end autonomous research workflow. Agents collaborate on literature review, planning, experiments, and report writing.

### 8.2 Azure AI Agents Labs
- **URL**: https://github.com/Azure/azure-ai-agents-labs
- **Source Type**: Microsoft Labs
- **Agent Count**: 5 labs with multiple agents
- **Description**: Hands-on labs for building AI Agents with Azure AI Agent Service SDK. Multi-agent system with Search, Report, Validation, and Orchestrator agents.

### 8.3 TinyAgent
- **URL**: https://github.com/askbudi/tinyagent
- **Source Type**: Open Source Project
- **Agent Count**: 1 SDK
- **Description**: Production-Ready LLM Agent SDK. Lightweight, event-driven, with hooks system.

### 8.4 Microagent
- **URL**: https://github.com/chrislatimer/microagent
- **Source Type**: Open Source (fork of OpenAI Swarm)
- **Agent Count**: 1 framework
- **Description**: Lightweight multi-agent framework. Fork of OpenAI Swarm with Groq and Anthropic LLM support.

### 8.5 Tiny Agents (Hugging Face)
- **URL**: https://huggingface.co/blog/tiny-agents
- **Source Type**: HuggingFace Tutorial
- **Agent Count**: Tutorial agent (50 lines of code)
- **Description**: MCP-powered agent in 50 lines of code. Built with huggingface.js mcp-client.

### 8.6 Browser-Use
- **URL**: https://github.com/browser-use/browser-use
- **Source Type**: Open Source
- **Agent Count**: 1 agent framework
- **Description**: Make websites accessible for AI agents. Rust core + browser harness. 41k+ stars.

### 8.7 Vercel Agent Browser
- **URL**: https://github.com/vercel-labs/agent-browser
- **Source Type**: Company (Vercel)
- **Agent Count**: 1 browser automation CLI
- **Description**: Fast native Rust CLI for browser automation. Installable via npm, Homebrew, or Cargo.

### 8.8 Open Computer Use (Coasty AI)
- **URL**: https://github.com/coasty-ai/open-computer-use
- **Source Type**: Open Source
- **Agent Count**: 4 agents (Browser, Terminal, Desktop, Planner)
- **Description**: Open-source platform for AI agents with real computer control. Similar to Claude Computer Use but fully open-source.

### 8.9 Cua (Computer-Use Agents)
- **URL**: https://github.com/trycua/cua
- **Source Type**: Open Source
- **Agent Count**: Multiple packages (cuabot, cua-agent, cua-bench, etc.)
- **Description**: Open-source infrastructure for Computer-Use Agents. Sandboxes, SDKs, benchmarks for training/evaluating agents on full desktops (macOS, Linux, Windows).

### 8.10 Operator! (Multi-Agent Orchestration)
- **URL**: https://github.com/untra/operator
- **Source Type**: Open Source
- **Agent Count**: TUI orchestrator for multiple agents
- **Description**: Multi-agent orchestration for kanban-shaped software development. Manages Claude Code, Codex, Gemini CLI across projects.

### 8.11 Awesome Agent Skills
- **URL**: https://github.com/VoltAgent/awesome-agent-skills
- **Source Type**: Curated Collection
- **Agent Count**: 1000+ agent skills
- **Description**: Curated collection of 1000+ agent skills from official dev teams and community. Compatible with Claude Code, Codex, Gemini CLI, Cursor, etc.

### 8.12 AgentScope (Alibaba)
- **URL**: https://github.com/agentscope-ai/agentscope
- **Source Type**: Research/Company
- **Agent Count**: Multi-agent framework
- **Description**: Build and run agents you can see, understand and trust. FastAPI-based multi-tenancy, multi-session agent service with Web UI.

### 8.13 CAMEL (Community)
- **URL**: https://github.com/camel-ai/camel
- **Source Type**: Open Source
- **Agent Count**: Multi-agent framework
- **Description**: First and best multi-agent framework. Finding the Scaling Law of Agents. Task-driven autonomous agents.

### 8.14 Pydantic Deep Agents
- **URL**: https://github.com/vstorm-co/pydantic-deepagents
- **Source Type**: Open Source
- **Agent Count**: 1 agent harness (with subagent support)
- **Description**: Batteries-included deep agent harness on Pydantic AI. Tool-calling, sandboxed execution, multi-agent teams, skills, checkpoints, unlimited context.

### 8.15 Pydantic AI Harness
- **URL**: https://github.com/pydantic/pydantic-ai-harness
- **Source Type**: Open Source (Pydantic ecosystem)
- **Agent Count**: 1 ecosystem agent harness
- **Description**: Ecosystem agent combining CodeMode, MCP, WebSearch, Thinking, Context Management, SubAgents, Skills, TODO tracking, Shields.

### 8.16 Letta (formerly MemGPT)
- **URL**: https://github.com/letta-ai/letta
- **Source Type**: Open Source
- **Agent Count**: 1 framework
- **Description**: Universal standard for portable AI agents. Open file format (.af) for packaging agents with memory and behavior intact.

### 8.17 Goose (Block/Square)
- **URL**: https://github.com/block/goose
- **Source Type**: Company (Block)
- **Agent Count**: 1 local-first agent framework
- **Description**: Open source, local-first AI agent framework. Contributed to Linux Foundation's AAIF. MCP-based integration.

---

## 9. OPENAI AGENTS SDK EXAMPLES

### 9.1 OpenAI Agents SDK - Official Examples
- **URL**: https://openai.github.io/openai-agents-python/examples/
- **Source Type**: Official SDK Examples
- **Agent Count**: 30+ example scripts
- **Description**: Categorized examples: agent_patterns (workflows, handoffs, guardrails, human-in-the-loop), basic (hello world, tools, lifecycle, streaming), customer_service (airline), financial_research, handoffs, hosted_mcp, mcp, memory, model_providers, realtime, reasoning_content, research_bot.

### 9.2 OpenAI Customer Service Agents Demo
- **URL**: https://github.com/openai/openai-cs-agents-demo
- **Source Type**: Official Demo
- **Agent Count**: 6 specialized agents
- **Description**: Airline customer service system with Triage, Flight Info, Booking, Seat Services, FAQ, and Refunds agents. Next.js UI + Python backend.

### 9.3 OpenAI Voice Agent SDK Sample
- **URL**: https://github.com/openai/openai-voice-agent-sdk-sample
- **Source Type**: Official Demo
- **Agent Count**: 1 voice agent
- **Description**: Voice agent using FastAPI backend + Next.js frontend. Multi-turn conversation, push-to-talk, function calling, streaming.

### 9.4 OpenAI Realtime Agents
- **URL**: https://github.com/openai/openai-realtime-agents
- **Source Type**: Official Demo
- **Agent Count**: Multiple patterns
- **Description**: Chat-Supervisor and Sequential Handoff patterns built on Realtime API. Next.js TypeScript app.

### 9.5 OpenAI Swarm (Educational)
- **URL**: https://github.com/openai/swarm
- **Source Type**: Official (Educational)
- **Agent Count**: Educational framework
- **Description**: Lightweight, scalable multi-agent orchestration. Examples: triage, weather, airline, support_bot, personal_shopper.

### 9.6 OpenAI Agents Demos with Temporal
- **URL**: https://github.com/temporal-community/openai-agents-demos
- **Source Type**: Community (Temporal)
- **Agent Count**: 4 demo workflows
- **Description**: Temporal + OpenAI Agents SDK integration. Hello World, Tools, Research Bot, and Interactive Research workflows.

---

## 10. SUMMARY STATISTICS

| Category | Sources Found | Estimated Agent Count |
|----------|--------------|---------------------|
| Hugging Face Spaces | 4+ | 300,000+ Spaces (many agent-runnable) |
| Kaggle Notebooks | 4+ | 11,000+ student submissions |
| GitLab | 4+ | 600+ agents from hackathon |
| Company Open Source | 30+ | 100+ individual agent repos |
| Research Labs | 8+ | Multiple agents + benchmarks |
| Benchmarks/Evaluation | 9+ | 50+ benchmarks, 1000+ tasks |
| Competitions/Hackathons | 8+ | 1000s of submitted agents |
| Specific Collections | 17+ | 100+ specialized agents |
| OpenAI SDK Examples | 6+ | 50+ example implementations |

**TOTAL ESTIMATED INDIVIDUALLY CODED AGENTS: 10,000+**

---

## 11. KEY LESSER-KNOWN SOURCES

The most valuable **lesser-known** sources for finding runnable agent code:

1. **GitLab AI Catalog** (600+ agents from recent hackathon) - https://docs.gitlab.com/user/duo_agent_platform/agents/
2. **Hugging Face Spaces** (300K spaces with `agents.md` endpoints) - https://huggingface.co/spaces
3. **SWE-agent ecosystem** (Princeton/Stanford) - https://github.com/SWE-agent
4. **IBM/Agentics** framework - https://github.com/IBM/Agentics
5. **NVIDIA NeMo Agent Toolkit** - https://github.com/NVIDIA/NeMo-Agent-Toolkit
6. **Apache Flink Agents** - https://github.com/apache/flink-agents
7. **Agent Laboratory** (5-agent research system) - https://github.com/SamuelSchmidgall/AgentLaboratory
8. **Panda** (AI2 autonomous discovery) - https://github.com/allenai/panda
9. **Cua** (Computer-Use Agents) - https://github.com/trycua/cua
10. **Pydantic Deep Agents** - https://github.com/vstorm-co/pydantic-deepagents
11. **Operator!** (multi-agent orchestrator) - https://github.com/untra/operator
12. **Agent Skills Leaderboard** (4500+ repos) - https://github.com/jaychempan/Agent-Skills-Leaderboard

---

*Report generated from comprehensive web research covering 40+ searches across platforms.*
*Last updated: June 2026*
