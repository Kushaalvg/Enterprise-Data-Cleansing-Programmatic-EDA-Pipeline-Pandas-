# 🐍 Enterprise Data Cleansing & Programmatic EDA Pipeline (Pandas)

## 📌 Project Overview
This repository contains advanced data engineering, string normalization, and exploratory business intelligence (EDA) workflows executed completely within Python using **Pandas** and **NumPy**. Real-world enterprise datasets are rarely clean or standardized. This portfolio contains two full-scale analytics projects that process separate industrial datasets to solve distinct database optimization and macro-demographic analysis hurdles.

Rather than relying on manual row-by-row filtration, these pipelines utilize highly scalable vectorized operations to convert chaotic data records into structured, high-integrity assets ready for production-level downstream BI dashboards or ML engines.

---

## 🎯 Core Business Objectives Solved
1. **Automated Data Quality Engineering:** Designed systematic regex and string-stripping pipelines to sanitize customer records, phone indices, and compound address values.
2. **Missing Input Resolution & Imputation:** Implemented vector-based fill logic and string replacements to reconcile missing structural data blocks without breaking relational schemas.
3. **Macro Demographic Exploration:** Conducted descriptive multi-axis aggregations and statistical boundary mapping across global population records from 1970 to 2022.

---

## 🛠️ Tech Stack & Key Data Science Libraries
* **Core Framework:** Python 3 (Jupyter Notebook Ecosystem)
* **Data Processing & Vectors:** Pandas, NumPy
* **Data Ingestion Engines:** OpenPyXL (Excel parsing engine)
* **Statistical Visualization:** Seaborn, Matplotlib

---

## 📂 Project 1: Customer Call List Cleaning & Schema Optimization
* **Business Use Case:** A direct sales team needs an optimized customer call sheet. The raw input contains duplicate records, invalid phone strings, irregular boolean entries, and unparsed address text fields.
* **Key Implementation Methods:**
  * **Deduplication:** Programmatic evaluation and removal of redundant entry blocks using `df.drop_duplicates()`.
  * **String Normalization:** Applied regular expression sanitization via `.str.replace(r'\D', '', regex=True)` to strip non-numeric artifacts from customer phone numbers and reformatted into clean standard indices (`000-000-0000`).
  * **Categorical Standardization:** Mapped fragmented string variants (e.g., matching combinations of `Yes`, `Y`, `No`, `N`) into unified boolean indicators (`Y`/`N`).
  * **Compound Field Splitting:** Parsed nested string columns into structural columns (`Street_Address`, `State`, `Zip_Code`) using text boundaries:
    ```python
    df[['Street_Address', 'State', 'Zip_Code']] = df['Address'].str.split(',', expand=True)
    ```
  * **Regulatory Compliance Compliance:** Filtered out database entries flagged as `Do_Not_Contact == 'Y'` or records missing critical contact columns (`Phone_Number == ''`) to preserve operational legal boundaries.

---

## 📂 Project 2: Global Population Macro Exploratory Analysis (EDA)
* **Business Use Case:** Exploring macro-economic historical data shifts across a 234-country population index to establish rapid descriptive summaries for strategic resource allocation.
* **Key Implementation Methods:**
  * **Database Diagnostics:** Inspected structural metrics using `.info()`, `.describe()`, `.isnull().sum()`, and `.nunique()` to discover internal data shapes and coordinate matrix limits.
  * **Data Structuring Controls:** Configured custom global visualization floating point settings to eliminate notation noise on high-value populations:
    ```python
    pd.set_option('display.float_format', lambda x: '%.2f' % x)
    ```
  * **Multi-Axis Sorting:** Discovered the top 10 most populated international sectors by sorting world percentages with `.sort_values(by="World Population Percentage", ascending=False)`.
  * **Statistical Matrix Mapping:** Built feature-to-feature matrix mappings via `.corr(numeric_only=True)` to discover historical trend growth speeds and mapped correlations using **Seaborn Heatmaps** and **Matplotlib Boxplots** to identify distribution outliers across global continents.

---

## 📊 Structural Pipeline & Data Quality Impact Metrics

| Analysis Layer | Raw Dataset Condition (Ingested Data) | Optimized Production Condition (Analysis-Ready) | Downstream Value Passed to Business BI |
| :--- | :--- | :--- | :--- |
| **Record Uniqueness** | Redundant client entries present | **0 Duplicates** (Systematically pruned) | Prevents artificial inflation of contact lists. |
| **Phone Validation** | Mixed text characters, sashes, and pipes (`123/643/9775`) | **Standardized Delimited Strings** (`123-643-9775`) | Minimizes human error and dials clients smoothly. |
| **Address Architecture**| Long compound string blocks | **Parsed Columns** (Street, State, Zip) | Allows regional filtering and demographic mapping. |
| **Matrix Exploration** | Raw un-summarized rows | **Correlated and Visualized Layouts** | Grants C-suite rapid views of global population run-rates. |

---

## 🏁 Conclusion
This Python track demonstrates the versatility of the Pandas framework in handling two completely separate data environments—moving smoothly from granular, operation-level data cleaning to high-level macro-economic trend discovery. Both systems are fully optimized to serve as clean data layers for downstream deployment into Power BI or Tableau dashboard environments.
