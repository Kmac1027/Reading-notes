# Read: 08 - SQL

- [SQL Cheat Sheet](http://www.cheat-sheets.org/sites/sql.su/)
- [Download A Primer on SQL](https://openlibra.com/en/book/download/a-primer-on-sql-3rd-edition)
 **as a note i did download this and is in my local 301 folder on my laptop**

## Introduction to SQL

- SQL, or Structured Query Language, is a language designed to allow both technical and non-technical users query, manipulate, and transform data from a relational database. And due to its simplicity, SQL databases provide safe and scalable storage for millions of websites and 
- There are many popular SQL databases including SQLite, MySQL, Postgres, Oracle and Microsoft SQL Server. All of them support the common SQL language standard, which is what this site will be teaching, but each implementation can differ in the additional features and storage types it supports.mobile applications.

### Relational databases

- Before learning the SQL syntax, it's important to have a model for what a relational database actually is. A relational database represents a collection of related (two-dimensional) tables. Each of the tables are similar to an Excel spreadsheet, with a fixed number of named columns (the attributes or properties of the table) and any number of rows of data.
- **EXAMPLE** Table: Vehicles
```
Id	Make/Model	#Wheels	#Doors	  Type
1	  Ford Focus	  4 	     4     	Sedan
2	Tesla Roadster	4	     2	     Sports
3	Kawakasi Ninja	2	      0	     Motorcycle
4	McLarenFormula1	4	      0	       Race
5	Tesla S	         4	     4	     Sedan
```
- By learning SQL, the goal is to learn how to answer specific questions about this data, like "What types of vehicles are on the road have less than four wheels?", or "How many models of cars does Tesla produce?", to help us make better decisions down the road.

## SQL Lesson 1: SELECT queries 101

- To retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries. A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned. It has a specific syntax though, which is what we are going to learn in the following exercises.

- As we mentioned in the introduction, you can think of a table in SQL as a type of an entity (ie. Dogs), and each row in that table as a specific instance of that type (ie. A pug, a beagle, a different colored pug, etc). This means that the columns would then represent the common properties shared by all instances of that entity (ie. Color of fur, length of tail, etc).

- Given a table of data, the most basic query we could write would be one that selects for a couple columns (properties) of the table with all the rows (instances).
```
SELECT column, another_column, …
FROM mytable;
```
- The result of this query will be a two-dimensional set of rows and columns, effectively a copy of the table, but only with the columns that we requested.
- If we want to retrieve absolutely all the columns of data from a table, we can then use the asterisk (*) shorthand in place of listing all the column names individually.
```
SELECT * 
FROM mytable;
```
## Finished Excercises

[Back to code 301 notes](../301.md)