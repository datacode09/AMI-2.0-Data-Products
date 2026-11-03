# AMI-2.0-Data-Products

Reference material for the data products utilities need to operate an Itron-based AMI 2.0 program.

> **Status: provisional.** Content is built from public Itron datasheets, product pages and
> industry practice, not from Itron technical manuals. Rows are tagged as stated in a public
> source **[S]** or inferred **[I]**. Validate against Itron documentation and your own
> deployment (endpoints, firmware, network, head-end/MDM) before relying on it.

## Contents

| Document | Purpose |
|---|---|
| [Data Product Inventory](docs/ami-2.0-data-product-inventory.md) | Core AMI data: metering, outage/power quality, MDM exports, grid-edge analytics |
| [Data Products by Domain](docs/ami-2.0-data-products-by-domain.md) | About 100 candidate data products across 12 utility domains: telecom, meter-to-bill, meter-to-cash, work/order management, meter triage, customer programs, dispatch/outage, asset management, protection and control, distribution ops/planning, interconnection/DER, regulatory/finance, and the enterprise data platform |
| [Business Glossary](docs/ami-2.0-business-glossary.md) | Definitions of AMI 2.0, Itron and utility business terms |

## Suggested reading order

1. Glossary, for shared vocabulary.
2. Inventory, for what AMI 2.0 produces.
3. Data products by domain, for what each part of the utility can build from it.

## Known gaps

- No Itron manuals are in the repo (IEE MDM integration guide, AMI data export reference,
  event/alarm catalog).
- Export schemas, event catalogs, SLAs and the Riva vs. OpenWay differences are unconfirmed.
- Edge (distributed intelligence) and voltage-channel capabilities need confirming per endpoint.

## Contributing

- Keep the [S]/[I] tags accurate; change [I] to [S] only with a cited source.
- Add Itron manuals under `docs/sources/` and cite them in the relevant tables.
- For each prioritized product, add owner, schema, latency, quality targets and consumers.
