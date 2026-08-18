---
id: 7aac7822-d655-4747-bd32-cfee78789838
title: "Git History"
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
source_path: "/Users/brunojaamaa/Desktop/aethereum-public/.git"
---

# Git History

**Two commits, forty-two minutes apart, and the second one is the point.**

| | |
|---|---|
| Commits | **2** |
| Branch | `main` only. No other local or remote branch |
| Author | Bruno Jaamaa, **2 of 2** |
| Tags | **none** |
| Remote | `origin` → `https://github.com/br9704/aethereum.git` |
| Working tree | ✅ clean · **0** unpushed |
| Days since last commit | **56** as of 2026-08-17 |

## The two commits

| | Time | Subject |
|---|---|---|
| `9193973` | 2026-06-22 **17:10** | `Aethereum: public docs + MCP spec + examples (no source)` |
| `b2c6954` | 2026-06-22 **17:52** | **`remove MIT licence (not open source); all rights reserved`** |

The first commit created the repo. The second, forty-two minutes later, corrected a licensing decision before anyone could act on it.

**That second commit is the whole editorial position of this repo.** Aethereum is a product with a **public protocol**, not an open-source project. The MCP spec is published so any MCP-speaking client can talk to it; the implementation stays in the private `hive` repo. `README.md` now closes with:

> © 2026 Bruno Jaamaa. All rights reserved. Aethereum is a hosted product; this repo is its public documentation. The product, the CLI, and the engine are not open source.

There is no `LICENSE` file in the repo, and there should not be one. **Do not add one.**

## Context — what else was happening on 2026-06-22

The `hive` product repo started **2026-06-10**, twelve days earlier, and would reach 1,170 commits by 2026-08-15. This repo was cut early, at what would have been roughly week two of the product, and never revisited.

That timing explains the drift. `MCP.md` documents the tool surface as it stood in late June. The surface then grew, was audited on 2026-07-28 against rule R26, and had two tools un-deprecated on 2026-08-04 — none of which reached this file. See [[(Note) Drift Against 0.9.9]].

## What "no commits since June" does and does not mean

🚀 It does **not** mean abandoned. A docs repo that says the right thing needs no commits.

⚠️ It **does** mean unverified. Nothing in the estate checks that this repo still matches the product. `hive` has `apps/web/lib/tool-count-consistency.test.ts` which cross-checks every "N tools" claim in its own README against the code — **that test cannot see this repo.**

## Related

[[(Note) What This Repo Is]] · [[(Note) Drift Against 0.9.9]] · [[(Guide) Shard — Changelog From Git]] · [[(Index) 00 Overview]]
