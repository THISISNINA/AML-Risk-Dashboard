# AML Compliance and Risk Analysis Dashboard

## Project Overview
This Power BI dashboard was developed to automate Anti-Money Laundering (AML) monitoring and risk-scoring. The tool streamlines the identification of high-risk transactions and PEP (Politically Exposed Persons) matches, allowing compliance teams to prioritize investigation and Enhanced Due Diligence (EDD).

---

## Key Features
* **Automated Risk Scoring**: Logic-based categorization of clients into High, Medium, and Low risk tiers.
* **PEP Monitoring**: Tracking for high-priority matches to improve investigation speed.
* **Data Filtering**: Integrated slicers for filtering by risk level, payment method, and transaction thresholds.
* **Core Metrics**: KPI tracking for total transaction volume and alert frequency.

---

## Technical Implementation

### 1. Risk Scoring Logic (DAX)
The risk model uses a weighted scoring engine based on PEP status, payment method, and transaction value.

```dax
RiskLevel_Status = 
VAR Score = 
    IF('in'[Is_PEP] = "Yes", 50, 0) + 
    IF('in'[Payment_Method] = "Cash", 30, 0) + 
    IF('in'[Transaction_Value] > 100000, 20, 0)
RETURN
    SWITCH(TRUE(),
        Score >= 70, "High",
        Score >= 40, "Medium",
        "Low"
    )

```

### 2. Logic and Sorting

* **Circular Dependency Resolution**: Fixed internal Power BI calculation errors by decoupling sort-order keys from the status labels.
* **Custom Sorting**: Implemented logic to ensure a Low-Medium-High progression in the user interface.

---

## Dashboard Preview


---

## Data Privacy and Attribution

**Note on Data Source:** This dashboard is built using strictly synthetic data.

* **Synthetic Data**: All names, account details, and transaction values are AI-generated.
* **Privacy**: No real-world private or confidential information was used in this project.
* **Purpose**: This dataset was created specifically to demonstrate DAX logic and data modeling within a compliance context.

---

## Files in this Repository

* **AML_Analysis.pbix**: The Power BI project file.
* **AML_Dataset.csv**: The synthetic raw data used for the analysis.
* **README.md**: Project documentation.

```
