# Pharma AI RAG Repository

This repository serves as a demonstration of a Retrieval‑Augmented Generation (RAG) system for the pharmaceutical domain.  It contains code, documentation, and a live GitHub Pages site that showcases how an AI assistant can surface relevant conference and regulatory events for pharma professionals.

## Contents

| File/Directory | Purpose |
| -------------- | ------- |
| `ARCHITECTURE.md` | Detailed system design and architecture of the RAG pipeline. |
| `VALIDATION_APPROACH.md` | Documentation on how the system aligns with GAMP 5 and CSV validation expectations. |
| `ROADMAP.md` | Phase‑by‑phase progress tracker for ongoing development. |
| `index.html` | Live showcase site served via GitHub Pages.  It contains an interactive explorer of global pharma events. |
| `agents/orchestrator/` | Contains the orchestrator agent responsible for coordinating retrieval and generation. |
| `knowledge_base/` | Contains documentation for the hybrid retrieval mechanism and knowledge base. |
| `.gitignore` | Protects sensitive environment and API key files from being committed. |

## Live Demo

The `index.html` file in this repository is published via [GitHub Pages](https://pages.github.com/) and is accessible at:

```
https://gauravpandey36.github.io/pharma-ai-rag-repo/
```

This page provides an interactive interface for exploring hundreds of pharmaceutical events across regions, departments, and other filters.

## Usage

1. Clone or fork this repository.
2. Follow the instructions in `ARCHITECTURE.md` to understand how the RAG system is designed.
3. Review `VALIDATION_APPROACH.md` for guidance on validation and compliance.
4. To contribute, submit a pull request with your proposed changes and ensure you update the relevant documents.

## License

This project is licensed under the MIT License.