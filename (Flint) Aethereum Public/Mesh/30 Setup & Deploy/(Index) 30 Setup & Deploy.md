---
id: 01b94535-a4fe-4833-8792-e54ff4a2814c
title: "30 Setup & Deploy"
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

# 30 Setup & Deploy

**There is no setup and there is no deploy.** This section is one page because that is the honest size of the answer, and because the question it settles is the one most likely to be got wrong.

## Setup

```bash
git clone https://github.com/br9704/aethereum.git
```

That is all. No `npm install` — there is no `package.json`. No build, no dev server, no environment variable, no secret. Five markdown/JSON/bash files, editable in any text editor.

## Deploy

**Nothing is deployed from this repo.** `git push` to `br9704/aethereum` and the change is live on GitHub. There is no build step between the file and the reader.

Evidence, all checked 2026-08-17:

| Check | Result |
|---|---|
| `.github/` workflows | ❌ none |
| `index.html`, `_config.yml`, `CNAME` | ❌ none |
| static-site generator config | ❌ none |
| `package.json` | ❌ none |
| `https://br9704.github.io/aethereum/` | **404** — GitHub Pages is not enabled |

## ⚠️ This repo is NOT the source of `www.aethereum.dev`

This is the question the brief asked, and the answer is unambiguous.

`www.aethereum.dev` is served by **Vercel, running Next.js**, from `apps/web` in the **private `br9704/hive` monorepo**. Verified with live HTTP calls on 2026-08-17:

```
GET https://www.aethereum.dev/               -> 200
     server: Vercel
     x-powered-by: Next.js
     x-vercel-id: syd1::iad1::...
GET https://www.aethereum.dev/docs           -> 200
GET https://www.aethereum.dev/integrations   -> 200
GET https://www.aethereum.dev/api/mcp        -> 401   (live, auth-gated)
GET https://www.aethereum.dev/api/health     -> {"ok":true,"checks":{"db":"ok"}}
```

That last response is a database health check. **A static docs repo does not have a database.** The site is the product's dashboard, and the HIVE vault records the same thing from the other side.

**The relationship is one-directional: this repo points at `aethereum.dev`. It does not produce it.** `README.md` links out to the site three times; the site does not build from anything here. The `/docs` route at `aethereum.dev/docs` is a **separate, Next.js-rendered documentation surface** that lives in `hive`, and it is not derived from `MCP.md`.

That means the estate carries **two independent documentation surfaces** for the same MCP tools:

```
br9704/hive  ──► apps/web on Vercel ──► www.aethereum.dev/docs   (maintained, in-repo tests)
br9704/aethereum ──► GitHub only     ──► MCP.md                   (last touched 2026-06-22)
```

Nothing keeps them in agreement. See [[(Note) Drift Against 0.9.9]].

## How it actually reaches readers

Three routes, and the first is the one that matters:

1. **npm.** `aethereum@0.9.9` declares `repository: https://github.com/br9704/aethereum.git`. Everyone who clicks "Repository" on npmjs.com/package/aethereum arrives here. The package also declares `bugs: https://github.com/br9704/aethereum/issues`, so **this repo is the public issue tracker for the CLI**.
2. **Search.** `github.com/br9704/aethereum` is the URL a person guesses from the package name.
3. **Direct link.** From `aethereum.dev`, if the site links out to it.

## Maintenance

There is only one recurring job, and it is not a deploy: **check `MCP.md` against the product's tool surface.** That is [[(Guide) Shard — Spec Drift Check]].

## Up

[[(Map) Master Map]] · [[(Report) Project Summary]] · [[(Note) What This Repo Is]]
