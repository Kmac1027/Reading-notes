# Read: 14a - DB Normalization

## Database Normalization (Explained in Simple English)

### Introduction to Database Normalization

- Database normalization is a process used to organize a database into tables and columns.  The main idea with this is that a table should be about a specific topic and only supporting topics included. Take a spreadsheet containing the information as an example, where the data contains salespeople and customers serving several purposes:
  1. Identify salespeople in your organization
  1. List all customers your company calls upon to sell a product
  1. Identify which salespeople call on specific customers.
- By limiting a table to one purpose you reduce the number of duplicate data contained within your database. This eliminates some issues stemming from database modifications.
- To achieve these objectives, we’ll use some established rules. As you apply these rules, new tables are formed. The progression from unruly to optimized passes through several normal forms.
- There are three normal forms most databases adhere to using.  As tables satisfy each successive database normalization form, they become less prone to database modification anomalies and more focused toward a sole purpose or topic. Before we move on be sure you understand the definition of a database table.

### Reasons for Database Normalization

- There are three main reasons to normalize a database.  The first is to minimize duplicate data, the second is to minimize or avoid data modification issues, and the third is to simplify queries. 
- As we go through the various states of normalization we’ll discuss how each form addresses these issues, but to start, let’s look at some data which hasn’t been normalized and discuss some potential pitfalls. 
- As a DBA this raises a red flag.  In general I like to see tables that have one purpose.  Having the table serve many purposes introduces many of the challenges; namely, data duplication, data update issues, and increased effort to query data.

### Data Duplication and Modification Anomalies

- Insert Anomaly
  - There are facts we cannot record until we know information for the entire row.  In our example we cannot record a new sales office until we also know the sales person.  Why?  Because in order to create the record, we need provide a primary key.  In our case this is the EmployeeID.
- Update Anomaly
  - In this case we have the same information in several rows. For instance if the office number changes, then there are multiple updates that need to be made.  If we don’t update all rows, then inconsistencies appear.
- Deletion Anomaly
  -Deletion of a row causes removal of more than one set of facts.  For instance, if John Hunt retires, then deleting that row cause us to lose information about the New York office.

### Search and Sort Issues

- The last reason we’ll consider is making it easier to search and sort your data.  In the SalesStaff table if you want to search for a specific customer such as Ford, you would have to write a query like
```
SELECT SalesOffice
FROM SalesStaff
WHERE Customer1 = ‘Ford’ OR
      Customer2 = ‘Ford’ OR
      Customer3 = ‘Ford’
```
- Clearly if the customer were somehow in one column our query would be simpler.  Also, consider if you want to run a query and sort by customer. 
- Our current table makes this tough. You would have to use three separate UNION queries! You can eliminate or reduce these anomalies by separating the data into different tables. This puts the data into tables serving a single purpose.
- The process to redesign the table is database normalization.

### Definition of Database Normalization

- There are three common forms of database normalization: 1st, 2nd, and 3rd normal form. They are also abbreviated as 1NF, 2NF, and 3NF respectively. 
- The forms are progressive, meaning that to qualify for 3rd normal form a table must first satisfy the rules for 2nd normal form, and 2nd normal form must adhere to those for 1st normal form. Before we discuss the various forms and rules in detail, let’s summarize the various forms:
  1. First Normal Form – The information is stored in a relational table with each column containing atomic values. There are no repeating groups of columns.
  1. Second Normal Form – The table is in first normal form and all the columns depend on the table’s primary key.
  1. Third Normal Form – the table is in second normal form and all of its columns are not transitively dependent on the primary key
  
[Back to code 301 notes](../301.md)