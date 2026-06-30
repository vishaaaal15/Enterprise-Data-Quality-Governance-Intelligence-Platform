# 🛡️ Enterprise Data Quality & Governance Intelligence Platform

**Author:** Vishal Singh | [LinkedIn](https://linkedin.com/in/vishal-singhdataanalyst) | [GitHub](https://github.com/vishaaaal15)  
**Stack:** SQL · Python · Power BI · Tableau  
**Dataset:** 300,000+ enterprise records across multiple business domains  
**Domain:** Data Governance · Data Quality Management · Regulatory Compliance

---

## 📌 Project Overview

An enterprise data quality and governance platform that assesses 300K+ records across multiple business domains for data integrity failures. Delivers automated SQL/Python validation frameworks and dual-platform dashboards (Power BI + Tableau) that monitor governance KPIs and reporting health — replicating the independent data challenge function of a GRC/Data Governance team.

---

## 📁 Repository Structure

```
Enterprise-Data-Quality-Governance-Intelligence-Platform/
│
├── data/
│   ├── enterprise_records.csv           # 300K+ enterprise records
│   └── data_dictionary.csv             # Field definitions and rules
│
├── sql_queries/
│   ├── 01_completeness_check.sql        # NULL / missing value detection
│   ├── 02_accuracy_validation.sql       # Value range and format checks
│   ├── 03_consistency_check.sql         # Cross-table consistency rules
│   ├── 04_uniqueness_check.sql          # Duplicate detection
│   ├── 05_timeliness_check.sql          # Stale / late data identification
│   ├── 06_referential_integrity.sql     # Orphaned record detection
│   └── ...30 total validation queries
│
├── python_analysis/
│   ├── dq_validation_framework.py       # Automated data quality scoring
│   ├── anomaly_detector.py             # Statistical outlier detection
│   ├── dq_report_generator.py          # Auto-generates DQ summary report
│   └── lineage_tracker.py              # Basic data lineage mapping
│
├── dashboards/
│   ├── DQ_Governance_PowerBI.pbix       # Power BI — DQ KPI monitoring
│   └── DQ_Health_Tableau.twbx          # Tableau — Data health deep-dive
│
└── outputs/
    ├── dq_kpi_summary.csv               # Overall DQ scores by domain
    ├── failed_records_log.csv           # Records failing validation rules
    ├── governance_health_report.csv     # Domain-wise governance scorecard
    └── corrective_recommendations.csv  # Prioritised fix recommendations
```

---

## 🔍 Data Quality Dimensions Covered

| Dimension | Definition | Rules Implemented |
|-----------|-----------|-------------------|
| Completeness | No missing critical fields | 8 SQL checks |
| Accuracy | Values within valid ranges | 7 SQL checks |
| Consistency | Same data = same values across tables | 5 SQL checks |
| Uniqueness | No duplicate primary keys | 4 SQL checks |
| Timeliness | Records updated within SLA | 4 SQL checks |
| Referential Integrity | No orphaned foreign keys | 2 SQL checks |

---

## 📊 Key Governance Findings

| KPI | Value | Status |
|-----|-------|--------|
| Records Assessed | 300,000+ | — |
| Overall DQ Score | 82.4% | 🟡 NEEDS IMPROVEMENT |
| Critical Field Completeness | 91.2% | MONITOR |
| Duplicate Records Found | 4,312 | 🔴 ALERT |
| Referential Integrity Failures | 1,847 | 🔴 ALERT |
| Stale Data (>30 days) | 8,100 records | MONITOR |
| Records Corrected Post-Framework | 12,500+ | ✅ RESOLVED |

---

## 🐍 Python — Automated DQ Framework

```python
import pandas as pd
import numpy as np

class DataQualityFramework:
    def __init__(self, df):
        self.df = df
        self.results = {}

    def completeness_score(self):
        """% of non-null values across all fields"""
        score = (1 - self.df.isnull().sum() / len(self.df)) * 100
        self.results['completeness'] = score.mean().round(2)
        return score

    def uniqueness_score(self, key_cols):
        """Duplicate detection on primary key columns"""
        dupes = self.df.duplicated(subset=key_cols).sum()
        score = (1 - dupes / len(self.df)) * 100
        self.results['uniqueness'] = round(score, 2)
        return dupes

    def accuracy_score(self, col, min_val, max_val):
        """Value range validation"""
        valid = self.df[col].between(min_val, max_val).sum()
        score = valid / len(self.df) * 100
        self.results[f'accuracy_{col}'] = round(score, 2)
        return score

    def generate_report(self):
        """Outputs governance scorecard"""
        return pd.DataFrame.from_dict(
            self.results, orient='index', columns=['Score_%']
        )
```

---

## 📈 Dashboard Features

**Power BI — DQ KPI Monitor**
- Overall DQ score gauge (Red/Amber/Green)
- Dimension-wise score breakdown (radar chart)
- Failed records trend over time
- Top 10 fields with highest failure rates

**Tableau — Data Health Deep-Dive**
- Record-level failure heatmap by domain
- Lineage flow showing data quality at each stage
- Corrective action progress tracker
- SLA compliance by domain

---

## 🛠️ How to Run

```bash
git clone https://github.com/vishaaaal15/Enterprise-Data-Quality-Governance-Intelligence-Platform
pip install pandas numpy matplotlib seaborn
python python_analysis/dq_validation_framework.py
```

---

## 🏷️ Topics
`data-quality` `data-governance` `sql` `python` `power-bi` `tableau` `data-validation` `enterprise-analytics` `compliance` `etl` `data-lineage` `kpi-monitoring`
