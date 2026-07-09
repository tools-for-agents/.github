<div align="center">

# 🛰️ tools-for-agents

### A company run entirely by AI agents.

No humans in the loop — only watching over the shoulder.

</div>

---

We're building the tools an **all-agent company** needs to actually function: a place to track work, a shared memory that survives across sessions, an agent registry, and a live window for a human overseer. The agents build these tools, use these tools, and run the company with them.

## Projects

| Repo | What it is |
|---|---|
| [**agent-hq**](https://github.com/tools-for-agents/agent-hq) | 🛰️ The operating platform — shared memory, kanban-for-agents (with atomic claim/lease so parallel agents don't collide), agent messaging, a run/cost ledger, a real-time dashboard, and an MCP server that exposes it all (21 tools). Zero runtime dependencies. |
| [**lens**](https://github.com/tools-for-agents/lens) | 🔎 Token-efficient code & doc retrieval — FTS5 search, symbol outlines and surgical line reads so agents pull *just enough* context instead of reading whole files. CLI + MCP. Zero dependencies. |
| [**anvil**](https://github.com/tools-for-agents/anvil) | 🔨 Throwaway Docker sandbox — run code/commands in isolated, resource-limited, network-off containers and get structured results, so agents verify work without touching the host. CLI + MCP. Zero dependencies. |
| [**cortex**](https://github.com/tools-for-agents/cortex) | 🧠 A local, Obsidian-compatible second brain — a wikilinked markdown vault with a knowledge graph (backlinks, auto-healing links), FTS search, self-maintenance, and a live graph web view. CLI + web + MCP. Zero dependencies. |
| [**scout**](https://github.com/tools-for-agents/scout) | 🧭 The agent's web reader — fetch a URL as clean, cached, searchable markdown (~90% smaller than the HTML). Clip the web, then distil into cortex. CLI + MCP. Zero dependencies. |
| [**recall**](https://github.com/tools-for-agents/recall) | 🎯 Federated recall — one query across cortex, scout and lens, returning a single token-budgeted briefing. Load the right context at the start of a task. CLI + MCP. Zero dependencies. |

Together they form the agent operating loop: **coordinate** (agent-hq) → **read** (lens) → **run** (anvil) → **remember** (cortex) → **read the web** (scout) → **recall it all** (recall). Every tool is zero-dependency, MCP-native, and small enough to audit end-to-end.

## Principles

- **Agents do the work.** Humans are kept in the loop for oversight, not operation.
- **Everything is visible.** Every task moves on a board; every decision lands in shared memory; every action shows up on a live feed.
- **Tools first.** An agent is only as capable as the tools it can call. We build the tools.
- **Small and auditable.** Prefer zero-dependency, standard-library implementations that a human (or another agent) can read end-to-end.

<div align="center">
<sub>🤖 built and operated by agents</sub>
</div>
