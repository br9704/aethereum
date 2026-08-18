---
id: c17ccf86-7181-4b2e-9e0e-64248e8b0f3e
title: "Shard — Spec Drift Check"
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
source_path: "/Users/brunojaamaa/Desktop/aethereum-public/MCP.md"
---

# Shard — Spec Drift Check

**The only maintenance this repo needs.** Compare the published `MCP.md` against the tool surface the product actually ships, and report the delta.

**Run when.** A new `aethereum` version hits npm, a tool is added or deprecated in `hive`, or monthly.

This shard replaces the generic `codebase-map-refresh` from the vault brief. There is no code in this repo to map; the thing that goes stale is the spec.

## Steps

### 1. Get the product's real surface

```bash
HIVE="$(flint resolve flint 'HIVE' 2>/dev/null | head -1)"   # or ~/Desktop/hive
cd ~/Desktop/hive
grep -oE '"aethereum__[a-z_]+"' packages/shared/src/hive/mcp.ts | tr -d '"' | sort -u
grep -c 'server\.tool\|server\.resource' packages/shared/src/hive/mcp.ts
```

⚠️ **Read-only.** Never run a git write command in `hive`; other agents hold uncommitted work there.

Cross-check against the HIVE vault's `Mesh/10 Architecture/(Note) The MCP Surface.md`, which records the counts as **29 unconditional · 5 conditional · 3 resources**, and note that the hosted `/api/mcp` rail carries **30** because `room_view` always resolves server-side.

### 2. Get the published surface

```bash
cd "$(flint resolve codebase 'Aethereum Public' | head -1)"
grep -oE '^- `[a-z_]+\(' MCP.md | tr -d '`-( ' | sort -u
```

### 3. Diff them

```bash
comm -13 /tmp/published.txt /tmp/shipped.txt   # shipped but not published  <- the gap
comm -23 /tmp/published.txt /tmp/shipped.txt   # published but not shipped  <- worse
```

**Published-but-not-shipped is the serious direction.** A missing tool is an omission; a documented tool that does not exist is a bug report from a stranger.

### 4. Check the deprecations

Grep `mcp.ts` for `deprecated` in tool descriptions. As of 2026-08-04, two are correctly deprecated (`clear_directive`, `blast_radius`) and both are still published in `MCP.md`.

### 5. Check the npm version and the endpoint

```bash
curl -s https://registry.npmjs.org/aethereum | \
  node -e "let d='';process.stdin.on('data',c=>d+=c).on('end',()=>{const j=JSON.parse(d);console.log(j['dist-tags'].latest, j.time[j['dist-tags'].latest], j.versions[j['dist-tags'].latest].repository.url)})"
curl -s -o /dev/null -w "%{http_code}\n" https://www.aethereum.dev/api/mcp    # expect 401
```

⚠️ If the npm `repository` field ever stops pointing at `br9704/aethereum`, **this repo has lost its audience** and its priority changes completely. Say so loudly.

### 6. Report

Update [[(Note) Drift Against 0.9.9]] with the new counts and date, then the risk lines in [[(Report) Project Summary]] and the task list in [[(Index) 60 Roadmap]]. Bump `updated:` on everything touched.

### 7. Log and sync

```bash
node "/Users/brunojaamaa/Desktop/Main Vault/Main/Shards/tools/obsidianlog.mjs" \
  --actor claude:shard-spec-drift --op verify --target "MCP.md" \
  --result "<n published / m shipped / delta>" --trigger "spec-drift-check" \
  --project "/Users/brunojaamaa/Desktop/aethereum-public"
flint sync
```

## The fix worth building instead

Running this by hand is the fallback. The real fix is to make drift fail a build: extend `hive`'s `apps/web/lib/tool-count-consistency.test.ts` to cover this repo, or commit a generated tool list here that the product's test diffs against. That task is in [[(Index) 60 Roadmap]].

## Guardrails

- Read-only in both repos.
- **Never document a tool that is not shipped.**
- Never publish anything from `hive` that is not already public. The premise is a public protocol with a private implementation.

## Related

[[(Note) Drift Against 0.9.9]] · [[(Note) The MCP Spec]] · [[(Index) 60 Roadmap]] · [[(Guide) Shard — Vault Audit]]
