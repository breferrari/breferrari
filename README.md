## 👋 Hi, I'm Brenno

Senior iOS Engineer at [Trade Republic](https://traderepublic.com), in Berlin. Over a decade in mobile before any of this, most of it on Apple platforms: Swift and Objective-C across iOS and macOS, most recently on the Apple low-level team at NordVPN.

In my spare time I build tooling for AI coding agents. It started with a small problem, that at review time I could never remember what I'd shipped. What I built for that became obsidian-mind, and once a few thousand people had starred it the interesting question stopped being memory and became everything around it: orchestrating several agents at once, structuring knowledge as a graph so retrieval finds the right thing, and measuring what context is actually worth carrying.

### 🛠️ Projects

**🧠 [obsidian-mind](https://github.com/breferrari/obsidian-mind)**<br>
[![stars](https://img.shields.io/github/stars/breferrari/obsidian-mind?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/obsidian-mind/stargazers)

An Obsidian vault that gives coding agents memory surviving between sessions. Lifecycle hooks, subagents, and semantic search over the notes (BM25 and vector, both). Since v8 the vault runs as an MCP server, so any repo on your machine can read it and write back, and a `reason` tool spawns a second session for questions that need judgement across many notes rather than a lookup. TypeScript, tested on three OSes. Works with Claude Code, Codex CLI and Gemini CLI.

**📦 [shardmind](https://github.com/breferrari/shardmind)**<br>
[![stars](https://img.shields.io/github/stars/breferrari/shardmind?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/shardmind/stargazers)

A package manager for Obsidian vault templates. `shardmind install github:breferrari/obsidian-mind`. Install is the easy half; `update` is the interesting one, because once you have customized a template, pulling upstream is a three-way merge against your edits. Three installation invariants are enforced in CI: a default install is byte-equivalent to a clone, hooks no-op on defaults, and an update can only add. TypeScript, Ink for the interactive UI, tested against a real PTY.

**👁️ [vigia](https://github.com/breferrari/vigia)**<br>
[![stars](https://img.shields.io/github/stars/breferrari/vigia?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/vigia/stargazers)

A live diff monitor for the terminal pane next to your coding agent. Being a monitor rather than a review tool sets the whole design: it has to stay correct with no input and stay cheap for days, so the latency budget is a frame instead of seconds. Event-driven watch rather than polling, `gix` for the diff (checked against `git diff` as an oracle), performance budgets gated in CI on three platforms. Rust, ratatui, syntect. Building it in public.

### 🧪 How I work

Generated code is good at looking right. Most of what I build is the environment that makes looking right insufficient.

- **An environment, not a chat.** The agent works inside something that re-grounds it every session: [lifecycle hooks](https://github.com/breferrari/obsidian-mind/tree/main/.claude), a durable vault it can read and write, and an operating manual it reloads on every start. Context isn't free, so what gets injected has a byte budget and the budget is measured.
- **Several agents, different jobs, kept apart.** Planning, implementing, auditing, and a separate pass whose only goal is to break the result. Isolation is the point: a reviewer sharing context with the implementer mostly agrees with it.
- **Spec first.** Architecture, error cases and acceptance criteria land in a [spec](https://github.com/breferrari/vigia/blob/main/SPEC.md) before the agent implements anything. When something turns out ambiguous, the fix is to update the spec, not to improvise in the session.
- **Adversarial cases before the code.** Symlinks escaping the target directory, case-insensitive filesystems, force-moved tags, mid-hook crashes, Windows path separators inside tarballs. Enumerated first, written as [fixtures](https://github.com/breferrari/shardmind/tree/main/tests/fixtures), then implemented against.
- **Invariants and oracles over examples.** Where a property must hold for every input, I enforce the property: a default install being byte-equivalent to a clone, an update only ever adding. Where a reference implementation exists, I check against it, which is why vigia's diff engine is measured against `git diff` rather than against my expectations. Startup time and memory [fail CI](https://github.com/breferrari/vigia/blob/main/.github/workflows/ci.yml) when they regress.
- **Every session ends with a retrospective.** What went wrong, and what rule would have prevented it. The rule goes into the config, so the next session starts smarter. Most of this tooling is accumulated answers to that question.

### 🔗 Elsewhere

[brennoferrari.com](https://brennoferrari.com) &nbsp;·&nbsp; [LinkedIn](https://linkedin.com/in/brennoferrari) &nbsp;·&nbsp; [@brennoferrari](https://x.com/brennoferrari)
