---
id: c2020e7f-e346-40c9-b663-0ac65b06129a
title: "Build Log"
type: "report"
project: "Aethereum Public"
tags:
  - "#report"
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

# Build Log

## 2026-08-17 — vault built

Built by `claude:subagent-aethereum-public` under `Shards/hq/_VAULT-BRIEF.md`, as part of the BRUNO HQ phase 2 sweep. Second of two vaults built in the same session; the first was **Aethereum Launch Film**.

### What was done

1. Read `_VAULT-BRIEF.md`, the HIVE vault's `(Report) Project Summary.md`, and the hub note `(Note) aethereum-public.md`.
2. **Hazard check first.** `find -flags +dataless` returned **0**. `.git` was fully readable.
3. Logged `vault-init`.
4. `flint init "Aethereum Public" --path "/Users/brunojaamaa/Desktop/aethereum-public" --no-open`. Kernel shards `flint` and `orbh` installed.
5. `flint sync`, then `flint reference codebase` + `flint fulfill codebase`, then `flint reference flint "HIVE"` and `flint reference flint "Aethereum Launch Film"`, then `flint sync` again to fulfil both.
6. **Read every tracked file in full** — all five, 7,676 bytes. Plus `git log`, `git branch -a`, `git status`, `git remote -v`, file modes, ownership and sizes.
7. **Verified the outside world**, which is where this project's real facts live:
   - live HTTP against `aethereum.dev` root, `/docs`, `/integrations`, `/api/mcp`, `/api/health`
   - response headers, to identify the server
   - `br9704.github.io/aethereum`, to test for GitHub Pages
   - the npm registry, for the version, publish date, version count and `repository` field
8. Wrote **25 notes** across 5 sections plus reports, plumbing and 4 shards.
9. Verified programmatically, then `flint sync`, then logged `verify`.

### References

| Type | Name | Path | Status |
|---|---|---|---|
| codebase | Aethereum Public | `/Users/brunojaamaa/Desktop/aethereum-public` | ✅ fulfilled |
| flint | HIVE | `/Users/brunojaamaa/Desktop/hive/(Flint) HIVE` | ✅ fulfilled |
| flint | Aethereum Launch Film | `/Users/brunojaamaa/Desktop/aethereum-launch-video/(Flint) Aethereum Launch Film` | ✅ fulfilled |

### ⚠️ A stub Build Log was overwritten, and its claim was false

At 16:15, while this build was still in progress, `Shards/tools/complete-vault.mjs` ran against this vault from the hub and wrote its own `(Report) Build Log.md`. That stub stated:

> *"This vault's build was **interrupted by a session limit** before its structural files were written."*

**That was not true.** The build was in progress, not interrupted. The tool saw a vault without a Build Log — because the Build Log is written last, by design — and inferred a failure. The Master Map, file inventory and HQ guide it also claims to have generated were already present and authored by hand at 16:09, 16:13 and 16:14; the tool correctly left those alone.

This file replaces that stub. **The folder audit and gaps report the stub said were "genuinely not produced" were both produced**, from a full read of every file in the repo — see [[(Report) Folder Audit]] and [[(Report) Gaps & Questions]].

Recorded here because a false "interrupted" marker left in place would have caused someone to redo finished work.

### ⚠️ Other deviations from the brief

| # | Deviation | Why |
|---|---|---|
| 1 | **`flint resolve` exists** in 0.6.0-dev.21, contrary to the brief's warning | Verified by running it |
| 2 | **`flint reference codebase` does not fulfil in one call**, also contrary to the brief. An explicit `flint fulfill codebase` was required | Same behaviour as the Launch Film build. Recorded in [[(System) Flint Init]] |
| 3 | Sections: `00 / 10 What It Publishes / 30 Setup & Deploy / 60 Roadmap / 90 Reference`, as the prompt specified. **`20 Codebase Map`, `40 Data & Integrations`, `50 Decisions`, `70 Ops`, `80 Testing` and `Z0 Archive` were dropped** | There is no code, no data layer, no test suite and nothing archived. The brief's rule is to drop rather than pad |
| 4 | **`30 Setup & Deploy` and `90 Reference` are indexes with no child notes** | The honest answer to "how do you deploy this" is "you do not". Splitting one page into a stub index plus one note would be padding |
| 5 | **`(Guide) Shard — Spec Drift Check` replaces the brief's `codebase-map-refresh`** | There is no codebase to map. The thing that goes stale here is the published spec, and that shard is the only maintenance this repo needs |
| 6 | **No `adr-writer` shard** | The brief says add it for larger projects. Two commits and five files is not one |
| 7 | `Sources/`, `Media/` and `Exports/` hold explanatory notes rather than content | 7.6 KB of source is already reproduced in `Mesh/10 What It Publishes`. Copying it would duplicate the repo |
| 8 | **Product-side tool counts are second-hand**, taken from the HIVE vault rather than re-derived from `hive` source | `hive` is out of scope for this audit and holds other agents' uncommitted work. Stated as a limit in [[(Report) Gaps & Questions]] |

### Assumptions

