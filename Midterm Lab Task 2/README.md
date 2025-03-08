# Midterm Lab Task 2 - Data Cleaning and Preparation using Power Query
This portfolio contains the steps I followed for cleaning, transforming, and reshaping job posting data using Power Query Editor in Excel. 
### Data Cleaning and Transformation Steps

## Part 1: Data Cleaning and Transformation Steps

### 1. **Data Import and Initial Cleaning**
- Loading the Data: The raw data is loaded from a CSV file.
- Cleaning Salary Estimate: We remove unwanted characters from the Salary Estimate column (text after the opening parenthesis) to clean the data.
- Creating Min and Max Salary Columns: Using the extracted salary values, two new columns Min Sal and Max Sal are created to represent the salary range for each job.

### 2. **Role Classification**
- Grouping Job Titles: A new column called "Role Type" is created to classify the job titles into five categories:
  - Data Scientist
  - Data Analyst
  - Data Engineer
  - Machine Learning Engineer
  - Other (for non-classifiable roles)

### 3. **Location Data Cleanup**
- **Standardizing Locations**: Custom formulas are used to standardize location names and abbreviations. For example, "New Jersey" is replaced with ", NJ", "California" with ", CA", and so on.
- **Splitting Location**: The location column is split into two parts: one for the location and another for the state abbreviation.

### 4. **Handling Negative Values**
- **Cleaning Negative Values**: We remove or filter out invalid negative values from columns like Competitors, Revenue, and Industry.

### 5. **Handling Company Size**
- **Splitting Company Size**: The Size column is split into two parts: MinCompanySize and MaxCompanySize.

### 6. **Final Cleanup**
- **Cleaning Company Names**: We remove the word "Rates" from company names.
- **Removing Unnecessary Columns**: Any non-useful columns (like description columns) are removed.



## Screenshots

- **Before Cleaning**: ![1.Before Cleaning](/Midterm%20Lab%20Task%202/images/old.PNG)
- **After Cleaning**: ![2.After Cleaning](/Midterm%20Lab%20Task%202/images/uncleanpic1.PNG)
- ![2.1](/Midterm%20Lab%20Task%202/images/uncleanpic2.png)
- ![2.2](/Midterm%20Lab%20Task%202/images/uncleanpic3.png)

## Part 2: **Reshape and Group the Tables**
### 1. Duplicate the Raw Data for "Sal By Role Type"
- Duplicate the Unclean DS Jobs query.
- Rename the query to **Sal By Role Type dup**.

### 2. Select Columns and Transform Data for "Sal By Role Type"
- Select columns: **Role Type**, **Min Sal**, **Max Sal**.
- Convert **Min Sal** and **Max Sal** to **Currency**.
- Multiply **Min Sal** and **Max Sal** by 1000.
- Group by **Role Type** and calculate average **Min Sal** and **Max Sal**.

### 3. Create a Reference for "Sal By Role Size"
- Reference the raw data query.
- Rename it to **Sal By Role Size ref**.
- Select columns: **Size**, **Min Sal**, **Max Sal**.
- Convert **Min Sal** and **Max Sal** to **Currency** and multiply by 1000.
- Group by **Size** and calculate average salary.

### 4. Merge Queries with State Mapping
- Merge raw data with state mapping query.
- Rename merged column to **State Full Name**.
- Remove null and blank values from **State Abbreviations**.

### 5. Create a Reference for "Sal By State"
- Reference the raw data query.
- Rename it to **Sal By State ref**.
- Select columns: **State Full Name**, **Min Sal**, **Max Sal**.
- Convert **Min Sal** and **Max Sal** to **Currency** and multiply by 1000.
- Group by **State Full Name** and calculate average salary.

### 6. View Dependencies and References
- View dependencies to check query relationships.
- Duplicates are independent; references are dependent on the original data.

## Final Queries
- **Sal By Role Type dup**: Grouped salary data by role type.
- **Sal By Role Size ref**: Grouped salary data by company size.
- **Sal By State ref**: Grouped salary data by state.
- **Uncleaned DS Jobs**: Raw dataset used for transformations.

### Screenshots of Queries
- Insert screenshots for:
  - [**Sal By Role Type** query](/Midterm%20Lab%20Task%202/images/uncleanpic1.PNG)
  - 
  - ![**Sal By Role Size** query](/Midterm%20Lab%20Task%202/images/Sal%20by%20Size%20ref.PNG)
  - [**Sal By State** query](/Midterm%20Lab%20Task%202/images/uncleanpic1.PNG)
  
