---
id: cb6b6bbb-1e82-4ce3-8733-ffe0d0528f41
title: "90 Reference"
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

# 90 Reference

**Lookups, and the disambiguation table that saves the most time.**

## ⚠️ Three things called Aethereum

| Name | What | Public? | Path or URL |
|---|---|---|---|
| **`br9704/aethereum`** | **this repo.** Docs + MCP spec + 2 examples. No source | ✅ | `~/Desktop/aethereum-public` · https://github.com/br9704/aethereum |
| **`br9704/hive`** | the product monorepo. **All** the source | 🔒 | `~/Desktop/hive` · https://github.com/br9704/hive |
| **npm `aethereum`** | the published CLI, **0.9.9**, 27 versions | ✅ | https://www.npmjs.com/package/aethereum |

The local folder is `aethereum-public`; the remote is `br9704/aethereum`. **The names do not match.** Grep for the wrong one and you find nothing.

## External links

| | |
|---|---|
| This repo | https://github.com/br9704/aethereum |
| Issue tracker for the CLI | https://github.com/br9704/aethereum/issues — declared in npm `bugs` |
| Website | https://www.aethereum.dev — **200**, Vercel + Next.js, served from `hive` |
| Docs | https://www.aethereum.dev/docs — **200**, a separate surface from `MCP.md` |
| Integrations | https://www.aethereum.dev/integrations — **200** |
| Hosted MCP rail | https://www.aethereum.dev/api/mcp — **401**, live and auth-gated |
| Health | https://www.aethereum.dev/api/health — `{"ok":true,"checks":{"db":"ok"}}` |
| npm package | https://www.npmjs.com/package/aethereum |
| MCP protocol | https://modelcontextprotocol.io |

All HTTP statuses verified 2026-08-17.

## npm package metadata, verified 2026-08-17

| Field | Value |
|---|---|
| `latest` | **0.9.9** |
| published | 2026-08-08T08:07:51Z |
| versions | **27** |
| `repository` | `https://github.com/br9704/aethereum.git` ← **this repo** |
| `homepage` | `https://www.aethereum.dev` |
| `bugs` | `https://github.com/br9704/aethereum/issues` |
| `description` | *"The coordination layer for AI coding agents: contracts, intent, and collision alerts across machines."* |

## Sibling vaults

| Vault | Path | Relationship |
|---|---|---|
| **HIVE** | `/Users/brunojaamaa/Desktop/hive/(Flint) HIVE` | the product this repo documents. Declared as a Flint reference |
| **Aethereum Launch Film** | `/Users/brunojaamaa/Desktop/aethereum-launch-video/(Flint) Aethereum Launch Film` | the 108 s launch film. Declared as a Flint reference |
| **BRUNO HQ** | `/Users/brunojaamaa/Desktop/Main Vault/Main` | the hub |

Resolve either sibling with `flint resolve` rather than hardcoding a path.

## Glossary — the terms this repo uses

| Term | Means |
|---|---|
| **MCP** | Model Context Protocol. The tool interface any MCP-speaking agent can consume |
| **a room** | The shared coordination space. Created free and accountless by `npx aethereum init` |
| **the rail** | `get_team_context`. Every tool surfaces through it |
| **a contract** | A registered interface shape, versioned, with a stability flag |
| **the handshake** | The interface-contract negotiation: propose → respond with a counter-shape → finalise. The flagship |
| **fail soft** | Rule R15 in the product: if Aethereum is offline the agent keeps working. Handlers never throw |
| **exactly once** | Alert delivery. `get_team_context` consumes a cursor |
| **hive** | The internal codename for the product monorepo. Never surfaced publicly |

## Up

[[(Map) Master Map]] · [[(Report) Project Summary]] · [[(Note) What This Repo Is]]
