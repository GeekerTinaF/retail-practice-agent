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

Scores belong to **signals**, not to accounts. An account with two signals
has two scores.

### 2.1 Dimensions

Score each dimension 0, 1 or 2 using these anchors.

| Code | Dimension | 0 | 1 | 2 |
|---|---|---|---|---|
| F | **Facility event** | None | Existing site changed (extension, closure, retrofit) | New site announced, under construction or ramping up |
| V | **Volume event** | None, or declining volumes | Growth or consolidation stated in general terms | Quantified volume shift (e.g. an acquisition, network consolidation, or a new client moving volume) |
| T | **Technology event** | None | General statement of automation or technology intent | Named technology, vendor or investment amount |
| P | **Operational pain** | None evident | Indirect (cost pressure, margin pressure) | Directly reported in fulfilment (fulfilment cost ratio up, labour dispute, ramp-up cost, capacity constraint) |
| S | **Timing / project stage** | Completed or fully awarded (>12 months ago) | Live and in optimisation, or plan announced without a date | Upcoming or in progress within 0–18 months (announced, ramping, tender) |
| E | **Evidence strength** | Unconfirmed only (tier 5 / single secondary) | Tier 3–4 | Tier 1–2 |
| A | **Automation relevance** | No plausible link to warehouse automation | Indirect link (network, volume, cost) | Direct link to goods-to-person, AMR, picking, sorting, storage or returns processes |

**Scoring notes**

- **E** is scored on the **best source for the signal itself**, not for
  surrounding context. A tier 1 revenue figure does not raise E for a
  site-level fact reported only in trade press.
- **T and S with a competitor present:** a named vendor scores T = 2. If
  that vendor's deployment is complete and was awarded more than 12 months
  ago, S = 0 unless a further phase is Reported (see
  `competitor-observation.md` §4).
- When in doubt between two scores, take the **lower** one and say why.

### 2.2 Bands

**Total score:** 0–14.

| Band | Rule | Meaning |
|---|---|---|
| **High** | Total ≥ 10 **and** E = 2 **and** A ≥ 1 | Build a full Commercial Intelligence Chain (§3). Open deep-dive intelligence actions. |
| **Medium** | Total 6–9, **or** ≥ 10 but failing a gate above | Add to the watchlist with defined signal conditions. A chain is optional. |
| **Low** | Total ≤ 5 | Record as context. Review on a periodic cadence. |

**Gates**

- **Evidence gate:** a signal with E = 0 can never exceed Low. A signal
  with E = 1 can never exceed Medium.
- **Relevance gate:** a signal with A = 0 can never exceed Low.

### 2.3 Rationale rules

- Every **non-zero** score gets a short rationale (a few words), e.g.
  "F2 new 22,000 m² site due 2026".
- Every score of **2** cites the source number that supports it.
- Every score is **Analysis**. The rationale must point to Reported facts;
  it must not introduce new facts.

### 2.4 Scoring record

Present every scored signal in this form. It is the content of the
Intelligence Priority cell in report §4 and of the `signals-data` JSON.

```
Signal ID:   [CC]-[SUB]-S[nn]
Scores:      F_ V_ T_ P_ S_ E_ A_      Total: __ / 14
Gate:        Passed | Evidence gate (E=_) | Relevance gate (A=0)
Band:        High | Medium | Low
Rationale:   F_ … · V_ … · T_ … · P_ … · S_ … · E_ … · A_ …
Change:      [band in previous report → band now, with reason] | First scored
```

### 2.5 Worked example (illustrative — not a real account)

> Account X announces a new 30,000 m² e-commerce DC due in 12 months
> (company press release, tier 1), citing order growth of 40% and a named
> AMR vendor.
>
> F2 new site due within 12 months [1] · V2 quantified order growth [1] ·
> T2 vendor named [1] · P0 no fulfilment pain reported · S2 in progress,
> 0–18 months [1] · E2 tier 1 · A2 AMR picking.
> **Total 12 → gates passed → High.**
>
> The same facts reported only in trade press give E1 → total 11 →
> evidence gate → **Medium**.

### 2.6 Band changes between reports

When a previous report on the same scope exists, compare each signal that
appears in both:

- show the band change and the dimension(s) that moved;
- a signal that has dropped out (completed, cancelled, no longer in the
  window) is listed once as "Resolved" with the reason;
- never raise a band without a new or stronger source.

## 3. Commercial Intelligence Chain

Build a chain for every High-priority signal, and optionally for Medium
ones.

### 3.1 Links

| # | Link | Content | Allowed labels |
|---|---|---|---|
| 1 | **Observed Signal** | What was reported, with a source | Reported / Unconfirmed |
| 2 | **Operational Challenge** | The warehouse or fulfilment problem this creates or reveals | Reported only if the source states it; otherwise Analysis |
| 3 | **Automation Requirement** | The capability the operation would need (e.g. capacity that can scale for peaks, storage density, item picking) | Analysis |
| 4 | **Relevant Automation Use Case** | Generic use case (goods-to-person, AMR transport, sorting, returns, putaway, omnichannel pick), plus any Reported incumbent vendor | Analysis (incumbent: Reported) |
| 5 | **Potential Geek+ Capability** | The Geek+ product family that could address it, stated as a possibility | Analysis. Never phrase it as a need or a fit confirmed by the company |
| 6 | **Evidence Gap** | What we do not know that would confirm or refute links 2–5 | — |
| 7 | **Next Intelligence Action** | A concrete action that closes a link-6 gap | — |

### 3.2 Link record

Each link carries:

- **label** (from the table above);
- **source refs** (numbers from report §8), required for links 1 and 2 and
  for any incumbent vendor in link 4;
- **confidence** (High / Medium / Low, using the rule in report-spec §1a);
- **text**: one or two sentences.

Link-specific requirements:

| Link | Requirement |
|---|---|
| 1 | Quote the fact, not its interpretation. Date and source tier visible. |
| 2 | Say whether the challenge is **stated by the source** (Reported) or **inferred** (Analysis). |
| 3 | Describe a capability, not a product. |
| 4 | Name the generic use case. If a vendor is Reported at the site, name it and its scope (`competitor-observation.md`). If none is known, write "Incumbent vendor: Unknown". |
| 5 | Use only generic Geek+ product families (§4). If an incumbent exists, phrase the possibility as complementary, an adjacent process, or a later phase — never as replacement. |
| 6 | Each gap is a question that can be answered. List the watchlist ID(s) it feeds. |
| 7 | Format: **action · source to check · owner · check-by date**. One action per gap where possible. |

### 3.3 Stop rules

- Links 3–5 are always Analysis unless the company itself has said so
  publicly.
- If link 2 cannot be supported even as reasonable analysis, **stop the
  chain** at link 1 and record the signal as context.
- If link 3 cannot be stated without assuming the company's internal
  processes, stop at link 2, write the assumption as a link-6 gap, and still
  give a link 7.
- The Next Intelligence Action must be something that can actually be done.
  "Monitor the account" alone is not enough; specify which source and what
  to look for. "Sales Ops to run a CRM check on [account]" is a valid action.

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
- Never compare Geek+ with a competitor's performance, price or
  suitability (`evidence-policy.md` §10).
