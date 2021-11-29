## First Steps ##

Make sure you have the username and password for the _dixdbreadonly_ account on hand. They have been emailed to you with this version of the tutorial, but they will be stored in the UNC Sharepoint directory for the CHW project in the future.

## Installing and Starting OpenRefine ##

First, [download OpenRefine](https://openrefine.org/download.html) to your computer by selecting the appropriate distribution for your operating system.

![image](https://user-images.githubusercontent.com/7553742/143791890-08cb2288-0327-4eb4-a484-70a454ddaa09.png)

Because OpenRefine is written in Java, you may need to install Java to your machine. 

- *Windows* <br>
If you do not already have Java/JRE8 installed on your computer, either install select the Windows Kit with Embedded Java distribution or download and [install Java](https://www.java.com/en/download/manual.jsp) before running the Windows Kit. Java does not come pre-installed on most Windows PCs.

- *Mac OS or Linux*<br>
You may already have Java installed. To verify this, open a terminal using the Terminal application (in Applications or Applications->Utilities) and type the following command: `java -version`. <br> If you get a response prefixed with `java version`, you have Java installed. If not, install [install Java](https://www.java.com/en/download/manual.jsp) before installing the Mac OS or Linux Kit.


## Accessing the Database ##
1. In the Create Project Tab, select *Database* from the *Get Data From* menu.
2. Populate each field as follows:
<img src="https://user-images.githubusercontent.com/7553742/143791548-9e9a67e9-5508-4e8d-bef5-a29c3298dc09.png " width="700">
- Name: This is your name for the connection settings. It can be anything you choose, as long as it's short and doesn't have spaces or special characters in it. I used *dix-db*.
- Type: Because the database is a [PostgreSQL](https://www.postgresql.org/about/) relational database, this needs to be set to PostgreSQL.
- Host: This is the web address or hostname of the database server. This was emailed to you and is stored on Sharepoint as well.
- Port: The DB is currently hosted on port 5432. 
- User: Currently *dixdbreadonly* is the read-only account recommended for analysis and exploration.
- Password: This was provided to you via email and is part of the credentials on Sharepoint.
- Database: The current production DB is *dix*.
- 
## Troubleshooting ##

