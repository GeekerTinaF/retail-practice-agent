# Report Specification — V0.2

This spec defines the standard retail intelligence report. By default it is a
self-contained HTML file in `outputs/`, with no build step and no external
data calls at view time.

The report is an **intelligence system output** that runs:

**Market → Account → Fulfilment → Commercial**

It is not a market-research report. Every section must help Marketing, Sales
and Sales Ops answer: what changed, who is affected, why it matters
operationally, where automation may be relevant, what we don't know, and
what to monitor next.

The spec is market-neutral. Replace `[country]`, `[subcategory]` and the
segment names with the report's scope (segments come from `taxonomy.md` §1
and `data/subcategories.yaml`).

## Architecture

| # | Section | Answers |
|---|---|---|
| 0 | Header | Scope, dates, data cut-off, label key, disclaimer |
| 1 | Executive Intelligence | Five questions, headline KPIs, competitor line |
| 2 | Market & Fulfilment Context | Quantitative proof (charts), segment developments, fulfilment themes |
| 3 | Account Universe | Who matters in this market, whether or not there is news |
| 4 | Active Account Signals | Who has verified recent developments, with a scored Intelligence Priority |
| 5 | Competitor Landscape | Which tracked automation vendors are verifiably present, and where |
| 6 | Commercial Intelligence Chains | For High-priority signals: signal → … → next action |
| 7 | Intelligence Watchlist | What to monitor, what counts as a signal, source, owner, next check |
| 8 | Evidence Gaps, Conflicts & Sources | What we don't know, where sources disagree, full traceability |

Sections 3 and 4 are always separate tables. An account appears in §3
whether or not it has a signal. §4 holds only verified developments in the
research window.

---

## §0 Header

Include:

- title;
- reporting date and last-updated timestamp;
- research date and research window for account signals;
- geographic scope, with benchmarks labelled as such;
- industry scope (subcategory and segments);
- data cut-off per source family;
- the label key (Reported / Calculated / Forecast / Analysis / Unconfirmed);
- the relationship disclaimer: no Geek+ relationship is implied unless one
  is cited;
- the previous report on the same scope, if one exists (file name and date).

## §1 Executive Intelligence

This is a decision interface, not a summary. It has three parts, in this
order.

### 1a. The five questions

| Question | Answer format |
|---|---|
| **1. Current market state** | A state indicator per dimension (e.g. Demand: Contracting / Flat / Growing; Online: Slowing / Growing; Operators: Stressed / Stable), then a one-line verdict. 1–2 decisive evidence points. |
| **2. What materially changed** | At most 3 changes. Each is one line with its date. If a previous report exists, compare against it and say "New", "Escalated" or "Resolved". If none exists, say "First report on this scope; changes are within the research window". |
| **3. Where fulfilment activity is concentrating** | Name the operators, site types and geographies where logistics capacity, investment or change is concentrating. |
| **4. Accounts with meaningful signals** | High and Medium signals only, each with band, total score and a 5–8 word description, linking to §4. If nothing reaches High, say why in one line (which gate failed). |
| **5. What Geek+ should monitor next** | The top 3–5 watchlist items, highest priority and nearest check date first, linking to §7. |

Each answer carries a **confidence** tag:

| Confidence | Rule |
|---|---|
| **High** | Supported by at least one tier 1–2 source, with no unresolved conflict |
| **Medium** | Supported by tier 3–4 sources only, or by tier 1–2 with an unresolved conflict |
| **Low** | Rests on a single source, on Unconfirmed items, or on a known evidence gap |

Confidence describes the evidence, not the judgement. It is not a label on
its own; the answer still carries Analysis and the cited facts still carry
Reported.

### 1b. Headline KPIs (4–6 cards)

- **Promotion test:** a KPI is promoted only if it **materially changes the
  interpretation** of the market or the commercial situation. Ask: "If this
  number were different, would the executive conclusion change?" If not,
  put it in §2.
- Each card carries: label; value and unit; period; geography; evidence
  label; source with date; a **"So what"** line (Analysis, one line).
- Prefer a balanced set that covers demand, channel shift, fulfilment or
  capacity activity, and a commercial or account signal.
- Never promote a KPI because it looks good, and never promote one without
  a reliable source. If one is missing, show fewer cards.

### 1c. Competitor line

One line: which tracked vendors (`data/competitors.yaml`) were verifiably
observed in this scope, with links to §5. If none: "No tracked vendor
verifiably observed in this scope."

### Rules

- About 300 words for 1a and 1c combined.
- No charts. No numbers without a label.
- Every answer is a judgement (Analysis) supported by 1–2 cited Reported
  facts.
