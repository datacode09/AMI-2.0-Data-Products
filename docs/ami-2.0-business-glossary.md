# AMI 2.0 Business Glossary

**Status: PROVISIONAL.** Definitions reflect common industry usage and public Itron
material. Items marked *(Itron)* are Itron-specific terms; validate against Itron manuals
and your utility's own definitions before treating as authoritative.
See also: [Data Product Inventory](ami-2.0-data-product-inventory.md).

## Programs and platforms

| Term | Definition |
|---|---|
| **AMI (Advanced Metering Infrastructure)** | Meters, communications network and back-office systems that collect and deliver usage and event data two-way. |
| **AMI 1.0** | First-generation AMI, mainly for automated meter reading, billing and basic outage notification. |
| **AMI 2.0** | Next-generation AMI with edge computing in the meter or network, higher-resolution data and grid-edge applications (voltage, DER, outage analytics) beyond billing. |
| **Grid edge** | The distribution-level boundary near customers: meters, transformers, DER and local devices. |
| **Distributed Intelligence (DI)** *(Itron)* | Running applications on the meter or edge device so analytics happen close to the data. |
| **IEOS (Intelligent Edge Operating System)** *(Itron)* | Itron's edge data and application layer; includes DataHub. |
| **DataHub** *(Itron)* | Component for subscribing to and distributing edge analytics results. |
| **IEE (Itron Enterprise Edition)** *(Itron)* | Itron's enterprise data platform, including the MDM and cloud analytics offerings. |
| **IEE MDM** *(Itron)* | Meter data management module for interval, register and event data. |
| **IEE Cloud AI** *(Itron)* | Cloud analytics for outage insights, grid visibility, forecasting, anomaly detection and revenue assurance. |
| **OpenWay / Riva** *(Itron)* | Itron endpoint and network families. Exact scope relative to AMI 2.0 to be confirmed. |

## Systems

| Term | Definition |
|---|---|
| **Head-end system (HES) / Collection system** | Collects and manages communication with meters; delivers raw reads and events. |
| **MDM / MDMS** | Meter data management: stores, validates, estimates and publishes meter data. |
| **CIS** | Customer information system: accounts, premises, rates. |
| **Billing system** | Turns billing determinants into bills; often part of CIS. |
| **OMS** | Outage management system: detects, locates and tracks outages. |
| **DMS / ADMS** | (Advanced) distribution management system: monitors and controls the distribution network. |
| **DERMS** | DER management system. |
| **GIS** | Geographic information system; network connectivity model of assets and customers. |
| **WMS** | Work management system: field orders and crews. |
| **ESB** | Enterprise service bus: integration layer between utility systems. |

## Data and measurement terms

| Term | Definition |
|---|---|
| **Interval data / load profile** | Energy or demand recorded at fixed periods (e.g. 5, 15, 60 min). |
| **Register read** | Cumulative or billing-period value (kWh, kW demand, TOU buckets). |
| **Billing determinant** | Value used to compute a bill (usage, demand, TOU totals). |
| **Demand (kW)** | Rate of energy use over a defined interval; peak demand drives some charges. |
| **TOU (time of use)** | Rate structure varying by time of day. |
| **Channel** | One recorded data stream in a meter, e.g. kWh delivered or voltage. |
| **Event** | A recorded occurrence in a meter (tamper, outage, voltage excursion). |
| **Alarm** | An event escalated for immediate notification. |
| **Exception** | A read or process that failed validation or timing expectations. |
| **Last gasp** | Message a meter sends on power loss, using stored energy. |
| **Restoration notice** | Message sent when power returns. |
| **Power quality (PQ)** | Voltage and waveform characteristics versus standards. |
| **Sag / swell** | Short-duration voltage drop / rise. |
| **On-demand read / ping** | Operator-initiated read or status check of a meter. |
| **Read success rate** | Share of expected reads received on time; key AMI health KPI. |
| **Latency** | Delay between measurement and availability in a system. |

## Data quality and operations

| Term | Definition |
|---|---|
| **VEE (Validation, Estimation, Editing)** | MDM process producing billing-quality data from raw reads. |
| **Validation** | Rules check for gaps, spikes, zero reads, duplicates. |
| **Estimation** | Filling missing or invalid intervals by an approved method. |
| **Editing** | Manual or rule-based correction of data with audit trail. |
| **Data export** | Scheduled or on-demand file/API delivery to downstream systems (AMI Data Export, Readings Export, Billing Register Export in IEE). |
| **Settlement** | Aggregating interval data for market or wholesale reconciliation. |
| **Data retention** | How long data is stored; IEE Essentials lists two years by default. |
| **Data product** | A governed, documented dataset or feed with an owner, schema, quality targets and consumers. |

## Business use cases

| Term | Definition |
|---|---|
| **Revenue assurance** | Detecting lost revenue (theft, meter faults, billing errors). |
| **Non-technical loss** | Energy lost to theft, unmetered use or errors rather than physical network loss. |
| **Conservation voltage reduction (CVR)** | Lowering voltage within limits to cut energy use; relies on voltage data. |
| **DER (distributed energy resources)** | Rooftop solar, storage, EVs, flexible load. |
| **Non-wires alternative (NWA)** | Using DER or demand flexibility instead of network upgrades. |
| **Demand response (DR)** | Customer load reduction on request or signal. |
| **Load disaggregation** | Estimating appliance-level use from meter data. |
| **Transformer loading** | Aggregating customer data per transformer to find overloads. |
| **Outage analytics** | Using meter signals to confirm, scope and verify outages and restoration. |
