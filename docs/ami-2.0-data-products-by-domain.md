# AMI 2.0 Data Products by Utility Domain

**Status: PROVISIONAL / design catalog.** Product candidates derived from the
[inventory](ami-2.0-data-product-inventory.md) and industry practice, not from Itron manuals. Almost
all rows are **[I]** (inferred); validate feasibility against the deployed endpoint, firmware,
network and Itron platform capabilities. Terms: [glossary](ami-2.0-business-glossary.md).

**Why AMI 2.0 specifically:** compared with AMI 1.0, it adds edge computing in the meter
(distributed intelligence), high-resolution voltage/current and waveform-derived data, event-driven
push, and DER visibility, which opens products for protection, planning and grid operations,
beyond billing.

**Source signal abbreviations:** INT = interval kWh/kW; REG = registers; VLT = voltage/PQ profile;
EVT = events/alarms; LG/RN = last gasp/restoration; DI = edge app output; COM = network/radio
telemetry; DEV = device inventory/status/firmware; CFG = meter configuration.

---

## 1. Telecom / AMI Network (RF mesh, cellular, backhaul)

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Network health scorecard | Read success, latency, hop counts, link quality per collector/cell | COM, DEV | Telecom ops |
| Collector / access point performance | Load, backlog, uptime, throughput | COM | Telecom ops |
| Coverage gap map | Endpoints with weak or no comms | COM, GIS | Network planning |
| Firmware campaign status | Rollout progress, failures, versions | DEV, CFG | Meter ops |
| Comms-based outage corroboration | Mesh neighbor loss patterns to confirm outages | COM, LG | OMS, telecom |
| Backhaul capacity & cost | Data volume per link/carrier | COM | Telecom finance |
| Cybersecurity events | Auth failures, tamper, rogue devices | EVT, COM | Security ops |

## 2. Meter-to-Bill

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Billing-ready usage (VEE) | Validated/estimated interval and register data per account | INT, REG | CIS/billing |
| Billing determinants feed | kWh, kW demand, TOU buckets, reactive energy | INT, REG | Billing |
| Bill-cycle read completeness | Missing/late reads before bill run | INT, REG, COM | Billing ops |
| VEE exception queue | Rejected/estimated intervals with reasons | VEE | Billing analysts |
| Estimation audit trail | Method, original vs. edited values | VEE | Audit, regulatory |
| Net metering / bidirectional billing data | Delivered/received energy with DER flags | INT, REG | Billing |
| Rate-change/TOU re-bill dataset | Interval data for retroactive recalculation | INT | Billing |
| High-bill investigation pack | Usage history, events, voltage and comparison to peers | INT, EVT | Call center |
| Meter-to-premise-to-account linkage | Reconciled device/service point/account relationships | DEV, CIS | Billing, data governance |

## 3. Meter-to-Cash (credit, collections, revenue protection)

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Remote connect/disconnect log | Commands, confirmations, failures, timing | EVT, DEV | Collections, field |
| Disconnect-eligibility check | Pre-check of safe-to-disconnect (load, DER, medical flags) | INT, CIS | Collections |
| Prepay/pay-as-you-go balance consumption | Near-real-time usage for balances | INT | Prepay/CIS |
| Revenue protection alerts | Tamper, reverse flow, bypass, inversion signals | EVT, INT | Revenue protection |
| Non-technical-loss indicators | Energy balance gaps per transformer/feeder | INT, VLT | Revenue assurance |
| Zero-consumption on active account | Likely meter failure/theft/vacant | INT, CIS | Revenue assurance |
| Dispute evidence package | Reads, events, voltage, timestamps for a contested bill | INT, EVT | Customer service |
| Meter accuracy / drift indicators | Comparisons across meters and transformer totals | INT | Metering |
| Move-in / move-out reads | Special reads on date of change | REG | CIS |

## 4. Work and Order Management

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Meter exchange/install work queue | Failed/offline/tamper meters needing field action | DEV, EVT | WMS |
| Service-order status verification | Remote confirmation that install/reconnect worked | EVT, INT | WMS/CIS |
| Meter installation validation | Commissioning checks: comms, phase, voltage, polarity | DEV, VLT | Field |
| Wrong-wiring / phase-swap detection | Anomalies indicating incorrect install | VLT, INT | Field QA |
| Truck-roll avoidance recommendations | Issues resolvable remotely (ping, re-read, reconfigure) | DEV, EVT | Dispatch |
| Field order closure data | Auto-verified completion | EVT | WMS |
| Meter shop test results | Returned meter diagnostics | DEV | Meter shop |

### 4a. Meter Triage (cross-domain: metering ops, telecom, field, billing)

