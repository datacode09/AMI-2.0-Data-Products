# AMI 2.0 (Itron) – Data Product Inventory for Utilities

**Status: PROVISIONAL.** Built from public Itron datasheets, product pages and
third-party documents. No Itron technical manuals (IEE MDM integration guide,
AMI data export reference, event/alarm catalog) were available. Itron's hosts were
not reachable from the build environment, so primary documents were read only as
search-result excerpts.

Legend: **[S]** = stated in a public source, **[I]** = inferred from industry practice, to be validated against Itron manuals.

## 1. Core metering data (collection / head-end layer)

| Data product | Description | Basis |
|---|---|---|
| Interval (load profile) data | kWh/kW per channel; 5/10/15/30/60-min recording; voltage profile channels on some meters | [S] |
| Register / billing reads | Billing-cycle and daily register reads, demand, TOU | [S] |
| Events & exceptions | Recorded with each interval; meter/device events | [S] |
| On-demand reads / pings | Operator-initiated read or status check | [I] |
| Meter / device inventory & status | Device registry, firmware, comms health | [I] |

## 2. Outage & power quality data

| Data product | Description | Basis |
|---|---|---|
| Last-gasp outage notifications | Real-time notice on power loss (ultracapacitor-backed) | [S] |
| Restoration notifications | Sent when AC power returns | [S] |
| Voltage events | Start/end time, peak voltage, phase, duration (sag/swell/over/under) | [S] |
| Power quality tests | Up to 12 tests, event-count or time-window reporting | [S] |
| Daily min/max voltage, interval voltage | Voltage profile for planning/compliance | [S] (comparable vendor) / [I] |
| Outage event feed to OMS | Consumed by OMS, CIS and work management | [S] |

## 3. Meter data management (MDM) products

| Data product | Description | Basis |
|---|---|---|
| Validated, estimated, edited (VEE) interval/register data | Billing-quality data | [S] |
| AMI Data Export | Bulk export of AMI data to downstream systems | [S] |
| Readings Export | Meter readings export | [S] |
| Billing Register Export | Billing determinants to CIS/billing | [S] |
| Device event reports and exports | Event reporting, exception monitoring | [S] |
| Settlements data | Market/settlement interval aggregates | [S] (IEE MDM Settlements) |
| Long-term data store | IEE Essentials: two years default (interval, register, events, alarms) | [S] |
| Integration interfaces | File-based plus synchronous/asynchronous web service APIs; ESB | [S] |

## 4. AMI 2.0 / grid-edge data products

| Data product | Description | Basis |
|---|---|---|
| Edge-processed data via IEOS | Intelligent Edge Operating System; DataHub subscriptions deliver analytics results | [S] |
| Outage insights | Outage analytics (IEE Cloud AI) | [S] |
| Grid visibility | Transformer / feeder / phase-level views | [S] |
| Forecasting | Load and DER forecasts | [S] |
| Anomaly detection & revenue assurance | Theft, tamper, meter anomalies | [S] |
| DER / distribution load management | IntelliFLEX, claimed up to ~20% added capacity (vendor claim, unverified) | [S] |
| Distributed intelligence (DI) app outputs | Partner apps (e.g. customer engagement, demand-side management) | [S] |
| Customer-level load disaggregation / engagement data | Third-party analytics on AMI 2.0 data | [S] (partner claims) |

## 5. Downstream consumers (what utilities feed)

CIS/billing, OMS, DMS/ADMS, work management, GIS (for network connectivity
models), DER management, customer engagement portals, regulatory/settlement
reporting. [S]/[I]

## 6. Open questions for Itron manuals

1. Exact event/alarm catalog and severities.
2. Export file schemas, frequency, and SLAs.
3. Whether Riva-based endpoints add or change data products vs. earlier OpenWay devices.
4. Edge/DI data model and subscription semantics (IEOS DataHub).
5. Retention beyond two years, and data-quality KPIs (read success rate, VEE rejection rate).

## Sources

- https://na.itron.com/o/commerce-media/accounts/-1/attachments/3795395
- https://es.itron.com/o/commerce-media/accounts/-1/attachments/3801179
- https://es.itron.com/o/commerce-media/accounts/-1/attachments/3801140
- https://apps.itron.com/ItronGlossary/Content/Topics/I/IEE%20Meter%20Data%20Management%20(MDM)%20Settlements.htm
- https://www.tescometering.com/wp-content/uploads/2025/06/PECO-TESCO-Emergency-Response-Practices-to-Meter-Alarms-072225.pdf
- https://mfn.se/all/a/itron/itron-introduces-iee-cloud-ai-enabling-grid-edge-use-cases-from-a-trusted-data-foundation-47818c91
- https://na.itron.com/fi/products/grid-edge-essentials
- https://www.streetinsider.com/Corporate+News/Itron+%28ITRI%29+Launches+IntelliFLEX+Solution/24488700.html
