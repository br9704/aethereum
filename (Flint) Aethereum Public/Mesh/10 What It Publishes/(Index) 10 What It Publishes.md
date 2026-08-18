---
id: dfe5290f-e747-47ab-aebb-4a50804c7c77
title: "10 What It Publishes"
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

# 10 What It Publishes

**Five files, 7,676 bytes, three jobs.** Explain the product, specify the protocol, get someone running in one command.

## Notes

| Note | What it answers |
|---|---|
| [[(Note) The MCP Spec]] | `MCP.md` — the 25 published tools, and the 4 that are missing |
| [[(Note) The README and Examples]] | The pitch, the licence position, and the two example files |

## The complete contents

| File | Bytes | Job |
|---|---|---|
| `README.md` | 4,044 | Explain the product and state the licence |
| `MCP.md` | 3,168 | **Specify the protocol.** The reason the repo is worth keeping |
| `examples/mcp.json` | 111 | Copy-paste MCP config for any MCP-speaking agent |
| `examples/init.sh` | 279 | The one-command quickstart, plus two commented follow-ups |
| `.gitignore` | 74 | Node boilerplate for a repo containing no Node |

That is the entire repository. There is no sixth file.

## The one connection string

Both `README.md` and `MCP.md` publish the same endpoint, and `examples/mcp.json` is that block on its own:

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

Verified 2026-08-17: `https://www.aethereum.dev/api/mcp` returns HTTP **401**, which is correct — the rail exists and requires auth.

## Up

[[(Map) Master Map]] · [[(Index) Complete File Inventory]]
