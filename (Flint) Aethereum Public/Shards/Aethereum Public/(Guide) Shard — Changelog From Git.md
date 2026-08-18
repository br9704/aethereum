---
id: 362fd126-740a-447e-b4d5-cde65887f2ec
title: "Shard — Changelog From Git"
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
source_path: "/Users/brunojaamaa/Desktop/aethereum-public/.git"
---

# Shard — Changelog From Git

**Purpose.** Keep [[(Note) Git History]] and the `last_commit` frontmatter in [[(Report) Project Summary]] accurate.

**Run when.** A commit lands here. Given the history, that is rare — **a third commit is itself the news.**

## Steps

```bash
cd "$(flint resolve codebase 'Aethereum Public' | head -1)"
git log --format='%h|%ad|%an|%s' --date=iso
git rev-list --count HEAD
git branch -a
git status --short
git log @{u}.. --oneline | wc -l
git remote -v
```

Then:

1. **Note the commit count.** It has been **2** since 2026-06-22. Any change is material and should be reported to the hub, not just recorded here.
2. **Read every new commit's diff.** With a repo this small there is no excuse for summarising.
   ```bash
   git show --stat <sha>
   ```
3. **Check whether the commit closed a drift item.** If `MCP.md` changed, re-run [[(Guide) Shard — Spec Drift Check]] immediately and update [[(Note) Drift Against 0.9.9]] rather than leaving two accounts of the same fact.
4. ⚠️ **Check whether a `LICENSE` file appeared.** Its absence is a deliberate decision (`b2c6954 remove MIT licence (not open source); all rights reserved`). If one has been added, that is a **licensing change**, not a housekeeping commit, and it needs escalating.
5. Update [[(Note) Git History]], then `last_commit` and `status` in [[(Report) Project Summary]] frontmatter, then the counts in [[(Index) 00 Overview]].
6. Log with `--op note-update`, then `flint sync`.

## The status question

The project is `shipped`, not `dormant`. Keep it that way while the repo says the right thing and needs no commits. **If `MCP.md` falls far enough behind that it misleads a reader, `shipped` stops being true** — at that point it is `active` with work outstanding, or the repo should be pointed elsewhere. Judge it against [[(Note) Drift Against 0.9.9]], not against the calendar.

## Guardrails

- **Read-only git only:** `log`, `show`, `status`, `branch`, `diff`, `diff --stat`.
- Never `commit`, `push`, `checkout`, `stash`, `reset`, `clean`, or any `gh repo` command.

## Related

[[(Note) Git History]] · [[(Report) Project Summary]] · [[(Guide) Shard — Spec Drift Check]]
