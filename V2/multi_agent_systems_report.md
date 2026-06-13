# Multi-Agent Systems and Agent Swarms — Research Findings

## Overview

This report catalogs **orchestrated multi-agent systems** found on GitHub where multiple individually-coded agents work together. Each system contains anywhere from 3 to 60+ individual agent implementations.

---

## 1. MetaGPT ⭐ 68.7k stars

- **Repository:** https://github.com/FoundationAgents/MetaGPT
- **System Name:** MetaGPT — The Multi-Agent Framework
- **Number of Individual Agents/Roles:** **14+ distinct roles** (5 core SOP roles + 9+ specialized roles)
- **Description:** Simulates an entire software company. The 5 core SOP roles are: **Product Manager** (writes PRD), **Architect** (system design), **Project Manager** (task breakdown), **Engineer** (code implementation), and **QA Engineer** (testing). Additional roles include: Data Interpreter, Researcher, Sales, Customer Service, Teacher, Tutorial Assistant, Searcher, Assistant, Invoice OCR Assistant, and Prompt Engineer. Uses structured communication via publish-subscribe pattern.

---

## 2. ChatDev ⭐ 33.4k stars

- **Repository:** https://github.com/OpenBMB/ChatDev
- **System Name:** ChatDev — Virtual Software Company
- **Number of Individual Agents/Roles:** **7+ core roles** (ChatDev 1.0); flexible in 2.0
- **Description:** A virtual software company where agents play organizational roles. Core ChatDev 1.0 roles: **CEO** (decision maker), **CPO** (product strategy), **CTO** (tech infrastructure), **Programmer** (code writing), **Reviewer** (code review/static debugging), **Tester** (dynamic testing/black-box), and **Art Designer** (UI/generating images). Uses ChatChain for orchestrating agent communication across design, coding, and testing phases. ChatDev 2.0 (DevAll) extends this to a zero-code multi-agent platform supporting thousands of agents in DAG topologies via MacNet and Puppeteer orchestration.

---

## 3. AgentScope ⭐ 26.7k stars

- **Repository:** https://github.com/agentscope-ai/agentscope
- **System Name:** AgentScope — Production-Ready Multi-Agent Framework
- **Number of Individual Agents/Roles:** **5+ built-in agent types** (ReActAgent, UserAgent, Browser-use Agent, Deep Research Agent, Meta-planner Agent)
- **Description:** From Alibaba's DAMO Academy. Provides ReActAgent as the core agent architecture, UserAgent for human interaction, Browser-use Agent for web automation via Playwright MCP, Deep Research Agent for comprehensive research with query expansion/reflection/summarization, and a Meta-planner Agent. Supports A2A protocol, MCP protocol, real-time steering, parallel tool calls, and AgentScope-Runtime for production deployment. Also includes Friday (Studio copilot assistant).

---

## 4. CAMEL ⭐ 17.2k stars

- **Repository:** https://github.com/camel-ai/camel
- **System Name:** CAMEL — Communicative Agents for Mind Exploration
- **Number of Individual Agents/Roles:** **10+ distinct agent implementations**
- **Description:** Pioneer in multi-agent role-play. Built-in agent types: **ChatAgent** (conversational), **CriticAgent** (evaluation), **KnowledgeGraphAgent** (KG construction), **MCPAgent** (MCP protocol), **MultiHopGeneratorAgent**, **ProgrammedAgentInstruction**, **RepoAgent** (repository analysis), **RoleAssignmentAgent**, **SearchAgent**, and **TaskAgent**. Also powers OWL (Open World Learning), a multi-agent system that achieved #1 on the GAIA benchmark (58.18 score).

---

## 5. CrewAI

- **Repository:** https://github.com/crewAIInc/crewAI
- **System Name:** CrewAI — Multi-Agent Automation Framework
- **Number of Individual Agents/Roles:** **User-defined** (framework supports unlimited agents)
- **Description:** Lean, standalone Python framework (independent of LangChain). 100,000+ certified developers. Supports **Crews** (autonomous agent collaboration) and **Flows** (event-driven workflows). Agents are user-defined with roles, goals, backstories, and tools. The framework handles orchestration, delegation, and task sequencing. Notable for being fully standalone and production-ready.

---

## 6. AG2 (formerly AutoGen) ⭐ 39k+ stars

- **Repository:** https://github.com/ag2ai/ag2
- **System Name:** AG2 — Open-Source AgentOS
- **Number of Individual Agents/Roles:** **6+ built-in agent types**
- **Description:** Multi-agent conversation framework from Microsoft. Core agents: **ConversableAgent** (base), **UserProxyAgent** (human-in-the-loop), **AssistantAgent**, **GroupChatManager** (orchestrates group chats), plus nested chat agents. Supports flexible orchestration patterns: group chats, sequential chats, hierarchical patterns, swarm patterns. Provides 9+ group orchestration patterns in the Pattern Cookbook.

