---
id: e5245b3e-fa41-43ba-822d-0131974ea84f
title: "Sources"
type: "index"
project: "Aethereum Public"
tags:
  - "#index"
  - "#project"
  - "#ld/living"
  - "#stack/markdown"
  - "#status/shipped"
  - "#cluster/aethereum"
status: shipped
created: "2026-08-17"
updated: "2026-08-17"
source_path: "/Users/brunojaamaa/Desktop/aethereum-public"
---

# Sources

**Read-only. Nothing in this folder is authored here.**

`Sources/Repos/` and `Sources/Bundles/` were created by `flint init` and are **empty by design**. The entire source repo is 7,676 bytes across five files, all of them reproduced or summarised in full inside `Mesh/10 What It Publishes`. Copying them here would duplicate the repo rather than reference it.

## Where the sources are

| Source | Path or URL | Kind |
|---|---|---|
| The codebase | `/Users/brunojaamaa/Desktop/aethereum-public` | Flint codebase reference — `flint resolve codebase "Aethereum Public"` |
| The MCP spec | `/Users/brunojaamaa/Desktop/aethereum-public/MCP.md` | 3,168 bytes |
| The pitch | `/Users/brunojaamaa/Desktop/aethereum-public/README.md` | 4,044 bytes |
| The product (private) | `/Users/brunojaamaa/Desktop/hive` | Flint reference `HIVE` |
| The authoritative tool surface | `~/Desktop/hive/packages/shared/src/hive/mcp.ts` | 2,442 lines, 34 registrations |
| The live site | `https://www.aethereum.dev` | served from `hive` on Vercel |
| The npm package | `https://registry.npmjs.org/aethereum` | 0.9.9, 27 versions |
| The hub | `/Users/brunojaamaa/Desktop/Main Vault/Main` | |

## The one worth pinning

If drift ever needs to be provable rather than argued, the thing to snapshot into `Sources/Bundles/` is **the tool list generated from `hive`'s `mcp.ts`** — not `MCP.md`, which is already in git here. [[(Guide) Shard — Spec Drift Check]] describes how to produce it.

## Rules

- **Do not edit anything under `Sources/`.**
- Link by absolute path rather than copying.
- Never copy anything from `hive` that is not already public. This repo's whole premise is that the implementation stays private.

## Related

[[(Index) Complete File Inventory]] · [[(Guide) Shard — Spec Drift Check]] · [[(System) Flint Init]]
