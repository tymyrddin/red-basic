# SQL injection login bypass

## Attack tree

```text
1 SQL injection login bypass
    1.1 Find out if the database is vulnerable (AND)
        1.1.1 Inject data in the query without breaking it
    1.2 Build an SQL segment that will modify the WHERE clause and make it true (AND)
        1.2.1 Use login page logic to create an SQL segment on admin 
    1.3 Inject 
```

## Example building SQL segments to modify the WHERE clause and make it true

```text
SELECT * FROM users WHERE username='$USERNAME' AND password='$PASSWORD'
```

Assume a login form with two input fields (username and password) which are both vulnerable (page breaks on 
entering a `'` and responds to changed queries), meaning, the backend script generates a query to validate username and 
password provided by the user and quotes are not correctly handled (escaped) by the application and allow an adversary 
to modify the query. 

The page logic:

```text
admin
wrong' OR 'a'='a
```

Results in a WHERE clause which is true:

```text
SELECT * FROM users WHERE username='admin' AND password='wrong' OR 'a'='a'
```
Because of operator precedence, the AND condition is evaluated first. Then the OR operator is evaluated, making the 
WHERE clause true. Even more, the condition will be true for all rows of the users table and as a result,
username is ignored and the adversary will be logged in as the first user in users table.

The page logic:

```text
admin' --
whatever
```

Also results in a WHERE clause which is true, but now the adversary logs in as admin:

```text
SELECT * FROM users WHERE username='admin' -- AND password='whatever'
```

Line commenting eliminates a part of the login condition and gains access.
Note: For some DBMS, a space needs to be added before and after `--`.

## Notes

If the simple login bypass is not working, check with Burp proxy whether there is client side filtering. If so, modify the request.

## Cheatsheets
* [MySQL commands](cheatsheets:docs/databases/mysql-commands)

## Mitigations
* [Parameterised statements](app-mitigations:docs/databases/parameterised)
* [Input validation](app-mitigations:docs/databases/Input-validation)