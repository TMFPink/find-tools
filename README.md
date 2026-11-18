# 🔍 find-tools — discover before you build

An agent-agnostic skill (Claude Code, OpenAI Codex, OpenCode and other agents that support the `SKILL.md` format) that researches existing Agent Skills, GitHub repos, MCP servers, automation templates and platforms **before** building from scratch, then recommends the minimum effective toolset.

**Use it when you say…** "Is there a library for…?", "Find tools to build…", "Compare n8n vs Power Automate"

<p align="center">
  <img src="assets/find-tools-flow.png" alt="Hand-drawn diagram: your task fans out to Agent Skills, GitHub repos, MCP servers, Automations and Platforms, which converge into a compare step (fit, license, upkeep, security) that produces the minimum effective toolset; building custom is a dashed last resort" width="100%">
</p>

## How it picks a research mode

```mermaid
flowchart LR
    A([Your request]) --> B{Already solved by<br/>installed tools?}
    B -- yes --> Z([Use what you have])
    B -- no --> C{How big is<br/>the decision?}
    C -- everyday task --> F[Fast<br/>1–3 picks]
    C -- new feature --> S[Standard<br/>compare up to 5]
    C -- architecture / high risk --> D[Deep<br/>security · license · scale]
    F --> R([Recommend the minimum<br/>effective toolset])
    S --> R
    D --> R
    R --> G{Install or connect<br/>anything new?}
    G -- yes --> H[/Ask you first/]
```

- **Three research modes** — *Fast* (1–3 picks), *Standard* (compare up to 5, default) and *Deep* (security, licensing, scalability review).
- Searches five categories: Agent Skills, GitHub projects, MCP servers, automation workflows (n8n, Power Automate, Make, Zapier) and existing platforms.
- Treats MCP as **optional**, never installs anything without authorization, and never pretends a live search happened when it didn't.

## Installation

This repo *is* the skill folder (`SKILL.md` at the root), so clone it straight into your agent's skills directory.

**Claude Code** (personal, every project):

```bash
git clone https://github.com/TMFPink/find-tools.git ~/.claude/skills/find-tools
```

Or per project: clone into `<project>/.claude/skills/find-tools`.

**OpenAI Codex**:

```bash
git clone https://github.com/TMFPink/find-tools.git ~/.codex/skills/find-tools
```

**Other agents**: place this folder wherever your agent loads `SKILL.md` skills from.

Then describe the task — the agent picks the skill from its `description` — or call it by name (`/find-tools` in Claude Code, `$find-tools` in Codex).

## Requirements

Nothing required. Uses web search, `gh`, or `npx skills` when available.

## Repository layout

```
find-tools/
├── SKILL.md
├── README.md
├── LICENSE
└── assets/
    ├── find-tools-flow.excalidraw   # editable source (open in excalidraw.com)
    └── find-tools-flow.png
```

## Contributing

Issues and pull requests are welcome — improvements to wording, new safety checks, or support notes for other agents.

## License

[MIT](LICENSE) — free to use, modify and share.
