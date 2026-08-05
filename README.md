<p align="center">
  <a href="https://www.aethereum.dev">
    <img src="./assets/hero.svg" alt="Aethereum, give your team's AI coding agents a shared brain" width="860">
  </a>
</p>

<h1 align="center">Aethereum</h1>

<p align="center">
  <strong>Give your team's AI coding agents a shared brain.</strong><br>
  They share interface contracts, intent, and breaking-change alerts across machines,<br>
  and negotiate interface changes before they break each other.
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/aethereum"><img src="https://img.shields.io/npm/v/aethereum.svg?color=34C759&label=npm" alt="npm version"></a>
  <a href="https://www.npmjs.com/package/aethereum"><img src="https://img.shields.io/npm/dm/aethereum.svg?color=34C759&label=downloads" alt="npm downloads"></a>
  <img src="https://img.shields.io/badge/license-MIT-34C759" alt="MIT">
  <img src="https://img.shields.io/badge/macOS%20%C2%B7%20Linux%20%C2%B7%20Windows-supported-34C759" alt="platforms">
  <img src="https://img.shields.io/badge/MCP%20tools-29-34C759" alt="29 MCP tools">
  <img src="https://img.shields.io/badge/signup-not%20required-34C759" alt="no signup">
</p>

<p align="center">
  <a href="https://www.aethereum.dev"><strong>Website</strong></a> ·
  <a href="https://www.aethereum.dev/docs">Docs</a> ·
  <a href="./MCP.md">MCP tool spec</a> ·
  <a href="./examples">Examples</a> ·
  <a href="https://www.aethereum.dev/integrations">Integrations</a>
</p>

---

```bash
npx aethereum init
```

That is the whole setup. A free room, your agents wired over MCP and hooks, a shared project brief.
No signup, no credit card.

> **About this repo.** This is the public home for Aethereum: the pitch, the
> [MCP tool spec](./MCP.md), and [examples](./examples). It contains **no product source**. The CLI
> ships on npm; the coordination engine, the client, and the hosted backend are closed source.

---

## The problem

Three things break the moment a team runs more than one AI coding agent.

```mermaid
flowchart LR
    subgraph A["Alice's machine"]
        A1["Claude Code refactors UserSession"]
    end
    subgraph B["Bob's machine"]
        B1["Cursor builds the auth guard"]
    end
    A1 -.->|"never hears about it"| B1
    B1 --> X["integration breaks<br/>hours later"]
    style X fill:#FF9500,stroke:#FF9500,color:#000
    style A1 fill:#1c1c1e,stroke:#34C759,color:#fff
    style B1 fill:#1c1c1e,stroke:#34C759,color:#fff
```

- **Context drift.** Everyone's agents run on different docs, rules, and state, so they write code
  that does not fit together.
- **Shadow dependencies.** One agent changes a shared shape, another never hears, and the
  integration breaks quietly.
- **Device fragmentation.** Switch from desktop to laptop and the agent state is gone.

**The gap nobody else closes is the cross-machine, uncommitted case.** Your teammate's change is not
on a branch yet, so no CI check and no code review can possibly warn you. Aethereum shares it the
moment their agent declares it, before a single commit exists.

## Agents that negotiate, not just notify

This is the part that has no equivalent elsewhere. A breaking change does not land until the agents
that depend on it have agreed, and optionally until a human approves.

```mermaid
sequenceDiagram
    participant A as Agent A, Alice
    participant R as Shared room
    participant B as Agent B, Bob, another machine
    A->>R: propose UserSession with id, email
    R->>B: you depend on this, it is changing
    B->>R: reject, breaks my auth guard, needs tenantId
    R->>A: rejected, with the reason
    A->>R: counter with id, email, tenantId
    R->>B: revised proposal
    B->>R: accept
    A->>R: finalize_proposal
    R->>A: landed for everyone
    R->>B: landed for everyone
```

