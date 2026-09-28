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

## Architecture

| # | Section | Answers |
|---|---|---|
| 0 | Header | Scope, dates, data cut-off, label key |
| 1 | Executive Intelligence | The five executive questions |
| 2 | Headline Signals (4–6 KPIs) | Which numbers change the interpretation? |
| 3 | Market Context | Quantitative proof, with charts that each prove one sentence |
| 4 | Segment Intelligence | Apparel / Luxury / Accessories & Jewellery (or the segments of the scope) |
| 5 | Account Universe | Who matters in this market, whether or not there is news |
| 6 | Active Account Signals | Who has verified recent developments, with Intelligence Priority |
| 7 | Fulfilment Intelligence | Where logistics activity is concentrating, and what it means operationally |
| 8 | Commercial Intelligence Chains | For High-priority signals: signal → … → next action |
| 9 | Evidence Gaps & Source Conflicts | What we don't know, and where sources disagree |
| 10 | Intelligence Watchlist | What to monitor, what counts as a signal, source, cadence |
| 11 | Sources & Methodology | Full traceability |

---

## §0 Header

Include:

- title;
- reporting date;
- last-updated timestamp;
- geographic scope, with benchmarks labelled as such;
- industry scope;
- data cut-off per source family;
- research date;
- the label key (Reported / Calculated / Forecast / Analysis / Unconfirmed);
- the relationship disclaimer: no Geek+ relationship is implied unless one
  is cited.

## §1 Executive Intelligence

This is a decision interface, not a summary. It has **five fixed
questions**, answered in this order:

| Question | Answer format |
|---|---|
| **1. Current market state** | A one-line verdict with a state indicator (e.g. Contracting / Flat / Growing; Stressed / Stable). Give 1–2 decisive evidence points. |
| **2. What materially changed** | At most 3 changes since the previous report or the reference period. Each change is one line with its date. |
| **3. Where fulfilment activity is concentrating** | Name the operators, site types and geographies where logistics capacity, investment or change is concentrating. |
| **4. Accounts with meaningful signals** | Accounts with a High or Medium Intelligence Priority, each with band and a 5–8 word signal description. Link to §6. |
| **5. What Geek+ should monitor next** | The top 3–5 watchlist items. Link to §10. |

**Rules**

- About 250 words in total.
- No charts. No numbers without a label.
- Every answer is a judgement (Analysis) supported by 1–2 cited Reported
  facts.
- Do not repeat section content. Synthesise across sections.
- A "Bottom line" of at most two sentences is allowed.

## §2 Headline Signals — KPI discipline

- Show **4–6 KPI cards**. All other quantitative evidence goes in §3.
- **Promotion test:** a KPI is promoted only if it **materially changes the
  interpretation** of the market or the commercial situation. Ask: "If this
  number were different, would the executive conclusion change?" If not,
  put it in §3.
- Each card carries:
  - label;
  - value and unit;
  - period;
  - geography;
  - evidence label;
  - source with date;
  - a **"So what"** line (Analysis, one line).
- Prefer a balanced set that covers demand, channel shift, fulfilment or
  capacity activity, and a commercial or account signal.
- Never promote a KPI because it looks good, and never promote one without
  a reliable source. If one is missing, show fewer cards.

## §3 Market Context

- Holds the supporting quantitative evidence, as compact tables and charts.
- Every chart follows `visualization-guidelines.md`: the message comes
  first, then a spec block, the metadata and the limitations.
- Default of 3–5 charts. Each chart maps to an executive question in §1.

## §4 Segment Intelligence

For each segment, show only the most important developments, at most 2–3
per segment. Each development has these fields:

- **What happened**
- **Evidence** (Reported)
- **Why it matters** (Analysis)
- **Affected companies**
- **Logistics implication** (Analysis)

If a segment has little evidence, say so in an explicit evidence-gap card.
Never pad a thin segment.

## §5 Account Universe

The strategically relevant companies in the market, **whether or not there
is recent news**.

- **Target source:** the account-mapping database, once it exists
  (`accounts/` or a future data file).
- **Until then:** use an **interim universe**.
  - State the inclusion criteria, e.g. a top retailer by fashion revenue in
    a cited ranking, a major platform, a major brand with a German DC, or a
    major 3PL serving fashion.
  - Label the universe "Interim — not from account-mapping database".
- **Fields per account:**
  - company;
  - role (see `taxonomy.md` §4);
  - segment;
  - HQ country;
  - known market logistics footprint (site, type, source);
  - reason for inclusion;
  - active signal (Yes, linking to §6, or No);
  - last verified date.
