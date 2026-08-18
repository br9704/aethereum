---
id: f14218bf-8d76-4c73-a84c-8ff4ac14555c
title: "Drift Against 0.9.9"
type: "note"
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

# Drift Against 0.9.9

**Verdict: stale, but not wrong.** Nothing `MCP.md` says is false. It is **incomplete** — it documents **25 of the 29** MCP tools that npm `aethereum@0.9.9` actually ships, and it publishes two tools the product has since deprecated.

## The timeline

| Date | Event |
|---|---|
| 2026-06-10 | `hive` product repo starts |
| **2026-06-22** | **This repo's two commits. `MCP.md` written. Nothing changes here after this date** |
| 2026-07-28 | The product's core-loop audit applies rule R26 and deprecates five tools in their descriptions |
| 2026-08-04 | A re-check un-deprecates two of them (`claim_ticket`, `set_contract_status`) as factually wrong |
| **2026-08-08** | **npm `aethereum` 0.9.9 published** — the 27th version |
| 2026-08-17 | This audit |

**56 days** between the last commit here and today. Roughly **20 of the 27** npm versions were published after this repo was last touched.

## Counting method

`MCP.md`'s bullets were counted by group, and compared against the HIVE vault's `Mesh/10 Architecture/(Note) The MCP Surface.md`, which derives its count from `packages/shared/src/hive/mcp.ts` — **2,442 lines, 34 registrations**, asserted by `packages/shared/src/hive/mcp-surface.test.ts`.

```
MCP.md documents:  4 core + 4 memory + 3 coordination + 3 negotiation
                 + 3 loop + 2 mission control + 1 human + 3 tickets + 2 insight  =  25
Product ships:     29 unconditional  +  5 conditional  +  3 resources
Gap:               25 + 4 = 29 ✓
```

The arithmetic closes exactly, which is a good sign the comparison is sound rather than approximate.

## The four missing tools

| Tool | Group | Consequence of omitting it |
|---|---|---|
| **`await_team_events`** | the rail | ⚠️ **The one that costs something.** It long-polls for up to **28 seconds** and is the closest thing to live push on the hosted rail — no hooks, no tmux. A third-party client author reading only this spec would build a polling loop by hand and never learn the supported mechanism exists |
| `get_contract_history` | contracts | No documented way to read a contract's version history |
| `depend_on` | contracts | ⚠️ This is what makes alerts **dependency-aware**, which is the README's headline claim. Publishing the claim without the tool that produces it is the sharpest inconsistency in the repo |
| `set_ruleset` | contracts | Room-level rules are undocumented |

Note that three of the four are contract tools. **The contract group is the product's flagship and the least completely documented group in its public spec.**

## Two tools published that the product deprecates

Both are deprecated **in their description only** and remain registered, so they still work — the spec is not broken, just behind the product's own guidance.

- `clear_directive`
- `blast_radius`

Both failed rule **R26** in the 2026-07-28 audit: *"If the daemon, the hook, or the diff could have produced the argument, it is not a tool."*

## Omitted entirely, without acknowledgement

**5 conditional tools:**

| Tool | Gate |
|---|---|
| `share_code` · `fetch_code` · `list_code` | capability `codeSharing`, disabled by `AETHEREUM_CODE_SHARING=0` |
| `offer_handoff` | opt-in, `AETHEREUM_OFFER_HANDOFF=1` |
| `room_view` | registered when a live view URL resolves |

⚠️ `room_view` **always resolves server-side**, so the **hosted `/api/mcp` rail carries 30 tools, not 29** — and the hosted rail is the only one this document tells you to connect to.

**3 MCP resources:** `aethereum://room/state` · `aethereum://room/contracts` · `aethereum://room/presence`. Not mentioned at all. A resources section is a five-line addition with genuine value to anyone building a client.

## The counts you would quote, and which are safe

| Claim | Safe? |
|---|---|
| "all tools ride one `get_team_context` rail" | ✅ accurate |
| "they fail soft" | ✅ accurate — rule R15 in the product |
| the negotiation trio is the flagship | ✅ accurate |
| "delivered exactly once" (alerts) | ✅ accurate — `get_team_context` consumes a cursor |
| "source code never leaves your machine" | ✅ accurate as written, with a nuance: three gated tools exist to move code, disabled by default |
| **any specific tool count** | ⚠️ `MCP.md` never states a number, which is the one thing that saves it. Do not add one without generating it |

That last row is worth keeping. **The spec's own restraint is what keeps it merely incomplete rather than false.**

## Why nothing caught this

`hive` carries `apps/web/lib/tool-count-consistency.test.ts`, which cross-checks every "N tools" claim in its own README and marketing copy against the code, and `packages/shared/src/hive/mcp-surface.test.ts`, which asserts the registration count. The HIVE vault's rule is blunt: **"Change a tool, change that test."**

**Neither test can see this repo.** It is in a different git repository, on a different remote, with no shared build. The drift was structurally undetectable until someone looked.

That is the finding worth acting on — not the four missing bullets, but the fact that nothing would have told anyone.

## Related

[[(Note) The MCP Spec]] · [[(Guide) Shard — Spec Drift Check]] · [[(Note) Git History]] · [[(Index) 60 Roadmap]]
