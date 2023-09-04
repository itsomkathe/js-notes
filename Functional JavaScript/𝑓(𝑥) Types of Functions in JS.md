
**Table of Contents**

- [[#Function Statement aka Function Declaration]]
- [[#Function Expression]]
	- [[#Difference Between Function Statement and Function Expression]]


There are several types of fuctions and a lot of jargons associated with them. 

### Function Statement aka Function Declaration

The traditional way of creating the function is known as a function statement. 

```js
function greet(name){
	console.log(`Hello ${name}`)
}
```

### Function Expression

When an anonymous function is stored inside a variable, it is called as a function expression.

```js
const greet = function(name){
	console.log(`Hello ${name}`)
}

greet();
```

##### Difference Between Function Statement and Function Expression

When hoisting, we cannot call the function expression before it's declaration. This is because variables get their value assigned in thread environment (while executing). 
On the other hand, we can call function statement before declaration. 
More detailed answere is [[👽 Hoisting in JS#Hoisting Arrow Functions and Function Expressions?]]

### Named Function Expression

In this type, function inside a function expression is not anonymous, rather its a function with a name.

```js
const greet = function sayHello(name){
	console.log(`Hello ${name}`)
	//✅ Valid
	sayHello(`${name} ${name}`);
}

greet();
//🚨 Invalid: Throws ReferanceError
sayHello();
```

We cannot call the named function with it's name, as it is inside a local scope. But, we can call the named function inside itself, for something like recursion.

### Anonymous Function

An anonymous function is a function without a name. We cannot just declare an anonymous function, because they need to be stored in some variable as we did in [[#Function Expression]]. 

```js
//🚨 Results out to be a syntax error
function (){
	console.log("Hello World!")
}
```

### First Class Function

When we use a function as any other variable, it is known as first class function. Using as a variable means
- **Passing as an argument**, 
- **Returning from a function**, 
- **Assigning it to a variable**

```js
//Passing as a argument
fun(function (){

});

//Returning a function
function fun(cb){
	cb();
	return function (){
	};
}
```

### Callback Functions

Callback function is a function which is passed as an argument to another function to be executed later in the code.  

```js
setTimeout(function(){
	console.log("Printed after 5 seconds!")
}, 5000);
```

Here we passed a callback function to `setTimeout`. It can also be a named function or pre-declared function.

