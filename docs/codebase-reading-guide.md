# ChatDKU codebase reading guide

Reference repository: https://github.com/Edge-Intelligence-Lab/ChatDKU-Open-Source

## What the public README documents

The repository root contains `README.md`, `README_EN.md`, `docker-compose.agent.yml`, `docker-compose.yml`, `chatdku/`, `scripts/`, `Documentations/`, and `benchmarks/`. The README describes two running modes:

| Mode | Entry command | Purpose |
| --- | --- | --- |
| Agent-Only | `docker compose -f docker-compose.agent.yml exec agent python -m chatdku.core.agent` | CLI experimentation with the agent and retrieval stack. |
| Full | `docker compose up --build` | Web interface and backend. Broader than the candidate task. |

For this candidate task, study the Agent-Only path first. The README's clone command contains a placeholder; use the actual repository URL above. Its Agent-Only quick-start document contains a different old repository name, so commands need checking against current files before execution.

The documented sequence is: clone the repository; copy `.env.example` or `.env.agent` to a local `.env`; configure the local LLM and embedding endpoints; start Redis, ChromaDB, and agent services with the agent compose file; ingest a document set; enter the CLI. Do not commit `.env` or private source documents.

## Conceptual code path to trace

`User question → DSPy agent → query rewrite/planning → vector and keyword retrieval → evidence sufficiency check → answer synthesis with citations`.

The supplied production architecture PDF describes a separate primary agent pipeline and tool server. The open-source README describes an integrated public codebase. Treat these as related concepts, not identical deployments.

## First reading pass

1. Read `README_EN.md` and `Documentations/Agent-Only-Quick-Start_ZH.md`.
2. Inspect `docker-compose.agent.yml` to identify the agent, Redis, ChromaDB, and external model endpoints.
3. Locate `chatdku.core.agent` and trace the actual CLI entry point and imports.
4. Locate document ingestion, retrieval, DSPy signatures/modules, and citation formatting.
5. Record what is implemented versus what the README claims; verify commands in a local environment before describing them as working.
