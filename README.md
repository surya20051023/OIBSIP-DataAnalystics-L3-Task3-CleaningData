# OIBSIP-DataAnalystics-L3-Cleaning-Data-
# Task 3: Data Cleaning and Data Quality Analysis

## Project Overview

This project demonstrates a systematic approach to cleaning a messy dataset using Python, Pandas, NumPy, and Jupyter Notebook. The main objective is to identify data quality issues, apply appropriate cleaning techniques, document each decision, and transform the raw data into a clean, analysis-ready dataset.

The Titanic passenger dataset is used as a practical example. A copy of the dataset is modified to introduce additional data quality issues, allowing the cleaning workflow to demonstrate missing-value handling, duplicate removal, standardisation, data type correction, and outlier detection.

## Objectives

- Load the dataset and generate an initial data quality report.
- Identify missing values and select appropriate handling strategies.
- Detect and remove duplicate records.
- Standardise inconsistent categorical values and text formatting.
- Detect numerical outliers using the Interquartile Range (IQR) method.
- Correct data types, including numeric values, identifiers, and dates.
- Compare data quality before and after cleaning.
- Export the cleaned dataset and supporting reports as CSV files.

## Technologies Used

- **Python** — programming language
- **Pandas** — data manipulation and cleaning
- **NumPy** — numerical operations and missing-value handling
- **Matplotlib** — data visualisation
- **Seaborn** — boxplots and outlier visualisation
- **Jupyter Notebook** — interactive development and documentation

## Dataset

**Dataset name:** Titanic Passenger Dataset

**Source:**  
https://www.kaggle.com/datasets/yasserh/titanic-dataset

**Alternative source:**  
https://github.com/datasciencedojo/datasets/blob/master/titanic.csv

The dataset contains passenger information such as passenger ID, survival status, passenger class, name, gender, age, family relationships, ticket details, fare, cabin, and embarkation port.

For demonstration purposes, a copy of the original dataset is used to introduce additional data quality issues. The original dataset is preserved unchanged.

## Data Quality Issues Addressed

The project investigates the following issues:

1. Missing values in numerical and categorical columns.
2. Duplicate rows that may cause records to be counted more than once.
3. Inconsistent categorical values, such as different representations of gender and embarkation ports.
4. Incorrect data types, such as numeric values stored as strings.
5. Mixed date formats requiring conversion to datetime.
6. Invalid numerical values, including negative ages and fares.
7. Outliers in numerical columns such as age, fare, and family counts.

## Data Cleaning Methodology

### 1. Data Loading and Inspection

The raw dataset is loaded using Pandas. Its dimensions, column names, data types, missing values, and descriptive statistics are examined to understand its initial condition.

### 2. Data Quality Report

A quality report is generated containing:
- Null count and null percentage for each column.
- Number of unique values.
- Data types.
- Total duplicate rows.
- Minimum and maximum values for relevant numeric columns.

### 3. Missing Data Handling

Missing values are handled according to the meaning of each column:

- **Age:** Median imputation grouped by passenger class and gender, with the overall median as a fallback.
- **Fare:** Median imputation grouped by passenger class, with the overall median as a fallback.
- **Embarked:** Mode imputation using the most frequent valid category.
- **Cabin:** A `HasCabin` indicator is created before removing the highly incomplete original column.
- **Unparseable dates:** Reviewed and retained as missing until an explicit removal or correction decision is applied.

These strategies avoid blindly replacing all missing values with zero.

### 4. Duplicate Removal

Exact duplicate records are identified using Pandas and removed using `drop_duplicates()`. The number of duplicate rows removed is recorded for the final report.

### 5. Data Standardisation

Inconsistent text values are cleaned by removing leading and trailing whitespace and mapping equivalent categorical labels to consistent values.

For example:
- `M`, `male`, and `Male` are standardised to `Male`.
- Variations of embarkation port names are mapped to the corresponding codes.

### 6. Data Type Correction

Numeric columns are converted to appropriate numeric types, passenger identifiers are represented as strings, and date values are converted to Pandas datetime format.

### 7. Outlier Detection

The Interquartile Range (IQR) method is used to identify unusual numerical observations.

The lower and upper boundaries are calculated as:

- IQR = Q3 − Q1
- Lower bound = Q1 − 1.5 × IQR
- Upper bound = Q3 + 1.5 × IQR

Outliers are flagged and reviewed rather than automatically removed. Valid extreme observations are retained to avoid unnecessary information loss.

### 8. Before-and-After Comparison

The final quality report compares the raw and cleaned datasets using:
- Row count.
- Total missing cells.
- Duplicate row count.
- Data type accuracy.
- Data type changes.

### 9. Export

The cleaned dataset and supporting quality reports are exported to CSV files for further analysis.

## Project Structure

```text
Task3-Data-Cleaning/
│
├── titanic.csv
├── Task3_Data_Cleaning.ipynb
│
└── output/
    ├── titanic_messy.csv
    ├── titanic_cleaned.csv
    ├── data_quality_before_after.csv
    ├── outlier_report.csv
    └── dtype_comparison.csv
│
└── README.md
```

The `titanic.csv` file is the original source dataset. The notebook creates `titanic_messy.csv` for demonstration and generates the cleaned dataset and reports in the `output/` directory.

## Installation and Setup

### Step 1: Clone or download the project

Download the project files and place them in a local folder.

### Step 2: Install dependencies

Run the following command in a terminal or Jupyter Notebook:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Step 3: Place the dataset

Download the Titanic CSV file and place it in the project directory with the filename `titanic.csv`.

### Step 4: Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `Task3_Data_Cleaning.ipynb`.

### Step 5: Run the notebook

Execute the notebook cells in order, from importing libraries and loading the dataset through cleaning, validation, comparison, and export.

## Output Files

| File | Description |
|---|---|
| `titanic_messy.csv` | Dataset copy containing deliberate quality issues |
| `titanic_cleaned.csv` | Cleaned dataset ready for analysis |
| `data_quality_before_after.csv` | Before-and-after data quality metrics |
| `outlier_report.csv` | IQR boundaries and outlier counts |
| `dtype_comparison.csv` | Data types before and after cleaning |

## Expected Outcomes

After completing the project, the user will have:

- A documented data-cleaning workflow.
- A reproducible data quality report.
- A cleaned dataset with standardised values and corrected data types.
- A record of duplicate removal and missing-value handling decisions.
- An outlier analysis report.
- A before-and-after quality comparison.
- A CSV file suitable for further exploratory data analysis.

The exact results depend on the source dataset version and the cleaning operations performed. The notebook's generated reports should be used for actual counts rather than assuming predetermined values.

## Key Learnings

This project provides practical experience in:

- Data quality assessment.
- Missing-value treatment.
- Duplicate detection and removal.
- Categorical data standardisation.
- Data type conversion.
- Outlier detection using IQR.
- Data validation and reproducible workflows.
- Exporting clean data and documenting decisions.

## Conclusion

This project demonstrates how raw, inconsistent data can be transformed into a more reliable dataset through systematic inspection, cleaning, validation, and documentation. It emphasises the importance of choosing cleaning strategies based on the meaning of the data rather than applying arbitrary rules. The final dataset and supporting reports provide a foundation for future exploratory analysis and machine learning projects.

## Author
Natarajan Surya
**Project:** Task 3 — Data Cleaning  
**Technologies:** Python, Pandas, NumPy, Jupyter Notebook  
**Domain:** Data Analysis and Data Quality Management
