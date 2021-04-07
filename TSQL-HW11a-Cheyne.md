# T-SQL Homework Chapter 11a

---

**Cheyne Lowery**

**April 06, 2021**

**SQL-HW21-Cheyne.md**

---

1. *Variables* are used in T-SQL to temprarily store data values for later use in the same batch in which they were declared. To *declare* a variable, use the *DECLARE* statement. To *initialize* a variable, use a *SET* statement. You can declare and initialize the variable in the same step using just the *DECLARE* statement and assignment operator.
```sql
DECLARE @i AS INT;
SET @i = 10;
DECLARE @i AS INT = 10;
```

2. The *SET* method is safer for setting a variable than the assignment *SELECT* statement because it requires you use a scalar subquery to pull data - *SET* will fail if more than one value is returned whereas *SELECT* can return multiple values.

3. A *batch file* in SQL is a group of statements, whereas a *transaction* is an anatomic unit of work - single statement.

4. A *transaction* can be split between multiple batches by splitting it up into parts. A *batch* can have multiple *transactions* by nature.

5. A *unit of resolution* AKA *binding* is the checking of the existence of objects and columns.

6. A vaiable is always *local to the batch* within which it is defined.

7. The *SSMS GO statement* may be used to continue executing transactions despite an error thrown in the middle.

8. To *delimit* *if...else* constructions that contain multiple statements, use the *BEGIN* and *END* keywords; the *BEGIN* and *END* keywords define the scope of execution similar to brackets in C#.

9. T-SQL *does* contain a *switch...case* construct, *CASE expressions*. *CASE expressions* are NOT interchangeable with the *if...else* construct as *CASE expressions* DO NOT control the flow of your code.

10. The difference between a *relation* and a *cursor* is that a *relation* is anatomic (all data is processed as a set/ unit). A *cursor* processes data row-by-row.

11. The steps to use a *cursor* are as follows:
	1. Declare the cursor based on a query
	2. Open the cursor
	3. Fetch attribute values from the first cursor record into variables
	4. Iterate and process each row, fetching the attribute values from the next values, unit *@FETCH_STATUS* is *0*.
	5. Close the cursor
	6. Deallocate the cursor
	
12. A *local temporary table* is restricted to the session that created it, and all inner levels in the call stack.

13. *Global temporary tables* are *automatically destroyed* by SQL Server when the creating session disconnects *AND* there are no references to that table. The main difference between *local temporary tables* and *global temporary tables* is that the former is ONLY available to the session that created them and are destroyed when the session disconnects; the latter is available to ALL users and is ONLY destroyed when ALL sessions have disconnected from the table.

14. You may ONLY want to use a *table variable* instead of a *local temporary table* because the former is only stored in memory during the execution of a batch, and is thus optimized for minimal use as such. You may want to use a *local temporary table* instead of a *table variable* because the former can be used throughout the entire scope of the session.

15. A *table type* is used to preserve a table definition as an object in the database - can be used for *stored procedures* and *user-defined functions* to reduce the amount of code written. Example syntax for creating a *table type*:

```sql
	DROP TYPE IF EXISTS dbo.MyTableType;
	
	CREATE TYPE dbo.MyTableType AS Table
	(
	userID INT NOT NULL PRIMARY KEY,
	firstname VARCHAR(25) NOT NULL,
	lastname VARCHAR(25) NOT NULL
	);
```