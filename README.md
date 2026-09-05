# ire-public-data
Public regulatory data artifacts for the Investor Research Engine (Harmonate engagement).

## adv_7b1_registry.csv.gz
Private fund registry derived from SEC/FINRA IAPD FOIA monthly ADV filing data
(https://reports.adviserinfo.sec.gov/reports/foia/advFilingData/). IA + ERA Schedule D 7.B.(1)
joined to ADV Base (FilingID -> 1E1 CRD). Current-books semantics: per adviser, latest
filing's fund set only. Columns: crd,filing_id,date_submitted,fund_name,fund_id,fund_type,
gross_asset_value,state,country. Refreshed monthly (see engagement DAQ-744).
Built: 2026-09-05 (HRM-S136) | rows=127394 | sha256=d8c2fb35d19c591c3f1cae4ad4b3f7c942d3415f2bb256414a491ac6378e4ac6
Contains only public regulatory data. Tenancy migration to client org planned at handover.
