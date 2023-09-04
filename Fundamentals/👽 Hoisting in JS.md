
**Table of Contents**

- [[#What is Hoisting]]
- [[#Hoisting Arrow Functions and Function Expressions?]]

### What is Hoisting

Hoisting is a phenomenon in JS, by which we can access the variables and functions before initializing them. 
As we know, whenever JS code is run, the GEC is created. In that, before executing, the variables and functions get memory allocated. So technically, while executing the variables and functions should be accesible before declaration, because they have been already allocated the memory.
And that is true. 

See the code below.

```js
greetPerson();
console.log(x);

var x = 10;

function greetPerson(){
    console.log("Hello There!");
}
```

```
Hello There!
undefined
```

Before executing, see the GEC in watch mode. We have put the debugger before the first line. Before execution, the `greetPerson` has got the memory for its code and `x` has also got memory allocated.

 ![[Hoisting-1.png]]

The function gets the memory in the first phase. As execution starts in the second phase, function runs successfully. 
The variable is also accesible, however it is `undefined`. Becuase variables get assigned their value in the second phase. 

#### Hoisting Arrow Functions and Function Expressions?

The point to be noted is that we can call the function before declaration, only if the function is decalred using traditional way ie. using `function` keyword. 
Function expressions, arrow functions cannot be hoisted. Because, these functions are stored into a variable. And variables get their value assigned in the second phase.
So if we run the following code we get an error.

```js
greetPerson();

var greetPerson = ()=>{
	console.log("Hey There!")
}
```

```
> Uncaught TypeError: greetPerson is not a function
    at code.js:1:1
```

If we see in the GEC, `greetPerson` is present but the value is `undefined`.

![[Hoisting-2.png]]


> ⏭️ **Up Next:**  [[🔭 Scope Chaining and Lexical Environment]]
> 
>🔗 **Related:** 
>[[⛅ All about var, let and const]]