- Do not repeat section content. Synthesise across sections.
- A "Bottom line" of at most two sentences is allowed.

## §2 Market & Fulfilment Context

One section with three blocks.

### 2a. Market evidence

- Supporting quantitative evidence, as compact tables and charts.
- Every chart follows `visualization-guidelines.md`: the message comes
  first, then a spec block, the metadata and the limitations.
- Default of 3–5 charts. Each chart maps to an executive question in §1.

### 2b. Segment developments

For each segment, at most 2–3 developments. Each has:

- **What happened**
- **Evidence** (Reported)
- **Why it matters** (Analysis)
- **Affected companies**
- **Logistics implication** (Analysis)

If a segment has little evidence, say so in an explicit evidence-gap card.
Never pad a thin segment.

### 2c. Fulfilment themes

Organise by operational theme: distribution centres; warehouse expansion;
e-commerce fulfilment; omnichannel; returns; inventory; SKU complexity;
labour; peak; automation; 3PL relationships.

For each theme give the **observed signal** (Reported) and the
**operational implication** (Analysis). Leave out themes with no evidence,
and record them in §8 instead.

## §3 Account Universe

The strategically relevant companies in the market, **whether or not there
is recent news**.

- **Target source:** `data/accounts.csv`, once it holds rows for this scope.
- **Until then:** use an **interim universe**.
  - State the inclusion criteria, e.g. a top retailer by revenue in a cited
    ranking, a major platform, a major brand with a logistics site in
    `[country]`, or a major 3PL serving `[subcategory]`.
  - Label the universe "Interim — not from account-mapping database".
