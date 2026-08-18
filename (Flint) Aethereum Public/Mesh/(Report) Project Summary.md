---
id: e2770382-d8c4-4bd0-8389-dcd85be17d3a
title: "Aethereum Public — Project Summary"
type: project-summary
project: "Aethereum Public"
kind: coding
stack: "Markdown · JSON · Bash. No build, no dependencies, no source"
status: shipped
health: amber
health_note: "shipped and correct in shape, but eight weeks stale: it documents 25 of the 29 MCP tools that npm 0.9.9 actually ships, and it is the repo the npm package links to"
last_commit: "2026-06-22"
last_commit_note: "b2c6954 · remove MIT licence (not open source); all rights reserved"
path: "/Users/brunojaamaa/Desktop/aethereum-public"
live_url: "https://github.com/br9704/aethereum"
repo: "https://github.com/br9704/aethereum"
cluster: "aethereum"
tags:
  - "#report"
  - "#project"
  - "#ld/living"
  - "#status/shipped"
  - "#stack/markdown"
  - "#cluster/aethereum"
created: "2026-08-17"
updated: "2026-08-17"
---

# Aethereum Public — Project Summary

**The public front door for a product whose source is private.** Five files: a pitch, an MCP tool spec, a drop-in config and a one-line quickstart. No code, no build, no dependencies, no CI.

🚀 **shipped** — done in an afternoon on 2026-06-22 and correct in shape. It has simply not kept up with the product.

## What it actually publishes

| File | Bytes | What |
|---|---|---|
| `README.md` | 4,044 | The pitch: the problem, the shared brain, the negotiation handshake, how to run it, the privacy claim, and `© 2026 Bruno Jaamaa. All rights reserved.` |
| `MCP.md` | 3,168 | **The public MCP tool spec.** How to connect, and what each `aethereum__*` tool does |
| `examples/mcp.json` | 111 | A drop-in MCP config pointing at `https://www.aethereum.dev/api/mcp` |
| `examples/init.sh` | 279 | `npx aethereum init`, plus two commented follow-ups |
| `.gitignore` | 74 | Node boilerplate for a repo with no Node in it |

The whole repo is **7.6 KB of tracked content** inside a 1.1 MB folder, of which 1.0 MB is `.git`.

## It is NOT the source of `aethereum.dev`

**Verified 2026-08-17.** `www.aethereum.dev` returns HTTP **200** with `server: Vercel` and `x-powered-by: Next.js`. `/api/health` returns `{"ok":true,"checks":{"db":"ok"}}`. That is the **Next.js dashboard in the private `hive` monorepo**, deployed on Vercel.

This repo has no `index.html`, no `CNAME`, no static-site generator, no `package.json`, no workflow file and no GitHub Pages deployment — `https://br9704.github.io/aethereum/` returns **404**.

**It publishes to GitHub and nowhere else.** It points at `aethereum.dev`; it does not produce it. See [[(Index) 30 Setup & Deploy]].

## Why it exists, in one fact

**npm `aethereum@0.9.9` declares `repository: https://github.com/br9704/aethereum.git`.** Verified against the registry on 2026-08-17.

So every person who installs the CLI and clicks "Repository" on npmjs.com lands here. This repo is what a public GitHub presence looks like when the product is closed source: the protocol is published so other clients can speak to it, the implementation stays private.

The second of its two commits is the whole thesis: **`b2c6954 remove MIT licence (not open source); all rights reserved`**.

## Key numbers, verified 2026-08-17

| | |
|---|---|
| Tracked files | **5** |
| Commits | **2**, both 2026-06-22, both Bruno Jaamaa |
| Branch | `main` · clean · **0** unpushed |
| On disk | **1.1 MB** (`.git` is **1.0 MB**) |
| Remote | `https://github.com/br9704/aethereum.git` |
| Tools documented in `MCP.md` | **25** |
| Tools npm 0.9.9 actually ships | **29** unconditional, plus 5 conditional and 3 resources |
| Days since last commit | **56** |
| npm versions published since | **~20** of 27 |

## Top risks

1. ⚠️ **`MCP.md` is missing four shipped tools** — `await_team_events`, `get_contract_history`, `depend_on`, `set_ruleset`. The first is the most costly omission: it is the long-poll that is the closest thing to live push on the hosted rail. See [[(Note) Drift Against 0.9.9]].
2. ⚠️ **It documents two tools the product marks deprecated** — `clear_directive` and `blast_radius`.
3. 🟡 **Nothing detects the drift.** `hive` has a test that cross-checks every "N tools" claim in its own README against the code. **This repo is outside that test's reach.**
4. 🟡 **Two files in the same repo disagree.** `MCP.md` lists six editors that `init` configures; `README.md` lists five. `Cline` is in one and not the other.
5. 🟡 **The folder name and the repo name differ** (`aethereum-public` on disk, `br9704/aethereum` on GitHub), and the repo name is one character away from the private `br9704/hive` mental model. Easy to grep for the wrong thing.

## Next 5 actions

- [ ] Add the four missing tools to `MCP.md`, and remove or mark the two deprecated ones #task [project:: Aethereum Public] [priority:: high] ^t-jpybct7g
- [ ] Extend `hive`'s tool-count consistency test to cover this repo, or add a checked-in snapshot so drift fails a build somewhere #task [project:: Aethereum Public] [priority:: high] ^t-yat68tc7
- [ ] Reconcile the editor list between `README.md` and `MCP.md` #task [project:: Aethereum Public] ^t-gcwaesng
- [ ] Decide whether the CLI's `README` on npm should point at `aethereum.dev/docs` instead of a repo that lags the package #task [project:: Aethereum Public] ^t-mfvt2z4f
- [ ] Rename the local folder to `aethereum` to match the remote, or accept the mismatch and note it #task [project:: Aethereum Public] ^t-ccj6qsw2

## The links that matter

[[(Map) Master Map]] · [[(System) Flint Init]] · [[(Index) 00 Overview]] ·
[[(Note) What This Repo Is]] · [[(Note) The MCP Spec]] · [[(Index) 30 Setup & Deploy]] ·
[[(Note) Drift Against 0.9.9]] · [[(Index) 90 Reference]] · [[(Report) Gaps & Questions]]

## Related

[[(Guide) BRUNO HQ]] · [[(Report) Build Log]]
