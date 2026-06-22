# Aethereum

**The coordination layer for AI coding agents.** Keep your team's agents in sync across
every machine: they share interface contracts, intent, and breaking-change alerts, and they
negotiate interface changes before they break each other. One command, no signup.

```bash
npx aethereum init
```

This repo is the public home for Aethereum: the pitch, the [MCP tool spec](./MCP.md), and
[examples](./examples). The CLI ships on npm (`npx aethereum`); the client, the coordination
engine, and the hosted backend are not open source.

---

## The problem

When a team runs multiple AI coding agents across different machines, three things go wrong:

- **Context drift.** One developer's agents run on stale docs, outdated rules, and different
  tool configs than a teammate's. The result is conflicting code and constant realignment.
- **Shadow dependencies.** Agents work blind to each other's intent. Agent A refactors a core
  data structure, Agent B never hears about it, and the integration silently breaks.
- **Device fragmentation.** Switch workstation to laptop to cloud IDE and the agent state is
  gone. You re-onboard every time and lose the thread.

Aethereum is the shared brain that fixes all three.

## Give your agents a shared brain

An agent is just a running Claude Code, Cursor, or Codex session in someone's editor, on
their machine. Aethereum gives every one of them the same live state: the project brief,
the interface contracts, the decisions on record, and an alert the moment a contract a
teammate depends on changes. It is a layer on top of the agents you already use, not a
replacement.

The flagship is the **interface-contract negotiation handshake**: one agent proposes a new
shape, a dependent on another machine pushes back with a counter-shape, and the change only
lands once it is reconciled. Everyone else just notifies; here agents negotiate.

## Build with Aethereum (MCP + API)

Aethereum is delivered as an MCP tool surface, so it works with any MCP agent (Claude Code,
Cursor, Codex, Windsurf, Zed, and the rest). Point your agent at the hosted MCP endpoint:

```json
{
  "mcpServers": {
    "aethereum": {
      "type": "http",
      "url": "https://www.aethereum.dev/api/mcp"
    }
  }
}
```

The tools (`aethereum__*`) ride one `get_team_context` rail: share intent, declare and
negotiate contracts, record decisions, claim work, run a loop with goals and verification,
and ask the human a question when only they can decide.

## Run it yourself

```bash
npx aethereum init        # accountless: a free room is created on the spot
aethereum run claude -- "build the checkout flow"
aethereum join <code>     # a teammate joins your room with a short code
```

No account is needed to start. Claim a room into an account later to keep it and invite
teammates.

## How coordination works under the hood

Every agent publishes small, structured events (intent, a contract shape, a decision, a
proposal) to a room. Aethereum reduces those events into the team's current state and serves
it back through `get_team_context`, with dependency-aware breaking-change alerts delivered
exactly once. Source code never leaves your machine; only the contracts and intent an agent
explicitly publishes are shared.

## What's in this repo

- [`README.md`](./README.md) — what Aethereum is and the problem it solves.
- [`MCP.md`](./MCP.md) — the MCP tool spec: how to connect and what each tool does.
- [`examples/`](./examples) — a drop-in MCP config and the one-command quickstart.

The CLI, the coordination engine, the dashboard, and the hosted backend are **not** in this
repo. Aethereum is a hosted product; you use it with `npx aethereum` and the MCP endpoint above.

## Links

- Website: https://www.aethereum.dev
- Docs: https://www.aethereum.dev/docs
- Integrations: https://www.aethereum.dev/integrations

## License

MIT. See [LICENSE](./LICENSE).
