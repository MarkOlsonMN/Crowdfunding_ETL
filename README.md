# README - Crowdfunding_ETL  
  
## Project 2  
Class:      U of M Data Analytics and Visualization Boot Camp , Spring 2024  
Students:   Mark Olson, Jim Pieper  
Professor:  Thomas Bogue  ,  Assisted by Jordan Tompkins  
Date:       06/24/2024  
  
## Location of this Repro (Public)  
URL:        https://github.com/MarkOlsonMN/Crowdfunding_ETL  
  
## Code Source/Location within this Repo  
ReadMe : &nbsp;Crowdfunding_ETL/README.md  
  
ERD Diagram and pgAdmin Screenshots (screenshot folder) :&nbsp;&nbsp;Crowdfunding_ETL/PostgreSQL_pgAdmin_Screenshots/  

Project Files:  
&nbsp;&nbsp;&nbsp;&nbsp;Jupyter Notebook (Python code) :&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/ETL_Mini_Project_MOlson_JPpieper.ipynb  
&nbsp;&nbsp;&nbsp;&nbsp;Database Schema (SQL script) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/crowdfunding_db_schema.sql  
&nbsp;&nbsp;&nbsp;&nbsp;Generated Analysis Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/campaign.csv  
&nbsp;&nbsp;&nbsp;&nbsp;Generated Analysis Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/category.csv  
&nbsp;&nbsp;&nbsp;&nbsp;Generated Analysis Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/contacts.csv  
&nbsp;&nbsp;&nbsp;&nbsp;Generated Analysis Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/subcategory.csv  
&nbsp;&nbsp;&nbsp;&nbsp;Starting Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/contacts.xlsx  
&nbsp;&nbsp;&nbsp;&nbsp;Starting Data (data) :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Crowdfunding_ETL/Resources/crowdfunding.xlsx  
&nbsp;&nbsp;  
&nbsp;&nbsp;  
## PostgreSQL Database Creation Instructions:

The final section of this project involves creating a PostgreSQL Database,
and populating it using the CSV file data that was exported in earlier sections of the project.
Below are the steps taken to accomplish this final section of the project.  

<pre>
Database and Table Creation:
-----------------------------
1.) Open the "pgAdmin" tool and create a database named "Project_2".
2.) Find the newly created "Project_2" database in the left-hand explorer panel and expand that part of the tree.
3.) Right-click on "Project_2" and select "Query Tool" from the drop-down menu.
4.) When the Query window appears, select the "folder" icon near the top of window
    which will launch an open-file dialogue ... find and load the schema file named "crowdfunding_db_schema.sql".
        ( FYI: "crowdfunding_db_schema.sql" is the exported output from the ERD diagram creation step ... 
               in which the "quickdatabasediagrams.com" website was used to evaluate the structure
               of the 4 csv files exported earlier in the project ... thus creating an ERD diagram.
               Here is a related screenshot: "PostgreSQL_pgAdmin_Screenshots/ERD_Database_Diagram.png" )
5.) In the Query window , find the loaded schema SQL script and highlight the 4 "CREATE TABLE" commands,
    as well as the 3 "ALTER TABLE" commands.
6.) Run the selected highlighted SQL commands by pressing the "play" icon near top of the Query window.
7.) Verify the 4 tables were created sucessfully by expanding the tree in the left panel
    under "Project_2"/"Schemas"/"Tables".
    The following 4 tables should appear ... campaign, category, contacts, subcategory.
9.) Verify the 4 tables were created sucessfully using SQL ...
    Highlight each of the following lines of SQL script, one at a time, in the Query window ...
          select * from campaign;
          select * from category;
          select * from contacts;
          select * from subcategory;
    ... and then press the "play" icon near top of the Query window to view the current table contents
    for each table.
    As expected, all 4 tables exist, but are currently empty.

 ( FYI: Here is a related screenshot:
       "PostgreSQL_pgAdmin_Screenshots/pgAdmin_1__created_empty_tables_from_schema.png" )


Import CSV File Data Into Database Tables:
-------------------------------------------
10.) *** Due to foreign key relationships , the last file to be imported must be the "campaign" CSV data file. ***
     So, a suggested order to use for importing all the CSV file data would be ...
         1.) Resources/category.csv
         2.) Resources/subcategory.csv
         3.) Resources/contacts.csv
         4.) Resources/campaign.csv
11.) In the left-hand tree panel, under "Project_2"/"Schemas"/"Tables", find each of the four tables.
     Right-click on a table, select "Import/Export Data" from the drop-down menu, and do the following ...
      A.) On the "General" tab ...
            - verify "Import/Export" selection is set to "Import"
            - verify "Filename" selection is set to the appropriate csv file
               (found in "Resources" folder) for the particular table
            - verify "Format" selection is set to "csv"
      B.) On the "Options" tab ...   
            - verify "Header" selection is switched to ON position
      C.) Click "OK" at lower right-hand corner of Import window to run the import process.
      D.) Verify that table loads succesfully, by observing green tinted pop-up window stating "Process completed".

 ( FYI: Here are some related screenshots:
       "PostgreSQL_pgAdmin_Screenshots/pgAdmin_2__manual_import_table_data_proceedure.png"
       "PostgreSQL_pgAdmin_Screenshots/pgAdmin_3__import_table_result_success.png" )