---

## 7. Swarms ⭐ 1.5k+ stars

- **Repository:** https://github.com/kyegomez/swarms
- **System Name:** Swarms — Enterprise Multi-Agent Orchestration
- **Number of Individual Agents/Roles:** **60+ pre-built multi-agent architectures**
- **Description:** Comprehensive multi-agent orchestration framework with 60+ architectures: SequentialWorkflow, ConcurrentWorkflow, AgentRearrange, GraphWorkflow, MixtureOfAgents (MoA), GroupChat, ForestSwarm, HierarchicalSwarm, HeavySwarm (5 specialized agents), SwarmRouter, and more. Includes AutoSwarmBuilder for automatic agent generation. Features AOP (Agent Orchestration Protocol) for distributed deployment. Backward compatible with LangChain, AutoGen, CrewAI.

---

## 8. OpenAI Swarm ⭐ 19k+ stars

- **Repository:** https://github.com/openai/swarm (archived — replaced by Agents SDK)
- **System Name:** OpenAI Swarm — Lightweight Multi-Agent Orchestration
- **Number of Individual Agents/Roles:** **5+ example agent configurations**
- **Description:** Experimental educational framework for multi-agent orchestration. Built on two primitives: **Agents** and **handoffs**. Provided examples: triage_agent, weather_agent, airline (multi-agent customer service), support_bot, personal_shopper. Stateless architecture running on client side. Now evolved into the OpenAI Agents SDK.

---

## 9. AgentVerse ⭐ 6.5k+ stars

- **Repository:** https://github.com/OpenBMB/AgentVerse
- **System Name:** AgentVerse — Multi-Agent Deployment Framework
- **Number of Individual Agents/Roles:** **9 agents in NLP Classroom scenario** (scalable)
- **Description:** Provides two frameworks: task-solving and simulation. Notable simulation scenarios: **NLP Classroom** (1 professor + 8 students = 9 agents), **Prisoner's Dilemma**, **Software Design**, **Database Administrator**, **Pokemon Game**. Uses simulation_agent and simulation_env modules. Supports both task-solving (collaborative problem solving) and simulation (behavioral observation) modes.

---

## 10. Magentic-One (Microsoft)

- **Repository:** Part of Microsoft AutoGen: https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one
- **System Name:** Magentic-One — Generalist Multi-Agent System
- **Number of Individual Agents/Roles:** **5 agents** (4 specialists + 1 orchestrator)
- **Description:** Microsoft's generalist multi-agent system for solving complex tasks. Roles: **Orchestrator** (central coordinator/planner), **WebSurfer** (web information gathering), **FileSurfer** (document management), **Coding Agent** (programming), and **Computer Terminal Agent** (testing/deployment). Uses real-time task monitoring and adaptive replanning.

---

## 11. LangGraph Multi-Agent

- **Repository:** https://github.com/langchain-ai/langgraph (multi-agent patterns)
- **System Name:** LangGraph — Multi-Agent Patterns
- **Number of Individual Agents/Roles:** **3+ orchestration patterns** (supports unlimited agents)
- **Description:** Provides architectural patterns for multi-agent systems: **Supervisor** (central supervisor delegates to workers), **Swarm** (agents hand off dynamically), **Hierarchical** (multi-level supervision). Ships as langgraph-supervisor and langgraph-swarm packages. Supports full_history and last_message modes. Production-ready with memory, streaming, and human-in-the-loop support.

---

## 12. agentUniverse ⭐ 1.5k+ stars

- **Repository:** https://github.com/agentuniverse-ai/agentUniverse
- **System Name:** agentUniverse — Multi-Agent Framework from AntGroup
- **Number of Individual Agents/Roles:** **7 agents across 2 patterns** (PEER: 4, DOE: 3)
- **Description:** From AntGroup's financial business practices. Provides collaboration pattern components: **PEER pattern** (Plan, Execute, Express, Review — 4 specialized agents for reasoning/analysis) and **DOE pattern** (Data-fining, Opinion-inject, Express — 3 agents for data-intensive tasks). Domain-expert oriented with easy integration of SOPs and expert knowledge.

---

## 13. OWL (CAMEL-based)

- **Repository:** https://github.com/camel-ai/owl
- **System Name:** OWL — Open World Learning
- **Number of Individual Agents/Roles:** **Multiple specialized agents**
- **Description:** Built on the CAMEL framework. Multi-agent collaboration system where specialized agents cooperate through browsers, terminals, function calls, and MCP tools. **#1 on the GAIA open-source leaderboard** (58.18 score). Agents include web-browsing agents, terminal agents, tool-use agents, and MCP-enabled agents working collaboratively.

