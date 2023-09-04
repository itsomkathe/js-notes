
**Table of Contents**

- [[#Closures]]
- [[#Cases to Remember]]

### Closures

Without messing up, closure is simply **Function along with its lexical environment**.
Which means function with all referances to it's all parent's local variables and functions forms a closure.

> Closure = Function + Lexical Environment

See the code example below

```js
function x(){
    let a = 10;

    function y(){
        console.log(`a: ${a}`);
    }
    return y;
}

const fun = x();
fun();
```

```
a: 10
```

The function `x` return function `y`. Cool. 
Had `y` been called inside `x`, it would have printed the value 10, as we discussed in the article
[[🔭 Scope Chaining and Lexical Environment]] . 

But now `x` returns `y`, and `y` is called outside of the `x`. It still prints the value of `a` successfully. This is because `y` remembers its lexical environment. This is called a closure. So while returning, not only `y` was returned, but the closure was returned.

### Cases to Remember

1. Functions remember closures from every level.

```js
function x(){
    let a = 10;
    
    function y(){
        var b = 50;

        function z(){
            console.log(`a: ${a}`);
            console.log(`b: ${b}`);
        }
        return z;
    }
    return y();
}

const fun = x();
fun();
```

```
a: 10
b: 50
```

![[Closure-1.PNG]]

The scope of `z` includes closure of it's parent and grandparent. 

>Functions remember closures from every level.
>Closures work with all variable types ie. `var`, `let` and `const`

2. Closure refers to the address of the variable. 

```js
function x(){
    let a = 10;

    function y(){
        console.log(`a: ${a}`);
    }
    //Updating a's value
    a = 70;
    
    return y;
}

const fun = x();
fun();
```

```
a: 70
```

The `a` is printed as 70. Because, reassigning of `a` happens before the execution of `y`. And the closure points to the address of `a` in execution context. So updating the variable reflects the changes. 


>⏭️ **Up Next:**  [[⏰ All about setTimeout]]
> 
>🔗 **Related:** 
>[[🔭 Scope Chaining and Lexical Environment]]