Display Final Database Table Data:
-----------------------------------
12.) Display the resulting database tables after the import process has been completed.
     Verify the 4 tables have been populated sucessfully by using SQL ...
     Highlight each of the following lines of SQL script, one at a time, in the Query window ...
          select * from campaign;
          select * from category;
          select * from contacts;
          select * from subcategory;
    ... and then press the "play" icon near top of the Query window to view the current table contents
    for each table.
    As expected, all 4 tables exist, and each table is now populated with the intended data.

 ( FYI: Here are some related screenshots:
     "PostgreSQL_pgAdmin_Screenshots/pgAdmin_4a__campaign_table__data.png"
     "PostgreSQL_pgAdmin_Screenshots/pgAdmin_4b__category_table__data.png"
     "PostgreSQL_pgAdmin_Screenshots/pgAdmin_4c__contacts_table__data.png"
     "PostgreSQL_pgAdmin_Screenshots/pgAdmin_4d__subcategory_table__data.png" )
</pre>

&nbsp;&nbsp;  
&nbsp;&nbsp;  
## Original Project Description Notes:  
Project 2
Due Monday by 11:59pm Points 100 Submitting a text entry box or a website url
For the ETL mini project, you will work with a partner to practice building an ETL pipeline using Python, Pandas, and either Python dictionary methods or regular expressions to extract and transform the data. After you transform the data, you'll create four CSV files and use the CSV file data to create an ERD and a table schema. Finally, you’ll upload the CSV file data into a Postgres database.

Since this is a one-week project, make sure that you have done at least half of your project before the third day of class to stay on track.

Although you and your partner will divide the work, it’s essential to collaborate and communicate while working on different parts of the project. Be sure to check in with your partner regularly and offer support.

Files
Download the starter code and files to help you get started:

Project 2 ETL filesLinks to an external site.

Before You Begin
Have one member of your group create a new repository, named Crowdfunding_ETL, for this project. Add your partner as a collaborator. Do not add this project to an existing repository.

Clone the new repository to your computer.

Have one person rename the ETL_Mini_Project_starter_code.ipynb file with the first name initial and last name of each member of the group, for example, ETL_Mini_Project_NRomanoff_JSmith.ipynb. Then, add this Jupyter notebook file and the Resources folder containing the crowdfunding.xlsx and the contacts.xlsx files to your repository.

Push the changes to GitHub.

Have your partner pull the changes, so both of you have the same notebook available on your computer.

As you work through the project deliverables, you may find it helpful to break up the work across other notebooks that you each work on individually. However, once complete, please combine all the subsections back into the final ETL_Mini_Project notebook.

Instructions
The instructions for this mini project are divided into the following subsections:

Create the Category and Subcategory DataFrames
Create the Campaign DataFrame
Create the Contacts DataFrame
Create the Crowdfunding Database
Create the Category and Subcategory DataFrames
Extract and transform the crowdfunding.xlsx Excel data to create a category DataFrame that has the following columns:

A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories

A "category" column that contains only the category titles

The following image shows this category DataFrame:

category DataFrame

Export the category DataFrame as category.csv and save it to your GitHub repository.

Extract and transform the crowdfunding.xlsx Excel data to create a subcategory DataFrame that has the following columns:

A "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories

A "subcategory" column that contains only the subcategory titles

The following image shows this subcategory DataFrame:

subcategory DataFrame

Export the subcategory DataFrame as subcategory.csv and save it to your GitHub repository.

Create the Campaign DataFrame
Extract and transform the crowdfunding.xlsx Excel data to create a campaign DataFrame has the following columns:

The "cf_id" column

The "contact_id" column

The "company_name" column

The "blurb" column, renamed to "description"

The "goal" column, converted to the float data type

The "pledged" column, converted to the float data type

The "outcome" column

The "backers_count" column

The "country" column

The "currency" column

The "launched_at" column, renamed to "launch_date" and with the UTC times converted to the datetime format

The "deadline" column, renamed to "end_date" and with the UTC times converted to the datetime format

The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category DataFrame

The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame

The following image shows this campaign DataFrame:

campaign DataFrame

Export the campaign DataFrame as campaign.csv and save it to your GitHub repository.

Create the Contacts DataFrame
Choose one of the following two options for extracting and transforming the data from the contacts.xlsx Excel data:

Option 1: Use Python dictionary methods.

Option 2: Use regular expressions.

If you chose Option 1, complete the following steps:

Import the contacts.xlsx file into a DataFrame.
Iterate through the DataFrame, converting each row to a dictionary.
Iterate through each dictionary, doing the following:
Extract the dictionary values from the keys by using a Python list comprehension.
Add the values for each row to a new list.
Create a new DataFrame that contains the extracted data.
Split each "name" column value into a first and last name, and place each in a new column.
Clean and export the DataFrame as contacts.csv and save it to your GitHub repository.
If you chose Option 2, complete the following steps:

Import the contacts.xlsx file into a DataFrame.
Extract the "contact_id", "name", and "email" columns by using regular expressions.
Create a new DataFrame with the extracted data.
Convert the "contact_id" column to the integer type.
Split each "name" column value into a first and a last name, and place each in a new column.
Clean and then export the DataFrame as contacts.csv and save it to your GitHub repository.
Check that your final DataFrame resembles the one in the following image:

final contact DataFrame

Create the Crowdfunding Database
Inspect the four CSV files, and then sketch an ERD of the tables by using QuickDBDLinks to an external site..

Use the information from the ERD to create a table schema for each CSV file.

Note: Remember to specify the data types, primary keys, foreign keys, and other constraints.

Save the database schema as a Postgres file named crowdfunding_db_schema.sql, and save it to your GitHub repository.

Create a new Postgres database, named crowdfunding_db.

Using the database schema, create the tables in the correct order to handle the foreign keys.

Verify the table creation by running a SELECT statement for each table.

Import each CSV file into its corresponding SQL table.

Verify that each table has the correct data by running a SELECT statement for each.

Hints
To split each "category & sub-category" column value into "category" and "subcategory" column values, use df[["new_column1","new_column2"]] = df["column"].str.split(). Make sure to pass the correct parameters to the split() function.

To get the unique category and subcategory values from the "category" and "subcategory" columns, create a NumPy array where the array length equals the number of unique categories and unique subcategories from each column. For information about how to do so, see numpy.arangeLinks to an external site. in the NumPy documentation.

To create the category and subcategory identification numbers, use a list comprehension to add the "cat" string or the "subcat" string to each number in the category or the subcategory array, respectively.

For more information about creating a new Pandas DataFrame, see the pandas.DataFrameLinks to an external site. in the Pandas documentation.

To convert the "goal" and "pledged" columns to the float data type, use the astype() method.

To convert the "launch_date" and "end_date" UTC times to the datetime format, see the Transform_Grocery_Orders_Solved.ipynb activity solution.

For more information about how to add the "category_id" and "subcategory_id" unique identification numbers to the campaign DataFrame, see the pandas.DataFrame.mergeLinks to an external site. in the Pandas documentation.

Support and Resources
Your instructional team will provide support during classes and office hours. You will also have access to learning assistants and tutors to help you with topics as needed. Make sure to take advantage of these resources as you collaborate with your partner on this project.

Requirements
A Category DataFrame is Created (15 points)
The DataFrame contains a "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories (5 points)
The DataFrame has a "category" column that contains only the category titles (5 points)
The category DataFrame is exported as category.csv (5 points)
A Subcategory DataFrame is Created (15 points)
The DataFrame contains a "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories (5 points)
The DataFrame contains a "subcategory" column that contains only the subcategory titles (5 points)
The subcategory DataFrame is exported as subcategory.csv (5 points)
A Campaign DataFrame is Created (30 points)
The DataFrame has the following columns: (25 points)
A "cf_id" column
A "contact_id" column
A "company_name" column
A "description" column
A "goal" column that is a float data type
A "pledged" column that is a float data type
An "outcome" column
A "backers_count" column
A "country" column
A "currency" column
A "launch_date" with the time formatted as "YYYY-MM-DD"
An "end_date" with the time formatted as "YYYY-MM-DD"
A "category_id" column that contains the unique identification numbers matching those in the "category_id" column of the category DataFrame
A "subcategory_id" column that contains the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame
The campaign DataFrame is exported as campaign.csv (5 points)
A Contacts DataFrame is Created (15 points)
The DataFrame has the following columns: (10 points)
A "contact_id" column
A "first_name" column
A "last_name" column
An "email" column
The contacts DataFrame is exported as contacts.csv (5 points)
A Crowdfunding Database is Created (25 points)
A database schema labeled, crowdfunding_db_schema.sql is created (5 points)
A crowdfunding_db is created using the crowdfunding_db_schema.sql file (5 points)
The database has the appropriate primary and foreign keys and relationships (5 points)
Each CSV file is imported into the appropriate table without errors (5 points)
The data from each table is displayed using a SELECT * statement (5 points)
This project will be evaluated against the requirements and assigned a grade according to the following table:

Grade	Points
A (+/-)	90+
B (+/-)	80–89
C (+/-)	70–79
D (+/-)	60–69
F (+/-)	< 60
Submission
You are required to submit the URL of your GitHub repository for grading.

NOTE
Projects are requirements for graduation. While you are allowed to miss up to two Challenge assignments and still earn your certificate, projects cannot be skipped.

References
Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.
