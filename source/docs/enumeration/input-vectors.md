# Input vectors enumeration

```text
1 Test all application components that can accept user input, such as HTTP, POST and GET calls, HTML forms, and file uploads for vulnerabilities 
    1.1 Request parameters which can potentially be used for file-related operations
    1.2 Unusual file extensions 
    1.3 Interesting variable names  
```

## Examples

* (1.1) Request parameter: https://www.example.com/getUserProfile.jsp?item=whatever.htm
* (1.2) File extension: https://www.example.com/index.jsp?file=content
* (1.3) Variable name: https://www.example.com/main.php?home=index.htm