Meter triage = detect a meter/endpoint problem, classify the root cause, and route to the cheapest
fix (remote action, network fix, billing workaround or field visit).

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Non-communicating meter list | Meters missing expected reads, aged by days silent | INT, COM, DEV | Meter ops |
| Root-cause classification | Cause per meter: comms/RF coverage, collector/cell issue, meter hardware fault, power off (outage or disconnect), firmware, config, tamper, vacant premise | COM, DEV, EVT, LG/RN, CFG | Meter ops, telecom |
| Triage priority score | Ranks by bill-cycle risk, revenue at stake, critical/medical customer, repeat offender, safety (tamper, hot socket) | INT, CIS | Meter ops |
| Remote remediation outcomes | Ping, on-demand read, re-register, reboot, config/firmware push; results and success rates | DEV, CFG | Meter ops |
| Triage routing queue | Case assignment: remote fix, network team, billing estimation, field order | all | Dispatch, WMS |
| Field work order package | Meter ID, location, diagnosis, history of remote attempts, safety flags, suggested parts | DEV, EVT, GIS | Field, WMS |
| Billing-impact view | Accounts with missing reads heading into bill run, estimated vs. actual exposure | INT, CIS | Billing ops |
| Repeat-failure / bad-actor list | Meters or model/firmware/lot cohorts with recurring problems | DEV, EVT | Metering, vendor mgmt |
| Triage KPIs | Mean time to detect/resolve, % fixed remotely, truck rolls avoided, backlog by cause, read success rate | all | Management |
| Resolution feedback loop | Closure code and actual cause, used to refine classification | WMS | Analytics |

## 5. Customer Programs and Engagement

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Customer load shape library | Segmented interval profiles | INT | Marketing, planning |
| Demand response baselines & event performance | Baselines, curtailment measurement and settlement | INT | DR program |
| TOU/dynamic rate analysis | Bill impact and shifting behavior | INT | Rates, programs |
| Energy efficiency M&V dataset | Pre/post usage with weather normalization | INT | EE program |
| Appliance-level disaggregation | Load disaggregation signals (EV, HVAC, solar) | INT, DI | Programs, partners |
| EV charging detection | Charger identification and profiles | INT, DI | EV programs |
| Alerts and notifications | High usage, outage, voltage, budget alerts | INT, EVT | Customer portal |
| Customer data sharing (Green Button type) | Consent-governed data sets to customers and third parties | INT | Portal, third parties |
| Program eligibility targeting | Customers likely to benefit or qualify | INT | Programs |
| Low-income / vulnerable customer indicators | Usage-pattern flags with privacy controls | INT, CIS | Customer care |

## 6. Dispatch and Outage Operations

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Outage notifications (last gasp) | Per-meter outage with timestamp | LG | OMS |
| Restoration notifications | Per-meter power-on events | RN | OMS |
| Outage extent/scope inference | Grouping to transformer/lateral/feeder | LG, GIS | OMS, dispatch |
| Nested outage detection | Residual outages after main restoration | LG, RN | Dispatch |
| Restoration verification ("ping" sweep) | Confirm all customers restored | DEV | Dispatch, OMS |
| Momentary outage / blink counts | Reliability per customer/feeder | EVT | Reliability |
| Reliability indices dataset | SAIDI/SAIFI/CAIDI/MAIFI inputs by customer minutes | LG, RN | Regulatory, reliability |
| Storm damage assessment feed | Outage heatmaps and ETR inputs | LG, RN | Emergency ops |
| Crew dispatch priority inputs | Critical customer outages first | LG, CIS | Dispatch |

## 7. Asset Management

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Transformer loading profile | Aggregated customer interval data per transformer | INT, GIS | Asset mgmt, planning |
| Overload/ageing indicators | Duration above thresholds, estimated life consumption | INT, VLT | Asset mgmt |
| Meter fleet health | Failure rate by model/firmware/age/environment | DEV, EVT | Metering |
| Meter lifecycle & replacement planning | Predicted failures, battery/ultracap status | DEV | Metering |
| Customer-transformer connectivity validation | Detect mismatched GIS-to-meter mapping via voltage correlation | VLT, GIS | GIS, asset mgmt |
| Service transformer/secondary condition | Voltage drop, neutral issues, loose connections | VLT, EVT | Asset mgmt, field |
| Phase identification | Meter-to-phase mapping | VLT | GIS, planning |
| Asset condition event history | Event logs tied to assets | EVT | Asset mgmt |

