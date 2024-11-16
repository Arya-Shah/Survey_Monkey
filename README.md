# Description:

In this project, I undertook a comprehensive data analysis task that mirrors the complexities and challenges faced by data analysts in real-world scenarios. The primary objective was to transform a multifaceted, wide-format dataset exported from SurveyMonkey into a normalized, long-format structure using Python and the Pandas library. This transformation was essential to enable in-depth data analysis and facilitate sophisticated visualizations in tools like Tableau and Power BI.

# Detailed Overview:

## Dataset Characteristics:

Source: SurveyMonkey survey results provided by a client for data visualization purposes.
Structure:
Wide Format: The dataset initially consisted of over 100 columns, including multiple hierarchical levels of survey questions and sub-questions.
Hierarchical Headers: Two levels of headers were present—primary questions and sub-questions—necessitating complex data manipulation techniques.
Content:
Respondent Identifiers: Unique respondent_id for each participant, crucial for maintaining data integrity during transformations.
Demographic Information: Variables such as division_primary, division_secondary, position_level, gender, tenure, and employment_type provided dimensions for segmentation analysis.
Survey Responses: A variety of questions with multiple-choice responses, Likert scales, and open-ended questions, some with multiple sub-parts.

## Data Challenges Addressed:
Complex Headers and Multi-level Indexing: The presence of multi-level column headers required flattening and concatenation to create unique identifiers for each question and sub-question.
Wide to Long Format Transformation: The initial wide format was unsuitable for analysis and visualization, necessitating an unpivoting process to convert it into a long, tidy dataset.
Handling Missing Data: Addressed null values (NaN) resulting from incomplete responses to ensure accurate aggregations and analyses.
Data Privacy and Compliance: Ensured sensitive information was properly handled, adhering to data protection regulations and best practices.

## Key Data Analysis Techniques and Steps:
Data Ingestion and Loading:

Utilized pandas.read_excel() with precise parameters to read specific sheets from the Excel workbook.
Managed file paths dynamically using the os library to ensure portability and reproducibility of the code.
Data Cleaning and Preprocessing:

## Column Renaming and Standardization:
Normalized column names by converting them to lowercase and replacing spaces with underscores for consistency.
## Hierarchical Header Management:
Concatenated primary and sub-question headers using string manipulation techniques to create unique question_plus_subquestion identifiers.
Filled missing header values by propagating the previous non-null value downwards to maintain alignment.
## Dropping Irrelevant Columns:
Removed non-essential columns such as start_date, end_date, email_address, and other personally identifiable information.
## Data Type Conversion:
Ensured correct data types for each column, converting categorical variables to the category dtype for memory efficiency.
## Data Reshaping and Transformation:
## Melting (Unpivoting) the Dataset:
Applied the pandas.melt() function to transform the dataset from wide to long format.
Specified id_vars to retain demographic and identifier columns, and value_vars for the survey response columns.
Renamed the resulting columns to question and answer for clarity.
## Creating Composite Keys:
Generated composite keys for merging by combining columns where necessary, ensuring referential integrity.
## Data Integration and Enrichment:
## Joining Supplementary Data:
Merged the main DataFrame with additional DataFrames containing detailed question texts and metadata using pandas.merge().
Performed left joins on question_plus_subquestion to enrich the dataset without losing any response data.
## Avoiding Duplicates:
Checked for and resolved any duplication issues post-merge by verifying row counts and using drop_duplicates() when necessary.
## Aggregation and Statistical Analysis:
## Calculating Response Frequencies:
Grouped data using groupby() on question and answer to calculate the count of each response option.
Computed the total number of respondents per question to facilitate percentage calculations.
## Handling Missing Responses:
Filtered out null responses to ensure accurate aggregation.
Used fillna() to handle missing values where appropriate.
Data Export and Preparation for Visualization:

## Final Dataset Preparation:
Renamed columns to more user-friendly names, aligning with best practices for data presentation.
Ensured the dataset was free of indices and extraneous information by setting index=False during export.
## Exporting to Excel:
Utilized df.to_excel() to export the cleaned and transformed DataFrame to an Excel file compatible with visualization tools.

