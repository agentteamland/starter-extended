# 🧩 starter-extended

A minimal **example team** that demonstrates the AgentTeamLand inheritance mechanism.

## What it shows

- How a team **extends** another team (`extends: software-project-team@^1.0.0` in `team.json`)
- How a team **excludes** an inherited member it does not want (`excludes: ["ux-agent"]`)
- How a team **adds** its own agent on top of the parent (`stripe-agent` here)
- The canonical agent.md + children/ layout (per [agent-structure.md](https://github.com/agentteamland/core/blob/main/rules/agent-structure.md) — Identity / Area of Responsibility / Core Principles / Knowledge Base, with each topic under `children/{topic}.md` and `knowledge-base-summary` frontmatter)

## Install (try it)

```bash
cd your-project/
atl install starter-extended
```

This installs:
- The full `software-project-team` (13 agents, 3 skills) **except** `ux-agent`
- Plus the new `stripe-agent` defined in this repo

## Repo layout

```
.
├── README.md
├── LICENSE
├── team.json                      ← declares: extends + excludes + the new agent
└── agents/
    └── stripe-agent/
        ├── agent.md               ← Identity, Responsibility, Core Principles, Knowledge Base
        └── children/
            └── webhook-topology.md  (with knowledge-base-summary frontmatter)
```

## Customize

Copy this repo as a template for your own extension teams:

```bash
gh repo create your-org/your-extension-team --template agentteamland/starter-extended
```

Edit `team.json` to:
- Pick a different parent (`extends: design-system-team@^0.8.0`, etc.)
- Adjust `excludes` to drop members you don't want
- Add new agents, skills, or rules under `agents/`, `skills/`, `rules/`

Validate locally before pushing:

```bash
~/.claude/repos/agentteamland/core/scripts/validate-team-json.sh team.json
```

## License

MIT. See [LICENSE](LICENSE).

## History

- `v0.1.0` (2026-04-17): initial example demonstrating inheritance
- `v0.2.0` (2026-05-02): rescued during the platform-wide review (Phase 2.B/2.C migration applied: agent.md sections renamed to canonical schema + Knowledge Base section added; `knowledge-base-summary` frontmatter added to children files; Wiki + journal discipline core principle added; LICENSE + README added)
