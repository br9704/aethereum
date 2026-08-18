---
id: ebd8ae6a-ee30-417b-95fa-17fd3b4b1baa
title: "Folder Audit"
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

# Folder Audit

**Read-only audit of `/Users/brunojaamaa/Desktop/aethereum-public`, performed 2026-08-17.**

`find -flags +dataless` returned **0** files. Nothing here is an iCloud stub; every file body was safe to read, and every file was read in full. **This audit is complete, not sampled.**

| | |
|---|---|
| Total on disk | **1.1 MB** |
| `.git` | **1.0 MB** (91% of the folder) |
| Tracked files | **5** |
| Tracked bytes | **7,676** |
| Directories | **2** — the root and `examples/` |
| Top-level entries | 6 (incl. 2 dot-entries) |

---

## Root

**Path** `/Users/brunojaamaa/Desktop/aethereum-public`
**Purpose** The public GitHub home for Aethereum. Documentation only, no source.
**Category** coding · documentation
**Modified** 2026-06-22, except `.DS_Store` (2026-08-16) and `.git` (2026-08-17)
**Owner note** The folder is owned by `brunojaamaa:wheel`, unlike the sibling repos which are `brunojaamaa:staff`. Cosmetic; recorded because it is the only structural oddity on disk.

| File | Bytes | Modified | What |
|---|---|---|---|
| `README.md` | 4,044 | 2026-06-22 17:52 | The pitch, the file list, the three site links, and the all-rights-reserved notice |
| `MCP.md` | 3,168 | 2026-06-22 17:38 | **The public MCP tool spec.** 25 tools, plus connect and privacy sections |
| `.gitignore` | 74 | 2026-06-22 17:09 | Node boilerplate for a repo with no Node |
| `.DS_Store` | 6,148 | 2026-08-16 | 🗑️ macOS noise. Untracked and correctly ignored. **Larger than `MCP.md`** |

**Flags** `README.md` and `MCP.md` disagree on the editor list — five in one, six in the other, `Cline` present only in `MCP.md`. Both were committed in the same session.

---

## `examples/` — 2 files, 390 bytes

**Purpose** Copy-paste onboarding.
**Modified** 2026-06-22 17:39

| File | Bytes | What |
|---|---|---|
| `mcp.json` | 111 | The MCP config block, byte-identical to the one in `README.md` and `MCP.md`. Points at `https://www.aethereum.dev/api/mcp` |
| `init.sh` | 279 | One live command (`npx aethereum init`) and two commented follow-ups |

**Flags** ⚠️ `init.sh` carries a `#!/usr/bin/env bash` shebang but is mode `-rw-r--r--`, so it is **not executable**. `./examples/init.sh` fails with a permission error. Since the file exists to be read rather than run, the shebang is the mismatch.

**Dependencies** `mcp.json` and `init.sh` both depend on the live `aethereum.dev` deployment and on npm `aethereum` remaining published. Both verified live on 2026-08-17.

---

## Not present, and each absence is a finding

| Expected in a repo | Present? | What it means |
|---|---|---|
| `package.json` | ❌ | Not a package. Nothing installable |
| `LICENSE` | ❌ | **Deliberate.** Commit `b2c6954` removed the MIT licence. Do not restore it |
| `.github/` | ❌ | No CI. No test, no lint, no drift check |
| `index.html` / `_config.yml` / `CNAME` | ❌ | Not a website. GitHub Pages is off — `br9704.github.io/aethereum` returns **404** |
| `CONTRIBUTING.md` / `CODE_OF_CONDUCT.md` | ❌ | Consistent with a closed-source product |
| `.env*`, `*.pem`, `*.key` | ❌ | **No secrets of any kind.** Zero environment variables required |
| `node_modules/`, `dist/`, build output | ❌ | Nothing is built |
| any source file | ❌ | By design, and stated three times in `README.md` |

---

## Excluded

| Path | Reason |
|---|---|
| `.git/` internals | Brief rule 6. **1.0 MB** — 91% of the folder |
| `.DS_Store` | macOS noise, gitignored |
| `(Flint) Aethereum Public/` | This vault. ⚠️ **not** in `.gitignore`, so it shows as untracked in the repo |

---

## Duplicate, dead and abandoned

| Finding | Detail |
|---|---|
| 🟡 **Triplicated content** | The MCP config JSON appears three times: `README.md`, `MCP.md`, `examples/mcp.json`. Intentional — the example file exists to be copied — but it is three places to update if the endpoint moves |
| ⚫ **Dead config** | `.gitignore` lists `node_modules/`, `dist/`, `.turbo/`, `coverage/`, `*.tsbuildinfo` for a repo with no build. Only `.DS_Store` does any work |
| ⚠️ **Stale spec** | `MCP.md` documents **25 of 29** shipped tools. See [[(Note) Drift Against 0.9.9]] |
| ⚠️ **Internal contradiction** | The editor list differs between the two markdown files |
| 🟡 **Non-executable script** | `examples/init.sh` |
| 🟡 **Name mismatch** | Folder `aethereum-public` vs remote `br9704/aethereum` |
| 🗑️ **`.DS_Store` is 6,148 bytes** — 80% the size of the entire tracked repo. Amusing rather than a problem |

---

## Secrets

**None.** No `.env*`, no key material, no token, no credential in any tracked file. The repo requires zero environment variables and has no runtime.

The only external identifiers published are the public endpoint `https://www.aethereum.dev/api/mcp` and the public site URLs, all of which are meant to be public.

## Related

[[(Index) Complete File Inventory]] · [[(Report) Gaps & Questions]] · [[(Note) The README and Examples]] · [[(Index) 30 Setup & Deploy]]