- Unknown fields stay **"Unknown"**. Never fill a footprint from memory.
- An account is never excluded just because it has no recent news. If it
  has no active signal, record "No verified signal in research window".

## §6 Active Account Signals

Companies with verified developments inside the research window.

- **Columns:**
  - account;
  - signal (Reported);
  - date;
  - country;
  - category;
  - signal categories (framework §1);
  - evidence (source and tier);
  - logistics implication (Analysis);
  - **Intelligence Priority**, showing the seven component scores and the
    band (framework §2).
- Being listed here does **not** make an account a sales opportunity. Say
  so in the section lead.

## §7 Fulfilment Intelligence

Organise by operational theme:

- distribution centres;
- warehouse expansion;
- e-commerce fulfilment;
- omnichannel;
- returns;
- inventory;
- SKU complexity;
- labour;
- peak;
- automation;
- 3PL relationships.

For each theme give the **observed signal** (Reported) and the
**operational implication** (Analysis). Leave out themes with no evidence,
and record them in §9 instead.

## §8 Commercial Intelligence Chains

Build one chain per High-priority signal (framework §3), usually 2–4 chains.

- Present each chain as a 7-step horizontal or vertical flow.
- Show the evidence label on every link.
- Close with the section callout: "No source states that any account
  requires a Geek+ solution; chains are analytical."

## §9 Evidence Gaps & Source Conflicts

A consolidated register with two tables.

**Gaps table columns:**

- what is missing;
- why it matters;
- where it might be found;
- watchlist ID, if the gap became a watch item.

**Conflicts table columns:**

- claim;
- source A value;
- source B value;
- more authoritative source;
- explanation, or "unresolved".

## §10 Intelligence Watchlist

This replaces the generic Outlook. It is designed to be **machine-readable**
so that monitoring can later be automated.

| Field | Content |
|---|---|
| `id` | Stable ID, e.g. `DE-FASH-W01` |
| `account_or_market` | Account name, or market/segment |
| `monitor` | What to monitor |
| `signal_condition` | What would count as a meaningful signal. Make it specific and testable, e.g. "Otto Group names a second site for the Robotic Coordination Layer" |
| `why_it_matters` | Link to the operational or commercial question |
| `expected_source` | Source type plus the specific location (IR page, newsroom URL, Destatis release series, careers page) |
| `cadence` | Daily / weekly / monthly / quarterly / event-driven (e.g. earnings date) |
| `known_dates` | Confirmed scheduled events only (Reported). Unconfirmed dates are marked as such |
| `linked_signal` | §6 row or §9 gap it came from |
| `status` | Open / triggered / closed |

**Rules**

- Separate **confirmed scheduled events** (Reported dates) from **analytical
  expectations**.
- Also embed the watchlist in the HTML as a JSON block
  (`<script type="application/json" id="watchlist">`), so it can be
  extracted later.

## §11 Sources & Methodology

- Numbered source list. For each source give:
  - organisation;
  - title;
  - publication date;
  - URL;
  - access date;
  - tier.
- Methodology notes:
  - research date;
  - source hierarchy used;
  - data retrieval method for charts;
  - the method for every Calculated value;
  - how conflicts were handled.

---

## Signal record format (single items and news monitoring)

Use this format for briefs and news items that are not full reports.

```
## [Headline]
- Date: [publication date]        - Country: [country; grouping]
- Retail subcategory: [...]       - Account: [name or N/A]
- News classification: [primary; others]
- Source: [org, title, URL, tier]
Reported: [fact only]
Analysis: [interpretation]
Signal categories: [framework §1, or "Context only"]
Intelligence Priority: [F/V/T/P/S/E/A scores → band]
Evidence gap: [...]
Next intelligence action: [...]
```

## §13 QA checklist (run before delivery)

1. Every number has a unit, period, geography, source and label.
2. No placeholder or example data remains.
3. Every chart has a message, a spec block, metadata and limitations, and
   was rendered and inspected.
4. There are 4–6 headline KPIs, and each passes the promotion test.
5. The Account Universe includes important accounts even when they have no
   news.
6. Every Intelligence Priority shows its component scores, and the words
   "opportunity", "pipeline" and "sales priority" are not used.
7. Every Commercial Intelligence Chain labels links 3–5 as Analysis, and no
   chain states that a company needs Geek+.
8. Evidence gaps and conflicts are consolidated in §9.
9. Every watchlist item has a testable signal condition, a source and a
   cadence. The JSON block is present.
10. Source links have been checked. Links that block bots are listed for
    manual verification.
11. The layout is readable at ~1440 px and ~375 px, with no horizontal page
    scroll.