## 8. Protection, Control and Information Management (PCIM)

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Fault location support | Last gasp/voltage sag patterns to locate fault zone | LG, VLT, EVT | Protection engineering |
| Sag/swell event stream | Time-correlated voltage disturbances across meters | VLT, EVT | Protection, PQ |
| Protection-device operation corroboration | Evidence of recloser/fuse/breaker operations | LG, RN | Protection engineering |
| Fuse-blown / open-phase detection | Partial loss of phases | VLT, EVT | Dispatch, protection |
| Reverse power flow detection | DER backfeed relevant to protection settings | INT, VLT | Protection, interconnection |
| Post-event analysis package | Time-aligned event bundles for disturbances | EVT, VLT | Protection engineering |
| High-impedance/downed-conductor indicators | Edge-detected anomalies (if supported by endpoint DI) | DI | Protection, safety |

## 9. Distribution Operations and Planning (ADMS/DMS)

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Edge-of-grid voltage profile | Voltage at customer by feeder/phase/time | VLT | ADMS/DMS |
| Volt/VAR optimization & CVR inputs | End-of-line voltage for Volt/VAR control | VLT | ADMS |
| Load estimation / state estimation inputs | Measured load by node | INT | ADMS |
| Power quality compliance | Voltage excursions vs. standard (e.g. ANSI C84.1) | VLT, EVT | PQ engineering |
| Load forecast inputs | Granular historical load | INT | Planning |
| Hosting/loading headroom by feeder | Capacity for DER, EV, electrification | INT, VLT | Planning |
| Phase balance analysis | Load by phase | INT, VLT | Planning, ops |
| Switching/reconfiguration validation | Voltage and load after switching | VLT, INT | Operations |

## 10. Grid Interconnection and DER

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| DER detection / unregistered solar | Identify unreported generation via reverse flow | INT, DI | Interconnection |
| Interconnection application support | Existing load/voltage at point of interconnection | INT, VLT | Interconnection engineering |
| DER production & net load | Gross vs. net estimation | INT, DI | DERMS, operations |
| Export limit / curtailment compliance | Verification against agreed limits | INT, VLT | Interconnection |
| Voltage-rise / flicker at DER sites | PQ at interconnection points | VLT, EVT | Interconnection, PQ |
| Flexible connection / dynamic limit signals | Local constraint data for DER management | VLT, INT | DERMS |
| EV charger & storage visibility | Load pattern flags | INT, DI | Planning, programs |
| Virtual power plant (VPP) performance | Aggregate resource response | INT | DERMS, markets |
| Non-wires alternative M&V | Verified load reduction at constrained assets | INT | Planning |

## 11. Regulatory, Finance and Settlement

| Data product | Description | Sources | Consumers |
|---|---|---|---|
| Reliability and PQ regulatory reports | Source data for filings | LG, RN, VLT | Regulatory |
| Smart meter program KPIs | Deployment, read rate, benefits realization | DEV, COM | Executive, regulator |
| Benefits tracking | Truck rolls avoided, theft recovered, estimated bills reduced | multiple | Finance, program office |
| Settlement-grade interval data | Aggregated load for market settlement | INT | Market/settlements |
| Data-sharing audit log | Who accessed what customer data | platform | Privacy, compliance |

## 12. Enterprise Data Platform and Governance

| Data product | Description | Consumers |
|---|---|---|
| Canonical meter/premise/asset master | Reconciled device, service point, account, transformer, feeder | All domains |
| Time-series lake (raw + curated) | Historical interval, voltage, event data with retention tiers | Analytics |
| Data quality scorecard | Completeness, timeliness, accuracy per feed | Data governance |
| Consent and privacy registry | Customer permissions, retention, anonymization rules | Privacy, portals |
| Event/streaming bus topics | Real-time event distribution | Operations, DI apps |
| Data product catalog & lineage | Owners, schemas, SLAs, lineage | Governance |

---

## Cross-domain dependencies

- **Master data first:** meter-premise-account-transformer-feeder-phase linkage drives most products
  in domains 3, 6, 7, 8, 9 and 10.
- **Voltage data:** the biggest AMI 2.0 differentiator; confirm channel sampling, retention and
  collection frequency, since many products (7-10) depend on it.
- **Event timeliness:** operational products (6, 8) need push/low-latency paths. Billing products
  (2, 3) tolerate batch.
- **Privacy:** customer-level products (5, 3) need consent, aggregation and retention rules.

## Next steps

1. Confirm endpoint capabilities (voltage channels, edge apps, event catalog) from Itron manuals.
2. Prioritize by value and feasibility (suggested first wave: VEE billing data, outage/restoration
   feed, transformer loading, voltage profile, network health).
3. For each prioritized product, define owner, schema, refresh/latency, quality targets and
   consumers.
