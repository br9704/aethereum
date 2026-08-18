---
id: 8e13ae6c-ff68-4d86-9e58-d89e8e5d0eb6
title: "Shard — Onboarding Guide"
type: "guide"
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

# Shard — Onboarding Guide

**Purpose.** Bring an agent or a human up to speed in five minutes. For a five-file repo, five minutes is generous.

## The five-minute path

1. **[[(Report) Project Summary]]** — two minutes. It is most of what there is.
2. **[[(Note) What This Repo Is]]** — two minutes. Read the three-names table twice; it is the thing everyone gets wrong.
3. **[[(Note) Drift Against 0.9.9]]** — one minute. Whether what it says is still true.

Then read the repo itself. All five files, 7,676 bytes, take about four minutes.

## The four things to say out loud

1. **This is `br9704/aethereum` on GitHub, but `aethereum-public` on disk.** The names do not match. The private product repo is `br9704/hive`.
2. **This is NOT the source of `www.aethereum.dev`.** The site is Vercel + Next.js served from `hive`. This repo has no build, no CI and no GitHub Pages. It points at the site; it does not produce it.
3. **It is not open source, deliberately.** The second of two commits removed the MIT licence. Do not add one back.
4. **`MCP.md` documents 25 of 29 shipped MCP tools** and has not been touched since 2026-06-22. Nothing detects that.

## Why it matters despite being tiny

**npm `aethereum@0.9.9` declares this repo in its `repository` field, and its issues URL as the CLI's `bugs` tracker.** Everyone who installs the CLI and clicks "Repository" arrives here. Small does not mean unread.

## First commands

```bash
cd "$(flint resolve codebase 'Aethereum Public' | head -1)"
ls -la; ls -la examples
git log --oneline
wc -c README.md MCP.md examples/*
```

There is nothing to install and nothing to run.

## What to output

A short brief: what the repo is in one paragraph, the four points above, and a pointer at [[(Map) Master Map]]. If the reader's job is to change something, send them to [[(Guide) Shard — Spec Drift Check]] first.

## Related

[[(Map) Master Map]] · [[(Note) What This Repo Is]] · [[(Index) 30 Setup & Deploy]] · [[(Guide) Shard — Spec Drift Check]]