---

## 14. GPT-Newspaper ⭐ 2.5k+ stars

- **Repository:** https://github.com/rotemweiss57/gpt-newspaper
- **System Name:** GPT-Newspaper — Autonomous News Generation
- **Number of Individual Agents/Roles:** **7 specialized agents**
- **Description:** Autonomous agent for creating personalized newspapers. Agents: **SearchAgent** (news discovery), **CuratorAgent** (content filtering), **WriterAgent** (article creation), **CritiqueAgent** (quality feedback loop), **DesignerAgent** (layout), **EditorAgent** (newspaper assembly), **PublisherAgent** (delivery). Uses LangGraph for orchestration.

---

## 15. MACRec

- **Repository:** https://github.com/wzf2000/MACRec
- **System Name:** MACRec — Multi-Agent Collaboration for Recommendation
- **Number of Individual Agents/Roles:** **5 specialized agents**
- **Description:** Academic framework (SIGIR 2024) for recommendation systems. Agents: **Manager** (orchestration), **Analyst** (data analysis), **Searcher** (information retrieval), **Reflector** (feedback/RLHF), **TaskInterpreter** (task understanding). Uses collaboration system with reflection capability and PPO-based training for the Reflector agent.

---

## 16. Multi-Agent Coding System

- **Repository:** https://github.com/Danau5tin/multi-agent-coding-system
- **System Name:** Orchestrator — Multi-Agent AI Coder
- **Number of Individual Agents/Roles:** **3 agent types**
- **Description:** Ranked #13 on Stanford's TerminalBench. Three agent types: **Orchestrator Agent** (strategic coordinator, cannot touch code directly), **Explorer Agent** (read-only investigation/verification), **Coder Agent** (implementation with write access). Uses intelligent context sharing between agents. Also spawned Orca-Agent-v0.1 (RL-trained 14B model).

---

## 17. GenAI_Agents (Collection) ⭐ 10k+ stars

- **Repository:** https://github.com/nirdiamant/genai_agents
- **System Name:** GenAI_Agents — 50+ Agent Tutorials
- **Number of Individual Agents/Roles:** **50+ different agent implementations**
- **Description:** Comprehensive collection of 50+ agent tutorials and implementations. Includes multi-agent systems like: ATLAS (4 agents: Coordinator, Planner, Notewriter, Advisor), AInsight (3 agents: NewsSearcher, Summarizer, Publisher), Multi-Agent Research Team (5 agents: admin, developer, planner, executor, QA), Blog Writer (5 agents: admin, researcher, planner, writer, editor), Grocery Management (4 agents), Contextual Quoting (4 agents), and many more.

---

## Summary Table

| System | Stars | Agents/Roles | Type |
|--------|-------|-------------|------|
| MetaGPT | 68.7k | 14+ | Software Company |
| ChatDev | 33.4k | 7+ | Virtual Software Company |
| AgentScope | 26.7k | 5+ | Production Framework |
| CAMEL | 17.2k | 10+ | Research Framework |
| CrewAI | N/A | User-defined | Automation Framework |
| AG2/AutoGen | 39k+ | 6+ | Conversation Framework |
| Swarms | 1.5k+ | 60+ architectures | Orchestration Framework |
| OpenAI Swarm | 19k+ | 5+ examples | Educational Framework |
| AgentVerse | 6.5k+ | 9 (simulation) | Task + Simulation |
| Magentic-One | N/A | 5 | Generalist System |
| LangGraph | N/A | 3+ patterns | Pattern Library |
| agentUniverse | 1.5k+ | 7 (2 patterns) | Financial Framework |
| OWL | N/A | Multiple | GAIA Leader |
| GPT-Newspaper | 2.5k+ | 7 | News Generation |
| MACRec | N/A | 5 | Recommendation |
| Multi-Agent Coder | N/A | 3 | Code Generation |
| GenAI_Agents | 10k+ | 50+ tutorials | Tutorial Collection |

---

## Notes

- **MetaGPT** has the most built-in individual role implementations (14+) with distinct Python classes for each role
- **ChatDev** provides the most realistic software company simulation with 7+ organizationally-inspired roles
- **Swarms** offers the most pre-built architectures (60+) but these are orchestration patterns rather than individual agents
- **GenAI_Agents** contains the most individual agent implementations (50+) but as tutorials, not a unified system
- Most frameworks (CrewAI, LangGraph, AG2) focus on orchestration patterns rather than pre-built agent roles
- The trend is toward user-defined agents with framework-provided orchestration rather than fixed agent roles
