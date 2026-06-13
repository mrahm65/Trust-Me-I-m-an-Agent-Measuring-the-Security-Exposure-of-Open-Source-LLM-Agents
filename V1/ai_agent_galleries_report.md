# AI Agent Galleries & Examples - Major Frameworks Research Report

*Compiled on June 11, 2026*

---

## 1. LangChain / LangGraph

### Main Repository
- **URL**: https://github.com/langchain-ai/langgraph
- **Stars**: 34.5k+
- **LangGraph Examples**: https://github.com/langchain-ai/langgraph/tree/main/examples

### Example Categories (15+ agent categories)
| Category | Description |
|----------|-------------|
| `multi_agent` | Multi-agent orchestration patterns |
| `chatbots` | Conversational agent implementations |
| `customer-support` | Customer service agent workflows |
| `rag` | Retrieval-Augmented Generation agents |
| `human_in_the_loop` | Human approval/override patterns |
| `plan-and-execute` | Planning and execution agents |
| `reflection` | Self-reflecting agents |
| `reflexion` | Reflexion pattern agents |
| `lats` | Language Agent Tree Search |
| `llm-compiler` | LLM compiler agents |
| `rewoo` | ReWOO (Reasoning WithOut Observation) |
| `self-discover` | Self-discovering agents |
| `extraction` | Data extraction agents |
| `code_assistant` | Code assistant agents |
| `tutorials` | Step-by-step tutorials |

### LangChain Ecosystem
- **Deep Agents**: Higher-level agent package with built-in planning, subagents, filesystem
- **Documentation**: https://docs.langchain.com
- **Total Agent Examples**: 50+ across all repos

---

## 2. CrewAI

### Official Examples Repository
- **URL**: https://github.com/crewAIInc/crewAI-examples
- **Stars**: 6k
- **Forks**: 2.1k
- **Status**: Archived (Apr 20, 2026) - migrated to main repo
- **CrewAI Cookbook**: https://github.com/crewAIInc/crewAI-cookbook

### Examples by Category

#### Crews (12+ examples)
- Game Builder Crew - Multi-agent team for Python game development
- Instagram Post - Social media content generation
- Landing Page Generator - Full landing page creation
- Marketing Strategy - Campaign development
- Screenplay Writer - Text to screenplay conversion
- Job Posting - Automated job descriptions
- Stock Analysis - Financial analysis with SEC data
- Trip Planner - Travel planning and itinerary
- Surprise Trip - Personalized surprise travel
- Industry Agents - Industry-specific implementations
- Match Profile to Positions - CV-to-job matching
- Meta Quest Knowledge - PDF-based Q&A system

#### Flows (6+ examples)
- Content Creator Flow - Multi-crew content generation
- Email Auto Responder Flow - Automated email processing
- Lead Score Flow - Lead qualification with human review
- Meeting Assistant Flow - Meeting notes with integrations
- Self Evaluation Loop Flow - Iterative content improvement
- Write a Book with Flows - Automated book writing

#### Notebooks
- Jupyter notebooks for interactive tutorials
- Flows 101 notebook

### Total Agent Examples: ~20+ complete applications

---

## 3. AutoGPT

### Main Repository
- **URL**: https://github.com/Significant-Gravitas/AutoGPT
- **Stars**: 170k+
- **License**: MIT (agent code) / Polyform Shield (platform)

### Example Agents (Built-in)
1. **Generate Viral Videos Agent** - Reads Reddit trending topics, creates short-form videos
2. **Social Media Quote Agent** - YouTube transcription, quote extraction, social media posting

### AutoGPT Forge
- **Purpose**: Framework for building custom AutoGPT agents
- **Features**: Built-in testing, benchmarking (agbenchmark), code execution

### AutoGPT Platform
- Newer platform for building, deploying, and managing agents
- Web UI for agent management

### Total Verified Agent Examples: 2+ built-in, extensible via Forge

---

## 4. Microsoft AutoGen / AG2

### AG2 Repository (formerly AutoGen)
- **URL**: https://github.com/ag2ai/ag2
- **Stars**: 40k+
- **Documentation**: https://docs.ag2.ai

### AutoGen Framework (Microsoft)
- **URL**: https://github.com/microsoft/autogen
- **Stars**: 40k+
- **Status**: In maintenance mode - Microsoft recommends Microsoft Agent Framework for new projects

