# Explore XSS context

## Attack tree

```text
1 Reflected
    1.1 In Raw HTML
        1.1.1 Try creating new HTML tags
        1.1.2 Try using events or attributes supporting javascript: protocol
        1.1.3 Try bypassing protections
        1.1.4 Check whether the HTML content is being interpreted by a client side JS engine
    1.2 Inside an HTML tag
        1.2.1 Try exiting to raw HTML context
        1.2.2 Try creating new events/attributes to execute JS code
        1.2.3 Try bypassing protections
    1.3 Inside JavaScript code
        1.3.1 Try escaping the <script> tag
        1.3.2 Try escaping the string and execute different JS code
        1.3.3 Check input in template are literals
        1.3.4 Try bypassing protections
    1.4 Javascript function being executed
        1.4.1 Indicate the name of the function to execute
2 Used
```

## Examples

### In raw html

If input is reflected in the raw HTML page, use some HTML tag in order to execute JS code: 

```text
<img 
<iframe 
<svg 
<script 
...
```

### In html tag
If input is reflected inside the value of the attribute of a tag, try:

To escape from the attribute and from the tag (to be in the raw HTML) and create a new HTML tag to use: 

```text
"><img [...]
```

If escape from the attribute is possible, but not from the tag (`>` is encoded or deleted), depending on the tag, create an event that executes JS code: 

```text
" autofocus onfocus=alert(1) x="
```
If it is not possible to escape from the attribute (`"` is being encoded or deleted), then depending on which attribute the value is being reflected in, if you control the value or just a part of it is possible to use it. 

For example, if controlling an event like `onclick=`, it will be possible to make it execute arbitrary code when it is clicked. 

Another interesting example is the attribute `href`, where it is possible to use the `javascript:` protocol to execute arbitrary code: 

```text
href="javascript:alert(1)"
```

If input is reflected inside "unexpoitable tags", try the accesskey trick to use the vulnerability (this requires some social engineering): 

```text
" accesskey="x" onclick="alert(1)" x="
```

### Inside JavaScript code

In this case the input is reflected between `<script> [...] </script>` tags of an HTML page, inside a `.js` file or inside an attribute using `javascript:` protocol:

If reflected between `<script> [...] </script>` tags, even if the input is inside any kind of quotes, try to inject 
`</script>` and escape from this context. This works because the browser will first parse the HTML tags and then the 
content. As a result it will not notice the injected `</script>` tag inside the HTML code.

If reflected inside a JS string and the above trick is not working, try to exit the string, execute code and reconstruct the JS code (if there is any error, it won't be executed):

```text
'-alert(1)-'
';-alert(1)//
\';alert(1)//
```

If reflected inside template literals, try embedding JS expressions using `${ ... }` syntax: 

```text
var greetings = `Hello, ${alert(1)}`
```

### Javascript function

Several web pages have endpoints that accept as parameter the name of the function to execute. A common example to see 
in the wild is something like: 

    ?callback=callbackFunc.

A good way to find out if something given directly by the user is trying to be executed is modifying the param value 
(for example to 'Vulnerable') and looking in the console for errors. If found, a Same Origin Method Execution (SOME) 
exploitation may be possible.

## Notes

### Used
There is JS code that is using unsafely some data which can be controlled, like `location.href`. This can be used to 
execute arbitrary JavaScript code in DOM based XSS.

## Cheatsheets

* [XSS Filter Evasion Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html)