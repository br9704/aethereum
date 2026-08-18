---
id: 78ea6443-28cf-43ec-a126-df1708a52199
title: "60 Roadmap"
type: "index"
project: "Aethereum Public"
tags:
  - "#index"
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

# 60 Roadmap

**One job, and it is not a feature.** Bring `MCP.md` back into agreement with the product, then make the drift detectable instead of discoverable.

## Notes

| Note | What it answers |
|---|---|
| [[(Note) Drift Against 0.9.9]] | The full comparison, tool by tool, and what to do about it |

## The whole roadmap

- [ ] Add `await_team_events`, `get_contract_history`, `depend_on` and `set_ruleset` to `MCP.md` #task [project:: Aethereum Public] [priority:: high] ^t-0n4tzt3n
- [ ] Mark or remove `clear_directive` and `blast_radius`, both deprecated in the product #task [project:: Aethereum Public] ^t-ejgjfa37
- [ ] Add a short section for the **3 MCP resources** (`aethereum://room/state`, `/contracts`, `/presence`) — small addition, real value to a client author #task [project:: Aethereum Public] ^t-10vaiuu0
- [ ] Decide whether to publish the **5 conditional tools**, and whether to state that the hosted rail carries **30** rather than 29 #task [project:: Aethereum Public] ^t-5fz8ai3t
- [ ] Make drift fail a build. Extend `hive`'s `apps/web/lib/tool-count-consistency.test.ts` to cover this repo, or commit a generated snapshot here that the product's test diffs against #task [project:: Aethereum Public] [priority:: high] ^t-0v9udvus
- [ ] Reconcile the editor list: `README.md` says five, `MCP.md` says six. Cline is in one and not the other #task [project:: Aethereum Public] ^t-sop8rmap
- [ ] Decide the local folder name — rename `aethereum-public` to `aethereum` to match the remote, or record the mismatch permanently #task [project:: Aethereum Public] ^t-izspb0c2
- [ ] Decide whether `(Flint) Aethereum Public/` should be gitignored in the repo #task [project:: Aethereum Public] ^t-vnykmo0t

## What is explicitly NOT on the roadmap

- ⛔ **Do not add a `LICENSE` file.** Its removal was a deliberate second commit: *"remove MIT licence (not open source); all rights reserved"*.
- ⛔ **Do not publish source here.** The repo's entire premise is a public protocol with a private implementation.
- ⛔ **Do not turn it into a site.** `aethereum.dev/docs` already exists, is maintained, and is served from `hive`. A second published site would double the drift surface rather than halve it.

## Up

[[(Map) Master Map]] · [[(Report) Project Summary]]
