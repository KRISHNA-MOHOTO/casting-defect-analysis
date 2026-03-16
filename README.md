# 🏭 Manufacturing Casting Defect Analysis — SQL EDA Project

**Tools:** MySQL · Excel · Power BI *(dashboard in progress)*  
**Domain:** Manufacturing Operations · Quality Engineering  
**Skills Demonstrated:** Exploratory Data Analysis · Process Parameter Analysis · Defect Trend Investigation · Business Insight Communication

---

## 📌 Project Background

This project simulates a real-world manufacturing quality investigation for a metal casting production facility. The dataset covers **4,800 production batches** across 3 lines, 3 machines, 2 shifts, and 15 operators — spanning January to May 2024.

The business problem: **defect rates are unacceptably high.** The goal is to use SQL-based EDA to identify *where*, *when*, and *why* defects are occurring — and translate that into actionable operational recommendations.

> This project is part of my Data Analyst career transition portfolio. I bring 3+ years of hands-on experience as an Industrial Engineer in casting and manufacturing operations, which means I understand not just the data, but the real-world context behind it.

---

## 📂 Repository Structure

```
casting-defect-analysis/
│
├── README.md
├── data/
│   └── casting_defects_raw.csv        ← source dataset (synthetic)
└── sql/
    └── casting_defects_eda.sql        ← full EDA queries (MySQL)
```

---

## 📊 Dataset Overview

| Attribute | Detail |
|---|---|
| Rows (Batches) | 4,800 |
| Date Range | Jan 2024 – May 2024 |
| Total Parts Produced | 500,115 |
| Total Defects Found | 161,191 |
| **Overall Defect Rate** | **32.23%** |
| Production Lines | L-1, L-2, L-3 |
| Machines | M-01, M-02, M-03 |
| Shifts | Day, Night |
| Operators | 15 |
| Defect Types | Blowhole, Cold Shut, Misrun, Shrinkage |
| Process Parameters | Mold Temp (°C), Pour Temp (°C), Moisture %, Sand Ratio |

---

## 🔍 Key Findings

### 1. Overall Defect Rate — 32.23% 🚨
Nearly 1 in 3 parts produced had a defect. This is a critical quality issue requiring immediate investigation across machines, shifts, and process parameters.

---

### 2. Night Shift Underperforms Significantly
| Shift | Defect Rate |
|---|---|
| Day | 29.60% |
| **Night** | **34.86%** |

Night shift shows **~18% higher defect rate** than day shift. This gap could indicate fatigue-related issues, reduced supervision, or inconsistent process control during handovers — all common in real casting operations.

---

### 3. Machine M-03 Is the Biggest Problem
| Machine | Defect Rate |
|---|---|
| M-01 | 28.82% |
| M-02 | 29.13% |
| **M-03** | **38.95%** |

Machine M-03 has a defect rate **35% higher than M-01 and M-02**. This points to a potential maintenance issue, calibration drift, or machine-specific process instability that needs investigation.

---

### 4. Defect Types Are Evenly Distributed
| Defect Type | Total Defects | Share |
|---|---|---|
| Misrun | 41,162 | ~25.5% |
| Shrinkage | 40,200 | ~24.9% |
| Blowhole | 40,104 | ~24.9% |
| Cold Shut | 39,725 | ~24.6% |

All four defect types occur at nearly equal frequency — meaning this is not a single-cause problem. Multiple process parameters (temperature, moisture, sand ratio) are likely contributing simultaneously.

---

### 5. Process Parameters Show Out-of-Range Conditions
The SQL analysis bins each process parameter into Low / Optimal / High ranges and compares defect rates across bands. Key observations:

- **Moisture %** outside the optimal 3.0–4.5% range correlates with higher defect rates
- **Pour Temperature** deviating from the 1380–1420°C optimal window shows increased defects
- **Mold Temperature** above 215°C or below 195°C links to elevated defect occurrence
- **Sand Ratio** outside 0.82–0.88 correlates with more defects

> These findings align with my real-world DMAIC work at Bangalore Metallurgicals, where process parameter control was the primary lever for defect reduction.

---

## 🛠️ SQL Analysis Structure

The SQL file is organized into 6 sections:

| Section | Purpose |
|---|---|
| 0 — Table Setup | CREATE TABLE and CSV import instructions |
| 1 — Dataset Overview | Row counts, date range, null checks, data quality flags |
| 2 — Overall Defect Rate | Headline metric + monthly trend |
| 3 — Defect Breakdown | By shift, machine, line, defect type, operator, machine×shift cross-tab |
| 4 — Process Parameter Analysis | Moisture, pour temp, mold temp, sand ratio banded vs defect rate |
| 5 — Summary Statistics | Min, max, avg, stddev for all numeric columns |
| 6 — Export Queries | Ready-to-export CSVs for Power BI and Excel |

---

## 💡 Business Recommendations

Based on the SQL EDA findings:

1. **Prioritize M-03 for maintenance inspection** — its 38.95% defect rate is significantly above the facility average and both other machines
2. **Investigate Night Shift operations** — the ~5 percentage point gap vs Day shift warrants a process audit, shift handover review, and operator training assessment
3. **Tighten process parameter controls** — moisture %, pour temperature, and mold temperature are the primary controllable variables. Implementing SPC alerts at operator workstations can prevent out-of-range batches before defects occur
4. **No single defect type dominates** — since all four defect types are nearly equal in volume, a multi-variable approach (not a single fix) is needed

---

## 📈 Power BI Dashboard — In Progress 🚧

A Power BI dashboard is currently being developed to visualize:
- Monthly defect rate trend line
- Machine × Shift heatmap
- Pareto chart of defect types
- Process parameter scatter plots (moisture vs defect rate, pour temp vs defect rate)
- Operator performance comparison

---

## 👤 About Me

**Krishna Mohoto** — Industrial Engineer transitioning to Data Analyst  
3+ years in manufacturing operations, quality engineering (Volvo), and casting operations (Bangalore Metallurgicals)  
Led a real DMAIC initiative that reduced blowhole defects from **70% → 20%** in casting production

📧 krishnamohoto90@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/krishna-mohoto-3009b1175)

---

*Dataset is synthetic and created for portfolio purposes.The analysis was performed using MySQL on a local server. 
Queries were designed to replicate a typical manufacturing quality investigation workflow:
data validation → defect rate calculation → categorical breakdown → process parameter analysis.*
