# Competitor Observation

This file defines how the skill records **where warehouse-automation
vendors are publicly reported at European retail accounts**. It observes
the market. It does not evaluate, rank or compare vendors.

## 1. Tracked vendors

The tracked list is `data/competitors.yaml`. Only Geek+ EMEA decides who is
on it. Do not add a vendor to the registry because it appeared in research;
record it in the report as "Not tracked" instead (report-spec §5).

## 2. What counts as an observation

An observation is a **Reported** statement, from a tier 1–4 source, that a
named vendor's system is:

- installed or live at a named site;
- contracted, awarded or being integrated at a named account or 3PL;
- in a named pilot or proof of concept; or
- part of a named investment, partnership or equity stake with an account.

**Not observations** (record as context, or not at all):

- a vendor's generic marketing claim with no named account;
- an unnamed customer ("a leading European fashion retailer");
- tier 5 sources (LinkedIn posts, aggregators, AI summaries) — these may
  only point to a source to look for;
- a vendor logo on a trade-show stand or partner list.

A vendor's own case-study or press page counts as tier 1 **for the fact
that the deployment exists**. Its performance claims are the vendor's
claims and are labelled as such ("vendor-reported").

## 3. Observation record

| Field | Content |
|---|---|
| `vendor` | Vendor `id` from `data/competitors.yaml`, or name + "Not tracked" |
| `account` | The retail account whose goods are handled |
| `operator` | The site operator, if different (e.g. a 3PL) |
| `site` | Site name or town, and country (ISO2) |
| `technology` | As described by the source (e.g. "goods-to-person, 32 robots") — do not reclassify |
| `scope` | Processes, SKU range or volume, if Reported; else "Unknown" |
| `stage` | `announced` / `pilot` / `integrating` / `live` / `extended` / `decommissioned` / `investment-only` |
| `date` | Date of the reported event; also the publication date if different |
| `integrator` | Systems integrator, if Reported |
| `source` | Report source number, tier |
| `linked` | Signal ID (report §4) and/or watchlist ID |

Unknown fields stay "Unknown". Never infer a vendor from a technology
description (e.g. "cube storage" does not identify a vendor).

## 4. How observations affect scoring and chains

- A named vendor at the site scores **T = 2** for that signal
  (framework §2.1).
- A deployment that is **live and was awarded more than 12 months ago**,
  with no further phase Reported, scores **S = 0**. A Reported extension,
  new phase or second site scores S on that new event.
- In a chain, the vendor appears in **link 4** as the incumbent, labelled
  Reported. **Link 5** may then only describe Geek+ as complementary (an
  adjacent process, a different site, a later phase). Never write that an
  incumbent is replaceable, underperforming or at risk.
- An observation alone is not a signal. It becomes one only if it also
  fits a framework §1 category inside the research window.

## 5. Watchlist items

Create a watchlist item with `type: competitor` when an observation leaves
an open question that could change a chain, for example:

- whether a pilot moves to rollout;
- whether a live site is extended or a second site is named;
- whether an account that invested in a vendor deploys it.

The `signal_condition` must name the vendor and the event, e.g. "Vendor or
account announces an extension of robots or stations at site Y". Fill the
`competitors` field with the vendor id(s).

## 6. Prohibited

- Comparing vendors on performance, price, reliability or fit.
- Stating or implying that a vendor's customer is dissatisfied or looking
  to switch.
- Repeating a vendor's performance figures as fact (they are
  "vendor-reported").
- Inferring market share or installed base from observations.
- Any claim about a vendor's financial health, strategy or roadmap not
  stated in a tier 1–2 source.
