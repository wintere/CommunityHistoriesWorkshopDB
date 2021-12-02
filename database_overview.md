## Dix Database Overview

What's in it?  
- Admissions Ledger  
- General Case Book  
  
Where is it?  
- Campus server (with access limited to campus network)  
  
What is it?  
- A PostgreSQL database  
  
Who can help me with it?
- Email our campus accounts (ndnihart, ewinter)  
  
### Overview of database for non-technical audiences  
  
Admissions Ledger and General Dase Book -> transcribed into spreadsheets -> transformed into the database  

A relational database differs from a spreadsheet in a variety of ways, but one of the most pertinent is the deduplication of values. The following describes this process using the Admissions Ledger as an example (and putting familiar excel terminology in parentheses):  
- All data from the admissions ledger starts out in the main table (spreadsheet) - Admission, and is stored in fields (columns) similar to a spreadsheet. 
- For every field (column) that has duplicate values (example: nativity):
  - a separate table (worksheet) is created (example: new table = nativity)
  - this table stores the unique/deduplicated list of values alongside a key (id, unique number) (example: 1: North Carolina, 2: South Carolina) 
  - the data in the column in the original table is replaced with the key value that corresponds to the value previously in the field. (example: all instances of North Carolina are replaced with 1)
  - In the back end of the database, there is a reference that points this key value to the new table that was created
- For multivalue fields, 


Exmplain Views

Explain Tables
