# Commercial Intelligence Framework

This framework turns verified signals into commercial intelligence **without
overstating sales potential**. Its purpose is to decide **where further
intelligence gathering is justified**. It does not rank sales
opportunities.

## 1. Signal (trigger) categories

Tag each active account signal with every category that applies.

| Category | Examples |
|---|---|
| Facility / expansion | New or closed DC, capacity extension, relocation |
| Automation / technology investment | Vendor named, or investment amount stated |
| Leadership change | Supply chain, operations or logistics leadership |
| Financial pressure | Cost-reduction mandate, guidance cut, capex cut, restructuring |
| Labour | Labour shortage, labour cost, labour relations |
| M&A | Network consolidation or integration need |
| Stated automation intent | Public RFP or tender |
| Fulfilment model change | Outsourcing to or from a 3PL or platform; omnichannel redesign |
| Regulatory | Rules that change flows or where stock is held |

A finding that fits no category is recorded as **context**, not as a
signal. Do not force-fit it.

## 2. Intelligence Priority

Intelligence Priority is **not** sales priority. Sales priority needs CRM or
Sales input, which this skill does not have. **Never** use the words
"opportunity", "pipeline" or "sales priority" for a scored signal.

### 2.1 Dimensions

Score each dimension 0, 1 or 2 using these anchors.

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| **Facility event** | None | Existing site changed (extension, closure, retrofit) | New site announced, under construction or ramping up |
| **Volume event** | None, or declining volumes | Growth or consolidation stated in general terms | Quantified volume shift (e.g. an acquisition, network consolidation, or a new client moving volume) |
| **Technology event** | None | General statement of automation or technology intent | Named technology, vendor or investment amount |
| **Operational pain** | None evident | Indirect (cost pressure, margin pressure) | Directly reported in fulfilment (fulfilment cost ratio up, labour dispute, ramp-up cost, capacity constraint) |
| **Timing / project stage** | Completed or fully awarded (>12 months ago) | Live and in optimisation, or plan announced without a date | Upcoming or in progress within 0–18 months (announced, ramping, tender) |
| **Evidence strength** | Unconfirmed only (tier 5 / single secondary) | Tier 3–4 | Tier 1–2 |
| **Automation relevance** | No plausible link to warehouse automation | Indirect link (network, volume, cost) | Direct link to goods-to-person, AMR, picking, sorting, storage or returns processes |

### 2.2 Bands

**Total score:** 0–14.

| Band | Rule | Meaning |
|---|---|---|
| **High** | Total ≥ 10 **and** Evidence strength = 2 **and** Automation relevance ≥ 1 | Build a full Commercial Intelligence Chain (§3). Open deep-dive intelligence actions. |
| **Medium** | Total 6–9, **or** ≥ 10 but failing a gate above | Add to the watchlist with defined signal conditions. |
| **Low** | Total ≤ 5 | Record as context. Review on a periodic cadence. |

**Gates**

- **Evidence gate:** a signal with Evidence strength 0 can never exceed Low.
- **Relevance gate:** a signal with Automation relevance 0 can never
  exceed Low.

**Presentation**

- Always show the seven component scores next to the band, so the reasoning
  is auditable.
- Each score is **Analysis**. Give a one-line rationale for any dimension
  scored 2.

## 3. Commercial Intelligence Chain

Build a chain for every High-priority signal, and optionally for Medium
ones. Each link has a fixed evidence status.

| # | Link | Content | Allowed labels |
|---|---|---|---|
| 1 | **Observed Signal** | What was reported, with a source | Reported / Unconfirmed |
| 2 | **Operational Challenge** | The warehouse or fulfilment problem this creates or reveals | Reported only if the source states it; otherwise Analysis |
| 3 | **Automation Requirement** | The capability the operation would need (e.g. capacity that can scale for peaks, storage density, item picking) | Analysis |
| 4 | **Relevant Automation Use Case** | Generic use case (goods-to-person, AMR transport, sorting, returns, putaway, omnichannel pick) | Analysis |
| 5 | **Potential Geek+ Capability** | The Geek+ product family that could address it, stated as a possibility | Analysis. Never phrase it as a need or a fit confirmed by the company |
| 6 | **Evidence Gap** | What we do not know that would confirm or refute links 2–5 | — |
| 7 | **Next Intelligence Action** | A concrete action: source to check, person or team to ask, event to watch, or a CRM check by Sales Ops | — |

**Rules**

- Links 3–5 are always Analysis unless the company itself has said so
  publicly.
- If link 2 cannot be supported even as reasonable analysis, stop the chain
  and record the signal as context.
- The Next Intelligence Action must be something that can actually be done.
  "Monitor the account" alone is not enough; specify which source and what
  to look for.

## 4. Geek+ relevance rules

- Explain concretely why a development matters for warehouse automation
  (e.g. new DC footprint, SKU growth, peak volatility, labour constraint,
  network change).
- If there is no plausible relevance, write "No clear automation relevance
  identified". Do not force a link.
- Separate **observed fact** from **analytical implication** in every
  relevance statement.
- Capability references:
  - use generic Geek+ product families: goods-to-person / shelf-to-person,
    AMR / mobile robots, sorting, container handling;
  - do not name specific products or claim performance figures unless they
    come from a public Geek+ source, which must be cited;
  - public Geek+ reference cases may be cited, with their exact location
    and scope.
