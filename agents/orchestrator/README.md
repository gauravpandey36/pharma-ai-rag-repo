# Orchestrator Agent

This directory contains the core orchestrator agent responsible for coordinating retrieval of content and generating responses. The orchestrator handles high-level tasks such as:

- Accepting user queries and splitting them into sub-tasks.
- Invoking domain-specific models or tools to retrieve relevant documents.
- Managing prompts and context to ensure responses are coherent.
- Logging interactions for debugging and auditability.

## Running the orchestrator

1. Ensure that environment variables for any API keys or endpoints are set (see `.env.example`).
2. Install dependencies with pip or conda.
3. Run `python orchestrator.py` to start the orchestration service.

## Writing new agents or tools

New agents should follow the existing modular design and adhere to documented interfaces. Consider using the Retrieval Augmented Generation (RAG) pattern and GAMP 5 guidelines for development and validation.
