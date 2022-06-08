# SQL_database



This repository will serve to dive deeper into data modeling, engineering, and analysis. We will be creating entity relationship diagrams(ERDs), import data into a database, troubleshoot any errors that may arise, and create queries to answer questions about our data. 

For this module we will use postgres and pgAdmin.

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

We use "varchar" in a given column because the fields contain characters of varying length. "pk" indicates that the column is a primary key

We create our final diagram
<img width="1346" alt="Screen Shot 2022-06-07 at 11 40 24 AM" src="https://user-images.githubusercontent.com/82029390/172423142-9e91a6e8-c877-4460-800b-aca1151efbd6.png">


We now open PgAdmin to create our database. We create our first table for the departments CSV. By Adding "NOT NULL," we make sure to not import any data with empty fields as to maintain our data integrity.




Postgres holds the files, pgAdmin proces our access

PostgreSQL, commonly referred to as "Postgres," is a relational database system. This type of database consists of tables and their predefined relationships.

PgAdmin is the window into our database. This is where queries are written and executed and where results are viewed. 
