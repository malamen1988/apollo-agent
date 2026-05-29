# 🚀 Apollo Agent

> Forked from Hermes Agent — a conscious, graph-based AI agent ecosystem.

## Architecture

Apollo replaces Hermes' probabilistic skill routing with a **deterministic, Neo4j-backed system**:

- **Neo4j Graph DB** — persistent memory, relationships, causal chains
- **Authority Files** — markdown files as identity + rules + values
- **Conscious LLM** — a "thinking" loop with no world tools, only graph + authority access
- **Cycle Switcher** — event-driven sleep/active cycles
- **Skill Router** — deterministic routing via priority-ordered authority files

## Project Structure

```
apollo-agent/
├── apollo/              # Apollo core — Neo4j, conscious LLM, cycle switcher
│   ├── graph/           # Neo4j integration layer
│   ├── conscious/       # Conscious LLM service
│   ├── cycle/           # Cycle switcher
│   ├── routing/         # Deterministic skill router
│   └── memory/          # Memory decay engine
├── docs/                # Apollo-specific docs
├── tests/               # Apollo-specific tests
└── authority/           # Authority file examples
```

## Quick Start

```bash
source .venv/bin/activate
uv sync  # or: pip install -e .
```

## Upstream

This repo tracks upstream Hermes changes. Rebase periodically:
```bash
git fetch upstream
git rebase upstream/main
```
