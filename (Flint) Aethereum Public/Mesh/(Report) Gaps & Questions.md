---
id: 04619c07-b1d0-4b16-9d4a-e8b76d15a095
title: "Gaps & Questions"
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

# Gaps & Questions

**What this vault could not establish, and why.**

Fewer than usual: the repo is five files and every one was read in full, so the file-level facts are complete. The open questions are all about intent and about the world outside the repo.

## Open questions

| # | Question | Where I looked | Status |
|---|---|---|---|
| 1 | **Does anyone actually read this repo?** No traffic data on disk. It is linked from npm `repository` and declared as the CLI's `bugs` tracker, so the route exists, but usage is unknown | npm registry, repo | ❓ unknown |
| 2 | **Are there open GitHub issues here?** npm declares `github.com/br9704/aethereum/issues` as the CLI's issue tracker. Issue state was **not** checked — that would need `gh`, and the brief forbids `gh repo` operations | npm metadata | ❓ not checked, deliberately |
| 3 | **Was `MCP.md` ever intended to stay current?** No `CONTRIBUTING`, no CI, no note in either file about maintenance cadence. It reads as written-once | repo | ❓ owner intent |
| 4 | **Does `aethereum.dev/docs` derive from `MCP.md`?** Almost certainly not — it returns 200 from a Next.js app in the private `hive` repo, and this repo has no build. **But `hive` was not audited**, so a copy-in step there cannot be ruled out from here | live HTTP, this repo | ⚠️ high confidence, not proven |
| 5 | **Should `(Flint) Aethereum Public/` be gitignored?** `.gitignore` does not exclude it, so it will show as untracked. Same open question as the HIVE and Launch Film vaults | `.gitignore` | ❓ owner decision |
| 6 | **Should the local folder be renamed to `aethereum`?** It would match the remote and remove a recurring confusion, at the cost of breaking every path recorded in the hub | `git remote -v` | ❓ owner decision |
| 7 | **Why is this folder owned by `brunojaamaa:wheel`** when the sibling repos are `brunojaamaa:staff`? Cosmetic, but unexplained | `ls -la` | ❓ unknown |
| 8 | **Is `Cline` actually configured by `init`?** `MCP.md` says yes, `README.md` omits it. Only the CLI source in `hive` could settle it | both files | ❓ needs `hive` |

## Contradictions found

### Between the hub note and the repo

| Hub note says | Repo says | Resolution |
|---|---|---|
| "**5 files** — `README.md`, `MCP.md`, `examples/`, one `.sh`, one `.json`" | **5 tracked files**: `README.md`, `MCP.md`, `examples/init.sh`, `examples/mcp.json`, `.gitignore` | ✅ **Correct**, once `examples/` is read as the directory and `.gitignore` as the fifth. No correction needed |
| "`main` · **2 commits** (2026-06-22)" | identical | ✅ correct |
| "`~/Desktop/hive` — the actual product monorepo, **1,113 commits**" | HIVE vault reports **1,170** as of 2026-08-15 | 🟡 the hub note is 57 commits behind. Not this vault's fact to own, but worth flagging |

**The hub's note on this project is the most accurate one in the cluster.** It got the file count, the commit count, the date and the licence story right.

### Inside the repo

| | |
|---|---|
| `README.md` lists **five** editors (Claude Code, Cursor, Codex, Windsurf, Zed) | `MCP.md` lists **six** (adds Cline) |

### Between the repo and the product

`MCP.md` documents **25 of 29** shipped MCP tools, and publishes two the product deprecates. Full analysis in [[(Note) Drift Against 0.9.9]].

## Things deliberately not done

| | Reason |
|---|---|
| GitHub issues, stars, forks, traffic | Would require `gh repo` operations. Brief rule 1 forbids them |
| Auditing `~/Desktop/hive` | Out of scope. Product facts come from the HIVE vault and the npm registry |
| Opening `.git/` internals | Brief rule 6 |
| Authenticating to `/api/mcp` | The 401 is sufficient proof the rail is live |

## Limits of this audit

- **Every tracked file was read in full.** There is no sampling and no inference about file contents.
- **Product-side claims are second-hand.** The 29/5/3 tool counts come from the HIVE vault, which derives them from `packages/shared/src/hive/mcp.ts` and its assertion test. They were not re-derived from `hive` source here.
- **Live HTTP was checked once**, on 2026-08-17. A 200 today is not a guarantee tomorrow.
- **npm metadata was read from the registry**, not from a local install.

## Secrets

**None found.** No `.env*`, no key material, no credential. The repo requires zero environment variables and has no runtime.

## Related

[[(Report) Folder Audit]] · [[(Report) Build Log]] · [[(Note) Drift Against 0.9.9]] · [[(Index) 30 Setup & Deploy]]
