---
id: ecdc04db-96f5-436e-9df1-fac764c5f296
title: "Shard — Vault Audit"
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

# Shard — Vault Audit

**Purpose.** Rescan the repo, diff it against [[(Index) Complete File Inventory]], and report what changed.

**Run when.** Monthly, or before quoting any number from this vault.

## Steps

### 1. Safety first

```bash
P="/Users/brunojaamaa/Desktop/aethereum-public"
find "$P" -type f -flags +dataless 2>/dev/null | wc -l   # must be 0
```
Never read a file on that list — a dataless iCloud stub hangs indefinitely.

`timeout` does not exist on this Mac. Guard long commands with:
```bash
tmo() { local t=$1; shift; ( "$@" ) & local p=$!; ( sleep "$t"; kill -9 $p 2>/dev/null ) & local w=$!; wait $p 2>/dev/null; local rc=$?; kill -9 $w 2>/dev/null; return $rc; }
```

### 2. Rescan — the whole repo, not a sample

```bash
cd "$P"
git ls-files                     # expect exactly 5
wc -c $(git ls-files)            # expect 7676 total
du -sh . .git                    # expect 1.1M / 1.0M
find . -type f -not -path './.git/*' -not -path './(Flint)*'
git status --short
```

**Read all five files in full.** At 7.6 KB there is no reason to summarise, and a full read is what makes [[(Index) Complete File Inventory]] a total enumeration rather than an estimate.

### 3. Diff against the inventory

Report new files, removed files, and any byte-count change. **A sixth tracked file is news** — flag it rather than quietly adding a row.

Check specifically:
- Has a `LICENSE` appeared? That is a licensing change, not housekeeping. Escalate.
- Has a `.github/` directory appeared? That would mean CI now exists and [[(Index) 30 Setup & Deploy]] needs rewriting.
- Has an `index.html` or `CNAME` appeared? That would mean the repo now publishes a site, which changes the answer to the vault's central question.

### 4. Re-verify the external facts

They are outside git and go stale silently.

```bash
curl -s -o /dev/null -w "site:%{http_code} " https://www.aethereum.dev/
curl -s -o /dev/null -w "docs:%{http_code} " https://www.aethereum.dev/docs
curl -s -o /dev/null -w "integrations:%{http_code} " https://www.aethereum.dev/integrations
curl -s -o /dev/null -w "mcp:%{http_code} " https://www.aethereum.dev/api/mcp
curl -s -o /dev/null -w "pages:%{http_code}\n" https://br9704.github.io/aethereum/
curl -sI https://www.aethereum.dev/ | grep -i 'server\|x-powered-by'
curl -s https://registry.npmjs.org/aethereum | \
  node -e "let d='';process.stdin.on('data',c=>d+=c).on('end',()=>{const j=JSON.parse(d);const v=j['dist-tags'].latest;console.log(v,j.time[v],j.versions[v].repository.url,Object.keys(j.versions).length)})"
```

Baseline as of 2026-08-17: site **200**, docs **200**, integrations **200**, mcp **401**, pages **404**, `server: Vercel`, `x-powered-by: Next.js`, npm **0.9.9** / 27 versions / repository `br9704/aethereum`.

⚠️ If GitHub Pages ever returns **200**, or the npm `repository` field stops pointing here, the vault's central conclusions change and must be rewritten, not patched.

### 5. Run the spec drift check

[[(Guide) Shard — Spec Drift Check]]. It is the substance of this audit.

### 6. Report

Findings into [[(Report) Build Log]] under a dated heading. Update [[(Index) Complete File Inventory]] and [[(Report) Folder Audit]]. Bump `updated:` everywhere touched.

### 7. Log and sync

```bash
node "/Users/brunojaamaa/Desktop/Main Vault/Main/Shards/tools/obsidianlog.mjs" \
  --actor claude:shard-vault-audit --op verify --target "(Flint) Aethereum Public/" \
  --result "<findings>" --trigger "vault-audit" --project "$P"
flint sync
```

## Guardrails

- Read-only outside the vault.
- Never open `.git/` internals or anything matching `*silmu*` or `_secrets/`.
- No `gh repo` operations — that is why GitHub issue state is an open question in [[(Report) Gaps & Questions]] rather than a fact.

## Related

[[(Index) Complete File Inventory]] · [[(Report) Folder Audit]] · [[(Report) Build Log]] · [[(Guide) Shard — Spec Drift Check]]
