# 🧩 starter-extended

> Minimal example team that demonstrates the AgentTeamLand inheritance mechanism. Set up as a GitHub Template — fork it as the starting point for your own extension team.

The repo demonstrates the smallest viable inheritance team: declares `extends: software-project-team@^1.0.0` in `team.json`, drops `ux-agent` via `excludes`, adds a single new `stripe-agent` on top. ~50 lines of repo total.

To use as a template:

```bash
gh repo create your-org/your-extension-team --template agentteamland/starter-extended
```

Then edit `team.json` to pick a different parent, adjust excludes, add your own agents.

## 📚 Documentation

Full docs live at **[agentteamland.github.io/docs](https://agentteamland.github.io/docs/)**.

Most relevant sections:

- [Worked example: starter-extended](https://agentteamland.github.io/docs/authoring/starter-extended-example) — the full walkthrough of THIS repo (team.json fields, agent layout, when to extend vs author from scratch)
- [Inheritance](https://agentteamland.github.io/docs/authoring/inheritance) — the mechanism this example demonstrates (extends, excludes, override semantics, load order)
- [Children + learnings](https://agentteamland.github.io/docs/guide/children-and-learnings) — the agent.md / children/ layout used here (with `knowledge-base-summary` frontmatter contract)
- [`atl install`](https://agentteamland.github.io/docs/cli/install) — `atl install starter-extended` if you want to install this template-team directly to try it

## License

MIT. See [LICENSE](LICENSE).
