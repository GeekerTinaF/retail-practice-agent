# Visualization Guidelines

## The rule

**Every chart must prove one sentence.**

A chart exists only because it tests or supports a specific analytical
message. Having the data available is never a reason to add a chart.

## 1. Procedure

Follow these steps for every chart, in this order.

1. **Write the message first.** Write one declarative sentence that makes a
   claim, e.g. "Clothing prices are rising well below headline inflation."
   A topic label such as "Inflation 2023–2026" is not a message.
2. **Name the data needed to test it.** Choose the smallest dataset that
   could prove or disprove the sentence. If that data is not available from
   a tier 1–2 source, drop the chart.
3. **Test the message against the data.**
   - If the data contradicts the sentence, rewrite the sentence to match
     the data, or drop the chart.
   - Never adjust the framing (axis cropping, selective periods) so the
     data appears to support the sentence.
4. **Choose the form that proves the sentence.**
   - Line: a trend over time.
   - Bar: a comparison across categories.
   - Stacked bar: composition.
   - Scatter: a relationship between two measures, only when that
     relationship is the message.
   - A stat tile instead of a chart when the message is one number.
   - No pie charts unless part-to-whole is the message and there are six
     or fewer segments.
   - No dual axes.
5. **State the metadata** below the chart:
   - source (organisation, dataset or title, update or publication date);
   - period;
   - geography;
   - metric definition (unit, nominal or real, adjustment, index base);
   - evidence label (Reported / Calculated / Forecast).
6. **State the limitations**, including structural breaks, definition
   mismatches, missing periods and proxies used.

## 2. Chart specification block

Write this block (in working notes or an HTML comment) before building any
chart:

```
CHART ID:
MESSAGE (one sentence):
DECISION RELEVANCE: which executive question (report-spec §1) this chart supports
DATA REQUIRED:
DATA USED: source · dataset/title · period · geography · definition · label
TEST RESULT: supports / partially supports (message revised to: …) / does not support (dropped)
FORM + WHY:
LIMITATIONS:
```

## 3. Budget and placement

- **3–5 charts per report** is the default. Each extra chart must answer a
  different executive question.
- If two charts prove the same sentence, keep the stronger one.
- The chart title **is** the message sentence. The subtitle adds the
  quantitative proof, e.g. "gap of X points in [month]".
- Charts belong in the Market Context section. They do not go in the
  Executive Intelligence section, which uses text and signal indicators
  only.

## 4. Build standards

These continue from V0.1.

- **Data provenance:** use official APIs or published tables. Record the
  retrieval date. Store the extracted values in the page so they can be
  traced.
- **Accessibility:**
  - every chart has a data-table view;
  - hover tooltips add detail but never gate a value;
  - two or more series need a legend;
  - use categorical colours from a validated palette, in a fixed order.
- **Recessive chrome:** thin marks, hairline grid, and selective direct
  labels (endpoints and extremes only).
- **Rendering check:** render the chart and inspect it for label
  collisions, clipping and overflow at laptop width (~1440 px) and phone
  width (~375 px).
