## Dix Database Overview

TOC  
- [Basics](#basics)
- [Overview of database for non-technical audiences](#overview-of-database-for-non-technical-audiences)
- [Database Views](#database-views)
- [Database Tables](#database-tables)
  
  
### Basics    
  
What's in it?  
- Admissions Ledger  
- General Case Book  
  
Where is it?  
- On a campus server (with access limited to campus network)  
- (it's a PostgreSQL database)
  
How do I access it? 
- Use a tool such as OpenRefine, Metabase, or Tableau to connect to the database
- Connection/Access info is in SharePoint
  
Who can help me with it?
- Email our campus accounts (ndnihart, ewinter)  
  
  
### Overview of database for non-technical audiences  
  
Admissions Ledger and General Dase Book -> transcribed into spreadsheets -> transformed into the database  
  
A few basics that are important to understand:

- Excel is a type of non-relational database
- PostgreSQL is a type of relational database.

- Terminology parallels:
  - Spreadsheet: Database
  - Worksheet: Table
  - Column: Field
  - Row: Row
  
- A relational database largely does away with repetitive values using extra tables and relationships
  - **One-To-Many**: for a column (field) that has repetitive values
  - **Many-To-Many**: for a column (field) that has multiple values (in our case, also repetitive)

**Examples**
One To Many (Example: Nativity, containing the state in which the patient was born)
- the nativity column is deduplicated, and the unique values are stored in a new table called 'nativity'
  - the nativity table has a column for 'id' and 'nativity'
  - This might look like 1, North Carolina  2, South Carolina
- in the admission table, the 'nativity' column is replaced with a 'nativity_id' column that has an ID instead
  - Every instance of 'North Carolina' would be represented by the ID '1'
Why is this useful? 
- If we decided to change 'North Carolina' to 'NC', we would change a single cell in the 'nativity' table instead of thousands of cells in the 'admission' table
- When we enter new data, instead of writing 'North Carolina' every time, we would select it from a list - this reduces typos

Many To Many (Example: Occupation, containing the occupation of the patient)
- as above, the occupation column is deduplicated, and the unique values are stored in a new table called 'occupation'
  - the occcupation table has a column for 'id' and 'occupation'
  - This might look like 1, Farmer  2, Preacher
- you can only have one value per cell in a database, so we can't store multiple key values in a column in the 'admission' table
- therefore, instead of an 'occupation_id' column in the 'admission' table, there is a 'join' table
  - this table has two columns: 'admission_id' (to reference the unique key for each admission entry) and 'occupation_id' (to reference the unique key for each value in the new 'occupation' table)
  - for example, it patient with id 3546 was both a farmer and a preacher, the join table would have two rows: 3546, 1   3546, 2
Why is this useful?
- we can work with multivalue fields now (so data analysis and viz is much more accurate)!

**Takeaways**
- There is a table for every column that had repetitive values
- Multivalue columns are complex, and it requires extra work to associate these fields with the main table data



### Database Views

*A View is what we use to get a combined view of data across multiple tables (i.e. rejoining One To Many columns such as Nativity to a main column such as Admission, so that we see 'North Carolina' instead of '1')*
*note - views don't include multivalue fields, those have to be joined separately

The database has views that provide data from three contexts:
- The Admissions Ledger
- The General Case Book
- All Data (combined data from admissions ledger and general case book)
  
For each of the contexts, there are three sets of data provided:
- All data (everything except multivalue fields)
  ```
  admission_main; general_case_book_main; all_data_main
  ```
- All data minus pii (everything except multivalue fields and fields that include names)
  ```
  admission_main_less_pii; general_case_book_main_less_pii; all_data_main_less_pii
  ```
- Simple View (only the fields included in the ledger, without transcription metadata such as transcription confidence or additional patient data located)
  ```
  admission_main_simple; general_case_book_main_simple; all_data_main_simple
  ```

Think about what you're trying to look at - most likely, the Simple View will best one to view.

### Database Tables

#### Main Tables

**admission** - contains admission ledger data  
**general_case_book** - contains general case book data  
**patient** - contains opatient  

#### Many To Many (for multivalue fields) Tables

The following are used by both the admission and general_case_book database tables  
**occupation**  
**supposed_cause**  
**form** note that this corresponds to form in admission, but diagnosis in general_case_book  
  
The following are used by the admission table
**intake_condition**  
**final_condition**  
  
The following are used by the general_case_book table
**bowels_and_digestion**  
**sources_of_information**   
**use_of_opium_liquors_tobacco**    
  
  
#### One To Many (for repetitive fields) Tables  
  
The following are used by both the admission and general_case_book database tables  
**transcriptionist**  
**civil_condition**  
**sex**  
  
The following are used by both tables repeatedly  
**confidence** (for transcription confidence columns)  
**YNUNK** (for yes/no/some/unknown fields)  
  
The following are used by the admission table  
**race**  
**residence*  
**nativity**  
**dementia_praecox_classification**  
  
The following are used by the general_case_book table:  
**religion**  
**intellectual_capacity_in_health**  
**habits**  
**temperament**  
**muscular_development**  
**features**  
**general_physical_condition_on_admission**  
**appetite**  
**education, education_years**    
**duration_range**  
**state**  
**city**  
**relation**  




