## Sample Queries ##

A SQL query can be broken down into the following parts: 

**SELECT**: required: followed by a list of fields (columns) available in the table in the FROM clause, to select all fields use * <br>
**FROM** required: followed by one (or more, if you're more knowledgable about SQL) tables or views <br>
**WHERE** optional: followed by a conditional statement about values within fields that must hold true for the rows returned <br>
**LIMIT** optional: followed by the maximium number of rows you want returned <br>
; required: indicates the end of the simple query<br>

### Finding Patients Admitted by Date ###

For example, here is a query to survey the patients admitted during the Civil War.
```
SELECT full_name_transcribed, admission_date_norm, sex, age_norm, residence, supposed_cause_of_attack_transcribed, form_transcribed
FROM all_data_main 
WHERE admission_date_norm between '1861-03-12' and '1865-03-09';
```

Which results in the following rows...
![image](https://user-images.githubusercontent.com/7553742/143795405-a3f28e60-a630-47f6-bad9-c081774de778.png)

### Finding Patients By Name ###

Let's say while researching a specific patient, you want to see if other patients with the same last name -- potential family members -- were admitted to the asylum. You also need to know where the original ledger image for any candidates is in order to inspect the original record. However, because the ledger has plenty of instances of mispellings and human error, looking for precisely that name spelling may not be as helpful.

This is where the [LIKE](https://www.postgresql.org/docs/14/functions-matching.html#FUNCTIONS-LIKE) operator can help. The name *Bodenhamer* is sometimes spelled *Bodenhammer*. To accomodate both possibilites, I want to formulate a wildcard expression that captures both spellings.

*Boden%* will match any names that *begin with* Boden, like Bodenhamer, Bodenhammer, and Bodensm, but it won't match Bodden. <br>
*%oden%* will match any names that contain oden, like Woden, Bodenhamer, but it won't match Oden because the O in Oden is capitalized. 

Because it is unlikely that the transcriber would get the first letter incorrect, this query selects for patients with last names beginning with *Boden*. It also selects for the *located_in* field, which is crucial for matching database records to original ledger photographs.

```
SELECT admission_id, located_in, admission_date_norm, first_name, last_name, residence, nativity
 FROM all_data_main 
WHERE last_name LIKE 'Boden%';

```
Entering this query into OpenRefine results in the following...
![image](https://user-images.githubusercontent.com/7553742/144625521-fee74afd-a5e1-4c9b-913e-c065913772c1.png)

If you don't get the results you want, *Start Over* and adjust the WHERE clause.

To look up a patient's original ledger photograph, search [SharePoint](https://adminliveunc.sharepoint.com/:f:/r/sites/CommunityHistoriesWorkshop/Shared%20Documents/DixLedger?csf=1&web=1&e=3sJ4LY) for the record number in the *located_in* field. 
