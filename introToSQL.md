# Introduction to SQL  

## Dealing with existing table

---

### Lesson 1: **SELECT**  

to retrieve a data that exist in SQL database.
> **SELECT * FROM databaseName;**

**NOTE:**  * indicate to retrieve all column in database.

### Lesson 2  **CONSTRAINTS Pt. 1**

- We using **WHERE** to add condition to data we want to retrieve.

- We can use more than conditions using **And/or**  

> the Condition can be specify using some operator like:  

|   Operator           |    Condition                  |       SQL Ex.                   |
|   -----              |    ------                     |         ----                    |
|  =, !=, < <=, >, >=  | numerical operators           |     col_name <> 5               |
|   BETWEEN .. AND     | Range between 2 value         |  col_name BETWEEN 5 AND 4       |
| NOT BETWEEN .. AND   | Not between 2 value range     |  col_name  NOT BETWEEN 5 AND 4  |
|       IN(..)         | if Number exist in a list     |  col_name IN (1,2,3,4,5)        |
|     NOT IN(..)       | if Number NOT exist in a list |  col_name NOT IN (1,2,3,4,5)    |

### Lesson 3  

|   Operator           |    Condition                                                                            |       SQL Ex.                   |
|   -----              |    ------                                                                               |         ----                    |
|          =           | check if data is equal                                                                  |     col_name = 5                |
|       != or <>       | check if data is Not equal                                                              |     col_name != 5               |
|         LIKE         | if case sensitive exact String                                                          |  col_name LIKE "ABCDE"                |
|      NOT LIKE        | if case sensitive exact String  inequality comparison                                   |  col_name NOT LIKE "ABCDE"            |
|          %           | to Justify the string whatever it start in the beginning or middle or int the last      |  col_name LIKE "%AT%"                 |
|          _          | Used to match a single character                                                         |  col_name LIKE "RA_"                  |

### Lesson 4: Filtering and sorting Query results  

- **DISTINCT**: DISTINCT used after SELECT keyword to remove the redundancy information.  

- **ORDER BY**:  Make the result organized in ascending or descending order.  

- **Limit**: we use LIMIT to choose a certain number of rows from the result.

- **Offset**: to determine the start point we want to begin from there.

 **Lesson 5 is a review.**  

### Lesson 6: JOIN  

- Using **INNER JOIN** to merge two table or more.

## Modifying on table  

---

### Lesson 13: INSERT

- Use **INSERT INTO** keyword to insert new value to the table.  

### Lesson 14: UPDATE  

- It's to change an existing data.  

> We  using the UPDATE keyword with Set Keyword to change the value. In Addition to need a condition  to specify the data we want to edit.  

### Lesson 15: DELETE

- Remove an existing data using DELETE Keyword with condition. If we don't put the condition all the data in table will be clear.  

## updating TABLE and Creating, deleting Database  

---

### Lesson 16: **CREATE Database**  

Add new Table in database using:  

> **CREATE TABLE IF EXIST TableName(  
> ColoumName Datatype Constraint,  
> AnotherColoumName Datatype Constraint,  
> ..  
> );**  

### Lesson 17: **Altering table**  

In Altering Table we have 3 type:  

1. **ALTER ... ADD ... DEFAULT**  
to add new column with default value.  

2. **ALTER ... DROP**  to remove column.  

3. **ALTER ... RENAME ... TO**  

### Lesson 18: **Drop table**

- **DROP TABLE IF EXIST tableName** to drop table and we use IF EXIST to sure we have a table to delete because if the database dont have the software assume that as an error.  
