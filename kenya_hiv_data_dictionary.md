# Kenya HIV Insight Project - Data Dictionary

## Document Information
- **Version**: 1.0
- **Data Coverage Period**: 2007-2024
- **Geographic Coverage**: Kenya (National, County, Sub-county levels)

---

## Table of Contents
1. [Demographic Variables](#demographic-variables)
2. [Geographic Variables](#geographic-variables)
3. [HIV Testing Variables](#hiv-testing-variables)
4. [HIV Status and Clinical Variables](#hiv-status-and-clinical-variables)
5. [Treatment and Care Variables](#treatment-and-care-variables)
6. [Prevention Variables](#prevention-variables)
7. [Behavioral Variables](#behavioral-variables)
8. [Survey and Data Source Variables](#survey-and-data-source-variables)
9. [Calculated Indicators](#calculated-indicators)
10. [Data Quality Variables](#data-quality-variables)

---

## Demographic Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `age` | Age of respondent in years | Integer | 0-99 | KENPHIA, KAIS | Age at time of survey |
| `age_group` | Standardized age categories | Categorical | 15-24, 25-34, 35-49, 50+ | Derived | Used for analysis groupings |
| `age_group_detailed` | Detailed age categories | Categorical | 15-19, 20-24, 25-29, 30-34, 35-39, 40-44, 45-49, 50+ | Derived | Fine-grained age analysis |
| `sex` | Biological sex | Categorical | Male, Female | KENPHIA, KAIS | Self-reported |
| `gender` | Gender identity | Categorical | Male, Female, Other | KENPHIA | Where available |
| `marital_status` | Current marital status | Categorical | Never married, Married, Divorced/Separated, Widowed | KENPHIA, KAIS | Current status at survey |
| `education_level` | Highest education completed | Categorical | None, Primary, Secondary, Higher | KENPHIA, KAIS | Formal education only |
| `occupation` | Primary occupation | Categorical | Unemployed, Formal employment, Informal employment, Student, Other | KENPHIA, KAIS | Current occupation |
| `wealth_quintile` | Household wealth index | Categorical | Poorest, Poor, Middle, Rich, Richest | KENPHIA, KAIS | Asset-based wealth index |

---

## Geographic Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `county` | County of residence | Categorical | 47 Kenya counties | KENPHIA, KAIS | Based on 2010 constitution |
| `county_code` | Numeric county identifier | Integer | 001-047 | Official | Kenya National Bureau of Statistics codes |
| `sub_county` | Sub-county of residence | Categorical | Variable | DHIS2, NDW | Administrative unit |
| `residence_type` | Urban or rural residence | Categorical | Urban, Rural | KENPHIA, KAIS | Based on KNBS classification |
| `region` | Regional grouping | Categorical | Nairobi, Central, Coast, Eastern, North Eastern, Nyanza, Rift Valley, Western | Derived | Historical regional groupings |
| `facility_level` | Health facility level | Categorical | Level 1-6 | DHIS2, NDW | Kenya health system levels |
| `facility_type` | Type of health facility | Categorical | Public, Private, Faith-based | DHIS2, NDW | Facility ownership |

---

## HIV Testing Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `ever_tested` | Ever tested for HIV | Binary | Yes, No | KENPHIA, KAIS | Self-reported |
| `last_test_timing` | Time since last HIV test | Categorical | <12 months, 12-24 months, >24 months, Never | KENPHIA, KAIS | Self-reported |
| `test_result_received` | Received last test result | Binary | Yes, No | KENPHIA, KAIS | Self-reported |
| `testing_location` | Location of last HIV test | Categorical | Health facility, VCT site, Mobile testing, Home-based, Other | KENPHIA, KAIS | Self-reported |
| `test_initiated_by` | Who initiated the test | Categorical | Self, Provider, Partner, Other | KENPHIA, KAIS | Self-reported |
| `knows_hiv_status` | Knows own HIV status | Binary | Yes, No | Derived | Based on testing history and results |
| `willing_to_test` | Willing to test for HIV | Binary | Yes, No | KENPHIA, KAIS | Among never tested |

---

## HIV Status and Clinical Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `hiv_status_self_report` | Self-reported HIV status | Categorical | Positive, Negative, Unknown | KENPHIA, KAIS | Self-reported |
| `hiv_status_biomarker` | Laboratory-confirmed HIV status | Categorical | Positive, Negative, Indeterminate | KENPHIA | Rapid test + confirmatory |
| `hiv_status_final` | Final HIV status determination | Categorical | Positive, Negative | Derived | Combines self-report and biomarker |
| `cd4_count` | CD4+ T cell count (cells/μL) | Integer | 0-2000+ | KENPHIA, NDW | Most recent available |
| `cd4_category` | CD4 count categories | Categorical | <200, 200-349, 350-499, ≥500 | Derived | WHO staging categories |
| `viral_load` | HIV viral load (copies/mL) | Integer | 0-10000000+ | KENPHIA, NDW | Most recent available |
| `viral_suppression` | Virally suppressed status | Binary | Suppressed (<1000), Not suppressed (≥1000) | Derived | Standard threshold |
| `who_stage` | WHO clinical stage | Categorical | Stage I, Stage II, Stage III, Stage IV | NDW | Clinical assessment |
| `diagnosis_date` | Date of HIV diagnosis | Date | YYYY-MM-DD | NDW | First positive test date |
| `time_since_diagnosis` | Years since HIV diagnosis | Float | 0-30+ | Derived | Calculated from diagnosis date |

---

## Treatment and Care Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `ever_on_art` | Ever initiated ART | Binary | Yes, No | KENPHIA, NDW | Self-reported or clinical |
| `currently_on_art` | Currently taking ART | Binary | Yes, No | KENPHIA, NDW | At time of survey/visit |
| `art_initiation_date` | Date ART was initiated | Date | YYYY-MM-DD | NDW | First ART prescription |
| `time_to_art_initiation` | Days from diagnosis to ART | Integer | 0-7300+ | Derived | Treatment delay measure |
| `art_regimen` | Current ART regimen | Categorical | 1st line, 2nd line, 3rd line | NDW | Treatment line |
| `art_adherence` | ART adherence level | Categorical | Good (≥95%), Fair (85-94%), Poor (<85%) | KENPHIA, NDW | Self-reported or pill count |
| `treatment_interruption` | Ever interrupted ART | Binary | Yes, No | NDW | Treatment gap >30 days |
| `retention_in_care` | Retained in HIV care | Binary | Yes, No | Derived | Active in care definition |
| `appointment_adherence` | Kept last appointment | Binary | Yes, No | NDW | Clinic attendance |
| `care_facility` | Primary care facility | Text | Facility name/code | NDW | Where receiving care |

---

## Prevention Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `male_circumcised` | Male circumcision status | Binary | Circumcised, Not circumcised | KENPHIA, KAIS | Males only |
| `circumcision_type` | Type of circumcision | Categorical | Medical, Traditional | KENPHIA, KAIS | Where applicable |
| `prep_aware` | Aware of PrEP | Binary | Yes, No | KENPHIA | Pre-exposure prophylaxis |
| `prep_use` | Ever used PrEP | Binary | Yes, No | KENPHIA | Self-reported |
| `current_prep_use` | Currently using PrEP | Binary | Yes, No | KENPHIA | At time of survey |
| `condom_last_sex` | Used condom at last sex | Binary | Yes, No | KENPHIA, KAIS | Self-reported |
| `consistent_condom_use` | Always uses condoms | Binary | Yes, No | KENPHIA, KAIS | With any partner |
| `pmtct_attendance` | Attended PMTCT services | Binary | Yes, No | KENPHIA | Pregnant women |
| `art_during_pregnancy` | Received ART during pregnancy | Binary | Yes, No | KENPHIA | PMTCT indicator |

---

## Behavioral Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `sexual_partners_12m` | Number of sexual partners (12 months) | Integer | 0-50+ | KENPHIA, KAIS | Self-reported |
| `multiple_partners` | Multiple sexual partners | Binary | Yes (≥2), No (0-1) | Derived | Risk behavior indicator |
| `age_first_sex` | Age at first sexual intercourse | Integer | 5-35+ | KENPHIA, KAIS | Self-reported |
| `transactional_sex` | Engaged in transactional sex | Binary | Yes, No | KENPHIA, KAIS | Received money/gifts for sex |
| `alcohol_before_sex` | Alcohol use before sex | Binary | Yes, No | KENPHIA, KAIS | Last sexual encounter |
| `injecting_drug_use` | Ever injected drugs | Binary | Yes, No | KENPHIA, KAIS | Intravenous drug use |
| `shared_needles` | Ever shared needles | Binary | Yes, No | KENPHIA, KAIS | Among drug users |
| `partner_hiv_status` | Partner's HIV status | Categorical | Positive, Negative, Unknown | KENPHIA, KAIS | Main partner |
| `serodiscordant_couple` | HIV serodiscordant couple | Binary | Yes, No | Derived | Different HIV status |

---

## Survey and Data Source Variables

| Variable Name | Description | Data Type | Values/Range | Source | Notes |
|---------------|-------------|-----------|--------------|---------|-------|
| `survey_year` | Year of data collection | Integer | 2007, 2012, 2018 | Survey metadata | Survey round |
| `survey_type` | Type of survey/data source | Categorical | KAIS, KENPHIA, DHIS2, NDW | Survey metadata | Data collection method |
| `interview_date` | Date of interview | Date | YYYY-MM-DD | Survey metadata | Data collection date |
| `sample_weight` | Survey sampling weight | Float | 0.001-50.0 | Survey metadata | For population estimates |
| `cluster_id` | Primary sampling unit ID | Text | Variable | Survey metadata | Geographic cluster |
| `stratum` | Sampling stratum | Text | Variable | Survey metadata | Sampling design |
| `response_status` | Interview completion status | Categorical | Complete, Partial, Non-response | Survey metadata | Data quality indicator |
| `data_source_priority` | Data source priority ranking | Integer | 1-5 | Derived | For data integration |

---

## Calculated Indicators

| Variable Name | Description | Data Type | Formula/Calculation | Notes |
|---------------|-------------|-----------|---------------------|-------|
| `hiv_prevalence` | HIV prevalence (%) | Float | (HIV+ individuals / Total tested) × 100 | Population-weighted |
| `testing_coverage` | HIV testing coverage (%) | Float | (Ever tested / Total eligible) × 100 | 15+ years |
| `knowledge_of_status` | Knowledge of HIV status (%) | Float | (Know status / HIV+) × 100 | Among HIV positive |
| `art_coverage` | ART coverage (%) | Float | (On ART / HIV+) × 100 | Among diagnosed |
| `viral_suppression_rate` | Viral suppression rate (%) | Float | (Suppressed / On ART) × 100 | <1000 copies/mL |
| `retention_rate` | Retention in care rate (%) | Float | (Active in care / Ever in care) × 100 | 12-month retention |
| `cascade_90_1` | First 90 achievement (%) | Float | (Diagnosed / HIV+) × 100 | Know status |
| `cascade_90_2` | Second 90 achievement (%) | Float | (On ART / Diagnosed) × 100 | On treatment |
| `cascade_90_3` | Third 90 achievement (%) | Float | (Suppressed / On ART) × 100 | Viral suppression |
| `incidence_rate` | HIV incidence rate | Float | New infections / Person-years at risk | Per 1000 person-years |

---

## Data Quality Variables

| Variable Name | Description | Data Type | Values/Range | Purpose |
|---------------|-------------|-----------|--------------|---------|
| `missing_data_flag` | Missing data indicator | Binary | Yes, No | Quality assessment |
| `outlier_flag` | Statistical outlier flag | Binary | Yes, No | Data validation |
| `consistency_check` | Cross-variable consistency | Binary | Pass, Fail | Logic validation |
| `geocoding_accuracy` | Geographic coding accuracy | Categorical | High, Medium, Low | Spatial data quality |
| `survey_confidence` | Survey-based confidence level | Categorical | High, Medium, Low | Estimate reliability |
| `sample_size` | Effective sample size | Integer | Variable | Power calculation |
| `design_effect` | Survey design effect | Float | 1.0-10.0 | Sampling efficiency |
| `data_completeness` | Record completeness score | Float | 0.0-1.0 | Overall data quality |

---

## Data Coding and Missing Values

### Standard Codes
- **Missing/Unknown**: 999, "Unknown", "Missing"
- **Not Applicable**: 998, "N/A"
- **Refused to Answer**: 997, "Refused"
- **System Missing**: NULL, blank

### Special Populations
- **Children**: Age-specific variables and thresholds
- **Pregnant Women**: Pregnancy-specific indicators
- **Key Populations**: Special risk group classifications
- **Clinical Populations**: Facility-based indicators

---

## Data Integration Notes

### Weighting
- Survey weights applied for population representativeness
- Post-stratification weights for demographic alignment
- Facility weights for health system data

### Geographic Harmonization
- Administrative boundaries aligned across data sources
- County-level aggregation for consistency
- Urban/rural classifications standardized

### Temporal Alignment
- Survey periods adjusted for seasonal variations
- Clinical data aligned to survey reference periods
- Trend analysis accounts for methodological changes

---

## Usage Guidelines

### Statistical Analysis
- Always apply appropriate survey weights
- Account for complex survey design in variance estimation
- Use confidence intervals for all prevalence estimates
- Consider design effects in sample size calculations

### Data Interpretation
- Understand data collection contexts and limitations
- Consider temporal gaps between data sources
- Account for geographic variations in data quality
- Validate findings across multiple indicators

### Visualization Recommendations
- Use appropriate scales for different indicator types
- Apply consistent color schemes across visualizations
- Include confidence intervals in trend analyses
- Provide data source annotations

---

*For additional information or clarification on any variables, please contact the project team.*