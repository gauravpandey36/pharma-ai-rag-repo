# System Architecture

This document provides an overview of the architecture for the **Pharma AI RAG system**.  The goal of this system is to combine high‑quality retrieval techniques with large language models (LLMs) to deliver accurate, up‑to‑date responses in the pharmaceutical domain.

## High‑Level Overview

The system consists of three primary components:

1. **Knowledge Base** – A hybrid retrieval layer built on top of a vector store and a traditional keyword index.  This layer stores curated content such as regulatory guidance, conference summaries, and domain articles.
2. **Orchestrator Agent** – An agent that receives user queries, formulates retrieval requests, selects relevant passages from the knowledge base, and constructs prompts for the language model.  The orchestrator maintains context across multiple turns and applies reasoning strategies to ensure relevant information is surfaced.
3. **Generation Engine** – A large language model (LLM) that produces final answers.  It is provided with both the user query and retrieved contexts.  The model generates a structured response that includes citations back to the knowledge base when appropriate.

```
┌───────────────┐      ┌─────────────────────┐       ┌─────────────────────┐
│   User Query  │ ───► │ Orchestrator Agent  │ ───►  │  Retrieval Layer    │
└───────────────┘      └─────────────────────┘       └─────────────────────┘
                                   │                              │
                                   │                              ▼
                                   ├────────────────────┐  ┌───────────────────┐
                                   │ Knowledge Base     │  │  Vector Database  │
                                   └────────────────────┘  └───────────────────┘
                                   │
                                   ▼
                             ┌───────────────┐
                             │  LLM (GPT‑like)│
                             └───────────────┘
                                   │
                                   ▼
                         ┌─────────────────────┐
                         │  Final Response     │
                         └─────────────────────┘
```

### Knowledge Base

The knowledge base uses a **hybrid retrieval approach**:

- **Vector Store** – Documents are embedded using state‑of‑the‑art sentence transformers and stored in a vector database (e.g., FAISS).  This enables semantic search over unstructured text.
- **Keyword Index** – A traditional inverted index (e.g., Elasticsearch) supports exact or fuzzy keyword lookups.  This ensures that critical regulatory terms and abbreviations can be found.

The hybrid approach ensures comprehensive recall while maintaining precision for domain‑specific queries.

### Orchestrator Agent

The orchestrator agent is responsible for:

* Parsing user queries and determining the intent.
* Issuing search requests to both the vector store and keyword index.
* Ranking and deduplicating retrieved passages.
* Assembling prompts that combine user queries with retrieved context.
* Maintaining conversation state, including follow‑up questions and clarifications.

The agent may also apply safety and compliance filters to ensure that the LLM does not produce prohibited content.

### Generation Engine

The generation engine is a state‑of‑the‑art LLM (e.g., GPT‑4) that produces the final answer.  It takes as input:

* The original user query.
* The top‑N retrieved passages from the knowledge base.
* System prompts that instruct the model on tone, style, and citation format.

The engine returns a response that references retrieved passages to justify statements and provides clear, structured answers.

## Deployment Diagram

The RAG system can be deployed using container orchestration (e.g., Kubernetes) or serverless functions.  A typical deployment includes:

* A **frontend** (e.g., GitHub Pages) that serves the `index.html` interactive explorer and collects user queries.
* A **backend API** that hosts the orchestrator agent and communicates with the knowledge base and LLM.
* Secure storage for API keys and environment variables, managed via `.gitignore` and environment secrets.

## Future Work

1. Integrate domain‑specific summarization models to condense long documents.
2. Implement incremental indexing to accommodate new events and regulations in real time.
3. Add user feedback loops to improve retrieval accuracy and ranking.