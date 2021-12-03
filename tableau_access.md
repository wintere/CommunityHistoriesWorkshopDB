## Install Tableau ##

To install Tableau on your personal machine, you will need to complete the Tableau for Students application, specify UNC as your academic institution, and have the email with the activation code sent to your UNC email address.

![image](https://user-images.githubusercontent.com/7553742/143797622-9d870ff0-3a01-4b74-8ea1-c4095b65cbfe.png)

Once your identity is verified, you should receive an activation with links to download Tableau and a product code.

The Tableau developers have helpfully [provided very thorough installation instructions](https://help.tableau.com/current/desktopdeploy/en-us/desktop_deploy_download_and_install.htm#tableau-desktop). Skip to the Tableau Desktop section when the installer downloaded and have the product code on hand.

## Install PostgreSQL Drivers ##

Because the CHW Database is a PostgreSQL database, you will need to install a driver so that Tableau can connect to the database. Select PostgreSQL, your operating system, and 64-bit [from the Tableau driver menu]( https://www.tableau.com/support/drivers) on their official site.

![image](https://user-images.githubusercontent.com/7553742/143797858-76324a41-04cb-4dfb-8ef5-13aa66893706.png)

Follow the driver installation instructions, then proceed.

## Select a Connection File ##

In order to factor the extremely complex and sparse data in the admissions ledger and especially the general casebook into many-to-many and many-to-one relationships that express the loosely structed source data, the data has been broken into several tables. The relationships between tables have been carefully organized in Tableau and saved into a file by Nate.

We recommend you access the data in Tableau using one of the *.twb* connection files in this repository. Download your connection file of choice from GitHub by clicking and saving the links and proceed.

<a href="https://raw.githubusercontent.com/wintere/CommunityHistoriesWorkshopDB/main/DixDatabaseOASISConnCombinedDatasetsSimpleData.twb" download />DixDatabaseOASISConnCombinedDatasetsSimpleData.twb</a>
This sample workbook contains a simplified view of the data in the database, with columns related to the transcription process removed. **RECOMMENDED**

<a href="https://raw.githubusercontent.com/wintere/CommunityHistoriesWorkshopDB/main/DixDatabaseOASISConnCombinedDatasetsSimpleData.twb" download />DixDatabaseOASISConnCombinedDatasetsFullData.twb</a>
This sample workbook contains all view with all fields in the database.

After clicking a *.twb* file, Tableau should open and prompt you for a connection password.
Supply the username and password provided in your email or stored in the CHW Sharepoint drive.

![image](https://user-images.githubusercontent.com/7553742/143803991-ae519350-02a3-4a47-ad46-6e77d3927d2e.png)

The query will could take up to a minute to execute given the size of the data.

When it finishes, Tableau should open to a workbook with a sample visualization. Have fun!

Keep in mind that this dataset is fundamentally sparse, sometimes illegible, and in places incomplete. Just because a visualization looks nice -- something Tableau is good at -- doesn't mean the visualization correlated with the quantitative truth of the database, much less the historical truth we have pieces of at best.

## Learning About Relational Databases and Tableau ##

If you would like to learn more about visualization, how to apply visualizations, and to learn about Tableau in a classroom setting, consider enrolling [INLS 541: Information Visualization](https://sils.unc.edu/courses#541) or a similar data visualization course.

If you have background knowledge of databases but are new to Tableau and want to teach yourself, Tableau has [a guide for exploring the newly connected data](https://help.tableau.com/current/guides/get-started-tutorial/en-us/get-started-tutorial-drag.htm).

## Troubleshooting ##

Email my UNC account (ewinter) so I can help fix the problem and add it to this tutorial.
