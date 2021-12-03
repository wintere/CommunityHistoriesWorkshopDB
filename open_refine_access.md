## First Steps ##

Make sure you have the username and password for the _dixdbreadonly_ account on hand. They have been emailed to you with this version of the tutorial, but they will be stored in the UNC Sharepoint directory for the CHW project in the future.

There are some limitations of accessing the database views like "all_data_main" or "all_data_main_simple" through OpenRefine. Multivalue fields like "Form of Insanity" are not compatible with the tool. 

## Installing and Starting OpenRefine ##

First, [download OpenRefine](https://openrefine.org/download.html) to your computer by selecting the appropriate distribution for your operating system.

![image](https://user-images.githubusercontent.com/7553742/143791890-08cb2288-0327-4eb4-a484-70a454ddaa09.png)

Because OpenRefine is written in Java, you may need to install Java to your machine. 

- *Windows* <br>
If you do not already have Java/JRE8 installed on your computer, either install select the Windows Kit with Embedded Java distribution or download and [install Java](https://www.java.com/en/download/manual.jsp) before running the Windows Kit. Java does not come pre-installed on most Windows PCs. Now, follow the instructions on the distribution page. OpenRefine should open in a browser window once you've run *openrefine.exe*.

- *Mac OS or Linux*<br>
You may already have Java installed. To verify this, open a terminal using the Terminal application (in Applications or Applications->Utilities) and type the following command: `java -version`. <br> If you get a response prefixed with `java version`, you have Java installed. If not, install [install Java](https://www.java.com/en/download/manual.jsp) before installing the Mac OS or Linux Kit. Now, follow the instructions on the distribution page,


## Accessing the Database ##
In the Create Project Tab, select *Database* from the *Get Data From* menu.
<img src="https://user-images.githubusercontent.com/7553742/143791548-9e9a67e9-5508-4e8d-bef5-a29c3298dc09.png " width="700"> <br>
Populate each field from the [credentials stored on SharePoint](https://adminliveunc.sharepoint.com/:t:/r/sites/CommunityHistoriesWorkshop/Shared%20Documents/Database/dixdbreadonly_credentials.txt?csf=1&web=1&e=6ZcpEU) as follows:
- Name: This is your name for the connection settings. It can be anything you choose, as long as it's short and doesn't have spaces or special characters in it. I used *dix-db*.
- Type: Because the database is a [PostgreSQL](https://www.postgresql.org/about/) relational database, this needs to be set to PostgreSQL.
- Host: This is the web address or hostname of the database server. This was emailed to you and is stored on Sharepoint as well.
- Port: The DB is currently hosted on port 5432. 
- User: Currently *dixdbreadonly* is the read-only account recommended for analysis and exploration.
- Password: This was provided to you via email and is part of the credentials on Sharepoint.
- Database: The current production DB is *dix*.
 
 Once you have entered this information, select *Test Connection*. If the connection test is successful, *Connect*.
 
## Querying the Database ##
![image](https://user-images.githubusercontent.com/7553742/143794223-dbc7e82f-c997-4a0d-821b-20e0e98ec132.png)

Once you've successfully connected, you will be prompted to write a SQL query representing the table(s) and rows you would like to view. Before selecting a table to access, [read over the database documentation to get a sense of what data is available where](https://github.com/wintere/CommunityHistoriesWorkshopDB/blob/main/database_overview.md).

If you're new to SQL, I would start with a general query that selects all possible fields from one of the following simplified views with join operations already applied:

- admission_main: the entire transcribed contents of the admissions ledger CSV
- admission_main_simple: the contents of the admissions ledger CSV with columns dedicated to tracking the transcription process, like the name of the person who transcribed each row removed. Recommended over *admission_main* for most uses.
- general_case_book_main: the entire transcribed contents of the general casebook CSV
- general_case_book_main_simple: the contents of the general casebook CSV with columns dedicated to tracking the transcription process, like the name of the person who transcribed each row removed. Recommended over *admission_main* for most uses.
- all_data_main: everything, the admissions ledger joined with the general casebook. **WARNING: This is quite large and will load slowly**
- all_data_main_simple: *all_data_main* with transcription related fields removed.

For example, a query that selects all rows and columns from the simplified admissions ledger would look as follows. With this query type, you can arbitrarily plug in a table name or view with a *;* to examine all the data in that table. 
```
SELECT* FROM admission_simple;
```
Or, for a query to survey the patients admitted during the Civil War...
```
SELECT full_name_transcribed, admission_date_norm, sex, age_norm, residence, supposed_cause_of_attack_transcribed, form_transcribed
FROM all_data_main 
WHERE admission_date_norm between '1861-03-12' and '1865-03-09';
```

**SELECT**: required: followed by a list of fields (columns) available in the table in the FROM clause, to select all fields use * <br>
**FROM** required: followed by one (or more, if you're more knowledgable about SQL) tables or views <br>
**WHERE** optional: followed by a conditional statement about values within fields that must hold true for the rows returned <br>
**LIMIT** optional: followed by the maximium number of rows you want returned <br>
; required: indicates the end of the simple query<br>

To adjust your query or query something else, select the *Start Over* button at the top left corner of the results table. If you're not sure which fields are in which table I would recommend an initial query the below in order to get a sense of the precise field names, then write *Start Over* and write more specific query.

```
SELECT *
FROM admission
LIMIT 1;
```

![image](https://user-images.githubusercontent.com/7553742/143795405-a3f28e60-a630-47f6-bad9-c081774de778.png)


Once you are satisfied with your query preview, select the *Create Project* button at the top right. You should now be able to sort, scroll, and explore the resulting data. 

**NOTE: Any changes you make to the data here are local and *will not* change the contents of the data as stored in the database. Please reach out to the database admins if you would like to make corrections to transcribed fields.**

## Troubleshooting ##
1. Is your UNC VPN connected? If not, connect it.
2. Is Java installed? If not, install it.
