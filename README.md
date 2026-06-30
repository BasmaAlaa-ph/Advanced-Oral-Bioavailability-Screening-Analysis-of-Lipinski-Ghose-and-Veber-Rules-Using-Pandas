# Advanced Oral Bioavailability Screening Analysis of Lipinski, Ghose and Veber Rules Using Pandas

A high-performance cheminformatics tool designed to automate oral bioavailability filtering. This pipeline translates medicinal chemistry rules into highly optimized Python logic, screening a dataset of **15,166 compounds** across 9 molecular descriptors in seconds.

## 🧪 Integrated Filters
* **Lipinski's Rule of 5:** Benchmarking fundamental membrane permeability.
* **Ghose Filter:** Enforcing rigid boundaries for functional drug-like properties.
* **Veber's Rules:** Assessing molecular flexibility and Polar Surface Area (TPSA).
* **LogP Sweet Spot:** Targeting the ideal hydrophilic-lipophilic balance (0.5–3.5).

## 📊 Technical Highlights & Engineering Decisions
* **High-Performance Vectorization:** Eliminated slow, non-scalable Python loops. By leveraging Boolean evaluation and `.astype(int)`, cumulative molecular violations are computed via fast matrix addition across 15k+ rows.
* **Defensive Data Auditing:** Resolved implicit string-to-numeric type mismatches in raw data using `pd.to_numeric(errors='coerce')`, ensuring zero pipeline crashes while safeguarding dataset integrity.
* **Strict Multi-Parametric Consensus:** Implemented decoupled data subsets with `.copy()` to block memory leaks, applying row-wise vector alignment (`.apply(axis=1)`) to evaluate all four chemical filters simultaneously.

## 📈 Screening Results & Insights
* **Lipinski Pass Rate:** 90.21%
* **Veber Pass Rate:** 71.97%
* **Ghose Pass Rate:** 46.20%
* **LogP Sweet Spot:** 44.13%
* **Consensus (Passed All Filters):** **22.48%**

*Takeaway: The steep drop to a 22.48% consensus rate highlights the computational bottleneck in early-stage R&D drug discovery—the molecular "sweet spot" is exceptionally narrow.*

## 🚀 Repository Contents
* `*.ipynb`: Interactive Google Colab notebook featuring data exploration, debugging logs, and live outputs.
* `*.py`: Production-ready, clean Python script version of the automation logic.
