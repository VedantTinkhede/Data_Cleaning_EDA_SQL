 # Data Cleaning SQL Queries - Layoffs Dataset 

This README outlines the steps and rationale behind cleaning the layoffs dataset using SQL. The cleaning process improves data quality by removing duplicates, standardizing fields, handling missing values, and dropping unnecessary columns, while preserving the raw data in a staging table.

<br>

##  Process Overview 

 1. Data Preparation: 
    A staging table (layoffs_staging) is created to safeguard the original data, allowing transformations without risk to the raw dataset.

 2. Removing Duplicates: 
    We use row_number() to identify duplicate rows based on key columns like company, location, and date. Rows with row_num > 1 are removed to retain only unique entries.

 3. Standardizing Data:
    
    Standardization improves consistency by:
    
    Trimming whitespace from company names.
    
    Unifying variations of industry names (e.g., normalizing crypto variations to Crypto).
    
    Correcting inconsistencies in country fields.
    
    Converting date from text to DATE format for better date operations.

 4. Handling Null and Blank Values:
    Missing or blank values in industry are set to NULL. Gaps are filled by matching records on common identifiers like company to propagate existing values where possible.

 5. Removing Unnecessary Data:
    Rows with both total_laid_off and percentage_laid_off as NULL are deleted.
    The auxiliary row_num column used for duplicate detection is dropped to clean up the table structure.


<br>

## Final Step 

A final query verifies the cleaned dataset:

    SELECT * FROM layoffs_staging2;

<br>

 ## Summary 
 
This process ensures a clean, consistent, and reliable dataset for analysis. It removes redundancies, enforces data integrity, and structures data for improved usability.