### Example Types
- **Conversable Agent** - Basic two-agent collaboration (coder + reviewer)
- **Orchestrating Multiple Agents** - Swarms, group chats, nested chats
- **Human in the Loop** - User approval workflows
- **Tools** - External tool integration
- **Pattern Cookbook** - 9 group orchestration patterns
- **Structured Output** - Typed responses
- **RAG** - Retrieval Augmented Generation
- **Code Execution** - Running generated code safely

### AutoGen Studio
- Low-code UI for prototyping multi-agent workflows
- Gallery for community components
- **URL**: Built into microsoft/autogen repo

### Example Applications Repository
- Dedicated repo with wide range of use cases
- Jupyter notebooks collection

### Total Agent Examples: 15+ patterns + application examples

---

## 5. LlamaIndex

### Documentation & Examples
- **Agents Docs**: https://docs.llamaindex.ai/en/stable/understanding/agent/
- **Main Repo**: https://github.com/run-llama/llama_index
- **Stars**: 40k+

### Agent Types
1. **Function Calling Agents** - LLMs with function calling capabilities
2. **ReAct Agents** - Reasoning + Acting agents for complex tasks
3. **Advanced Custom Agents** - Complex methods for sophisticated workflows

### Multi-Agent Patterns
- **AgentWorkflow** - Linear "swarm" pattern with handoffs
- **Orchestrator Agent** - Sub-agents as tools pattern

### Example Use Cases
- Research agent (search + record notes)
- Write agent (markdown report generation)
- Review agent (feedback and critique)
- Report generation pipeline

### Total Agent Examples: 10+ documented patterns

---

## 6. Microsoft Semantic Kernel

### Main Repository
- **URL**: https://github.com/microsoft/semantic-kernel
- **Stars**: 25k+
- **Status**: Now "Microsoft Agent Framework" (MAF) at v1.0

### Agent Samples (100+ detailed samples)
- **Location**: `python/samples/concepts/` and `python/samples/getting_started/`

#### Agent Categories

| Category | Sample Count | Description |
|----------|-------------|-------------|
| Azure AI Agent | 20+ | Azure AI integration with search, code interpreter |
| Bedrock Agent | 9 | AWS Bedrock agent integration |
| Chat Completion Agent | 11 | OpenAI/Anthropic chat agents |
| Mixed Agent Group Chat | 6 | Multi-agent collaboration |
| OpenAI Assistant Agent | 20+ | OpenAI Assistant API integration |
| OpenAI Responses Agent | 10+ | OpenAI Responses API |

#### Sample Types
- Simple chat agents
- Agents with plugins/tools
- Multi-agent group chats
- Function calling agents
- Streaming agents
- Human-in-the-loop agents
- Agents with structured outputs
- RAG agents
- Process framework examples (Plan and Execute)

### Total Agent Examples: 80+ agent-specific samples

---

## 7. Haystack (deepset)

### Main Repository
- **URL**: https://github.com/deepset-ai/haystack
- **Stars**: 20k+

### Cookbook Repository
- **URL**: https://github.com/deepset-ai/haystack-cookbook
- **Stars**: 541
- **Notebooks**: 50+ total

### Agent-Focused Notebooks
| Notebook | Description |
|----------|-------------|
| `agent-breakpoints.ipynb` | Debugging agent execution |
| `agent_powered_retrieval.ipynb` | Agent-based retrieval |
| `agent_with_human_in_the_loop.ipynb` | Human approval workflows |
| `agentic_itinerary_planning_openstreetmap.ipynb` | Travel planning agent |
| `browser_agents.ipynb` | Web browser agents |
| `github_issue_resolver_agent.ipynb` | GitHub issue resolution |
| `github_pr_creator_agent.ipynb` | Pull request creation |
| `ai_sales_research_assistant.ipynb` | Sales research agent |
| `function_calling_with_OpenAIChatGenerator.ipynb` | Function calling |
| `feedback-analysis-agent-with-AzureAISearch.ipynb` | Feedback analysis |

### Total Agent Examples: 10+ agent-focused notebooks, 50+ total cookbook examples

---

## 8. OpenAI Assistants / Agents SDK

