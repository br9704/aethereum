---
id: 85f78bc4-d6a7-4c21-be91-d232c199536f
title: "The README and Examples"
type: "note"
project: "Aethereum Public"
tags:
  - "#note"
  - "#project"
  - "#ld/living"
  - "#stack/markdown"
  - "#status/shipped"
  - "#cluster/aethereum"
status: shipped
created: "2026-08-17"
updated: "2026-08-17"
source_path: "/Users/brunojaamaa/Desktop/aethereum-public/README.md"
---

# The README and Examples

## `README.md` — 4,044 bytes

**The pitch, and the only place the licence position is stated.** Structure, in order:

| Section | Content |
|---|---|
| Hook | *"The coordination layer for AI coding agents."* Then `npx aethereum init` in a fenced block, above the fold |
| Scope | What is in this repo and what is not, stated in the third paragraph rather than buried |
| **The problem** | Three named failure modes: context drift, shadow dependencies, device fragmentation |
| **Give your agents a shared brain** | Defines an agent as *"just a running Claude Code, Cursor, or Codex session in someone's editor"*. States the flagship: the interface-contract negotiation handshake |
| **Build with Aethereum** | The MCP config block and the tool families in one sentence |
| **Run it yourself** | Three commands: `init`, `run`, `join` |
| **How coordination works** | Events → reduce → `get_team_context`, with alerts **delivered exactly once** |
| **What's in this repo** | A three-item file list, then a blunt restatement that the CLI, engine, dashboard and backend are not here |
| **Links** | `aethereum.dev`, `/docs`, `/integrations` |
| **Copyright** | © 2026 Bruno Jaamaa. All rights reserved |

### The three published links — all verified live 2026-08-17

| URL | Status |
|---|---|
| `https://www.aethereum.dev` | **200** |
| `https://www.aethereum.dev/docs` | **200** |
| `https://www.aethereum.dev/integrations` | **200** |

None is broken. All three are served by the Next.js app in the private `hive` repo, on Vercel.

### The one internal contradiction

`README.md` names the editors Aethereum works with as *"Claude Code, Cursor, Codex, Windsurf, Zed, and the rest"* — **five**.
`MCP.md` says `init` writes config for *"Claude Code, Cursor, Codex, Windsurf, Cline, and Zed"* — **six**.

**Cline appears in one file and not the other**, in the same repo, committed in the same session. Trivial, but it is the kind of thing a reader notices before they notice anything good.

## `examples/mcp.json` — 111 bytes

The MCP config block on its own, so it can be copied into a `.mcp.json` without editing:

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

Byte-identical to the block in both `README.md` and `MCP.md`. The endpoint returns **401** when called anonymously, which is the correct signal that the rail is live and gated.

## `examples/init.sh` — 279 bytes

Not really a script. One live command and two commented follow-ups:

```bash
#!/usr/bin/env bash
# One command: create a free Aethereum room (no signup) and wire your agents.
npx aethereum init

# Then run your agent in the room:
# aethereum run claude -- "build the checkout flow"
# A teammate joins with a short code:
# aethereum join <code>
```

⚠️ It carries a shebang but is **not executable** (mode `-rw-r--r--`). Anyone following the obvious instinct and running `./examples/init.sh` gets a permission error. Since the file's whole purpose is to be read rather than run, the shebang is arguably the mistake, not the mode.

## `.gitignore` — 74 bytes

`node_modules/` · `dist/` · `.turbo/` · `coverage/` · `*.tsbuildinfo` · `.env` · `.env.*` · `.DS_Store`

**Boilerplate carried over from a Node monorepo into a repo with no Node in it.** Harmless, and mildly misleading — it implies a build that does not exist. The one line doing real work is `.DS_Store`, and there is a `.DS_Store` on disk, untracked, correctly ignored.

⚠️ It does **not** ignore `(Flint) Aethereum Public/`, so this vault shows as untracked in the repo. See [[(Report) Gaps & Questions]].

## Related

[[(Note) The MCP Spec]] · [[(Note) What This Repo Is]] · [[(Index) 30 Setup & Deploy]] · [[(Index) 10 What It Publishes]]
