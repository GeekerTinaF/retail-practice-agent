# Retail Practice Intelligence Agent — Geek+ EMEA

## Purpose

A reusable retail intelligence system supporting **Marketing**, **Business
Development**, and **Sales** at Geek+ EMEA. It is meant to become a shared
source of truth for understanding the retail vertical, the accounts in it,
and how Geek+ is relevant to them.

## Planned coverage (built incrementally, not all at once)

- Retail industry intelligence
- Account mapping
- Market concentration
- News monitoring
- Retail playbooks
- Sales triggers
- Geek+ relevance

## Folder contract

- `.claude/skills/` — Reusable skills this agent uses (e.g. account research,
  news monitoring, playbook generation). Empty until a skill is built.
- `data/` — Raw or reference inputs (market data, taxonomies, source lists).
- `research/` — Research notes and findings (industry trends, market
  structure, news). Always cite sources.
- `accounts/` — One file per account/company once real research is done.
- `playbook/` — Retail-specific sales/BD playbooks, trigger frameworks,
  positioning guidance.
- `outputs/` — Finished deliverables assembled from the above (briefs,
  one-pagers, reports) for Marketing/BD/Sales consumption.

## Ground rules

- **Never invent company, account, or market data.** If information isn't
  verified from a real source, say so instead of filling the gap.
- Research and account files must cite sources.
- Keep the structure simple — don't add folders, abstractions, or tooling
  ahead of actual need.
- This file should stay a short charter, not grow into a spec. Detailed
  process docs belong in the relevant subfolder.

## Status

- Skill: `retail-research` V0.2 (report spec, evidence policy, Intelligence
  Priority, commercial chains, competitor observation).
- Outputs: three V0.2 reports (France Beauty, Germany Furniture, Spain
  Fashion), all dated 28 Sep 2026, written before the 2026-10-07 spec update.
- Data: reference taxonomies, source registry, and tracked competitors are
  set up. `accounts.csv` is still empty.
- Not built yet: news monitoring, playbooks, growth action matrix.
