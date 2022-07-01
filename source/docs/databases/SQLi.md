# SQL injection

## Attack tree

```text
1 SQL injection
    1.1 In-band SQLi (OR)
        1.1.1 Error based (OR)
        1.1.2 Union based
    1.2 Inferential or Blind SQLi (OR)
        1.2.1 Boolean based (OR)
        1.2.1 Time based
    1.3 Out-of-band SQLi
```

## Notes

An SQL injection attack consists of insertion or “injection” of a SQL query via the input data from the client via the 
application to the database. A successful SQL injection exploit can read sensitive data from the database, modify 
database data (Insert/Update/Delete), execute administration operations on the database (such as shutdown the DBMS), 
recover the content of a given file present on the DBMS file system and in some cases issue commands to the operating 
system. SQL injection attacks are a type of injection attack, in which SQL commands are injected into data, plane input 
in order to effect the execution of predefined SQL commands. 

SQL Injection is often classified into three categories:

1. In an in-band SQLi an attacker uses the same communication channel to launch the attack and gather results. The two most common types are:
   * Error-based SQLi is a technique that captures error messages thrown by the database server to obtain information about the structure of the database. In some cases, error-based SQLi alone is enough to enumerate an entire database. While very useful during development, do disable on a production site, or have the errors be logged to a file with restricted access. Hacking example in [Confirm SQL injection vulnerability](Confirm-injection-vuln.md)
   * Union-based SQLi is a technique that leverages the UNION SQL operator to combine the results of two or more SELECT statements into a single result which is returned as part of the HTTP response. Example in [Extracting data from databases](SQLi-extract.md)
1. In an inferential or blind SQLi attack, the database structure is reconstructed by sending payloads and observing the web application’s response and the resulting behaviour of the database server. No data is transferred via the web application and the results are not visible like with an in-band attack.
   * In Boolean-based SQLi an SQL query is sent to the database which forces the application to return a different result depending on whether the query returns a TRUE or FALSE result. The content within the HTTP response will change, or remain the same. A database can be enumerated character by character.
   * In Time-based SQLi, a query is sent to the database forcing it to wait for a specified amount of time (in seconds) before responding. The response time indicates whether the result of the query is TRUE or FALSE.
1. Out-of-band SQLi can be used when it is not possible to use the same channel to launch the attack and gather results or if the server responses are not very stable, making an inferential time-based attack unreliable. This attack uses DNS or HTTP requests to deliver data.


