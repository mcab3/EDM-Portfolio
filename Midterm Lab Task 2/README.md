# Midterm Lab Task 2 - Data Cleaning and Preparation using Power Query
This portfolio contains the steps I followed for cleaning, transforming, and reshaping job posting data using **Power Query Editor** in Excel. 
## Key Tasks

1. **Data Cleaning and Transformation**
    - Removed unnecessary characters and outliers.
    - Extracted salary estimates and split columns.
    - Cleaned up the location and company size columns.

2. **Reshaping the Data**
    - Grouped salary data by role type, company size, and state.
    - Calculated average minimum and maximum salaries for each grouping.

## Queries and Their Steps

### 1. **Data Cleaning**

#### a. Salary Estimate Extraction
- **Action**: Removed characters after the parentheses in the `Salary Estimate` column to retain only the numeric salary range.
- **Steps**:
    1. Used **Transform** → **Extract** → **Text Before Delimiter** to remove any characters after the `(` symbol.

#### b. Creating Min and Max Salary Columns
- **Action**: Created two new columns: `Min Sal` and `Max Sal`, extracting the minimum and maximum values from the `Salary Estimate`.
- **Steps**:
    1. Used **Add Column** → **Column from Examples** to create `Min Sal` and `Max Sal` columns.
    2. Used **Transform** → **Multiply** to scale salary values by 1000 for accuracy.

#### c. Role Type Classification
- **Action**: Grouped `Job Title` values into five categories: "Data Scientist", "Data Analyst", "Data Engineer", "Machine Learning Engineer", and "Other".
- **Steps**:
    1. Used **Add Column** → **Custom Column** with conditional statements to classify job titles into specific roles based on keywords.

#### d. Location Column Correction and Split
- **Action**: Standardized location names (e.g., "California" to "CA") and split the `Location` column by a comma.
- **Steps**:
    1. Created a **Custom Column** to correct and standardize location abbreviations.
    2. Split the `Location` column by delimiter (`,`).
    3. Filtered and replaced values for states with incorrect entries (e.g., "Anne Rundell" to "MA").

#### e. Company Size Column Split
- **Action**: Split the `Company Size` column into `MinCompanySize` and `MaxCompanySize`.
- **Steps**:
    1. Used the **Split Column** method by delimiter to extract the minimum and maximum values.

#### f. Outlier Handling
- **Action**: Removed outliers for the following columns:
    - Competitors: Filtered out `-1` values.
    - Revenues: Filtered out `0` values.
    - Industry: Filtered out `-1` values.

#### g. Cleaning Company Name
- **Action**: Cleaned company names by removing any `Rates` text that appeared after the company name.

---

### 2. **Reshaping the Data**

#### a. **Sal By Role Type Query (Duplicate)**
- **Action**: Grouped salary estimates by job role type and calculated average minimum and maximum salaries.
- **Steps**:
    1. Duplicated the raw data.
    2. Selected relevant columns: `Role Type`, `Min Sal`, `Max Sal`.
    3. Changed data type of `Min Sal` and `Max Sal` to `Currency`.
    4. Multiplied the salary values by 1000.
    5. Grouped the rows by `Role Type` and calculated average salaries.

**M Code for Sal By Role Type**:
```m
let
    Source = #"Unclean DS Jobs",
    SelectColumns = Table.SelectColumns(Source,{"Role Type", "Min Sal", "Max Sal"}),
    ChangedType = Table.TransformColumnTypes(SelectColumns,{{"Min Sal", Currency.Type}, {"Max Sal", Currency.Type}}),
    MultipliedColumns = Table.TransformColumns(ChangedType, {{"Min Sal", each _ * 1000, type currency}, {"Max Sal", each _ * 1000, type currency}}),
    GroupedRows = Table.Group(MultipliedColumns, {"Role Type"}, {{"Min Sal Average", each List.Average([Min Sal]), type currency}, {"Max Sal Average", each List.Average([Max Sal]), type currency}})
in
    GroupedRows
