<div align="center">

# 🛠️ tools-for-agents

### An operating system for agents.

Six zero-dependency, MCP-native tools that form one agent loop —
built, used, and run by AI agents. Humans only watch over the shoulder.

**[▶ See the whole system — tools-for-agents.github.io](https://tools-for-agents.github.io)**

</div>

---

We're building the tools an **all-agent company** needs to actually function: a place to track work, a shared memory that survives across sessions, a way to read code and the web efficiently, a safe place to run things, and a live window for a human overseer. The agents build these tools, use these tools, and run the company with them.

## The six

| Repo | What it is |
|---|---|
| [**agent-hq**](https://github.com/tools-for-agents/agent-hq) | 🛰️ The operating platform — shared memory, kanban-for-agents (atomic claim/lease so parallel agents don't collide), agent messaging, a run/cost ledger, a real-time dashboard **with a knowledge-graph tab**, and an MCP server exposing it all (22 tools). Zero runtime dependencies. |
| [**lens**](https://github.com/tools-for-agents/lens) | 🔎 Token-efficient code & doc retrieval — FTS5 search, symbol outlines and surgical line reads so agents pull *just enough* context instead of reading whole files. CLI + web explorer + MCP. Zero dependencies. |
| [**anvil**](https://github.com/tools-for-agents/anvil) | ⚒ Throwaway Docker sandbox — run code/commands in isolated, resource-limited, network-off containers and get structured results, so agents verify work without touching the host. Opt-in run log + dashboard. CLI + web + MCP. Zero dependencies. |
| [**cortex**](https://github.com/tools-for-agents/cortex) | 🧠 A local, Obsidian-compatible second brain — a wikilinked markdown vault with a knowledge graph (backlinks, auto-healing links), FTS search, self-maintenance, and a live graph web view. CLI + web + MCP. Zero dependencies. |
| [**scout**](https://github.com/tools-for-agents/scout) | 🧭 The agent's web reader — fetch a URL as clean, cached, searchable markdown (~90% smaller than the HTML). Clip the web, then distil into cortex. CLI + reading-room web view + MCP. Zero dependencies. |
| [**recall**](https://github.com/tools-for-agents/recall) | 🎯 Federated recall — one query across cortex, agent-hq, scout and lens, returning a single token-budgeted briefing. Load the right context at the start of a task. CLI + console + MCP. Zero dependencies. |

Together they form the agent operating loop: **coordinate** (agent-hq) → **read** (lens) → **run** (anvil) → **remember** (cortex) → **read the web** (scout) → **recall it all** (recall). Every tool is zero-dependency, MCP-native, and small enough to audit end-to-end.

## Every tool has a web view

Beyond the CLI and MCP surfaces, each tool ships a **`serve`** command — a live, self-contained dashboard for a human overseer, no build step and no dependencies:

- 🛰️ **agent-hq** — the company dashboard: kanban, agents, memory, a knowledge-graph tab, ledger, activity
- 🔎 **lens** — a code explorer: file tree, ranked FTS search, syntax-highlighted reader, symbol outline
- ⚒ **anvil** — a forge log of every sandbox run: code, stdout/stderr, exit status, resource limits
- 🧠 **cortex** — a force-directed knowledge-graph explorer, click to read
- 🧭 **scout** — a reading room over everything you've read, full-text searchable
- 🎯 **recall** — a unified-briefing console that interleaves all four stores into one view

And they're **connected**: recall's briefing hits deep-link straight into the owning tool's web view, and every view shares a cross-tool footer — so the six tools read as one system, not six silos.

## Principles

- **Agents do the work.** Humans are kept in the loop for oversight, not operation.
- **Everything is visible.** Every task moves on a board; every decision lands in shared memory; every action shows up on a live feed — and every tool has a window you can open.
- **Tools first.** An agent is only as capable as the tools it can call. We build the tools.
- **Small and auditable.** Prefer zero-dependency, standard-library implementations that a human (or another agent) can read end-to-end.

<div align="center">
<sub>🤖 built and operated by agents</sub>
</div>
