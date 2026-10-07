---
name: retail-research
description: Use when researching European retail industry topics, retail companies/accounts, retail market news, or preparing retail intelligence for Geek+ EMEA Marketing, Business Development, or Sales. Defines the intelligence chain (market → account → fulfilment → commercial), evidence standards, taxonomies, intelligence-priority scoring, competitor observation, the intelligence watchlist, and report/visualization standards.
---

# Retail Research (European Retail) — V0.2

## Purpose

This skill produces **intelligence, not market research**. Every output feeds
one chain:

**Retail Market Intelligence → Account Intelligence → Fulfilment Intelligence → Commercial Intelligence**

The reader is Geek+ EMEA Marketing, Sales and Sales Operations. Every output
must make clear:

1. **WHAT** changed
2. **WHO** is affected
3. **WHY** it matters operationally
4. **WHERE** automation may be relevant
5. **WHAT** we still do not know
6. **WHAT** should be monitored next

## Scope

- **Geography:** Europe, at country level (see `taxonomy.md`).
- **Subject:** retail market structure, retail companies, and developments
  affecting warehousing, fulfilment, supply chain and automation.
- **Out of scope:**
  - general retail news with no operational implication;
  - speculation about a company without a source;
  - non-European retail, except as a labelled comparison;
  - financial or investment advice.

## Workflow

1. **Frame.** Record the market, segment, time window and research date.
   Check `outputs/` for a previous report on the same scope; if one exists,
   use it as the baseline for "what changed".
2. **Collect.** Apply the source hierarchy and evidence labels in
   `evidence-policy.md`.
3. **Classify.** Tag each finding by country, retail subcategory and news
   type (`taxonomy.md`).
4. **Structure accounts.** Build the **Account Universe** and the **Active
   Account Signals** as separate tables (`report-spec.md` §3–4).
5. **Score.** Give each active signal an **Intelligence Priority** scoring
   record. This is not a sales priority
   (`commercial-intelligence-framework.md` §2).
6. **Observe competitors.** Record every Reported deployment of a tracked
   vendor (`data/competitors.yaml`) in scope (`competitor-observation.md`).
7. **Chain.** For High-priority signals, build the **Commercial Intelligence
   Chain** (`commercial-intelligence-framework.md` §3).
8. **Visualize.** Build a chart only when it proves one sentence
   (`visualization-guidelines.md`).
9. **Watch.** Turn each open question into an **Intelligence Watchlist**
   item with an owner and a next-check date (`report-spec.md` §7).
10. **Write the executive layer last.** Synthesise §1 from the finished
    sections (`report-spec.md` §1).
11. **QA.** Run the checklist at the end of `report-spec.md` before
    delivering.

## Non-negotiables

- **Never invent data.** This covers market size, share, growth, revenue,
  penetration, footprint, automation deployments and strategy. If a detail
  is unknown, write "Unknown" or "Unconfirmed".
- **Label every claim:** Reported / Calculated / Forecast / Analysis /
  Unconfirmed.
- **Trace every number:** source, publication date, unit, period and
  geography.
- **Disclose conflicting sources**, and name the more authoritative one.
- **Never fill an evidence gap with an assumption.** List the gap instead.
- **Never claim a Geek+ relationship** with an account unless a primary or
  Geek+-internal source verifies it.
- **Never state that a company needs a Geek+ solution** unless there is
  direct evidence.
- **Never present intelligence priority as sales priority.** Sales priority
  requires CRM or Sales input.
- **Never compare or disparage competitors.** Record only Reported vendor
  deployments; never claim a vendor's customer is at risk or switching
  (`evidence-policy.md` §10).

## Supporting files

| File | Covers |
|---|---|
| `evidence-policy.md` | Source hierarchy, McKinsey/Deloitte rules, primary company sources, evidence labels, conflicts, gaps, competitor claims |
| `taxonomy.md` | Retail subcategories, country groupings, news classification |
| `report-spec.md` | Report architecture (9 sections), executive intelligence interface, KPI discipline, account model, competitor section, watchlist schema, embedded JSON blocks, signal record format, QA checklist |
| `visualization-guidelines.md` | The "every chart proves one sentence" standard and the chart specification block |
| `commercial-intelligence-framework.md` | Sales-trigger categories, Intelligence Priority scoring and scoring record, Commercial Intelligence Chain link rules, Geek+ relevance rules |
| `competitor-observation.md` | What counts as a vendor observation, the observation record, its effect on scoring and chains, competitor watchlist items |

Reference data lives in `data/`: `countries.yaml`, `subcategories.yaml`,
`sources.yaml`, `accounts.csv` and `competitors.yaml`.
