# Project3

Group members:
Daniel Stephens, 
Maggie Puch, 
Heather Mills,  
Kevin Shaw

Project 3 Proposal - https://docs.google.com/document/d/1WbRGsEF2DYWcwjrOgg925kgXhEV1TOvrne444RviATo/edit 

Project 3 Class Presentation - https://docs.google.com/presentation/d/1X2oOnJIE_tC8D5DSQTcI9oSDcC9UzQYEogDXvHwDrX8/edit?usp=sharing

### Project Overview:
For project 3, our team used a CSV file from Kaggle with information regarding childhood allergies. The CSV file is extensive with over 50 columns and 300,000+ rows of data. Our primary steps for data updates are below: 
- Create an ERD containing all tables, data constraints, and primary and foreign keys
- Requirements for data formatting is defined
- Malformed data is identified and a plan is established to handle this data
- Data import: Only columns designed are imported from the CSV to our polars dataframe
- Rows that contain a negative value in the 'age_start_years' column are dropped
- Rows that contain 'null' on all conditionals are dropped
- Dataframe is created using Polars library. Subject_id and birth_year columns are integer data types. Gender, race_id, ethnicity_id are string data types
- Age_start_years and age_end_years are decimal data types. Update to 3 decimal points
- Values in gender columns are changed from Male and Female to M and F
- Values in the race_id and ethnicity columns are changed to reflect the two character code, ex. R0, R1, etc...
- 6 tables with keys and constraints matching ERD are created

### How to interact with our project:
Our project data was processed with Polars. Our SQL tables have been created in SQLite. To interact with our SQL tables, you can use Python with the SQLite3 Module.

### Ethical Considerations:
In handling the subject data table, ethical considerations take center stage to ensure a responsible and unbiased approach. To maintain privacy and eliminate the possibility of identifying individual subjects, no patient names are retained within the DataFrame. Instead, codes for race and ethnicity are utilized, referring to a separate reference table. This deliberate separation helps in anonymizing the data, allowing analysts to draw valuable insights without perpetuating bias. The subject's identity remains confidential, safeguarded by a system where understanding race and ethnicity is crucial but is treated with the utmost ethical standards. In employing this approach, the DataFrame becomes a powerful tool for analysis while upholding the principles of privacy and fairness.

### References for data source:  
Title: Childhood Allergies: Prevalence, Demographic data
URL: https://www.kaggle.com/datasets/thedevastator/childhood-allergies-prevalence-diagnosis-and-tre
Accessed on: January 8, 2024

### References for code support: 
- Polars User Guide: https://docs.pola.rs/user-guide/basics/reading-writing/#csv
- Filter function help: https://stackoverflow.com/questions/57627115/pyspark-filter-function-error-with-isnotnull-and-other-2-other-conditions
- Import a CSV file into a SQLite database: https://www.geeksforgeeks.org/how-to-import-a-csv-file-into-a-sqlite-database-table-using-python/
- OpenAI. (2022). ChatGPT Code https://chat.openai.com/ referenced for following code: filtered_df = filtered_df.with_columns([
    pl.col('GENDER_FACTOR').apply(lambda value: 'F' if value == "S1 - Female" else ('M' if value == "S0 - Male" else "O")).alias('GENDER')
])
