---
id: 19961534-9821-4704-b230-64b16e8f2e7d
title: "Complete File Inventory"
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

# Complete File Inventory

**Every file in `/Users/brunojaamaa/Desktop/aethereum-public`.** Compiled 2026-08-17. This is a total enumeration, not a summary — the repo is small enough that every file fits on one page, and every one was read in full.

## Tracked — 5 files, 7,676 bytes

| # | Path | Bytes | Type | Purpose |
|---|---|---|---|---|
| 1 | `README.md` | 4,044 | md | The pitch, the file list, the site links, `© 2026 Bruno Jaamaa. All rights reserved.` |
| 2 | `MCP.md` | 3,168 | md | **The public MCP tool spec.** 25 tools across 9 groups, plus connect and privacy |
| 3 | `examples/mcp.json` | 111 | json | Drop-in MCP config → `https://www.aethereum.dev/api/mcp` |
| 4 | `examples/init.sh` | 279 | sh | `npx aethereum init` + two commented follow-ups. ⚠️ shebang present, not executable |
| 5 | `.gitignore` | 74 | — | `node_modules/` `dist/` `.turbo/` `coverage/` `*.tsbuildinfo` `.env` `.env.*` `.DS_Store` |

`git ls-files | wc -l` → **5**. There is no sixth tracked file.

## Untracked

| Path | Bytes | Note |
|---|---|---|
| `.DS_Store` | 6,148 | 🗑️ macOS noise. Correctly ignored by `.gitignore` |
| `(Flint) Aethereum Public/` | — | This vault. ⚠️ **not** ignored, so `git status` will show it |

## Directories — 2

| Path | Files | Note |
|---|---|---|
| `.` (root) | 4 | 3 tracked + `.DS_Store` |
| `examples/` | 2 | both tracked |

There is no third directory outside `.git`.

## Excluded from this inventory

| Path | Reason |
|---|---|
| `.git/` internals | Brief rule 6. **1.0 MB**, 91% of the folder on disk |

**Dataless iCloud files: 0.** Every file body was safe to read, and every one was read.

## The comparison that matters

| | This repo | Sibling `hive` |
|---|---|---|
| Tracked files | **5** | ~2,895 |
| Commits | **2** | 1,170 |
| On disk | **1.1 MB** | 296 MB |
| Source files | **0** | thousands |

The ratio is the point. **This is 0.17% of the file count of the product it documents**, and that is the correct size for a published protocol with a private implementation.

## Related

[[(Report) Folder Audit]] · [[(Index) 10 What It Publishes]] · [[(Guide) Shard — Vault Audit]] · [[(Report) Gaps & Questions]]
