## Hi, I'm Brenno

Senior iOS Engineer at [Trade Republic](https://traderepublic.com), in Berlin. I build tooling for AI coding agents.

### Projects

**[obsidian-mind](https://github.com/breferrari/obsidian-mind)** &nbsp;[![stars](https://img.shields.io/github/stars/breferrari/obsidian-mind?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/obsidian-mind/stargazers)

An Obsidian vault that gives coding agents memory surviving between sessions. Lifecycle hooks, subagents, and semantic search over the notes (BM25 and vector, both). Since v8 the vault runs as an MCP server, so any repo on your machine can read it and write back, and a `reason` tool spawns a second session for questions that need judgement across many notes rather than a lookup. TypeScript, tested on three OSes. Works with Claude Code, Codex CLI and Gemini CLI.

**[shardmind](https://github.com/breferrari/shardmind)** &nbsp;[![stars](https://img.shields.io/github/stars/breferrari/shardmind?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/shardmind/stargazers)

A package manager for Obsidian vault templates. `shardmind install github:breferrari/obsidian-mind`. Install is the easy half; `update` is the interesting one, because once you have customized a template, pulling upstream is a three-way merge against your edits. Three installation invariants are enforced in CI: a default install is byte-equivalent to a clone, hooks no-op on defaults, and an update can only add. TypeScript, Ink for the interactive UI, tested against a real PTY.

**[vigia](https://github.com/breferrari/vigia)** &nbsp;[![stars](https://img.shields.io/github/stars/breferrari/vigia?style=flat-square&labelColor=0d1117&color=1f6feb)](https://github.com/breferrari/vigia/stargazers)

A live diff monitor for the terminal pane next to your coding agent. Being a monitor rather than a review tool sets the whole design: it has to stay correct with no input and stay cheap for days, so the latency budget is a frame instead of seconds. Event-driven watch rather than polling, `gix` for the diff (checked against `git diff` as an oracle), performance budgets gated in CI on three platforms. Rust, ratatui, syntect. Building it in public.

### Elsewhere

[brennoferrari.com](https://brennoferrari.com) &nbsp;·&nbsp; [LinkedIn](https://linkedin.com/in/brennoferrari) &nbsp;·&nbsp; [@brennoferrari](https://x.com/brennoferrari)
