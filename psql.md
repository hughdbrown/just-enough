# Just enough postgresql to poke yourself in the eye

## Connect to a database using psql
> \connect (or \c) database_name

## List all database using psql
> \list or \l: list all databases

## List tables in database using psql
> \dt: list all tables in the current database

## Load csv file from within psql
[reference](http://stackoverflow.com/questions/2987433/how-to-import-csv-file-data-into-a-postgres-table)

> \copy zip_codes FROM '/path/to/csv/ZIP_CODES.txt' DELIMITER ',' CSV
