---
id: e9cf9bdb-dafa-446f-9e7b-b735523d718c
title: "BRUNO HQ"
type: "guide"
project: "Aethereum Public"
tags:
  - "#note"
  - "#project"
  - "#ld/living"
  - "#status/shipped"
  - "#cluster/aethereum"
status: shipped
created: "2026-08-17"
updated: "2026-08-17"
source_path: "/Users/brunojaamaa/Desktop/Main Vault/Main/Mesh/(Map) BRUNO HQ.md"
---

# BRUNO HQ

**The hub vault, one level up.** This Flint is a child of it.

| | |
|---|---|
| Hub | `/Users/brunojaamaa/Desktop/Main Vault/Main` |
| Front door | `/Users/brunojaamaa/Desktop/Main Vault/Main/Mesh/(Map) BRUNO HQ.md` |
| This project's hub note | `Mesh/Notes/Projects/(Note) aethereum-public.md` |
| Cluster | `aethereum` |

## The rule

**The hub summarises. This vault and the repo beside it are the truth.** The hub's note on this project is the most accurate one in the cluster — file count, commit count, date and the licence story all check out. See [[(Report) Gaps & Questions]] for the one number that has moved since (the `hive` commit count, which is not this vault's fact to own).

## Siblings in the `aethereum` cluster

| Flint | Path | What it is |
|---|---|---|
| **HIVE** | `/Users/brunojaamaa/Desktop/hive/(Flint) HIVE` | the product. Private source, live at `aethereum.dev`. The flagship |
| **Aethereum Launch Film** | `/Users/brunojaamaa/Desktop/aethereum-launch-video/(Flint) Aethereum Launch Film` | the 108-second launch film, built in Remotion |
| **Aethereum Public** | this vault | the public docs repo |

Both siblings are declared as Flint references and auto-fulfil on sync. `ccline` is listed by the hub as cluster-adjacent.

**The cluster in one line:** `hive` builds it, `aethereum-public` publishes its protocol, and the launch film sells it.

## Logging

Every material action here appends to `/Users/brunojaamaa/Desktop/aethereum-public/OBSIDIANLOG.md` through the single writer:

```bash
node "/Users/brunojaamaa/Desktop/Main Vault/Main/Shards/tools/obsidianlog.mjs" \
  --actor claude:main --op note-update --target "<file>" \
  --result "<what happened>" --trigger "<why>" \
  --project "/Users/brunojaamaa/Desktop/aethereum-public"
```

Never append by hand.

## Related

[[(System) Flint Init]] · [[(Map) Master Map]] · [[(Report) Project Summary]]
