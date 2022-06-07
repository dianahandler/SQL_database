# SQL_database



This repository will serve to dive deeper into data modeling, engineering, and analysis. We will be creating entity relationship diagrams(ERDs), import data into a database, troubleshoot any errors that may arise, and create queries to answer questions about our data. 

SQL helps us learn how different data relates to one another. For this module we will use postgres and pgAdmin.

PH is a large company with thousands of employees. Ph looking towards future in two ways.  offering retirement packages for those who meet the criteria. They are also thinking which positions will need to be filled in the near future. The upcoming retirement numbers will leave thousands of open positions. We must find answers to the following questions:
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





Postgres holds the files, pgAdmin proces our access

PostgreSQL, commonly referred to as "Postgres," is a relational database system. This type of database consists of tables and their predefined relationships.

PgAdmin is the window into our database. This is where queries are written and executed and where results are viewed. 
