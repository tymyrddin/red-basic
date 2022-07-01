# Confirm SQL injection vulnerability

## Attack tree

```text
1 Confirm SQL injection vulnerability (AND)
	1.1 Find out how to inject data in the query without breaking it (OR)
		1.1.1 Find how to escape from the current context (AND)
		1.1.2 Fix the query so there are no errors
			1.1.2.1 Change input data of the previous query (OR)
			1.1.2.2 Add a comment symbol at the end
	1.2 Make it operate a logical operation giving the expected results (OR)
	1.3 Make it operate a mathematical operation giving the expected results (OR)
	1.4 Confirm with timing
2 Identify back-end
```

## Notes

* If for example, the GET parameter `?username=Name` returns the same content as `?username=Name' or '1'='1` then, an SQL injection was found.
* If it is not possible to see any change on the page being tested, try a blind SQL injection - make the DB perform actions which will have an impact on the time the page needs to load.
* If sleep functions are not allowed, make the query perform complex operations that will take several seconds.

## Cheatsheets
* [Comment syntax](cheatsheets:docs/databases/comments)
* [Escape context](cheatsheets:docs/databases/escape-context)
* [Identify backend](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection#dbms-identification)
