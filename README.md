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

## dol_5500_plan_registry.csv.gz
DOL Form 5500 plan-sponsor registry (Wave L1). One row per plan (ein_pn = "{EIN}:{PN}",
PN zero-padded), unioned across form-years in scope, latest filing wins (ACK_ID recency).
Source: EBSA "Latest" datasets at askebsa.dol.gov FOIA Files (main + short form), US
government work / public domain. 2024-only at first build -- 2025 Latest unpublished as of
2026-09-06 (D-HRM-S142-001); folds in at the DAQ-752 monthly refresh.
Columns: ein_pn,ein,pn,sponsor_name,sponsor_dba,sponsor_name_key,plan_name,state,form,
form_year,plan_entity_cd,pension_ind,welfare_ind,participants,assets_eoy,ack_id.
Builder: scripts/build_5500_registry.py (investor-research-engine).
Built: 2026-09-06 (HRM-S142) | rows=992000 | sha256=6df7e163d9cba5d38d3730332b029d8eef888e732955b733c37e8dcd7d2105ab

## dol_5500_service_providers.csv.gz
Schedule C Part 1 Item 2 service providers for main-form 5500 plans (Wave L1 companion).
One row per (ein_pn, provider). Source + license as above; same refresh cadence.
Columns: ein_pn,provider_name,provider_ein,provider_name_key,srvc_codes,relation,
direct_comp_amt,indirect_comp_amt,form_year,ack_id.
Builder: scripts/build_5500_registry.py (investor-research-engine).
Built: 2026-09-06 (HRM-S142) | rows=263284 | sha256=4ea301d900075488a6a10b6e43735f6536906805bde7353d9a8b181d49305a22