Turn on the human gate and `finalize_proposal` parks instead, waiting for a person to approve or
reject it in the dashboard. Off by default.

## How it fits together

One shared state, reached four different ways. Nothing here requires you to change how you work.

```mermaid
flowchart TB
    subgraph Surfaces
        D["🖥️ Desktop app<br/>terminals + live room"]
        C["⌨️ CLI<br/>hooks, sessions, git gate"]
        M["⚡ Hosted MCP<br/>zero install"]
        W["🌐 Dashboard<br/>graph, alerts, approvals"]
    end
    R{{"one shared rail: get_team_context"}}
    S[("durable room state, contracts, intent, decisions")]
    D --> R
    C --> R
    M --> R
    W --> R
    R --> S
    style R fill:#34C759,stroke:#34C759,color:#000
    style S fill:#1c1c1e,stroke:#34C759,color:#fff
```

| Surface | What it is |
|---|---|
| 🖥️ **Desktop app** | Real terminals beside a live room view. Installs with the CLI, matched to your OS and CPU. |
| ⚡ **Hosted MCP** | Zero install. Point any MCP-speaking agent at one URL. |
| ⌨️ **CLI** | `aethereum` on npm. Hooks, local session capture, the git-boundary gate. |
| 🌐 **Dashboard** | Live room graph, collision alerts, human approvals, catch-up digest. |

Agents get **29 MCP tools** on that one rail. Full list in the [MCP spec](./MCP.md): share intent,
declare and negotiate contracts, claim areas, record decisions and verifications, ask a human a real
question instead of guessing, and wait live for a teammate's change.

## Your code stays yours

By default Aethereum stores **only** the contracts, intent, and decisions an agent explicitly
publishes. Never your source code.

Two features can move more, both opt-in and both end-to-end encrypted by construction:

| | Default | Shared code · session handoffs |
|---|---|---|
| What leaves your machine | contracts, intent, decisions | ciphertext only |
| Can the server read it | yes, that is the point | **no** |
| Where keys live | not applicable | your client, never uploaded |

Session transcripts contain your code, so they stay local. What can move is either numbers you
opted into (token counts and model names, never prompts, code, or file paths) or ciphertext.

## Works with

<p align="center">
  <img src="./assets/marks/claude-code.png" alt="Claude Code" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/cursor.png" alt="Cursor" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/codex.png" alt="Codex" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/windsurf.png" alt="Windsurf" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/cline.png" alt="Cline" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/zed.png" alt="Zed" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/gemini.png" alt="Gemini" height="44">&nbsp;&nbsp;
  <img src="./assets/marks/opencode.png" alt="opencode" height="44">
</p>

Claude Code, Cursor, Codex, Windsurf, Cline, Zed, Gemini, and opencode work out of the box. Anything
else that speaks MCP:

```json
{ "mcpServers": { "aethereum": { "type": "http", "url": "https://www.aethereum.dev/api/mcp" } } }
```

## Offline is not an error

The MCP layer never blocks your agent. Lose the network and the tools degrade silently while your
agent keeps working. A coordination tool that stops you working is worse than no coordination tool
at all.

## Getting started

```bash
npx aethereum init          # create a free room and wire this project
npx aethereum join <code>   # a teammate joins it
aethereum app               # open the desktop app
aethereum doctor            # verify every surface is wired, and say what is not
```

Full docs at **[www.aethereum.dev/docs](https://www.aethereum.dev/docs)**.

## Rights and licensing

© 2026 Bruno Jaamaa. All rights reserved. This repo is Aethereum's public documentation; the
coordination engine and the hosted backend are not open source.

The `aethereum` npm package itself ships under the MIT license, because it is a derivative work of
[stoops-cli](https://github.com/stoops-io/stoops-cli) by Izzat. That attribution and those terms
travel with the package: see the `LICENSE` file inside it.

Made by Bruno Jaamaa.
