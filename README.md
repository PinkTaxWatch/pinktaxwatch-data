# PinkTaxWatch

**Open comparative affordability dataset for essential menstrual products across European retail markets.**

> Menstruation is biological. The cost of it depends on where you live.

Public-interest data project covering the **EU 27 + United Kingdom** — 28 markets, two confidence tiers. Every number visible on [pinktaxwatch.com](https://pinktaxwatch.com) is reproducible from the methodology and source mapping documented in this repository.

---

## Why is it called PinkTaxWatch?

The phrase "pink tax" entered general usage as a colloquial umbrella term for **gendered economic disadvantage** — anything that costs more, taxes more, or burdens more for women than for men. Strictly, the term refers to gender-based price discrimination on regular consumer products (razors, shampoo, deodorant). In public discourse, it commonly extends to menstrual product VAT, women's healthcare costs, and gender pay gaps.

PinkTaxWatch focuses specifically on **menstrual product affordability** — the intersection of retail prices, country-specific VAT (sometimes called the "tampon tax"), and female net income normalisation. This is one component of the broader "pink tax" conversation, made measurable.

The project uses "pink tax" in its colloquial umbrella sense because:

1. It is the term general audiences search for and recognise
2. Menstrual-product affordability is the empirically tractable subset that publicly available data can measure rigorously across 28 markets
3. The strict gender-pricing comparison (e.g. women's razor vs men's razor across countries) requires sustained brand-pair surveys that don't yet exist at the EU 27 scale

Methodological scope and explicit boundaries are documented in the [Terminology and scope boundaries](#terminology-and-scope-boundaries) section below.

---

## What this dataset contains

Monthly affordability snapshots for the EU 27 + United Kingdom — 28 markets with explicit confidence-tier flagging per country per snapshot. Three metrics per country:

| Metric | Definition |
|---|---|
| Share of net income | VAT-inclusive monthly basket ÷ female net monthly income × 100 |
| Hours of work / year | Annual time-cost at the country's typical female full-time net hourly wage |
| Lifetime cost (39-year cohort) | Cumulative cost across menstrual lifespan (age 12–51) |

Each published value carries a `confidence_tier` flag (A / B) indicating the level of retail-side verification for that country in that snapshot. See [Coverage scope](#coverage-scope) for the tier definitions.

Basket: fixed-composition selection of mid-tier disposable absorbent products (pads and tampons), priced inclusive of country-specific VAT, converted to EUR at the ECB daily reference rate on snapshot date.

---

## Sources

| Source | Purpose | Cadence |
|---|---|---|
| Eurostat `earn_nt_net` | Female net median monthly income (sex-stratified, FTE) | Annual (Eurostat publication) |
| EC TEDB | VAT rates on menstrual products per member state | Quarterly audit + event-driven |
| ECB SDW | EUR reference rates | Monthly, aligned to snapshot date |
| Retail observations | Apify scrapers against primary national retailers (Tier A); regional analogues and HICP fallback (Tier B) | Monthly |

---

## Coverage scope

**Geographic scope: EU 27 + United Kingdom** (28 markets). Every country in scope appears in every snapshot, with explicit **confidence-tier classification** per country. This is the project's commitment to *disclosure quality over false uniformity*: the user sees verification depth alongside the number.

### Tier A — retailer-verified

Direct retail observations from primary national retailers via the scraping pipeline, with full audit trail per observation (retailer URL, capture timestamp, product SKU, pack size, methodology-versioned adjustments where applicable). Coverage includes the multinational drogerie / drugstore chain cluster (dm, Rossmann, Müller, Kruidvat) where SKU-level cross-country comparability is most robust, plus comparable national chains in larger markets where direct equivalence is not available.

- Germany
- Austria
- Hungary
- Poland
- Czechia
- Slovakia
- Romania
- Croatia
- Netherlands
- Belgium
- United Kingdom
- France
- Spain
- Italy
- Ireland
- Sweden
- Denmark
- Finland

### Tier B — estimated / pending verification

Approximated values from regional analogues and Eurostat consumer price index (HICP) data, pending retail pipeline expansion to that market. Each Tier B row is flagged `audit_trail: in_progress` in published snapshots.

- Portugal
- Greece
- Slovenia
- Bulgaria
- Estonia
- Latvia
- Lithuania
- Luxembourg
- Cyprus
- Malta

### Tier transitions

The target state is **Tier A coverage across all 28 markets**. Tier transitions are tracked per monthly snapshot, and historical Tier B values are retained alongside their later Tier A successors for trend continuity. Each snapshot's `methodology_version` field indicates the tier classification in effect when the value was published.

---

## Collection pipeline

```
[Apify actors] → [Make.com orchestration] → [Airtable canonical store] → [Supabase / site backend]
```

Each retail observation captures:

```
country, confidence_tier, retailer, retailer_url,
product_brand, product_line, pack_size_units,
observed_price, currency, vat_rate_applied,
observation_date, archive_reference,
methodology_version
```

Income and FX inputs are pulled directly from Eurostat REST and ECB SDW APIs on their natural cadence.

For Tier A markets where SKU equivalence with the chain cluster is not direct, modelling adjustments are documented in `/methodology/normalization.md`. For Tier B markets, the regional analogue mapping and HICP fallback formula are documented in `/methodology/tier-b-modeling.md`.

---

## Methodology

```
Affordability Index = VAT-inclusive monthly retail basket price
                      ────────────────────────────────────────── × 100
                              Female net monthly income
```

Retail prices in EU member states are VAT-inclusive at point of sale, so the formula does not multiply by VAT separately — VAT is already embedded in the observed price. The TEDB VAT rate is tracked alongside as transparency metadata and for scenario modelling (e.g. 0% VAT counterfactual).

Full methodology: [pinktaxwatch.com/methodology](https://pinktaxwatch.com/methodology)

---

## Repository structure

```
/data
  /snapshots          monthly affordability snapshots (CSV + JSON)
  /raw                raw retail observations per country
  /sources            cached upstream pulls (Eurostat, ECB, TEDB)
/methodology
  basket-composition.md
  normalization.md
  tier-b-modeling.md
  versioning.md
/scrapers
  README.md           Apify actor configurations and per-retailer notes
/docs
  pipeline.md
  changelog.md
  roadmap.md
LICENSE
README.md
```

---

## Data access

Published snapshots are available as CSV and JSON under `/data/snapshots/`. Each file is tagged with the methodology version that produced it and includes the `confidence_tier` field per country row.

Direct snapshot URL pattern:
```
https://github.com/PinkTaxWatch/pinktaxwatch-data/raw/main/data/snapshots/YYYY-MM/index.csv
```

A public read-only API is on the v2.0 roadmap.

---

## Limitations

- Monthly snapshots, not real-time pricing.
- Standardised benchmark, not individual spending forecast.
- Tier A values may include methodology-versioned modelling adjustments where direct SKU equivalence is not available; Tier B values are approximations pending retail pipeline expansion. Both cases are flagged explicitly in published snapshots.
- Retail price variance within a country (regional, promotional, seasonal) is not captured by a single national snapshot.
- Disposable products only — reusable alternatives (cups, period underwear, reusable pads) are excluded from the current basket.
- Scraper coverage is subject to retailer site changes; broken actors fall back to the most recent valid observation, flagged with a stale-snapshot indicator.
- Affordability is not access — countries with free public menstrual product provision (the Scotland model, in force since 2022) reduce out-of-pocket cost to zero for accessing populations, but the affordability index continues to measure retail cost. These are deliberately different metrics.

---

## Terminology and scope boundaries

The strict methodological scope of this dataset, as a reference for citation and audit:

**In scope:** Retail price of disposable menstrual products (pads and tampons) sold at primary national retailers in the EU 27 + United Kingdom; country-specific VAT applied to those products; female net monthly income at full-time equivalent; derived affordability ratios computed from these inputs.

**Out of scope:** Gender-based price discrimination on non-menstrual products (the "pink tax" in its strict consumer-goods sense — razors, shampoo, deodorant, etc.); out-of-pocket healthcare costs related to menstrual or reproductive health; free public menstrual provision schemes (which reduce real-world cost but not retail price); reusable alternative products; individual purchasing behaviour; regional, promotional, or seasonal price variance within a country.

**"Tampon tax" usage:** Some sources use "tampon tax" specifically for the government VAT or sales tax component of menstrual product cost. PinkTaxWatch measures the combined effect of retail price, VAT, and female-income normalisation — VAT alone is not the affordability metric, but the TEDB rate is tracked and reported as a separate metadata field on every snapshot for transparency.

The project name "PinkTaxWatch" uses "pink tax" in its colloquial umbrella sense, as discussed in the [Why is it called PinkTaxWatch?](#why-is-it-called-pinktaxwatch) section above. Future dataset extensions toward gender-pricing comparison work are tracked in `/docs/roadmap.md`.

---

## License

- **Data:** [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)
- **Code:** MIT

---

## Citation

```bibtex
@misc{pinktaxwatch2026,
  title  = {European Menstrual Affordability Index},
  author = {{PinkTaxWatch}},
  year   = {2026},
  url    = {https://github.com/PinkTaxWatch/pinktaxwatch-data}
}
```

Plain-text citation:

> PinkTaxWatch (2026). *European Menstrual Affordability Index*. https://github.com/PinkTaxWatch/pinktaxwatch-data

---

## Contact

- Site: [pinktaxwatch.com](https://pinktaxwatch.com)
- Data corrections, source flags, methodology questions: open an Issue on this repository
- Editorial inquiries: info@pinktaxwatch.com
