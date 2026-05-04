# East Africa Spice Sector — SME Lending Pipeline

An internal tool for tracking agri-SME lending candidates across Uganda, Madagascar, and Tanzania. Built for the CRS Innovative Finance team as part of the design process for a spice sector lending facility.

## What this is

A filterable, sortable directory of spice sector SMEs evaluated as potential borrowers for a new CRS-managed lending facility. Each entry includes a financial profile (revenues, staff, capital need), CRS relationship status, donor/investor history, and data confidence ratings that distinguish between verified figures, company-reported numbers, and estimates derived from proxy signals.

This is a working document, not a published dataset. Figures are updated as research and interviews progress.

## Structure

```
spice-sme-pipeline/
├── index.html        — frontend (shared across all countries)
├── uganda.json       — Uganda SME entries
├── madagascar.json   — Madagascar SME entries (forthcoming)
├── tanzania.json     — Tanzania SME entries (forthcoming)
└── README.md
```

The HTML frontend loads whichever country JSON is selected. To add or update entries, edit the relevant JSON file — the HTML never needs to change.

## Data schema

Each entry in the JSON files follows this structure:

| Field | Description |
|---|---|
| `id` | Unique identifier, e.g. `uga-001` |
| `name` | Company name |
| `founded` | Year founded |
| `hq_location` | District / region |
| `website` | Company website |
| `primary_contact` | Name and title of key contact |
| `org_type` | Private company / Cooperative / Social enterprise / Family business |
| `value_chain_role` | Position in the value chain |
| `primary_products` | List of primary crops / products |
| `farmer_network_size` | Number of smallholder outgrowers |
| `certifications` | Certifications held |
| `export_markets` | Export destinations |
| `revenue_usd_est` | Estimated annual revenue (range) |
| `revenue_source` | Source of the revenue figure — see confidence legend below |
| `revenue_confidence` | High / Medium / Low |
| `staff_count_est` | Estimated headcount (range) |
| `staff_source` | Source of the staff figure |
| `staff_confidence` | High / Medium / Low |
| `existing_debt` | Known loan or equity facilities |
| `has_audited_accounts` | Yes / No / Unknown |
| `capital_need_est_usd` | Estimated loan size needed (range) |
| `capital_use_of_funds` | Intended use of loan proceeds |
| `capital_need_source` | Basis for the capital need estimate |
| `capital_need_confidence` | High / Medium / Low |
| `crs_relationship` | Active partner / Indirect / None confirmed |
| `crs_notes` | CRS-specific context and deal notes |
| `donor_history` | Array of past donors/investors with amounts and years |
| `lending_readiness_tier` | Tier 1 — Investment Ready / Tier 2 — Near Ready / Tier 3 — Needs TA First |
| `pipeline_status` | Prospect / In Conversation / Active |
| `livelihood_score` | 1–5 rating of farmer reach and depth of engagement |
| `environment_focus` | Yes / No / Partial |
| `women_focus` | Yes / No / Partial |
| `data_confidence` | Overall confidence in the entry: High / Medium / Low |
| `sme_classification_note` | Flag if the company may exceed SME size thresholds |
| `last_updated` | Date of last update (YYYY-MM) |
| `notes` | Open field for additional context |

## Data source legend

Financial figures are only as reliable as their source. Every monetary and headcount field carries a `_source` tag:

| Source label | Meaning |
|---|---|
| **Verified** | From audited accounts, signed investor documents, or official filings |
| **Reported** | Stated by the company (website, interview) but not independently verified |
| **Claude estimate** | Derived from proxy signals — investor ticket sizes, farmer network scale, comparable operators |
| **Unknown** | No basis for even an estimate |

Treat all "Claude estimate" figures as placeholders to be confirmed through direct engagement or document review.

## Lending readiness tiers

| Tier | Label | Typical profile |
|---|---|---|
| **Tier 1** | Investment Ready | Existing external financing, audited or investor-reviewed accounts, established export relationships, $500K+ loan appetite |
| **Tier 2** | Near Ready | Operational track record, some external validation, may need light TA or certification support before first loan, $100K–$500K |
| **Tier 3** | Needs TA First | Early stage or opaque financials, strong livelihoods mission but not yet bankable; pre-lending technical assistance required, <$100K |

## Updating the data

To add a new company, append a new JSON object to the relevant country file following the schema above. To update an existing entry, find it by `id` and edit the relevant fields. Increment `last_updated` to the current month.

The `id` format is `[country-code]-[three-digit-number]`, e.g. `uga-006`, `mdg-001`, `tza-001`.

When a figure is updated from an estimate to a verified or reported value, update both the value field and the corresponding `_source` and `_confidence` fields.

## Countries

| Country | File | Status |
|---|---|---|
| Uganda | `uganda.json` | Active — 5 entries |
| Madagascar | `madagascar.json` | Forthcoming |
| Tanzania | `tanzania.json` | Forthcoming |

## Context

This tool is part of a broader CRS Innovative Finance initiative to design a blended finance lending facility targeting spice sector SMEs in East Africa. The facility aims to raise investment capital from CRS donors and deploy it as loans to vanilla, clove, pepper, and related spice SMEs, with a focus on livelihoods impact and environmental sustainability.

Related resources: CRS TSIRO Alliance (Madagascar/Uganda), VANEX (Uganda vanilla exporters association), VINES project (Uganda).
