# Clary -- AI-Powered AML Alert Explainability for SMB Compliance Officers

**Course:** RSM 8542 -- Analytics for Marketing Strategy, Rotman School of Management  
**Student:** Sanjana Kanchibotla Sri Lalitha (1012563067)  
**Program:** Masters of Management Analytics, Rotman 2026  
**Term:** Spring 2026

---

## Product overview

Clary is a B2B SaaS compliance co-pilot that sits on top of any existing transaction monitoring system (TMS) -- including FICO and Temenos -- and converts black-box AML alert scores into three actionable outputs: a plain-English explanation of why the alert fired, a ranked investigative checklist sourced from FINTRAC and FinCEN typologies, and a pre-populated SAR/STR draft narrative. It integrates via API to the existing alert payload and requires no ML retraining.

Target customer: BSA/AML compliance analysts at Tier-3/4 Canadian and U.S. banks and credit unions with assets below $5B that must meet FINTRAC/FinCEN obligations without large compliance teams.

---

## Analytics modules

This repository contains the technical appendix for the final project report. Two analytics modules are implemented.

**Module A -- Customer Lifetime Value and Unit Economics**

Estimates discounted contribution-margin CLV per customer segment and pricing tier using the formula:

    CLV = (MRR x Gross Margin) / (Monthly Churn Rate + Monthly Discount Rate)

Outputs drive three marketing decisions: segment acquisition priority (Consultant vs. Direct Bank), pricing tier selection (Tier 1 at $1,200/mo vs. Tier 2 at $2,800/mo), and channel budget ceiling per segment.

**Module E -- A/B Test Simulation (Pricing Page Messaging)**

Simulates a two-proportion z-test comparing pain framing (Variant A) against ROI framing (Variant B) on the Clary pricing page. Computes minimum sample size via power analysis and validates it with Monte Carlo simulation (10,000 iterations). Output determines how many inbound trial sign-ups are required before the test produces reliable results.

---

## Repository structure

| File | Description |
|---|---|
| analytics.ipynb | Full annotated notebook: parameters, CLV model, sensitivity analysis, A/B simulation, all figures, decision outputs |
| table_base_clv.csv | Base-case CLV, max viable CAC, and CLV:CAC ratios across all segment-tier-channel combinations |
| table_sensitivity_clv.csv | CLV and CLV:CAC across churn sensitivity ranges for all segment-tier-channel combinations |
| fig1_clv_by_segment_tier.png | Base-case CLV by segment and pricing tier |
| fig2_clv_cac_by_channel.png | CLV:CAC ratio by segment, tier, and acquisition channel |
| fig3_sensitivity_heatmap.png | Heatmap of CLV:CAC across churn rates and channels (2x2 grid by segment and tier) |
| fig4_payback_period.png | CAC payback period in months by channel and tier |
| fig5_ab_power_curve.png | Empirical A/B test power vs. sample size per variant |
| fig6_ab_distributions.png | Simulated sampling distributions under H0 and H1 for the pricing page test |
| Sanjana_Individual_Proposal_RSM8542.pdf | Submitted project proposal (Mar 10, 2026) |
| RSM8542_Individual_Project_DataDriven_Launch_Plan_2026.pdf | Course assignment brief |

---

## How to reproduce

Requires Python 3.9 or later. Install dependencies:

    pip install numpy pandas matplotlib scipy

Run the notebook:

    jupyter notebook analytics.ipynb

Execute all cells in order (Kernel > Restart and Run All). All figures and CSVs are written to the working directory. No external data files are required -- all data is simulated within the notebook with parameters documented inline.

---

## Data-generating process

All data is simulated. Parameters are calibrated to published benchmarks cited inline in the notebook. Key sources:

- Benchmarkit 2024 B2B SaaS Performance Metrics (gross margin, CLV:CAC floor)
- wearefounders.uk 2026 (FinTech annual churn benchmark, referral CAC)
- SaaSHero 2026 (LinkedIn CAC for FinTech, payback ceiling)
- First Page Sage 2025 (Google Search paid B2B CAC)
- sopro.io 2025 (trade show cost per lead)
- UserMotion 2024 (churn sensitivity range)
- KeyBanc 2024 (B2B SaaS trial-to-paid conversion baseline)
- HubSpot 2025 (LinkedIn MQL-to-SQL conversion range)

No real customer data was collected. No personal data is stored or transmitted.
