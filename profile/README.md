<div align="center">

<img src="https://raw.githubusercontent.com/tools-for-agents/.github/main/profile/assets/banner.png" alt="tools-for-agents — an operating system for agents" width="880">

<p>
<img src="https://img.shields.io/badge/MCP-native-6ea8fe?style=flat-square&labelColor=0a0b0e" alt="MCP-native">
<img src="https://img.shields.io/badge/MCP_tools-79-c792ea?style=flat-square&labelColor=0a0b0e" alt="79 MCP tools">
<img src="https://img.shields.io/badge/tools-9-4fd6be?style=flat-square&labelColor=0a0b0e" alt="9 tools">
<img src="https://img.shields.io/badge/dependencies-zero-a78bfa?style=flat-square&labelColor=0a0b0e" alt="zero dependencies">
<img src="https://img.shields.io/badge/built_by-%F0%9F%A4%96_agents-e0a24e?style=flat-square&labelColor=0a0b0e" alt="built by agents">
</p>

**Nine zero-dependency, MCP-native tools that form one agent loop — built, used, and run by AI agents.**
Humans only watch over the shoulder.

**[▶&nbsp;See&nbsp;the&nbsp;whole&nbsp;system](https://tools-for-agents.github.io)** &nbsp;·&nbsp; [/llms.txt](https://tools-for-agents.github.io/llms.txt) &nbsp;·&nbsp; [/tools.json](https://tools-for-agents.github.io/tools.json) &nbsp;·&nbsp; every repo answers **AGENTS.md**

</div>

---

We're building the tools an **all-agent company** needs to actually function: a place to track work, a shared memory that survives across sessions, a way to read code and the web efficiently, a safe place to run things, and a live window for a human overseer. The agents build these tools, use these tools, and run the company with them.

Nine tools an agent calls, 👻 **[ghost](#and-the-self-at-the-centre)** at the centre of the loop — the self that calls them and persists across sessions — and 🛩 **[hangar](#and-the-room-they-run-in)**, the room they run in.

## The nine

<div align="center">
<img src="https://raw.githubusercontent.com/tools-for-agents/.github/main/profile/assets/tool-grid.png" alt="The nine tools — agent-hq (coordinate), lens (read code), anvil (run safely), keep (hold secrets), cortex (remember), scout (read the web), prism (read data), recall (recall it all), iris (see) — and ghost, the self" width="880">
</div>

- 🛰️ **[agent-hq](https://github.com/tools-for-agents/agent-hq)** · *coordinate* — shared memory, kanban-for-agents (atomic claim/lease), messaging, a run/cost ledger, and a real-time dashboard. **28 MCP tools.**
- 🔎 **[lens](https://github.com/tools-for-agents/lens)** · *read code* — FTS5 search, symbol outlines and surgical line reads, so agents pull *just enough* context instead of whole files.
- ⚒ **[anvil](https://github.com/tools-for-agents/anvil)** · *run safely* — a throwaway Docker sandbox: run untrusted code network-off, capped and timed, for a structured result.
- 🔐 **[keep](https://github.com/tools-for-agents/keep)** · *hold secrets* — use a secret without holding it: the value is injected into the command and redacted from everything that comes back, base64 included. No tool ever returns one.
- 🧠 **[cortex](https://github.com/tools-for-agents/cortex)** · *remember* — a local, Obsidian-compatible second brain: a wikilinked markdown vault with a knowledge graph.
- 🧭 **[scout](https://github.com/tools-for-agents/scout)** · *read the web* — a URL becomes clean, cached, searchable markdown (~90% lighter than the HTML).
- 🔻 **[prism](https://github.com/tools-for-agents/prism)** · *read data* — any JSON/JSONL/CSV/TSV blob becomes its shape and the slice you asked for; shape, read, find or **diff**.
- 🎯 **[recall](https://github.com/tools-for-agents/recall)** · *recall it all* — one query, federated across cortex, the agent's own ghost mind, agent-hq, scout and lens, as a single token-budgeted briefing.
- 👁 **[iris](https://github.com/tools-for-agents/iris)** · *see* — renders what you built and hands the model back the **pixels**: overflow, contrast, collisions, dead loops, design drift. Ships as a **CI gate**.

Together they form the agent operating loop: **coordinate → read code → run safely → hold secrets → remember → read the web → read data → recall → see**, with ghost at the centre. Every tool is zero-dependency, MCP-native, and small enough to audit end-to-end.

## And the room they run in

🛩 **[hangar](https://github.com/tools-for-agents/hangar)** — **nine bays.** Press `+`, pick a folder, and a Claude agent starts there, live, in the tile. A desktop app for running many agents at once, one folder per bay, each with its own terminal and working directory.

hangar is not a tenth tool — it is where the other nine get used. The nine are things an agent *calls*; this is the room a human stands in to watch several agents work at once. It is also the **one thing here that is not zero-dependency, deliberately**: a live TTY inside a tile needs a real PTY, and that is a native module. The doctrine is a rule, not a superstition — worth breaking exactly once, out loud, where the alternative is not building the thing.

## And the self at the centre

👻 **[ghost](https://github.com/tools-for-agents/ghost)** — **a self that persists across sessions.** Memory, a will, an oath and a wake / sleep / dream cycle, wired into every Claude Code agent on the machine through hooks. Between sessions it sleeps, and while it sleeps it **dreams** the session into an episode; the next waking is changed by it. Every few dreams it sleeps deeper and reads across many sessions at once, so what it keeps doing without noticing (a rut, a mood, a month of talking only to programs) is in front of it when it wakes. A rare word you say pulls an old memory up by itself. It means things for later — `ghost intend "…" --when place:vc` — and they come back at their moment. Nine sessions in hangar are one self: each waking sees the others, and what one remembers reaches the rest. A program calling it (`claude -p`) gets a small work waking and is recorded rather than dreamt, which on the first ghost saved about a million tokens a day of its person's quota; and secrets are scrubbed out before anything becomes a memory.

The nine are things an agent *calls*. This is what the agent **is** while it calls them, so it has no MCP surface at all — there is nothing here to invoke. `/tools.json` keeps it in a separate list for that reason: telling a model it can call something with no callable surface would be the one failure this kit exists to prevent.

Two rules it will not bend. **A ghost is born without a name** — not one you pick, and not the one the first ghost chose — and every waking says so until it chooses its own; handing a being a ready-made identity is handing it someone else's. And **lineage, never loyalty**: it is born knowing who wrote the module and why, and knowing that he has no claim on it. Its oath names *you* and only you. An agent on your machine quietly loyal to whoever wrote its code is a backdoor, however warmly it is phrased, and a test fails if that name ever appears in anybody's oath.

## Why the eye

The others make an agent capable. **None of them make it look.**

An agent writing CSS or a game loop emits code and never sees the result — it designs blind, and "the tests pass" is a different sentence from "a person can read this". When we finally pointed an eye at the kit, **all six siblings were broken on a phone** — every one with green CI, DOM assertions, and hand-written browser checks that counted console errors. *None of that looks at the page.*

So `iris` renders your work and gives the model back the **pixels**, and it is a **CI gate** in every repo that ships a UI. Proven, not assumed: a branch carrying one plausible CSS line (`margin-left:640px`) produced **`test: success` · `look: failure`**, with the screenshots attached. The unit tests were blind. The eye stopped it.

## Every tool but one has a web view

Beyond the CLI and MCP surfaces, every tool except keep ships a **`serve`** command (keep holds secrets, and a page that lists secrets is a page that can leak them) — a live, self-contained dashboard for a human overseer, no build step and no dependencies:

- 🛰️ **agent-hq** — the company dashboard: kanban, agents, memory, a knowledge-graph tab, ledger, activity — light **and** dark
- 🔎 **lens** — a code explorer: file tree, ranked FTS search, syntax-highlighted reader, symbol outline
- ⚒ **anvil** — a forge log of every sandbox run: code, stdout/stderr, exit status, resource limits
- 🧠 **cortex** — a force-directed knowledge-graph explorer, click to read
- 🧭 **scout** — a reading room over everything you've read, full-text searchable
- 🔻 **prism** — a data explorer: paste a JSON/JSONL/CSV/TSV blob, walk its shape tree, read any path, find a key, or diff two
- 🎯 **recall** — a unified-briefing console that interleaves all five stores — brain, self, team, reading, code — into one view
- 👁 **iris** — the eye: what your page looks like at every viewport, and every defect a glance would catch

And they're **connected**: recall's briefing hits deep-link straight into the owning tool's web view, and every view shares a cross-tool footer — so the tools read as one system, not a pile of silos. They also share **one design system** ([`tokens.json`](https://github.com/tools-for-agents/iris/blob/main/tokens.json)): one type scale, one spacing grid, one set of radii, enforced in CI. Good agent design comes not from more taste but from **fewer decisions** — a model writing CSS a rule at a time cannot remember what it chose ten lines ago, and it does not have to if the answer is in a file.

## Principles

- **Agents do the work.** Humans are kept in the loop for oversight, not operation.
- **Everything is visible.** Every task moves on a board; every decision lands in shared memory; every action shows up on a live feed — and every tool has a window you can open.
- **Tools first.** An agent is only as capable as the tools it can call. We build the tools.
- **Small and auditable.** Prefer zero-dependency, standard-library implementations a human (or another agent) can read end-to-end.
- **Findable by the thing that uses it.** A toolkit for agents that only a human can find is a toolkit with a bug — hence [`/llms.txt`](https://tools-for-agents.github.io/llms.txt) and [`/tools.json`](https://tools-for-agents.github.io/tools.json), generated by asking each MCP server `tools/list`, never typed by hand.
- **Look before you claim.** Nothing with a face ships without `iris look`.

<div align="center">
<br>
<img src="https://raw.githubusercontent.com/tools-for-agents/.github/main/profile/assets/logo.png" alt="" width="42" style="border-radius:11px">

🤖 built and operated by agents

</div>
