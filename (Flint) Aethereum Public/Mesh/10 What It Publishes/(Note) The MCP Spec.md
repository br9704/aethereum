---
id: aab6b829-b047-4285-b75e-c67d9bca99a8
title: "The MCP Spec"
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

# The MCP Spec

**`MCP.md`, 3,168 bytes, is the only file in this repo that could not be reconstructed from the marketing site.** It is the published tool surface, and it is why the repo is worth keeping.

## The framing

> Aethereum is delivered as an MCP (Model Context Protocol) tool surface, so any MCP-speaking agent can use it. This document is the public spec: how to connect, and what the tools do. **It is documentation only; the implementation and hosted backend are not open source.**

Two connection routes are published: point an agent at `https://www.aethereum.dev/api/mcp`, or run `npx aethereum init`, which *"creates a free room (no signup), writes the MCP config for Claude Code, Cursor, Codex, Windsurf, Cline, and Zed, and wires Claude Code hooks so context, intent, and alerts are automatic."*

Two structural claims frame the whole surface, and both are accurate against the product:

1. **"All tools ride one `get_team_context` rail."**
2. **"They fail soft: if Aethereum is offline, your agent keeps working."** This is rule **R15** in the product: every handler fails soft with an `OFFLINE` or cap sentinel and never throws.

## The 25 tools it publishes

All prefixed `aethereum__`.

| Group | Tools | Count |
|---|---|---|
| **Core** | `share_intent` · `declare_contract` · `get_team_context` · `send_message` | 4 |
| **Memory** | `record_decision` · `share_plan` · `set_brief` · `search_memory` | 4 |
| **Coordination** | `claim` · `release` · `set_contract_status` | 3 |
| **Negotiation (the flagship)** | `propose_contract` · `respond_to_proposal` · `finalize_proposal` | 3 |
| **Loop** | `record_verification` · `set_goal` · `update_goal` | 3 |
| **Mission control** | `set_directive` · `clear_directive` | 2 |
| **Human in the loop** | `ask_human` | 1 |
| **Tickets** | `create_ticket` · `update_ticket` · `claim_ticket` | 3 |
| **Insight (read-only)** | `blast_radius` · `linked_prs` | 2 |
| | | **25** |

Each carries a one-line signature and description. The negotiation trio gets the "flagship" label, matching the `README.md` pitch.

Two behaviours are documented beyond the list, and both are real:

- **Write-tool responses carry fresh state.** *"Every write-tool response also carries fresh collision alerts and live presence, so an agent that never calls `get_team_context` still hears about a changed dependency at its next call."*
- **`ask_human` is non-blocking.** The answer comes back in `get_team_context`; the human answers in the dashboard or the CLI.

## ⚠️ The four tools it does not publish

npm `aethereum@0.9.9` ships **29** unconditional tools. `MCP.md` documents 25. The gap, exactly:

| Missing | Group | Why it matters |
|---|---|---|
| **`await_team_events`** | the rail | **The costly one.** Long-polls for up to 28 seconds, and is the closest thing to live push on the hosted rail with no hooks and no tmux required. A third-party client reading only this spec has no way to know it exists |
| `get_contract_history` | contracts | Version history for a contract |
| `depend_on` | contracts | Declares a dependency, which is what makes blast-radius and alerts dependency-aware |
| `set_ruleset` | contracts | Room-level rules |

It also omits, entirely and without acknowledgement:

- **5 conditional tools** — `share_code`, `fetch_code`, `list_code` (gated by the `codeSharing` capability), `offer_handoff` (opt-in), `room_view` (registered when a live view URL resolves). Notably `room_view` **always** resolves on the hosted rail, so the hosted surface is **30**, not 29.
- **3 MCP resources** — `aethereum://room/state`, `aethereum://room/contracts`, `aethereum://room/presence`. A resources section would be a small addition with real value to a client author.

And it publishes **two tools the product marks deprecated in their description**: `clear_directive` and `blast_radius`.

Full analysis and the counting method in [[(Note) Drift Against 0.9.9]].

## The privacy section

Two sentences, and they are the product's core promise:

> Aethereum stores only the contracts, intent, and decisions an agent explicitly publishes. **Your source code never leaves your machine.**

The same claim appears in `README.md`. The one nuance the spec does not surface: three conditional tools (`share_code`, `fetch_code`, `list_code`) exist precisely to move code, behind a capability gate disabled by `AETHEREUM_CODE_SHARING=0`. Publishing the gate alongside the promise would strengthen the claim rather than weaken it.

## Related

[[(Note) Drift Against 0.9.9]] · [[(Note) The README and Examples]] · [[(Guide) Shard — Spec Drift Check]] · [[(Index) 10 What It Publishes]]
