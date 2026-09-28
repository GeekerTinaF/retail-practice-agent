# Data

The Retail Practice data layer: reference taxonomies and the account-mapping
table that retail-research outputs draw on.

| File | Purpose |
|---|---|
| `countries.yaml` | Country coverage. Assigns Tier 1 and Tier 2 markets; group entries (Nordics, CEE) list their member countries. |
| `subcategories.yaml` | Retail subcategory taxonomy, with optional segments beneath each subcategory. |
| `sources.yaml` | Source registry: each source's tier (per the skill's evidence policy), type, country and date last used. |
| `accounts.csv` | Account-mapping table, the future basis for a report's Account Universe. **The schema is set; no companies have been added yet.** |

## accounts.csv data dictionary

| Column | Type | Rules |
|---|---|---|
| `account_id` | string | A stable slug that never changes, e.g. `zalando`. |
| `company_name` | string | The legal or trading name. |
| `parent_group` | string | The owning group, if any. Leave empty if none. |
| `role` | enum | One of `retailer_store_led`, `retailer_online_led`, `brand_d2c_wholesale`, `marketplace_platform`, `3pl_fulfilment`, `cross_border_platform` (the account roles in the skill's `taxonomy.md` §4). |
| `subcategory_id` | id | A top-level `id` from `subcategories.yaml`. |
| `segment_id` | id | A segment `id` from `subcategories.yaml`. Leave empty if no segment applies. |
| `hq_country` | ISO2 | The country where the company is headquartered. |
| `operating_countries` | ISO2 list | Separated by `;`, and limited to countries in `countries.yaml`. |
| `known_logistics_footprint` | text | Verified sites only, separated by `;`, each as `site (type, status)`. **Write `Unknown` if nothing has been verified.** |
| `footprint_source_urls` | URL list | Separated by `;`. One or more sources per footprint claim. |
| `inclusion_reason` | text | Why the account belongs in the universe, e.g. its position in a cited ranking. |
| `inclusion_source_urls` | URL list | Separated by `;`. |
| `active_signal` | enum | `yes` or `no`. `yes` means a verified development within the current research window. |
| `intelligence_priority` | enum | `High`, `Medium`, `Low`, or empty. **This is not a sales priority.** |
| `priority_scores` | string | The seven dimension scores, formatted `F2;V2;T1;P2;S2;E2;A1` (per `commercial-intelligence-framework.md` §2). |
| `last_verified` | date | The date the row was last checked, as YYYY-MM-DD. |
| `notes` | text | Anything else, including evidence gaps. |

## Rules

- **Never invent account, footprint or market data.** Write `Unknown` rather
  than guess.
- **Cite a source for every factual field**, using the `*_source_urls`
  columns.
- **Use the reference files for ids and codes.** Country codes and
  subcategory ids must match `countries.yaml` and `subcategories.yaml`.
