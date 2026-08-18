# CLAUDE.md — Agent Bootstrap

**You are working inside the `(Flint) Aethereum Public` vault — the knowledge vault for `br9704/aethereum`, the public documentation repo for Aethereum.**

This vault is not the codebase. The codebase is at `/Users/brunojaamaa/Desktop/aethereum-public`.
Resolve it properly rather than hardcoding the path:

```bash
flint resolve codebase "Aethereum Public"
```

## Read this first

**`Mesh/(System) Flint Init.md`** — the workspace contract. What is where, the conventions,
and the safety rules.

## Then

1. `Mesh/(Report) Project Summary.md` — one page. For a five-file repo it is most of what there is.
2. `Mesh/(Map) Master Map.md` — the graph and the "start here if you want to…" list.
3. The section index you need: `00 Overview`, `10 What It Publishes`, `30 Setup & Deploy`,
   `60 Roadmap`, `90 Reference`.

## The four things that trip everyone up

1. **Three things are called Aethereum.** `br9704/aethereum` is **this repo** (public, docs, no
   source). `br9704/hive` is the product monorepo (**private**, all the source). npm `aethereum`
   is the published CLI at **0.9.9**. The folder on disk is `aethereum-public`; the remote is
   `br9704/aethereum`. **The names do not match.**
2. **This is NOT the source of `www.aethereum.dev`.** The site is Vercel + Next.js served from
   `hive`. This repo has no build, no CI, no GitHub Pages — `br9704.github.io/aethereum` is a
   **404**. It points at the site; it does not produce it.
3. **It is not open source, and that was deliberate.** The second of two commits removed the MIT
   licence: *"remove MIT licence (not open source); all rights reserved"*. **Do not add a
   `LICENSE` file.**
4. **`MCP.md` documents 25 of the 29 MCP tools npm 0.9.9 ships**, and publishes two the product
   has deprecated. It has not been touched since **2026-06-22**, and nothing detects the drift.

## Why it matters despite being five files

**npm `aethereum@0.9.9` declares `repository: https://github.com/br9704/aethereum.git` and its
issues URL as the CLI's `bugs` tracker.** Everyone who installs the CLI and clicks "Repository"
lands here.

## Hard rules

- **Read-only outside this vault.** Never `git commit`, `push`, `checkout`, `reset`, `stash` or
  `clean` in `/Users/brunojaamaa/Desktop/aethereum-public` — or in `~/Desktop/hive`.
- **Never document a tool that is not shipped.** Check
  `~/Desktop/hive/packages/shared/src/hive/mcp.ts` before adding anything to `MCP.md`.
- **Never publish source here.** The premise is a public protocol with a private implementation.
- **REPO WINS OVER NOTE**, and **the product wins over the spec.**
- **Log material actions** with
  `node "/Users/brunojaamaa/Desktop/Main Vault/Main/Shards/tools/obsidianlog.mjs"`.
- Run `flint sync` after adding notes.

## The one recurring job

`Shards/Aethereum Public/(Guide) Shard — Spec Drift Check.md`. Everything else here is stable.

Up: `Mesh/(Guide) BRUNO HQ.md` → the hub at `/Users/brunojaamaa/Desktop/Main Vault/Main`.
