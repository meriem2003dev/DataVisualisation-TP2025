# Practical Work: Data Cleaning, Preparation, and Variable Classification
 
**Objective:** To gain hands-on experience with foundational data cleaning techniques (duplicates, missing values, outliers) and to understand how to correctly classify variables for subsequent statistical analysis.

**Dataset URL:** `https://raw.githubusercontent.com/PacktPublishing/Hands-on-Exploratory-Data-Analysis-with-Python/refs/heads/master/Chapter%204/sales.csv`

---

## Part 1: Case Study - Cleaning and Preparing the Sales Dataset (Outlier Focus)

In this section, we will focus on calculating a key metric and identifying extreme transactions (outliers) that could skew subsequent analyses.

### Task 1.1: Data Acquisition and Initial Review

- **Load the Dataset:** Load the sales CSV file directly into a Pandas DataFrame named `df_sales`.
- **Initial Inspection:**
  - Use `df_sales.head()` to view the first few rows.
  - Use `df_sales.info()` to check data types and preliminary missing value counts.

### Task 1.2: Feature Engineering - Calculating Total Price

*Feature engineering is the process of creating new variables from existing ones to aid in modeling or analysis.*

- **Create TotalPrice:** Create a new column, `TotalPrice`, by multiplying the `Quantity` and `UnitPrice` columns.
  
  $$ \text{TotalPrice} = \text{Quantity} \times \text{UnitPrice} $$
  
- **Verification:** Display the first 5 rows, ensuring the new `TotalPrice` column has been calculated correctly.

### Task 1.3: Outlier Detection and Filtering

*Extreme values (outliers) in transactional data often represent data entry errors or highly unusual events that should be treated separately.*

- **Outlier Identification:** Identify how many transactions have a `TotalPrice` greater than a threshold of 3,000,000.
  - *Hint:* Use boolean indexing and the `shape` attribute.
- **Filtering:** Create a new DataFrame, `df_cleaned_outliers`, that excludes all transactions where `TotalPrice` exceeds 3,000,000.
- **Summary:** Calculate the difference in the number of rows between the original DataFrame (`df_sales`) and the new filtered DataFrame (`df_cleaned_outliers`).

---

## Part 2: Lab - Pandas Wrangling and Variable Classification

Now we shift focus to broader data wrangling techniques (deduplication, missing values, binning) and the crucial step of variable classification. Use the `df_sales` DataFrame for this part.

### A. Pandas Wrangling (Data Quality and Transformation)

#### Task A.1: Data Deduplication

*Data quality requires ensuring no records are duplicated, which can inflate counts and distort summary statistics.*

- **Identify Duplicates:** Find and display the total count of duplicated rows across all columns.
  - *Hint:* Use the `.duplicated()` method.
- **Removal:** Remove the identified duplicates from the DataFrame. When removing duplicates, ensure you retain the last observed record using the `keep='last'` parameter. Save the result to a new DataFrame named `df_no_duplicates`.
- **Verification:** Confirm the new DataFrame has the expected number of rows after removal.

#### Task A.2: Handling Missing Data

*In real-world data, missing values (NaN) are common.*

- **Missing Value Check:** Calculate the total number of missing values for every column in `df_no_duplicates`.
- **Deletion Technique (dropna):** Create a temporary DataFrame where all rows containing any missing value are deleted. Report the count of rows lost.
- **Imputation Technique (fillna):** For the column named `CustomerID` (which likely has missing values), fill all NaN values with the string `'ANON'`. 
  - *Note:* This is a simple imputation method suitable for categorical IDs.

#### Task A.3: Discretization and Binning

*Discretization (or binning) is the process of transforming a continuous numerical variable into a categorical (ordinal) variable.*

- **Apply Binning:** Use the `pd.cut()` function on the `Quantity` column of `df_no_duplicates` to create three equal-interval bins.
- **Name the labels** for the bins: `['Low Quantity', 'Medium Quantity', 'High Quantity']`.
- **Create New Column:** Save this new ordinal variable as `Quantity_Bin` in the DataFrame.
- **Analyze:** Use `.value_counts()` on `Quantity_Bin` to see the distribution of transactions across the three new categories.

### B. Variable Classification

*Understanding a variable's type and role is essential for selecting the correct statistical analysis or visualization.*

#### Task B.1: Classification by Statistical Type

Complete the table below to classify the following variables based on their statistical type.

| Variable Name | Statistical Type (Quantitative/Categorical) | Sub-Type (Discrete/Continuous or Nominal/Ordinal) |
|---------------|---------------------------------------------|---------------------------------------------------|
| UnitPrice     |                                             |                                                   |
| Quantity      |                                             |                                                   |
| Description   |                                             |                                                   |
| Country       |                                             |                                                   |
| TotalPrice    |                                             |                                                   |
| Quantity_Bin  |                                             |                                                   |

#### Task B.2: Classification by Role

*Consider a hypothetical regression analysis where the goal is to predict the `TotalPrice` of a transaction.*

- **Outcome Variable:** Identify the variable that would serve as the Outcome Variable (Dependent Variable).
- **Explanatory Variables:** List three variables from the dataset (including any you created) that you would initially propose as Explanatory Variables (Independent Variables). Justify why you chose each.

#### Task B.3: Creating Indicator (Dummy) Variables

*In regression models, categorical explanatory variables must often be converted into indicator (or dummy) variables that only take the value 0 or 1.*

- **Transformation:** Select the `Country` column. Use the Pandas function `pd.get_dummies()` to create a new DataFrame consisting solely of indicator variables for each unique country.
- **Display:** Display the head of this new dummy variable DataFrame. Explain what the value '1' signifies in the resulting columns.

### C. Conclusion: Reliable Variables

In a brief paragraph (3-4 sentences), explain the relationship between the data cleaning steps you performed (deduplication and handling missing values) and the concept of **Reliability** in a variable. Why are these steps necessary to ensure a variable is considered "reliable" for downstream analysis?
