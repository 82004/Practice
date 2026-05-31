# Data Engineering Notes(Scholarship)
# RIG academy

### MODULE 1 ###
I. Database and DBMS
II. Database Languages
III.  Datbase Models and Designs
IV. Database Engine


### I.
## What is database?
A database is an organized collection of data stored in computer systems.
Purpose: To conveniently and efficiently store, retrieve database information .
         To ensure the safety of information stored despite system crashes

### Database Management System(DBMS)
DBMS is a software that manages and handles the data within databases:store, retrieve, add and delete data.
Without DBMS, there will be messy data leading to data redundancy, no security:overall- inefficiency.
There are four types of DBMS:
1. Hierarchical
2. Network
3. Relational
4. Object-oriented.

# We are mostly familiar with relational models which are based on tables; making everything clearer with tuples and degrees.
** Tuple: A row or a record: contains data about one user
** Degree: A coulumn: contains values of a specific trait of users

## ------------------------------------------------------------------------------------

### II.
### Database Languages
1. Data Definition Language(DDL)
   - To define and structure databases
: CREATE, TRUNCATE, ALTER, DROP
CREATE - use this when creating tables and schemas => ```sql CREATE TABLE .. tableName.. (  );
ALTER - modify the tables and schemas => ```sql ALTER TABLE ..tableName.. (  );
TRUNCATE - delete all rows 
DROP - drops the whole thing(database, for example) => ```sql DROP DATABASE  ..dbName..;

2. Data Manipulation Language(DML)
   - To add, update, delete data from table:manipulate data
: INSERT, UPDATE, DELETE
INSERT - INSERT INTO (colName1,colName2,..) VALUES ('value1','value2',..);
UPDATE - UPDATE ..tableName.. SET ..changedInfo.. WHERE ..condition..;
DELETE - DELETE FROM ..tableName.. WHERE ..cond..;

3. Data Query Language(DQL)
  - To retrieve data
:SELECT
SELECT - SELECT ..colName or *(for all).. FROM ..tableName.. WHERE .. cond..;
Note: * is not recommended for major operations!

4. Data Control Language(DCL)
  - To grant/ revoke permissions 
:GRANT,REVOKE, FLUSH PRIVILEGES(for faster exec)
Scenario: Only the admins can see all info about the system. Sensitive data can be hidden from outsiders.

B4 granting or revoking, you need to create users to grant permissions. 
CREATE UER 'username'@'localhost' IDENTIFIED BY 'pasword';

GRANT - GRANT ..Sql commands.. ON ..tableName.. TO ..'username'@'localhost';
# More than one sql command can be added

REVOKE - REVOKE ..sqlCommand.. ON ..'username'@'localhost' FROM ..tableName..;
# Only one sql command can be here.

5. Transaction Control Language
   - paired with ACID, this is used to check if an operation can be successfully completed or not.
Scenario: you transfer $500 to your friend and you have a e-receipt saying 'you have transferred' but 
there's no incoming e-cash in your friend's account. This is a big issue! The money is lost between trasactions.
That's when TCL rolls around.

Transaction is a unit of execution program
START TRANSACTION;s
---
sql commands
---
COMMIT => if all commands are correct
ROLLBACK => if there's an error

## It guarantees four traits(ACID)
1. Atomicity - all or nothing
2. Consistency - during state changes, chaning into another states are promised to be consistent.
3. Isolation - No concurrent transaction, Only one at a time.
4. Durability - Permanent data are saved(after COMMIT)

So, in a nutshell, 
DDL creates the tables,
DQL for the retrieval,
DML for modification,
DCL for access control and
TCL for transaction consistency.

## ------------------------------------------------------------------------------------

### III.
### Datbase Models and Designs
Purpose : to meet the requirements of the users and to improve performance
1. Conceptual
2. Logical
3. Physical

* Conceptual model is the roadmap of the entire system.
- Defines 'what data do we need?'
e.g - ER diagrams
By business owners and data architects.

* Logical model 
Defines how the data should be structured logically'
# The infamous normalization happens in this stage.
By Data analysts and modelers.


* Physical Model
Defines 'how data should be implemented in a specific database'
e.g - MySQL, PostgreSQL etc(takes up physical spaces and involves creating, manipulating tables:DBMS)
By DBA and engineers

## ------------------------------------------------------------------------------------

### IV.
### Database Engine
1. Query Processor(Brain)
2. Transaction Management(Guard)
3. Storage Manager(Hands)

Query Processor : responsible for executing  and processing database queries.
1. DDL interpreter - Processes schema definitions/stores metadat(data about data)
2. DML compiler    - Convert SQL into low-level instructions/ generates execution plans/ chooses the most efficient one
3. Query Evaluation Engine - Improves performacne/reduces exec time
* Three components:
  i. Parser(CMD)
  ii. Optimizer
  iii. Execution

  Transaction Management

  Five phases
  i. Acive State - START TRANSACTION;
  ii. Partially Committed - All operations are done, waiting for final commit
  iii. Committed state - COMMIT
  iv. Failed - error after operations
  v. Termination - ROLLBACK

  Scenario: If a customer orders a product is the start of a transaction.
            The customer has chosen everything she/he needs and system checks are still pending- partailly committed
            if Both the order and payment completed - COMMIT(success),
            else if the payment fails or the cusomter changes her mind => failed state
            then ROLLBACK to terminate(cancel) the order 





