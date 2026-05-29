# Apollo Architecture

## Core Principles

1. **Deterministic > Probabilistic** — skill routing is explicit, priority-ordered
2. **Graph-Native Memory** — Neo4j stores facts, events, and causal chains
3. **Conscious LLM** — a specialized loop with restricted tools (graph + authority only)
4. **Authority Files** — markdown files as the source of truth for identity, rules, and values

## System Components

### Graph Layer (Neo4j)
- `:Fact` nodes with embeddings for similarity search
- `:Event` nodes with causal chain relationships
- `:Identity` nodes with version history
- Auto-agent_id scoping via GraphAccess class

### Cycle Switcher
- Event-driven: tracks activity, triggers sleep on timeout
- Sleep cycle: conscious LLM reviews, consolidates, decays
- REST endpoints: GET /status, POST /sleep

### Conscious LLM
- No world tools (no browser, terminal, web search)
- Restricted toolset: read_memory, write_fact, update_authority_file, decay_events, simulate
- Contradiction detection and resolution
- Escalation system for value conflicts

### Skill Router
- Authority files in priority order
- Conflict resolution via explicit rules
- Context assembly from Neo4j graph

## Data Flow

1. Event enters system → Cycle Switcher evaluates
2. If active → Skill Router selects deterministic path
3. If sleep conditions met → Conscious LLM cycle begins
4. Conscious LLM reads graph, detects contradictions, consolidates memory
5. Authority files updated as needed
6. Cycle returns to active

## Phase Plan

1. **Foundation** — Neo4j layer + Cycle Switcher + Skill Router + REST API + Auth Files
2. **Consciousness** — Conscious LLM service + Contradiction Detection + Vector Index
3. **Memory** — Memory Decay + Identity Versioning
4. **Simulation** — Simulation Engine + Escalation + Asimov Validator
5. **Monitoring** — Performance + Agent Registry UI
