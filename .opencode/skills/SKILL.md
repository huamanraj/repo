---
name: skills-router
description: >-
  Parent index for this repository's project skills. Read this first to route
  the task to the correct child SKILL.md under skills/. Use when any request
  may match a listed domain below.
---

# Project skills (routing)

When a user request matches a **route** below, open the listed **`SKILL.md`** with the Read tool and follow it for that task. Child skills live next to this file: `skills/<skill-folder>/SKILL.md`.

## Skill list

| Route (keywords / intent) | Folder | Full path (from repo root) |
|---------------------------|--------|----------------------------|
| Synthetic people, fake users, seed personas, fixtures without real PII, anonymized person examples, placeholder names/emails/phones for tests or docs | `example-person-data` | `skills/example-person-data/SKILL.md` |

## Routing rules

1. Prefer the **most specific** match if several could apply.
2. After you pick a route, **read that child `SKILL.md` in full** before generating data or patterns it defines.
3. If nothing matches, **do not** invent a child skill path; handle the request with normal tooling or ask a short clarifying question.

## Adding skills

When a new folder is added under `skills/` with its own `SKILL.md`, append a row to the table above with a clear route line and the folder name so agents keep a single place to discover skills in this repo.