### Python SDK Repository
- **URL**: https://github.com/openai/openai-agents-python
- **Stars**: 27.1k
- **Examples Directory**: `examples/`

### Example Categories (15 directories)
| Category | Examples Count | Description |
|----------|---------------|-------------|
| `basic` | 10+ | Hello world, tools, streaming, lifecycle |
| `agent_patterns` | 8+ | Routing, parallel execution, guardrails, HITL |
| `customer_service` | 1 | Full airline customer service system (6 agents) |
| `financial_research_agent` | 1 | Financial data analysis agent |
| `handoffs` | 2 | Agent handoff patterns |
| `hosted_mcp` | 4 | Hosted MCP integration |
| `mcp` | 8+ | Model Context Protocol examples |
| `memory` | 12+ | Session storage (SQLite, Redis, MongoDB) |
| `model_providers` | 5+ | Non-OpenAI model integration |
| `realtime` | 3+ | Real-time voice agents |
| `reasoning_content` | 3+ | Reasoning content handling |
| `research_bot` | 1 | Deep research clone |
| `sandbox` | 4+ | Sandboxed agent execution |
| `tools` | 12+ | Web search, file search, code interpreter |
| `voice` | 3+ | Voice-enabled agents |

### Additional OpenAI Example Repos
- **Customer Service Demo**: https://github.com/openai/openai-cs-agents-demo (6 agents)
- **Voice Agent SDK Sample**: https://github.com/openai/openai-voice-agent-sdk-sample
- **Realtime Agents**: https://github.com/openai/openai-realtime-agents
- **OpenAI Agents JS**: https://github.com/openai/openai-agents-js (TypeScript examples)

### Total Agent Examples: 80+ across all example directories

---

## 9. Google ADK (Agent Development Kit)

### Agent Garden
- **Blog**: https://developers.googleblog.com/en/agent-garden-samples-for-learning-discovering-and-building/
- **One-click deployment** to Agent Engine

### Agent Types Demonstrated
1. **LlmAgent** - Open-ended tasks with natural language
2. **SequentialAgent** - Pipeline-style execution
3. **ParallelAgent** - Concurrent multi-source processing
4. **LoopAgent** - Iterative refinement with stop conditions
5. **Nested Agents (Agent-as-a-Tool)** - Hierarchical delegation

### Composition Patterns
- Sequential composition (document processing)
- Parallel composition (multi-source research)
- Iterative refinement (content quality improvement)

### Sample Agents
- Weather agent - Basic tool usage
- Data pipeline agent - Extract, clean, summarize
- Document processor agent - Text extraction, sentiment, summary
- Research agent - News + academic + social media parallel search
- Content refiner agent - Iterative quality improvement

### Total Agent Examples: 6+ composition patterns with full code

---

## 10. PydanticAI

### Official Repository
- **URL**: https://github.com/pydantic/pydantic-ai
- **Stars**: 10k+

### Community Examples Repository
- **URL**: https://github.com/vstorm-co/pydantic-ai-examples
- **Examples**: 8 learning-path tutorials

### Official Examples
| Example | Description |
|---------|-------------|
| Direct Model Requests | Basic LLM API calls |
| Temperature | Model parameter control |
| Reasoning Effort | GPT-5.2 reasoning depth |
| Basic Sentiment | Structured outputs with Pydantic |
| Dynamic Classification | Runtime schema generation |
| Bielik (Local Models) | Local model with Ollama |
| History Processor | Multi-turn conversations |
| OCR Parsing | Document processing with validation |

### Additional Example Repos
- **PydanticAI + Temporal**: https://github.com/pydantic/pydantic-ai-temporal-example (Slack dinner bot)
- **Invoice Processing**: https://github.com/stephenc222/example-pydantic-ai-multi-modal
- **Getting Started Tutorial**: https://github.com/ProjectProRepo/How-to-Build-an-AI-Agent-with-Pydantic-AI

### Total Agent Examples: 10+ across community and official repos

---

## 11. AG2 (formerly AutoGen)

### Main Repository
- **URL**: https://github.com/ag2ai/ag2
- **Stars**: 40k+
- **PyPI**: `pip install ag2[openai]`

### Example Applications
- **Dedicated examples repo**: Wide range of use cases
- **Jupyter Notebooks collection**: Interactive tutorials

