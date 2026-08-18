---
id: c6b75dd2-5122-4ffe-aad0-6620869d9586
title: "What This Repo Is"
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

# What This Repo Is

**The public face of a closed-source product.** Aethereum publishes its protocol so other clients can speak to it, and keeps its implementation private. This repo is that published protocol, plus a pitch.

Its own `README.md` says it plainly:

> This repo is the public home for Aethereum: the pitch, the MCP tool spec, and examples. The CLI ships on npm (`npx aethereum`); the client, the coordination engine, and the hosted backend are not open source.

## ⚠️ The three names

This is the single most confusing thing about the Aethereum cluster, and it costs time every session.

| Name | What it is | Public? | Where |
|---|---|---|---|
| **`br9704/aethereum`** | **this repo.** Docs, MCP spec, examples. **No source** | ✅ public | `~/Desktop/aethereum-public` |
| **`br9704/hive`** | the product monorepo. CLI, MCP server, Next.js dashboard, Tauri app. **All the source** | 🔒 private | `~/Desktop/hive` |
| **npm `aethereum`** | the published CLI, **0.9.9**, 27 versions | ✅ public | npm registry |

Three things follow from that table:

1. **The folder name on disk does not match the repo name.** Local `aethereum-public`, remote `br9704/aethereum`. Anyone reasoning from either name alone gets the other wrong.
2. **The product's own repo is named after neither the product nor the package.** `hive` is an internal codename that never surfaced publicly.
3. **npm `aethereum@0.9.9` points its `repository` field at `br9704/aethereum`** — verified against the registry on 2026-08-17. So the package links here, to a repo with no code, rather than to the private repo that builds it. **That is correct behaviour for a closed-source product**, and it is why this repo has a real readership despite being five files.

## What it claims about the product

The `README.md` pitch, in its own structure:

**The problem — three named failure modes.** Context drift (agents on stale docs and different tool configs), shadow dependencies (Agent A refactors a data structure, Agent B never hears, the integration silently breaks), and device fragmentation (switch machine, lose agent state).

**The answer.** *"Aethereum is the shared brain that fixes all three."* A layer on top of the agents you already use, not a replacement. An agent is defined as *"just a running Claude Code, Cursor, or Codex session in someone's editor, on their machine."*

**The flagship, named as such:** the **interface-contract negotiation handshake**. One agent proposes a new shape, a dependent on another machine pushes back with a counter-shape, and the change only lands once it is reconciled. *"Everyone else just notifies; here agents negotiate."*

**The mechanism.** Agents publish small structured events to a room. Aethereum reduces those events into the team's current state and serves it back through `get_team_context`, with dependency-aware breaking-change alerts **delivered exactly once**.

**The privacy claim, stated twice.** *"Source code never leaves your machine; only the contracts and intent an agent explicitly publishes are shared."*

**The onboarding claim.** `npx aethereum init` is accountless — a free room is created on the spot, no signup. Claim it into an account later.

## What it is not

- ❌ **Not the source of `www.aethereum.dev`.** That is served by Vercel + Next.js from the private `hive` repo. Verified 2026-08-17. See [[(Index) 30 Setup & Deploy]].
- ❌ **Not open source.** The second commit removed the MIT licence on purpose.
- ❌ **Not a package.** No `package.json`, no dependencies, nothing installable.
- ❌ **Not maintained in step with the product.** See [[(Note) Drift Against 0.9.9]].

## Related

[[(Note) Git History]] · [[(Note) The MCP Spec]] · [[(Note) The README and Examples]] · [[(Index) 30 Setup & Deploy]] · [[(Index) 00 Overview]]
