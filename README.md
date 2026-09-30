# Privacy-Preserving Data Anonymization & Reidentification Analysis

## Overview

This project explores data anonymization and reidentification risks using
the **Give Me Some Credit** financial dataset.

The objective is to evaluate how different anonymization strategies affect
the ability to uniquely identify individuals while preserving useful
information for predictive modelling.

The project was developed using Python and Pandas as part of a data
privacy and anonymization laboratory.

---

## Objectives

- Identify personal, sensitive and quasi-identifying attributes
- Assess the identification power of dataset features
- Select features suitable for predictive modelling
- Apply generalization-based anonymization techniques
- Create different anonymization scenarios
- Measure reidentification rates
- Analyze the privacy–utility trade-off

---

## Dataset

**Give Me Some Credit**

- Population: **150,000 records**
- Domain: Financial / credit risk
- Target variable: `SeriousDlqin2yrs`

The original dataset is not included in this repository.

Dataset source: Kaggle — Give Me Some Credit

---

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Google Colab
- Jupyter Notebook

---

## Methodology

### 1. Data Profiling

Descriptive statistics were calculated for each feature, including:

- Number of records
- Missing values
- Minimum
- Maximum
- Mean
- Standard deviation

### 2. Privacy Classification

Each feature was classified according to:

- Personal data
- Sensitive data
- Identifier
- Quasi-identifier

### 3. Identification Power

Each feature was assigned an identification-power score from **0 to 3**:

| Score | Meaning |
|---|---|
| 0 | Very low / no direct reidentification power |
| 1 | Quasi-identifier with lower privacy risk |
| 2 | Sensitive quasi-identifier |
| 3 | Direct identifier or highly identifying attribute |

### 4. Anonymization

Generalization techniques were applied to selected numerical features.

Examples include:

- Age-range generalization
- Income-range generalization
- Category generalization
- Equal-frequency grouping

### 5. Reidentification Analysis

For each anonymization scenario, an identifier was constructed by combining
the selected feature values.

An identifier occurring only once was considered uniquely identifiable.

The reidentification rate was calculated as:

`Reidentification Rate = Unique Identifiers / Total Population × 100`

---

## Anonymization Scenarios

### Case A — All Predictors Anonymized

All selected predictor variables were generalized.

### Case B — Keep Identification Power 0–1

Variables with identification power 0 and 1 were retained,
while power-2 variables were generalized.

### Case C — Keep Identification Power 0–2

Variables with identification power 0, 1 and 2 were retained without
generalization.

---

## Results

| Scenario | Unique Identifiers | Population | Reidentification Rate |
|---|---:|---:|---:|
| Case A — All anonymized | 4,852 | 150,000 | **3.2347%** |
| Case B — Keep power 0–1 | 43,496 | 150,000 | **28.9973%** |
| Case C — Keep power 0–2 | 149,000 | 150,000 | **99.3333%** |

---

## Key Findings

The experiment demonstrates the relationship between data precision and
reidentification risk.

Generalizing the predictor variables substantially reduced the number of
unique feature combinations.

When more precise information was retained, the number of uniquely
identifiable records increased significantly.

The results also demonstrate the **privacy–utility trade-off**: stronger
generalization can improve privacy protection, while excessive
generalization may reduce the usefulness of the data for predictive
modelling.

---

## Project Structure

```text
privacy-anonymization-reidentification/
│
├── README.md
├── privacy-anonymization-reidentification.ipynb
└── report.pdf