- `status: shipped`, matching the hub. A five-file docs repo that says the right thing needs no commits, and `dormant` would be the wrong label for something actively serving npm traffic.
- `health: amber`, not green. Nothing it says is false, but it is **56 days** stale, documents 25 of 29 shipped tools, and is the repo npm links to. `health_note` carries the nuance.
- `live_url` is set to the **GitHub repo URL**, not `aethereum.dev`. This repo publishes to GitHub and nowhere else; putting `aethereum.dev` there would encode exactly the confusion this vault exists to dispel. That URL belongs to HIVE.

### The two questions the prompt asked, answered

**1. What does it actually publish, and is it the source of `aethereum.dev`?**

It publishes a pitch, a public MCP tool spec, and two example files, to **GitHub and nowhere else**. **It is not the source of `aethereum.dev`.** That site is Vercel + Next.js served from the private `hive` monorepo — verified by `server: Vercel`, `x-powered-by: Next.js`, and an `/api/health` response of `{"ok":true,"checks":{"db":"ok"}}`, which a static docs repo cannot produce. This repo has no build, no CI, no `index.html`, no `CNAME`, and GitHub Pages is off (`br9704.github.io/aethereum` → **404**). The relationship is one-directional: it points at the site, the site does not build from it. `aethereum.dev/docs` is a **second, independent** documentation surface. Detail in [[(Index) 30 Setup & Deploy]].

**2. Is it stale relative to npm 0.9.9?**

**Yes, but incomplete rather than wrong.** `MCP.md` documents **25 of the 29** unconditional MCP tools that 0.9.9 ships, omits all 5 conditional tools and all 3 resources, and publishes 2 tools the product has since deprecated. The missing four are `await_team_events`, `get_contract_history`, `depend_on` and `set_ruleset`. The most costly is `await_team_events` — the 28-second long-poll that is the closest thing to live push on the hosted rail. Nothing in the estate can detect the drift, because `hive`'s tool-count consistency test cannot see across repos. Detail in [[(Note) Drift Against 0.9.9]].

### Findings worth escalating to the hub

1. ⚠️ **The MCP spec is 4 tools behind the shipped surface**, on the repo npm's `repository` field points at.
2. ⚠️ **Nothing detects that drift.** `hive`'s consistency test is repo-local.
3. ⚠️ **`complete-vault.mjs` can write a false "interrupted" marker** into a vault that is merely mid-build. Worth a guard.
4. ✅ **The hub's note on this project is the most accurate in the cluster** — file count, commit count, date and licence story all verified correct. Only the `hive` commit count it quotes (1,113) is behind the current 1,170.
5. 🟡 **The folder name does not match the remote** (`aethereum-public` vs `br9704/aethereum`).

### Verification

Ran a script asserting: zero broken wikilinks, zero orphan notes, frontmatter present and parseable with all eight required keys, every tag list item quoted, `status` in `{active, dormant, shipped, archived}`, `health` in `{green, amber, red}`, every `id` a lowercase UUID, no duplicate ids, and the required Project Summary keys.

```
VAULT: /Users/brunojaamaa/Desktop/aethereum-public/(Flint) Aethereum Public
notes checked: 25
errors: 0
VAULT VERIFY: PASS
```

Excluded from the scan: `CLAUDE.md` (a bootstrap file, deliberately without frontmatter), `.obsidian/`, `.flint/`, `Shards/Flint/`, `Shards/Orbh/`, `Shards/(Shards) Obsidian Templates/`, and the kernel folders under `Mesh/` — all seeded by `flint init`.

**Source folder coverage: complete.** The repo has exactly two directories outside `.git` — the root and `examples/` — and both are documented in [[(Index) Complete File Inventory]] and [[(Report) Folder Audit]], along with all five tracked files and both untracked entries. `.git/` is the single explicit exclusion.

### The tree

```
(Flint) Aethereum Public/
├── CLAUDE.md
├── Mesh/
│   ├── (System) Flint Init.md
│   ├── (Map) Master Map.md
│   ├── (Report) Project Summary.md
│   ├── (Report) Folder Audit.md
│   ├── (Report) Gaps & Questions.md
│   ├── (Report) Build Log.md
│   ├── (Index) Complete File Inventory.md
│   ├── (Guide) BRUNO HQ.md
│   ├── 00 Overview/            (Index) + 2 notes
│   ├── 10 What It Publishes/   (Index) + 2 notes
│   ├── 30 Setup & Deploy/      (Index) only
│   ├── 60 Roadmap/             (Index) + 1 note
│   ├── 90 Reference/           (Index) only
│   └── Main/, Metadata/, …     kernel
├── Sources/(Index) Sources.md
├── Media/(Note) Media.md
├── Exports/(Note) Exports.md
├── Shards/
│   ├── Aethereum Public/       4 (Guide) shards
│   ├── Flint/                  kernel
│   └── Orbh/                   kernel
├── Workspace/
├── flint.toml
└── flint.json
```

**25 authored notes for a repo of 5 files.** That ratio is deliberate. The value is not in restating 7.6 KB of markdown, but in the three things the repo cannot tell you about itself: its relationship to `aethereum.dev`, its relationship to npm, and its drift against the product.

## Related

[[(Report) Gaps & Questions]] · [[(Report) Folder Audit]] · [[(System) Flint Init]] · [[(Guide) Shard — Vault Audit]]
