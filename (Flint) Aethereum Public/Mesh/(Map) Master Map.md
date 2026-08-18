---
id: ff82690b-575e-4873-a71b-5de3cfd30df1
title: "Master Map — Aethereum Public"
type: "map"
project: "Aethereum Public"
tags:
  - "#map"
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

# Master Map — Aethereum Public

The whole vault on one page. **Five sections, 25 authored notes**, for a repo of five files.

```mermaid
graph TD
  SUM["(Report) Project Summary"]
  SUM --> S00["00 Overview"]
  SUM --> S10["10 What It Publishes"]
  SUM --> S30["30 Setup &amp; Deploy"]
  SUM --> S60["60 Roadmap"]
  SUM --> S90["90 Reference"]

  S00 --> N1["What This Repo Is"]
  S00 --> N2["Git History"]
  S10 --> N3["The MCP Spec"]
  S10 --> N4["The README and Examples"]
  S60 --> N5["Drift Against 0.9.9"]

  SUM -.->|"documents the product in"| HIVE["(Flint) HIVE — private source"]
  SUM -.->|"points readers at"| WEB["www.aethereum.dev — served by hive/apps/web on Vercel"]
  SUM -.->|"linked from"| NPM["npm aethereum 0.9.9 · repository field"]
  SUM -.-> HQ["(Map) BRUNO HQ — the hub"]
```

## The linked outline

**Entry** — [[(Report) Project Summary]] · [[(System) Flint Init]] · [[(Guide) BRUNO HQ]]

**00 Overview** — [[(Index) 00 Overview]]
[[(Note) What This Repo Is]] · [[(Note) Git History]]

**10 What It Publishes** — [[(Index) 10 What It Publishes]]
[[(Note) The MCP Spec]] · [[(Note) The README and Examples]]

**30 Setup & Deploy** — [[(Index) 30 Setup & Deploy]] — no build, no deploy. The index is the content

**60 Roadmap** — [[(Index) 60 Roadmap]]
[[(Note) Drift Against 0.9.9]]

**90 Reference** — [[(Index) 90 Reference]]

**Reports** — [[(Report) Folder Audit]] · [[(Index) Complete File Inventory]] · [[(Report) Gaps & Questions]] · [[(Report) Build Log]]

**Plumbing** — [[(Index) Sources]] · [[(Note) Media]] · [[(Note) Exports]]

**Shards** — [[(Guide) Shard — Spec Drift Check]] · [[(Guide) Shard — Changelog From Git]] · [[(Guide) Shard — Onboarding Guide]] · [[(Guide) Shard — Vault Audit]]

## Start here if you want to…

| Want to… | Read |
|---|---|
| know what this repo is in 60 seconds | [[(Note) What This Repo Is]] |
| know whether this is the source of `aethereum.dev` | [[(Index) 30 Setup & Deploy]] — **it is not** |
| know if what it says is still true | [[(Note) Drift Against 0.9.9]] |
| read the published MCP tool list | [[(Note) The MCP Spec]] |
| understand the licence position | [[(Note) Git History]] |
| tell `br9704/aethereum` from `br9704/hive` | [[(Index) 90 Reference]] |
| fix the drift | [[(Guide) Shard — Spec Drift Check]] |
| see every file | [[(Index) Complete File Inventory]] |
| know what could not be verified | [[(Report) Gaps & Questions]] |

## Up

[[(Guide) BRUNO HQ]] → `/Users/brunojaamaa/Desktop/Main Vault/Main/Mesh/(Map) BRUNO HQ.md`
