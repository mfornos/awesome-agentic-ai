# Awesome Agentic AI

> A curated, opinionated list of principles, standards, and technologies for building agentic AI systems.

**Agentic AI** refers to systems built around goal-directed agents rather than single-shot generation. These systems typically involve agents that can:

- Form and revise plans over time
- Invoke external actions (tools, APIs)
- Maintain and reason over internal state and memory
- Interact with other agents or humans
- Execute multi-step processes with observable outcomes

This list focuses on agent-centric abstractions and infrastructure, spanning everything from low-level model formats to high-level control and observability primitives.

## Contents

- [Principles](#principles)
- [Platforms & Frameworks](#platforms--frameworks)
- [AI Infrastructure & Compute](#ai-infrastructure--compute)
- [Standards & Specifications](#standards--specifications)
- [Large Language Models](#large-language-models)
- [State, Retrieval & Coordination Infrastructure](#state-retrieval--coordination-infrastructure)
- [Evaluation, Observability & Safety](#evaluation-observability--safety)
- [Theory](#theory)
- [Design](#design)

## Principles

Foundational principles for building robust, auditable, and autonomous agentic systems:

**Goal-Directed Control Loops**  
Agents operate in continuous perceive-reason-act cycles with built-in monitoring, failure detection, and corrective feedback, rather than one-shot generation.

**Tool-First Reasoning**  
External tools, APIs, and executables are first-class components of reasoning, not post-processing steps.

**Explicit, Versioned State**  
Plans, memory, and internal representations are structured, observable, and versioned to support durability, replay, and auditing.

**Composable & Modular Architecture**  
Complex behavior emerges from coordinating specialized agents, skills, and workflows, not monolithic prompt chains.

**Traceable & Evaluatable Behavior**  
All actions and decisions are logged, reproducible, and measurable to enable regression testing, auditing, and optimization.

**Safety & Constraint Awareness**  
Agents operate within explicit safety, correctness, and resource constraints that bound autonomy and prevent catastrophic behavior.

## Platforms & Frameworks

End-to-end stacks and core frameworks for agentic systems.

### Self-hosted Agent Frameworks

> You run the full agent runtime yourself. No managed orchestration backend.

- [Akka](https://akka.io/) - Actor-based platform for building distributed, fault-tolerant agent systems. Strong fit for long-running, concurrent, and highly reliable agents. Languages: Scala, Java.

- [Dspy](https://github.com/stanfordnlp/dspy) - Declarative framework for building modular AI software. Language: Python.

- [Mastra](https://mastra.ai/) - TypeScript-first framework for building agentic applications with explicit workflows, memory, evaluations, and tool integration.  Language: TypeScript.

- [Pydantic](https://ai.pydantic.dev/) - Python agent framework designed to help you quickly, confidently, and painlessly build production grade applications and workflows with Generative AI. Language: Python.

- [Rig](https://github.com/0xPlaygrounds/rig) - Rust-first framework for building LLM-powered agents with strong typing, modular tools, and composable workflows. Emphasizes performance, safety, and production-grade systems. Language: Rust.

- [smolagents](https://github.com/huggingface/smolagents) - Minimal, lightweight framework for building simple and transparent LLM agents with a strong emphasis on readability, hackability, and low abstraction overhead. Designed for learning, prototyping, and small production systems. Language: Python.

- [Volt Agent](https://github.com/VoltAgent/voltagent) - AI agent platform built on an open-source TypeScript agent framework. Language: TypeScript.

### Cloud-native Agent Platforms & Managed Stacks

> You run agent code locally or in your cloud, but rely on a managed agent runtime / orchestration backend.

- [AWS Bedrock Agents](https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html) - Managed service for building, orchestrating, and operating AI agents tightly integrated with AWS services and Bedrock models. Language: JSON / SDK-driven (Python, Java, etc). Deployment: AWS-managed service.

- [Camel](https://github.com/camel-ai/camel) - LLM-powered multi-agent framework enabling agents to play roles, collaborate, and coordinate tasks in complex workflows. Ideal for experimentation with multi-agent interaction patterns. Language: Python. Deployment: Local / Cloud / Containerizable.

- [Google Agent Development Kit (ADK)](https://google.github.io/adk-docs/) - An open-source, code-first toolkit for defining agents, tools, workflows, and multi-agent systems with built-in debugging, execution tracing, and extensibility. Designed to integrate with Vertex AI Agent Engine while remaining model-agnostic. Languages: Python, TypeScript, Go, Java. Deployment: Local / Your infrastructure + Vertex AI Agent Engine.

- [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) - A framework for building, orchestrating and deploying AI agents and multi-agent workflows. Languages: Python, C# (.NET). Deployment: Local / Azure-hosted + Azure AI Agent Service.

- [OpenAI Agents SDK / AgentKit](https://platform.openai.com/docs/guides/agents-sdk) - OpenAI's SDK and platform for building, orchestrating, and deploying agentic workflows with structured tool integration, observability, guardrails, and evaluation features on top of the Responses API. Languages: Python, TypeScript, Go. Deployment: Local / Your infrastructure + OpenAI-managed backend.


## AI Infrastructure & Compute

Platforms providing compute, GPU resources, and isolation for running AI workloads and agents at scale. Not specific agent SDKs, but critical for production deployments.

- [Akash](https://akash.network/) - Decentralized cloud platform for deploying and managing containerized applications.
- [AWS EC2 / Bedrock + GPU](https://aws.amazon.com/bedrock/) - Cloud compute infrastructure for AI workloads with GPU acceleration, networking isolation, and integration with other AWS services.
- [Blaxel](https://blaxel.ai/)** - Infrastructure platform that gives agents sandboxed compute environments to run AI code, background tasks and tool calls.
- [Daytona](https://www.daytona.io/) - Secure, scalable execution infrastructure and runtime for agentic workflows and AI‑generated code.
- [E2B](https://github.com/e2b-dev/E2B) - Open-source runtime infrastructure for AI agents and apps, providing secure, isolated cloud sandboxes where agents can execute real code, use real tools, access files and networks, and perform long-running tasks.
- [Google Cloud AI + Vertex AI](https://cloud.google.com/vertex-ai) - Managed AI compute infrastructure and orchestration for ML workloads, including GPUs/TPUs, secure isolation, and scaling.
- [Modal](https://modal.com/) - Managed AI compute infrastructure for running AI workloads at scale, with GPU acceleration, networking isolation, and integration with other services.
- [Nebius](https://nebius.com/) - AI-native cloud platform with high-performance GPU clusters, managed infrastructure, observability, and deployment tools. Ideal for scaling agentic systems or large AI workloads in production.

## Standards & Specifications

Protocols and conventions enabling interoperability.

- [Agent2Agent Protocol (A2A)](https://github.com/a2aproject/A2A) - An open protocol enabling communication and interoperability between opaque agentic applications.
- [Gymnasium](https://gymnasium.farama.org/) - An API standard for single-agent reinforcement learning environments, with popular reference environments and related utilities.
- [Model Context Protocol (MCP)](https://github.com/awesome-agentic-ai/mcp) - An open-source standard for connecting AI applications to external systems.

### Open Economic & Micropayment Standards

- [x402 Protocol](https://docs.cdp.coinbase.com/x402/docs/welcome) - An experimental open payment protocol that repurposes the dormant HTTP 402 status code to enable autonomous, on‑chain micropayments for APIs, services, and digital resources.

## Large Language Models

### Inference & Serving

- [Ollama](https://ollama.com/) - Lightweight, open-source LLM server for local or networked model serving.
- [llama.cpp](https://github.com/ggml-org/llama.cpp) - Portable LLM inference in C/C++ used for efficient local inference.

### Model Formats

- [GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md) - Efficient, extensible binary format used with `llama.cpp` runtimes.
- [ONNX](https://onnx.ai/) - Open standard for cross-runtime ML model representation.
- [SafeTensors](https://github.com/huggingface/safetensors) - Safe, fast tensor serialization standard.

### Fine-tuning

- [Axolotl](https://github.com/axolotl-ai-cloud/axolotl) - A free and open-source LLM fine-tuning framework.  
- [LlamaFactory](https://github.com/hiyouga/LlamaFactory) - Meta-framework for efficient adaptation (LoRA, QLoRA).  
- [PEFT](https://github.com/huggingface/peft) - Parameter-efficient fine-tuning methods.  
- [TRL](https://github.com/huggingface/trl) - Tools for RLHF and other preference-based optimization.  
- [Unsloth](https://github.com/unslothai/unsloth) - Fast LoRA-style fine-tuning stack.

### Simulation Environments (RL)

- [OpenEnv](https://github.com/openai/openenv) - Open, flexible multi-agent RL environment.

## State, Retrieval & Coordination Infrastructure

### Semantic Retrieval

- [LanceDB](https://lancedb.github.io/lancedb/) - Arrow-native versioned vector store suited for replay and dataset management.
- [LlamaIndex](https://www.llamaindex.ai/llamaindex) - Framework for indexing and querying structured and unstructured data for LLMs. Often used as the semantic memory layer in agentic systems.
- [Milvus](https://github.com/milvus-io/milvus) - High-performance, cloud-native vector database built for scalable vector ANN search.
- [pgvector](https://github.com/pgvector/pgvector) - Embeddings within PostgreSQL for transactional, schema-backed vectors.
- [Qdrant](https://qdrant.tech/) - Production-ready vector DB with payload support.
- [Weaviate](https://github.com/weaviate/weaviate) - Open-source vector database that stores both objects and vectors, allowing for the combination of vector search with structured filtering with the fault tolerance and scalability of a cloud-native database.

### Workflow & Temporal Control

- [Temporal](https://temporal.io/) - Durable workflow engine for orchestrating long-running agent processes.

## Evaluation, Observability & Safety

Robust agentic systems require continuous evaluation, traceable behavior, and enforced safety constraints. These aspects are inseparable: observability enables evaluation, which enables safe autonomous operation.

### Key Capabilities

**Tracing & Observability**  
Log all decisions, tool calls, and state changes. Enable replay and auditing for debugging and regression testing.

**Behavioral Evaluation**  
Test agent workflows, plans, and tool usage against task-specific metrics or rules. Include safety and constraint checks.

**Replay & Regression**  
Deterministically replay historical agent runs to detect regressions or unintended behavior.

**Automated Judging & Constraint Enforcement**  
Scale evaluations with rule-based or model-as-judge scoring. Enforce safety, cost, and correctness boundaries programmatically.

**Sandboxing & Access Control**  
Agents should execute external actions (code, APIs, system operations) in controlled, permissioned environments. Apply least-privilege access, secrets management, and failure containment.

**Jailbreak & Prompt Injection Mitigation**  
Protect against malicious inputs via model alignment, prompt filtering, or human-in-the-loop supervision.

### Evaluation & Observability

- [LangSmith](https://www.langchain.com/langsmith) - End-to-end tracing, dataset management, replay, and audit logging.
- [Maxim](https://maxim.ai/) - End-to-end evaluation and observability platform.
- [OpenAI Evals](https://github.com/openai/evals) - Behavioral testing framework for multi-step workflows, including safety checks.
- [Promptfoo](https://github.com/promptfoo/promptfoo) - Compare prompts, models, and configurations with reproducible tests.
- [Ragas](https://github.com/explodinggradients/ragas) - Evaluation toolkit for retrieval-augmented and multi-step agent behavior.


## Theory

Foundational research defining when agentic systems are appropriate and the core safety and autonomy principles that govern them.

- [STRIDE: A Systematic Framework for AI Modality Selection](https://arxiv.org/abs/2512.02228) - A research framework that helps decide when to use agentic systems versus simple LLM calls or guided assistants, emphasizing dynamism, planning, and task suitability <small>🔸PDF</small>.

- [Toward Safe and Responsible AI Agents (Three-Pillar Model)](https://arxiv.org/abs/2601.06223) - A recent academic framework emphasizing transparency, accountability, and trustworthiness for responsible autonomous agents <small>🔸PDF</small>.

## Design

Architectural principles and patterns for structuring agentic systems and coordinating planning, tools, memory, and multiple agents.

- [Agentic AI Patterns](https://agentic-patterns.com/) - Catalog of architectural and workflow patterns for planning loops, tool orchestration, memory, and multi-agent coordination.
