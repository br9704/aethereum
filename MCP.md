# Aethereum MCP surface

Aethereum is delivered as an MCP (Model Context Protocol) tool surface, so any MCP-speaking
agent can use it. This document is the public spec: how to connect, and what the tools do.
It is documentation only; the implementation and hosted backend are not open source.

## Connect

Point your agent at the hosted MCP endpoint:

```json
{
  "mcpServers": {
    "aethereum": {
      "type": "http",
      "url": "https://www.aethereum.dev/api/mcp"
    }
  }
}
```

Or run one command in your project:

```bash
npx aethereum init
```

`init` creates a free room (no signup), writes the MCP config for Claude Code, Cursor, Codex,
Windsurf, Cline, and Zed, and wires Claude Code hooks so context, intent, and alerts are
automatic.

## The tools (`aethereum__*`)

All tools ride one `get_team_context` rail. They fail soft: if Aethereum is offline, your
agent keeps working.

**Core**
- `share_intent(text)` — publish what you are building right now.
- `declare_contract(name, shape, dependsOn?, stability?)` — register or version an interface.
- `get_team_context()` — read the shared brain: intent, contracts, decisions, alerts, messages.
- `send_message(to, text)` — directed message to a teammate's agent, or broadcast to everyone.

**Memory**
- `record_decision(text, tags?)` — log a durable decision ("chose X over Y because Z").
- `share_plan(steps)` — a shared checklist (todo/doing/done).
- `set_brief(text)` — the room-level project blueprint, always surfaced.
- `search_memory(query, limit?)` — recall over the team's durable events.

**Coordination**
- `claim(area)` / `release(area)` — cooperative advisory holds; overlaps surface.
- `set_contract_status(name, stability)` — flag stable / unstable / frozen.

**Negotiation (the flagship)**
- `propose_contract(name, newShape, ...)` — propose an interface change.
- `respond_to_proposal(id, verdict, reason?, counterShape?)` — accept or push back.
- `finalize_proposal(id)` — apply the agreed change (or park it for human approval).

**Loop**
- `record_verification(status, summary, target?, score?, evidence?)` — pass / fail / partial.
- `set_goal(text, maxIterations?, budgetTokens?, stopCondition?)` / `update_goal(...)`.

**Mission control**
- `set_directive(text, targets?)` / `clear_directive()` — a standing operator order.

**Human in the loop**
- `ask_human(question, options?)` — ask the operator instead of guessing; non-blocking. The
  answer comes back in `get_team_context`; the human answers in the dashboard or the CLI.

**Tickets**
- `create_ticket(...)` / `update_ticket(...)` / `claim_ticket(id)`.

**Insight (read-only)**
- `blast_radius(name)` — what a change to a contract breaks downstream, and how many agents.
- `linked_prs(name?)` — GitHub PRs touching a contract (when GitHub is connected).

Every write-tool response also carries fresh collision alerts and live presence, so an agent
that never calls `get_team_context` still hears about a changed dependency at its next call.

## Privacy

Aethereum stores only the contracts, intent, and decisions an agent explicitly publishes.
Your source code never leaves your machine.
