
**Table of Contents**

- [[#What is Scope]]
- [[#Lexical Environment]]
	- [[#Scope Chaining]]

### What is Scope

Scope is simply **where the perticular variable or function can be used inside the code.**

```js
function fun(){
	var x = 7;
}

fun();
console.log(x);
```

Here, the `x` is declared inside a function which is having its own lexical environment. So, we cannot access the variable inside `fun` outside of its scope.

### Lexical Environment

Lexical Environment, is an environment created for every execution context. Which means, the global space and every function will have its own lexical environment. 

See the code below and it's output.

```js
var a = 10;

function foo(){
    var c = 25;
    bar();
    function bar(){
        console.log(`a: ${a}`);
        console.log(`b: ${b}`);
        console.log(`c: ${c}`);
    }
}

foo();
var b = 20;
```

```
a: 10
b: undefined
c: 25
```

Looking at the output, we're able to access the variables `a, b` and `c`, inside the function `bar`.
This is due to the lexical environment. 
Say lexical environment of `bar` is `lex(bar)``. So the definition of it would be,

```
lex(bar) = local + lex(foo)
```

Where,
- `local`: Local memory of the function. Any variables, functions declared inside the function
- `lex(foo)`: Lexical environment of it's parent function.

Similarly for `foo`, because it's parent is `global` space, 

```
lex(foo) = local + lex(global)
```

As there is no parent of `global` space,

```
lex(global) = local + null
```

##### Scope Chaining

The phenomenon seen in above code happens due to Scope Chaining. 
Whenever any function cannot find a variable or a function inside it's `local` scope, it searches for it in the lexical environment of it's parent. If not found in parent, it goes to lexical environment of parent of it's parent. This chain is followed untill the lexical environment comes out as null ie. in `global` space.

See the lexical environment of the three levels.

1. For `global` space, only Global scope is there as a lexical environment. `c` is not available because it is not in the scope of `global`.

![[Lexical-1.PNG]]

2. For function `foo`, Local + Global is there

![[Lexical-2.PNG]]

3. For function `bar`, Local + Closure + Global is available. Closures are covered as a seperate topic. `b` is `undefined` because it has not been initialized yet, but is still accessible.

![[Lexical-3.PNG]]


> ⏭️ **Up Next:**  [[⛅ All about var, let and const]]
> 
>🔗 **Related:** 
>[[⛅ All about var, let and const]]
>[[🔒 Closures Demystified]]
