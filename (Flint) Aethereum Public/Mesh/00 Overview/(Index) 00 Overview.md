---
id: e666bcc1-1380-4f11-9bd7-ee6378ba84aa
title: "00 Overview"
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

# 00 Overview

**What this repo is and how it got here.**

## Notes

| Note | What it answers |
|---|---|
| [[(Note) What This Repo Is]] | The public front door for a closed-source product. And the three names that get confused |
| [[(Note) Git History]] | **2** commits, both on 2026-06-22. The second is the whole thesis |

## The thirty-second version

`br9704/aethereum` is the **public GitHub repo for Aethereum**, the coordination layer for AI coding agents. It contains the pitch, the MCP tool spec, and two example files. **It contains no source.**

The product itself lives in the private `br9704/hive` monorepo and ships as an npm CLI, a hosted MCP server, a Next.js dashboard at `www.aethereum.dev`, and a Tauri desktop app. None of that is here.

The reason it exists: **npm `aethereum@0.9.9` declares this repo in its `repository` field.** It is where the package's "Repository" link points.

## Key numbers, verified 2026-08-17

| | |
|---|---|
| Tracked files | **5** |
| Tracked content | **7,676 bytes** |
| Commits | **2**, both 2026-06-22 |
| Author | Bruno Jaamaa, 2 of 2 |
| Branch | `main` · clean · **0** unpushed |
| On disk | **1.1 MB** — `.git` is **1.0 MB** |
| Remote | `https://github.com/br9704/aethereum.git` |
| Build | ❌ none |
| CI | ❌ none |
| Dependencies | ❌ none |
| Licence | ❌ **deliberately none.** All rights reserved |

## The status, honestly

🚀 **shipped.** It did the job it was written for and has not needed a commit since. That is a legitimate steady state for a five-file docs repo, and "dormant" would be the wrong label.

But 🟡 **it has drifted.** The product shipped roughly twenty npm versions after this repo's last commit, and `MCP.md` now documents **25 of 29** shipped tools. See [[(Note) Drift Against 0.9.9]].

## Up

[[(Map) Master Map]] · [[(Report) Project Summary]]
