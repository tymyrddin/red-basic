# SQL injection login bypass

## Attack tree

```text
1 SQL injection login bypass
    1.1 Find out if the database is vulnerable
    1.2 Build an SQL segment that will modify the WHERE clause and make it true
        1.2.1 Use login page logic to create an SQL segment on admin 
    1.3 Inject
    1.4 Use SQL commands
```

## Cheatsheets
* [SQL injection login bypass](cheatsheets:docs/databases/mysql-login)
* [MySQL commands](cheatsheets:docs/databases/mysql)

## Mitigations
* [Parameterised statements](app-mitigations:docs/databases/parameterised)
* [Input validation](app-mitigations:docs/databases/Input-validation)