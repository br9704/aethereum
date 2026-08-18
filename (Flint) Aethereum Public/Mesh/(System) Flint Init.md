---
id: 06709715-8779-4525-b76d-1ee5b4169224
title: "Flint Init — Aethereum Public"
type: "system"
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
source_path: "/Users/brunojaamaa/Desktop/aethereum-public"
---

# Flint Init: Aethereum Public

**You are inside the `(Flint) Aethereum Public` vault — the knowledge vault for `br9704/aethereum`, the public documentation repo for Aethereum.**

This file is the contract. `CLAUDE.md` at the vault root is the short bootstrap that points here.

## What this vault is, and what it is not

The codebase is at `/Users/brunojaamaa/Desktop/aethereum-public`. It is **five tracked files, two commits, 1.1 MB on disk** — smaller than most single files in the sibling repos. **There is no source code in it at all**, by design.

So this vault is deliberately small. It exists to answer three questions that the repo itself does not answer, and that a reader will get wrong:

1. **What is the relationship between this repo and `www.aethereum.dev`?** They are not the same thing. See [[(Index) 30 Setup & Deploy]].
2. **Why does the folder name not match the repo name?** The folder is `aethereum-public`; the GitHub repo is `br9704/aethereum`. See [[(Note) What This Repo Is]].
3. **Is what it publishes still true?** Not entirely. It documents **25 of 29** shipped MCP tools and has not been touched since 2026-06-22. See [[(Note) Drift Against 0.9.9]].

## The three names that get confused

| Name | Is | Where |
|---|---|---|
| `br9704/aethereum` | **this repo.** Public. Docs only, no source | `~/Desktop/aethereum-public` |
| `br9704/hive` | the product monorepo. **Private.** All the source | `~/Desktop/hive` |
| npm `aethereum` | the published CLI, **0.9.9** | npm registry |

The npm package's `repository` field points at **this repo**, not at `hive`. That is the whole reason it exists.

## The one rule that matters

**REPO WINS OVER NOTE**, and for this project there is a second layer: **the product wins over the spec.** Where `MCP.md` here and `packages/shared/src/hive/mcp.ts` in `~/Desktop/hive` disagree, the product is right and this repo is stale. Every claim in this vault was verified on **2026-08-17** against the files, git, the npm registry and live HTTP calls to `www.aethereum.dev`.

## Resolving the codebase

```bash
flint resolve codebase "Aethereum Public"
# -> /Users/brunojaamaa/Desktop/aethereum-public
# Worktrees
#   [main] /Users/brunojaamaa/Desktop/aethereum-public (main)
```

Declared with `flint reference codebase "Aethereum Public" "<path>"`, then fulfilled with `flint fulfill codebase "Aethereum Public" "<path>"`. **Both calls are required** in CLI 0.6.0-dev.21 — `reference` alone leaves it unfulfilled.

Two sibling Flints are declared as references and auto-fulfil on sync: **HIVE** (`~/Desktop/hive/(Flint) HIVE`) and **Aethereum Launch Film** (`~/Desktop/aethereum-launch-video/(Flint) Aethereum Launch Film`).

## Session start path

1. **[[(Report) Project Summary]]** — one page, and for a repo this size it is most of what there is.
2. **[[(Map) Master Map]]** — the graph and the "start here if you want to…" list.
3. The section index you need. There are five: `00`, `10`, `30`, `60`, `90`.

## What lives where

| Folder | Holds |
|---|---|
| `Mesh/00 Overview` | What this repo is, and its two commits |
| `Mesh/10 What It Publishes` | The MCP spec, the README pitch, the examples |
| `Mesh/30 Setup & Deploy` | ⚠️ There is no build and no deploy. How it actually reaches readers |
| `Mesh/60 Roadmap` | The drift against npm 0.9.9, and what to do about it |
| `Mesh/90 Reference` | Links and the three-name disambiguation |
| `Sources/`, `Media/`, `Exports/` | Plumbing. All empty by design |
| `Shards/Aethereum Public/` | Four cognitive programs |
| `Mesh/Main`, `Mesh/Metadata`, `Shards/Flint`, `Shards/Orbh` | Flint kernel, seeded by `flint init`. Do not hand-edit |

Sections `20 Codebase Map`, `40 Data & Integrations`, `50 Decisions`, `70 Ops`, `80 Testing` and `Z0 Archive` were **dropped, not emptied**. There is no code to map, no data layer, no test suite and nothing archived. The brief's rule is to drop rather than pad.

The Flint kernel staging sections (`Mesh/Main/(Section) New`, `(Section) Working`, `(Section) Consolidated`) are unused by this build.

## Shards that apply

`flint init` installed **flint** and **orbh**. Four project shards live in `Shards/Aethereum Public/`:

[[(Guide) Shard — Spec Drift Check]] · [[(Guide) Shard — Changelog From Git]] · [[(Guide) Shard — Onboarding Guide]] · [[(Guide) Shard — Vault Audit]]

**[[(Guide) Shard — Spec Drift Check]] is the one that matters.** It is the only maintenance this repo needs.

## Conventions

- Every file is `(Type) Name.md`. Types in use: `(System)` `(Map)` `(Report)` `(Index)` `(Note)` `(Guide)`.
- Frontmatter on every note: `id` (lowercase UUID), `title`, `type`, `project`, `tags`, `status`, `created`, `updated`, plus `source_path` where a note describes something on disk.
- Tag order: kind tag, then `#project`, `#ld/living`, `#stack/markdown`, `#status/<state>`, `#cluster/aethereum`. **Tag list items are quoted** — an unquoted `#` starts a YAML comment and silently empties the list.
- `status` is one of `active` · `dormant` · `shipped` · `archived`. This project is **shipped**.
- Links are plain wikilinks with the full filename including the type prefix. Never aliased. Lists joined by ` · `.
- Status glyphs: 🟢 active · 🚀 shipped · 🟡 dormant · ⚫ archived · ⚠️ hazard · ❓ unknown.

## Rules for agents working here

1. **Read-only outside this vault.** No `git commit`, `push`, `checkout`, `reset`, `stash` or `clean` in `/Users/brunojaamaa/Desktop/aethereum-public`.
2. **This repo is not open source.** The second of its two commits removed the MIT licence: *"remove MIT licence (not open source); all rights reserved"*. Do not add a licence file, do not describe the project as open source, and do not publish source into it.
3. **Never document a tool that is not shipped.** Check `~/Desktop/hive/packages/shared/src/hive/mcp.ts` before adding anything to `MCP.md`.
4. **Verify before you write a number.** Every bolded number here has a command behind it.
5. **Log material actions** with `node "/Users/brunojaamaa/Desktop/Main Vault/Main/Shards/tools/obsidianlog.mjs"`.
6. **Run `flint sync`** after adding notes.

## Up

[[(Guide) BRUNO HQ]] — the hub at `/Users/brunojaamaa/Desktop/Main Vault/Main`.
