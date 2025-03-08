# Midterm Lab Task 2 - Data Cleaning and Preparation using Power Query
This portfolio contains the steps I followed for cleaning, transforming, and reshaping job posting data using **Power Query Editor** in Excel. 
### Data Cleaning and Transformation Steps

## Data Cleaning and Transformation Steps

### 1. **Data Import and Initial Cleaning**
- **Loading the Data**: The raw data is loaded from a CSV file.
- **Cleaning Salary Estimate**: We remove unwanted characters from the `Salary Estimate` column (text after the opening parenthesis) to clean the data.
- **Creating Min and Max Salary Columns**: Using the extracted salary values, two new columns (`Min Sal` and `Max Sal`) are created to represent the salary range for each job.

### 2. **Role Classification**
- **Grouping Job Titles**: A new column called `Role Type` is created to classify the job titles into five categories:
  - Data Scientist
  - Data Analyst
  - Data Engineer
  - Machine Learning Engineer
  - Other (for non-classifiable roles)

### 3. **Location Data Cleanup**
- **Standardizing Locations**: Custom formulas are used to standardize location names and abbreviations. For example, "New Jersey" is replaced with ", NJ", "California" with ", CA", and so on.
- **Splitting Location**: The location column is split into two parts: one for the location and another for the state abbreviation.

### 4. **Handling Negative Values**
- **Cleaning Negative Values**: We remove or filter out invalid negative values from columns like `Competitors`, `Revenue`, and `Industry`.

### 5. **Handling Company Size**
- **Splitting Company Size**: The `Size` column is split into two parts: `MinCompanySize` and `MaxCompanySize`.

### 6. **Final Cleanup**
- **Cleaning Company Names**: We remove the word "Rates" from company names.
- **Removing Unnecessary Columns**: Any non-useful columns (like description columns) are removed.

---

## Screenshots

- **Before Cleaning**: ![Before Cleaning](screenshots/before_cleaning.png)
- **After Cleaning**: ![After Cleaning](screenshots/after_cleaning.png)

