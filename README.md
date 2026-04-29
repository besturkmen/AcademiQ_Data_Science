# AcademiQ_Data_Science
PROJECT OVERVIEW, DATASET AND PIPELINE ARCHITECTURE

This project involves the initial data loading, cleaning, and preliminary exploration of a dataset titled 'github_top_repositories.csv'. The main objective has been to prepare the data for further analysis by:

Loading the Dataset: The github_top_repositories.csv file was loaded into a pandas DataFrame named dt.

Initial Data Inspection: Basic checks were performed to understand the dataset's structure, including viewing the first and last rows, checking its dimensions (number of rows and columns), and listing all column names.

Data Type and Missing Value Analysis: The dt.info() method was used to inspect data types and non-null counts for each column. A detailed analysis of missing values was conducted, showing both the count and the ratio of missing entries per column.

Column Standardization: Column names were cleaned and standardized by converting them to lowercase, replacing spaces and hyphens with underscores, and removing leading/trailing whitespace.

Data Cleaning (String Columns): All object (string) type columns were processed to remove any leading or trailing whitespace.
Handling Critical Missing Values: Rows with missing values in 'repository_name' or 'stars_count' columns were identified and removed, as these are considered critical for the dataset's integrity.

Numeric Type Conversion: Several key numeric columns ('stars_count', 'forks_count', 'watchers_count', 'open_issues_count') were explicitly converted to numeric data types, with a mechanism to handle any non-numeric entries by coercing them to NaN (Not a Number).
These steps ensure that the dataset is clean, consistently formatted, and ready for more in-depth exploratory data analysis or machine learning tasks.