- **Fields per account:**
  - company;
  - parent group;
  - role (see `taxonomy.md` §4);
  - segment;
  - HQ country;
  - known logistics footprint in `[country]` (site, type, source);
  - known automation vendor(s), Reported only, else "Unknown";
  - reason for inclusion;
  - active signal (Yes, linking to §4, or "No verified signal in research
    window");
  - last verified date.
- Unknown fields stay **"Unknown"**. Never fill a footprint or a vendor
  from memory.
- An account is never excluded just because it has no recent news.
- §3 carries **no priority score**. Scores belong to signals, not accounts.

## §4 Active Account Signals

Companies with verified developments inside the research window.

- **Section lead (fixed text):** "Being listed here does not make an account
  a sales opportunity. Intelligence Priority shows where more intelligence
  gathering is justified."
- **Columns:**
  - signal ID (e.g. `[CC]-[SUB]-S01`);
  - account;
  - signal (Reported);
  - date;
  - signal categories (framework §1);
  - evidence (source and tier);
  - logistics implication (Analysis);
  - **Intelligence Priority**: the scoring record from framework §2.4 —
    seven component scores, total, band, gate result and rationale.
- One row per signal. An account with two unrelated developments gets two
  rows.
- If a previous report exists, show the band change (e.g. "Medium → High")
  and its reason.
- Also embed the signals as JSON (`<script type="application/json"
  id="signals-data">`), using the fields in "Embedded data blocks" below.

## §5 Competitor Landscape

Follow `competitor-observation.md`.

- **Section lead (fixed text):** "Observations record where a tracked
  vendor is publicly reported at a retail account or its 3PL. They are not
  an assessment of any vendor."
- **Columns:** vendor; account (and operator, if a 3PL runs the site);
  site and country; technology as described by the source; deployment
  stage; date; source and tier; linked signal (§4) or watchlist ID.
- Include non-tracked vendors only if they appear in a §4 signal, and mark
  them "Not tracked".
- If no tracked vendor is observed, say so in one line. Do not pad.

## §6 Commercial Intelligence Chains

Build one chain per High-priority signal (framework §3), usually 2–4
chains. Medium signals may get a chain when the evidence supports one.

- Present each chain as a 7-step flow, using the link record in framework
  §3.2.
- Show the evidence label and confidence on every link.
- Link 6 lists watchlist IDs; link 7 shows owner and check-by date.
- Close with the section callout: "No source states that any account
  requires a Geek+ solution; chains are analytical."

## §7 Intelligence Watchlist

This replaces the generic Outlook. It is **machine-readable** so that
monitoring can later be automated.

| Field | Content |
|---|---|
| `id` | Stable ID: `[CC]-[SUB]-W[nn]`, e.g. `FR-BEAU-W01`. Never reused. |
| `account_or_market` | Account name, or market/segment |
| `type` | `account` / `market` / `regulatory` / `competitor` |
| `monitor` | What to monitor |
| `signal_condition` | What would count as a meaningful signal. Specific and testable, e.g. "Company X names a vendor for site Y" |
| `why_it_matters` | Link to the operational or commercial question |
| `expected_source` | Source type plus the specific location (IR page, newsroom URL, statistics release series, careers page) |
| `cadence` | Daily / weekly / monthly / quarterly / event-driven |
| `known_dates` | Confirmed scheduled events only (Reported). Unconfirmed dates are marked as such |
| `next_check` | The date the item should next be checked (YYYY-MM-DD): the earliest known date, or today + cadence |
| `priority` | Band of the linked signal (`High` / `Medium` / `Low`), or `Gap` if it came from §8 only |
| `owner` | Team responsible for checking: `Marketing` / `BD` / `Sales Ops` / `Retail Practice` |
| `linked_signal` | Signal ID (§4) and/or gap ID (§8) it came from |
| `competitors` | Tracked vendor ids involved (from `data/competitors.yaml`), or empty |
| `close_condition` | What evidence would close the item (e.g. "tier 1 confirmation of go-live") |
| `status` | `Open` / `Triggered` / `Closed` |
| `last_checked` | YYYY-MM-DD, or empty if never checked since the report |

**Rules**

- Sort the table by `priority`, then `next_check`.
- Separate **confirmed scheduled events** (Reported dates) from **analytical
  expectations**.
- A triggered item produces a signal record (format below). It does not
  silently change the report.
- Embed the watchlist as JSON (`<script type="application/json"
  id="watchlist-data">`), as an array of objects with the fields above.

## §8 Evidence Gaps, Conflicts & Sources

**Gaps table:** gap ID (`G[nn]`); what is missing; why it matters; where it
might be found; watchlist ID, if the gap became a watch item.

**Conflicts table:** claim; source A value; source B value; more
authoritative source; explanation, or "unresolved".

**Sources:** numbered list. For each source give organisation; title;
publication date; URL; access date; tier.

**Methodology notes:** research date; source hierarchy used; data retrieval
method for charts; the method for every Calculated value; how conflicts were
handled; links that blocked automated access and need manual checking.

---

## Embedded data blocks

Both blocks are JSON arrays, so they can be extracted without parsing the
page.

**`signals-data`** — one object per §4 row:

```json
{
  "id": "FR-BEAU-S01",
  "account": "…",
  "signal": "…",
  "date": "YYYY-MM or YYYY-MM-DD",
  "categories": ["Facility / expansion"],
  "sources": [14],
  "evidence_tier": 3,
  "scores": {"F": 2, "V": 2, "T": 1, "P": 1, "S": 2, "E": 1, "A": 2},
  "total": 11,
  "band": "Medium",
  "gate": "Evidence gate failed (E=1)",
  "competitors": ["scallog"],
  "watchlist": ["FR-BEAU-W01"]
}
```

**`watchlist-data`** — one object per §7 row, with the §7 field names.

---

## Signal record format (single items and news monitoring)

Use this format for briefs and news items that are not full reports.

```
## [Headline]
- Date: [publication date]        - Country: [country; grouping]
- Retail subcategory: [...]       - Account: [name or N/A]
- News classification: [primary; others]
- Source: [org, title, URL, tier]
- Watchlist item: [ID, if this triggered one]
Reported: [fact only]
Analysis: [interpretation]
Signal categories: [framework §1, or "Context only"]
Intelligence Priority: [F/V/T/P/S/E/A scores → total → band; gate result]
Competitor observation: [vendor id + stage, or "None"]
Evidence gap: [...]
Next intelligence action: [action · owner · check-by date]
```

## QA checklist (run before delivery)

1. Every number has a unit, period, geography, source and label.
2. No placeholder or example data remains.
3. Every chart has a message, a spec block, metadata and limitations, and
   was rendered and inspected.
4. There are 4–6 headline KPIs, and each passes the promotion test.
5. Every executive answer has a confidence tag that follows the rule.
6. The Account Universe (§3) and Active Account Signals (§4) are separate
   tables; §3 includes important accounts with no news and carries no
   scores.
7. Every signal shows its scoring record (seven scores, total, band, gate,
   rationale), and the words "opportunity", "pipeline" and "sales priority"
   are not used for a signal.
8. Every competitor observation has a source and tier, and none compares
   vendor performance or states that a vendor is displaceable.
9. Every chain labels links 3–5 as Analysis, links link 6 to a watchlist ID,
   gives link 7 an owner and date, and no chain states that a company needs
   Geek+.
10. Evidence gaps and conflicts are consolidated in §8.
11. Every watchlist item has a testable signal condition, a source, a
    cadence, a `next_check` date and an owner. Both JSON blocks are present
    and parse.
12. Source links have been checked. Links that block bots are listed for
    manual verification.
13. The layout is readable at ~1440 px and ~375 px, with no horizontal page
    scroll.
