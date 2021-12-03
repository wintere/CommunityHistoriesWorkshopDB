# CommunityHistoriesWorkshopDB
A README and helper scripts for the access and generation of data from the Community Histories Workshop asylum records project.

## About the Database
If this is your first time accessing the database, [skim over the database overview](https://github.com/wintere/CommunityHistoriesWorkshopDB/blob/main/database_overview.md) to get a sense of what tables and views are available. Keep this information open in another tab, as you will need to return to it when querying the database through either OpenRefine/SQL or Tableau.

## Setup
The CHW database of Dix records is hosted by [OASIS](https://oasis.unc.edu/) at UNC. It can only be accessed from eduroam on campus or through the campus VPN. In order to install the UNC VPN client on your machine, follow the tutorial for your operating system (Mac, Windows, Ubuntu) [here](https://help.unc.edu/sp?id=kb_article_view&sysparm_article=KB0010155&sys_kb_id=719db1eddb3fa41070551ffa689619eb).

You will need to be enrolled in Duo and have your secondary authentication device (likely a cell phone) on hand in order to access the VPN. Once the client is installed, connect to the VPN by entering *vpn.unc.edu* into the VPN, then *connect*.

![image](https://user-images.githubusercontent.com/7553742/144531047-0ccffe0a-604d-4363-857c-cb6595661312.png)

You will be prompted to populate your credentials to enable the VPN connection.
- Group: Select *UNCCampus* from the dropdown list.
- Username: This will be your Onyen.
- Password: This will be your Onyen password.
- Second Password: This will be your Duo authentication method, you have the following options.
1. "phone" will initiate an automated phone call to your phone registered to Duo
2. "push" will create a push to the Duo app, just like the authentication method for HeelMail
3. "sms" will give you an activation code to use via text OR
4. enter the current six digit passcode generated within the Duo app 

Once you're connected you should see a checkmarked/locked connection status in your VPN client.

![image](https://user-images.githubusercontent.com/7553742/143873814-9257f1ae-2008-4831-b9bd-a94da0ec1f42.png)

Proceed to one of the two access methods below. You will need to make sure you're connected to the campus VPN each time you access the database, regardless of which access method you choose.


## Decide How You Would Like to Access The Database
1. If you would like to examine the database for purposes of data cleaning, browsing, or for performing SQL queries, we recommend using OpenRefine to access the database [using the following tutorial.](https://github.com/wintere/CommunityHistoriesWorkshopDB/blob/main/open_refine_access.md)
2. If you would like to use the database to create visualizations, we recommend using the Tableau connector to access the data through Tableau [using the following tutorial instead](https://github.com/wintere/CommunityHistoriesWorkshopDB/blob/main/tableau_access.md).

## Learning More About Relational Databases, PostgreSQL

If you're new to relational databases and would like to learn about relational databases in a classroom setting, consider enrolling in [INLS 523].

If you would like to learn about SQL in order to write simple queries, I would recommend walking through [this set of interactive exercises](https://pgexercises.com/questions/basic/).

If you're an experienced SQL user and would like to learn about the PostgreSQL dialect, try [the official documentation](https://www.postgresql.org/docs/14/sql.html). To learn about the distribution and its implementation, consider reading [this textbook excerpt](https://www.db-book.com/online-chapters-dir/32.pdf).
