# SQL_database



This repository will serve to dive deeper into data modeling, engineering, and analysis. We will be creating entity relationship diagrams(ERDs), import data into a database, troubleshoot any errors that may arise, and create queries to answer questions about our data. 

For this task we will use postgres and pgAdmin.

PH is a large company with thousands of employees. They are looking towards future in two ways: 1) offering retirement packages for those who meet the criteria 2)Determining which positions will need to be filled in the near future. The upcoming retirement numbers will leave thousands of open positions. We must find answers to the following questions:
- Who will be retiring in the next few years?
- How many positions will PH need to fill?

This analysis will help PH by generating a list of all employees eligible for the retirement package. However the data provided to us comes in the form of 6 csv files because the various departments had largely been inputting their data into excel files. Our task is to generate a database to consolidate our data.

In this project, we will:
* Design an ERD that will apply to the data
* Import and export large CSV datasets into pgAdmin
* Utilize different joins to create new tables in pgAdmin
* Write SQL statements


### Identifying Data Relationships

Let us explore our data tables. When approaching data we like to answer some key questions:
* What data types are involved?
* How many files are we working with?
* Is our data easy to read?

We are provided six CSVs each with information regarding departments, department employee start dates, department managers, employees, salaries, and titles

We shall first establish our primary and foreign keys. 


### Entity Relationship Diagrams(ERDs)

An entity relationship diagram(ERD) is a type of flowchart that highlights different tables and their relationships to eachother. While it does not hold any data itself, it captures the pertinent information from eash CSV file:
* Primary keys
* Foreign keys
* Data types for each column

Our ERD shows the flow of information from one table to another, as exhibited below:

<img width="958" alt="Screen Shot 2022-06-07 at 10 51 48 AM" src="https://user-images.githubusercontent.com/82029390/172411615-25d40070-f4ba-4765-a246-64e0555f223a.png">

There are three types of ERDs: conceptual, logical, and physical. Each one builds upon the other. We need the conceptual ERD to build a logical ERD and we need the logical ERD to build a physical ERD.

## Mapping Our Database

We will create a map that ill show us each table in the database and the flow of data from one table to another. This allows us to easilly reference our data without having to access it. This is our data modeling process. We will use an online toll called Quick Database Diagrams(Quick DBD)

Conceptual diagram contains table name and column headers. This is simply the concept of the diagram. 
Logical diagrams contain all of the same information as the conceptual however it also includes data types and primary keys.
"Varchar" is used in a given column because the fields contain characters of varying length. "pk" indicates that the column is a primary key

The final diagram:
<img width="1346" alt="Screen Shot 2022-06-07 at 11 40 24 AM" src="https://user-images.githubusercontent.com/82029390/172423142-9e91a6e8-c877-4460-800b-aca1151efbd6.png">


We now open PgAdmin to create our database. We create our first table for the departments CSV. By Adding "NOT NULL," we make sure to not import any data with empty fields as to maintain our data integrity. It is also critical to add foreign and primary keys so that the relationship between each table is established in our database. We can additionally confirm that the table has been created ith the following code:

<img width="202" alt="Screen Shot 2022-06-08 at 12 45 56 PM" src="https://user-images.githubusercontent.com/82029390/172671966-542290c1-322c-4191-ad14-8f3cf8d773f0.png">

When this query is executed, the following output appears:

<img width="539" alt="Screen Shot 2022-06-08 at 12 46 16 PM" src="https://user-images.githubusercontent.com/82029390/172672082-6b06ae9c-7cd6-414d-9ffa-77125a925a9e.png">

The above table indicates that the columns and data types have been successfully created and all that is left is to import the data. It's generally good practice to check that all tables have been succesfully created lest we wish to run into any errors along the way! 

## Importing the Data

Now that we have created the six tables modeled after our ERD, the CSV data must be imported. First, we import our departments csv. To check that the data has successfully been imported, we can run our code from above for the departments data.

<img width="395" alt="Screen Shot 2022-06-08 at 12 54 12 PM" src="https://user-images.githubusercontent.com/82029390/172673437-69a54d46-17b4-4424-b1c6-917e73d2f495.png">

All looks quite well here. Let us now try to import the dept_emp data...

<img width="714" alt="Screen Shot 2022-06-08 at 12 29 08 PM" src="https://user-images.githubusercontent.com/82029390/172673696-25cc41f9-4095-47c8-95a5-1206d0bfc099.png">

......oh my! 

## Troubleshooting 

It appears that this csv was not successful in importing. Let's take a closer look at some of the elements of this error notification:

->  'dept_emp' violates foreign key constraint 'dept_emp_emp_no_fkey' 

(Ironically, reading error messages for code can sometimes be more difficult to understand than the code itself but it is always a good idea to parse out the objects mentioned that you can immediately reference. Here, we draw our attention to 'dept_emp_emp_no_fkey')

-> Key(emp_no)=(10001) is not present in table "employees"

Our foreign key "emp_no" seems to violate the foreign key constraint. While this tells us there is something off about this foreign key we have established in our dept_emp table, the second line allows us to further deduce the issue. The first row of the dept_emp table we just attempted to import( (emp_no)=(10001) ) is not present in our employees table. If we run SELECT * FROM employees; to view our employees table, we see that because the csv has not yet been imported, the table is blank.

When we created our dept_emp table, we established a foreign key "emp_no" that referenced the "emp_no" primary key in our employees table. However because the dept_emp data was imported *before* the employees data, there was no foreign key our dept_emp table could find. Hence why we received the error "(emp_no)=(10001) is not present in table 'employees' " because the employees table had no data to begin with.

Thus it is **critical** to pay close attention to the order in which we load in our data.

Once we import our employees csv data, we can import the dept_emp with no errors.




Postgres holds the files, pgAdmin proces our access

PostgreSQL, commonly referred to as "Postgres," is a relational database system. This type of database consists of tables and their predefined relationships.

PgAdmin is the window into our database. This is where queries are written and executed and where results are viewed. 
