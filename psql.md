# Just enough postgresql to poke yourself in the eye

## Exit psql
> \q

## Connect to a database using psql
> \connect (or \c) database_name

## Create Table
```
CREATE TABLE 'table' AS (Enter Query) # Create table named 'table', populate with results from 
									  # Query
```
## Delete Table
```
DROP TABLE 'table' # Delete table named 'table'
```

## List all database using psql
> \list or \l: list all databases

## List tables in database using psql
> \dt: list all tables in the current database

## Examine a Table
> \d table: list variables, types of each variable, and any modifiers in 'table'

## Load csv file from within psql
[reference](http://stackoverflow.com/questions/2987433/how-to-import-csv-file-data-into-a-postgres-table)

> \copy zip_codes FROM '/path/to/csv/ZIP_CODES.txt' DELIMITER ',' CSV

## Selecting Data

```
SELECT column1, column2 
FROM table1; # Returns column1 and column2 from table1. 

SELECT column1, column2 
FROM table1
WHERE column1 == value; # Returns column1 and column2 from table 1 for observations where 
						# column1 == value. You can also use greater than, less than, etc. as well
						# as throwing subqueries in there. 

SELECT AVG(column1), column2 
FROM table1 
WHERE column1 == value; # Returns average of column1 and column2 from table1 for observations 
						# where column1 == value. 
```

## Aliasing Columns

```
SELECT AVG(column1) as col1_avg
FROM table1; 	# Returns the average of column1 from table1, labeled as col1_avg. 