### Agent Concepts Demonstrated
- **Conversable Agent** - Basic two-agent patterns (coder + reviewer)
- **Orchestrating Multiple Agents** - Teacher + lesson planner + reviewer
- **Human in the Loop** - Human validator in group chat
- **Tools** - Function registration and execution
- **Structured Output** - Typed responses
- **RAG** - Retrieval Augmented Generation
- **Code Execution** - Docker-based code running

### Pattern Cookbook
- 9 group orchestration patterns
- Swarm patterns
- Group chat patterns
- Nested chat patterns
- Sequential chat patterns

### Total Agent Examples: 15+ patterns + application repo

---

## 12. Smolagents (HuggingFace)

### Main Repository
- **URL**: https://github.com/huggingface/smolagents
- **Stars**: 27.8k
- **Examples Directory**: `examples/`

### Example Files (9+ examples)
| Example | Description |
|---------|-------------|
| `async_agent/` | Async agent patterns |
| `open_deep_research/` | Open deep research implementation |
| `plan_customization/` | Human-in-the-loop plan customization |
| `agent_from_any_llm.py` | Multi-provider LLM support |
| `gradio_ui.py` | Gradio web interface |
| `inspect_multiagent_run.py` | Multi-agent debugging |
| `multi_llm_agent.py` | Multiple LLM coordination |
| `multiple_tools.py` | Tool usage examples |
| `rag.py` | RAG implementation |
| `rag_using_chromadb.py` | ChromaDB RAG |
| `sandboxed_execution.py` | Secure code execution |
| `structured_output_tool.py` | Structured tool outputs |
| `text_to_sql.py` | SQL generation agent |

### Community Examples
- **samwit/smolagents_examples**: 9 examples covering CodeAgent, ToolCallingAgent, multi-agent, Gradio UI

### Total Agent Examples: 15+ across official and community repos

---

## Summary Table

| # | Framework | Primary Gallery URL | Est. Agent Examples | Type |
|---|-----------|--------------------|--------------------:|------|
| 1 | LangChain/LangGraph | github.com/langchain-ai/langgraph/tree/main/examples | 50+ | Official examples |
| 2 | CrewAI | github.com/crewAIInc/crewAI-examples | 20+ | Official repo (archived) |
| 3 | AutoGPT | github.com/Significant-Gravitas/AutoGPT | 2+ built-in | Platform examples |
| 4 | Microsoft AutoGen/AG2 | github.com/ag2ai/ag2 + github.com/microsoft/autogen | 15+ | Official + patterns |
| 5 | LlamaIndex | docs.llamaindex.ai + github examples | 10+ | Documentation examples |
| 6 | Semantic Kernel (MAF) | github.com/microsoft/semantic-kernel | 80+ | 100+ detailed samples |
| 7 | Haystack | github.com/deepset-ai/haystack-cookbook | 10+ agent-focused | 50+ total cookbook |
| 8 | OpenAI Agents SDK | github.com/openai/openai-agents-python/examples | 80+ | 15 example categories |
| 9 | Google ADK | developers.googleblog.com/agent-garden | 6+ patterns | Agent Garden samples |
| 10 | PydanticAI | github.com/pydantic/pydantic-ai | 10+ | Community + official |
| 11 | AG2 | github.com/ag2ai/ag2 | 15+ | Patterns + applications |
| 12 | Smolagents | github.com/huggingface/smolagents/examples | 15+ | Official + community |

---

## Key Findings

1. **Most Examples**: OpenAI Agents SDK (~80+) and Microsoft Semantic Kernel (~80+) have the most comprehensive agent example collections
2. **Best Organized**: Semantic Kernel has the most structured sample library with clear categorization
3. **Multi-Agent Focus**: LangGraph, CrewAI, AutoGen/AG2, and Smolagents specialize in multi-agent orchestration examples
4. **Official Galleries**: Google ADK (Agent Garden) and CrewAI have dedicated "gallery" concepts for discovering agents
5. **Community Ecosystem**: PydanticAI and Smolagents have strong community-contributed example collections
6. **Enterprise Ready**: Semantic Kernel (now Microsoft Agent Framework) and OpenAI Agents SDK lead in production-ready patterns
