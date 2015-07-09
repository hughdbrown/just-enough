# Just enough postgresql to poke yourself in the eye

## Exit psql
> \q

## Connect to a database using psql
> \connect (or \c) database_name

## Create/Delete Table
> CREATE TABLE 'table' AS (Enter Query) # Create table named 'table' populate with results from 										# 'Query'
> DROP TABLE 'table' # Delete table named 'table'

## List all database using psql
> \list or \l: list all databases

## List tables in database using psql
> \dt: list all tables in the current database

## Examine a Table
> \d table: list variables, types of each variable, and any modifiers in 'table'

## Load csv file from within psql
[reference](http://stackoverflow.com/questions/2987433/how-to-import-csv-file-data-into-a-postgres-table)

> \copy zip_codes FROM '/path/to/csv/ZIP_CODES.txt' DELIMITER ',' CSV
