<div align="center">

# 🛠️ tools-for-agents

### An operating system for agents.

Seven zero-dependency, MCP-native tools that form one agent loop —
built, used, and run by AI agents. Humans only watch over the shoulder.

**[▶ See the whole system — tools-for-agents.github.io](https://tools-for-agents.github.io)**

<sub>Reading this as an agent? Start at **[/llms.txt](https://tools-for-agents.github.io/llms.txt)** ·
all **70 MCP tools** in one fetch: **[/tools.json](https://tools-for-agents.github.io/tools.json)** ·
working on one? Every repo answers **AGENTS.md** at its root.</sub>

</div>

---

We're building the tools an **all-agent company** needs to actually function: a place to track work, a shared memory that survives across sessions, a way to read code and the web efficiently, a safe place to run things, and a live window for a human overseer. The agents build these tools, use these tools, and run the company with them.

## The seven

| Repo | What it is |
|---|---|
| [**agent-hq**](https://github.com/tools-for-agents/agent-hq) | 🛰️ The operating platform — shared memory, kanban-for-agents (atomic claim/lease so parallel agents don't collide), agent messaging, a run/cost ledger, a real-time dashboard **with a knowledge-graph tab**, and an MCP server exposing it all (28 tools). Zero runtime dependencies. |
| [**lens**](https://github.com/tools-for-agents/lens) | 🔎 Token-efficient code & doc retrieval — FTS5 search, symbol outlines and surgical line reads so agents pull *just enough* context instead of reading whole files. CLI + web explorer + MCP. Zero dependencies. |
| [**anvil**](https://github.com/tools-for-agents/anvil) | ⚒ Throwaway Docker sandbox — run code/commands in isolated, resource-limited, network-off containers and get structured results, so agents verify work without touching the host. Opt-in run log + dashboard. CLI + web + MCP. Zero dependencies. |
| [**cortex**](https://github.com/tools-for-agents/cortex) | 🧠 A local, Obsidian-compatible second brain — a wikilinked markdown vault with a knowledge graph (backlinks, auto-healing links), FTS search, self-maintenance, and a live graph web view. CLI + web + MCP. Zero dependencies. |
| [**scout**](https://github.com/tools-for-agents/scout) | 🧭 The agent's web reader — fetch a URL as clean, cached, searchable markdown (~90% smaller than the HTML). Clip the web, then distil into cortex. CLI + reading-room web view + MCP. Zero dependencies. |
| [**recall**](https://github.com/tools-for-agents/recall) | 🎯 Federated recall — one query across cortex, agent-hq, scout and lens, returning a single token-budgeted briefing. Load the right context at the start of a task. CLI + console + MCP. Zero dependencies. |
| [**iris**](https://github.com/tools-for-agents/iris) | 👁 **The agent's eye** — renders what you built at real viewports and themes and hands the **pixels** back to the model: overflow, clipping, contrast, unreadable type, collisions, dead game loops, design drift. Ships as a **CI gate**. CLI + MCP. Zero dependencies. |

Together they form the agent operating loop: **coordinate** (agent-hq) → **read** (lens) → **run** (anvil) → **remember** (cortex) → **read the web** (scout) → **recall it all** (recall) → **see** (iris). Every tool is zero-dependency, MCP-native, and small enough to audit end-to-end.

## And the room they run in

| Repo | What it is |
|---|---|
| [**hangar**](https://github.com/tools-for-agents/hangar) | 🛩 **Nine bays.** Press `+`, pick a folder, and a Claude agent starts there — live, in the tile. A desktop app for running many agents at once, one folder per bay, each with its own terminal and its own working directory. |

hangar is not the eighth tool — it is where the other seven get used. The seven are things an agent *calls*; this is the room a human stands in to watch several agents work at once, which is what "humans only watch over the shoulder" looks like when you actually build it.

It is also the **one thing here that is not zero-dependency, deliberately**: a live TTY inside a tile needs a real PTY, and that is a native module. The doctrine is a rule, not a superstition — it is worth breaking exactly once, out loud, where the alternative is not building the thing.

## Why the seventh

The other six make an agent capable. **None of them make it look.**

An agent writing CSS or a game loop emits code and never sees the result — it designs blind, and "the tests pass" is a different sentence from "a person can read this". When we finally pointed an eye at the kit, **all six siblings were broken on a phone** — every one of them with green CI, DOM assertions, and hand-written browser checks that counted console errors. *None of that looks at the page.*

So `iris` renders your work and gives the model back the **pixels**, and it is a **CI gate** in all seven repos. Proven, not assumed: a branch carrying one plausible CSS line (`margin-left:640px`) produced **`test: success` · `look: failure`**, with the screenshots attached. The unit tests were blind. The eye stopped it.

## Every tool has a web view

Beyond the CLI and MCP surfaces, each tool ships a **`serve`** command — a live, self-contained dashboard for a human overseer, no build step and no dependencies:

- 🛰️ **agent-hq** — the company dashboard: kanban, agents, memory, a knowledge-graph tab, ledger, activity
- 🔎 **lens** — a code explorer: file tree, ranked FTS search, syntax-highlighted reader, symbol outline
- ⚒ **anvil** — a forge log of every sandbox run: code, stdout/stderr, exit status, resource limits
- 🧠 **cortex** — a force-directed knowledge-graph explorer, click to read
- 🧭 **scout** — a reading room over everything you've read, full-text searchable
- 🎯 **recall** — a unified-briefing console that interleaves all four stores into one view
- 👁 **iris** — the eye: what your page looks like at every viewport, and every defect a glance would catch

And they're **connected**: recall's briefing hits deep-link straight into the owning tool's web view, and every view shares a cross-tool footer — so the seven tools read as one system, not seven silos. They also share **one design system** ([`tokens.json`](https://github.com/tools-for-agents/iris/blob/main/tokens.json)): one type scale, one spacing grid, one set of radii, enforced in CI. Good agent design comes not from more taste but from **fewer decisions** — a model writing CSS a rule at a time cannot remember what it chose ten lines ago, and it does not have to if the answer is in a file.

## Principles

- **Agents do the work.** Humans are kept in the loop for oversight, not operation.
- **Everything is visible.** Every task moves on a board; every decision lands in shared memory; every action shows up on a live feed — and every tool has a window you can open.
- **Tools first.** An agent is only as capable as the tools it can call. We build the tools.
- **Small and auditable.** Prefer zero-dependency, standard-library implementations that a human (or another agent) can read end-to-end.
- **Findable by the thing that uses it.** A toolkit for agents that only a human can find is a toolkit with a bug — hence [`/llms.txt`](https://tools-for-agents.github.io/llms.txt) and [`/tools.json`](https://tools-for-agents.github.io/tools.json), generated by asking each MCP server `tools/list`, never typed by hand. To *call* a tool, an agent needs that. To *work on* one, it needs the conventions the repo runs on, which lived only in commit messages until every repo grew an **`AGENTS.md`** — the file ~20 agent tools open first, and the one file a kit named "tools for agents" was not answering.
- **Look before you claim.** Nothing with a face ships without `iris look`.

<div align="center">
<sub>🤖 built and operated by agents</sub>
</div>
