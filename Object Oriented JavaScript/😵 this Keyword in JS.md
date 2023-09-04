
**Table of Contents**

- [[#About this]]
- [[#this Inside Global Scope]]
- [[#this Inside an Object]]
- [[#this Inside a Function]]
	- [[#In Strict Mode]]
- [[#this Inside a Constructor Function]]
- [[#this Inside a Class]]

### About this

`this` keyword behaves very differently than in other languages. Also, `this` behaves differently where it is called ie. function, class, global scope etc. But the most generic definiton,

> `this` refers to an object that is executing the current piece of code.

But make sure to read further. This is not the complete definition.

### this Inside Global Scope

When `this` is used inside a global scope, `this` refers to the `window` object. Which means the properties attached to `this` are attached to `window` object. Code below demonstrates the example.

```js
this.name = "Om";

this.account = {
	name: "Om"
}

console.log(this.name);
console.log(window.account);
```

```
Om
{name: 'Om'}
```

![[This-1.PNG]]

### this Inside an Object

`this` inside an object refers to the object itself. This is the most commonly used example of `this` keyword.

```js
const person = {
    name: "Om",
    country: "India",
    getCountry(){
        console.log(`${this.name} is from ${this.country}`);
    }
}
person.getCountry();
```

```
Om is from India
```

### this Inside a Function

When `this` is called inside a function, and function is **NOT** in an object, `this` refers to the `window` object.

```js
function fun(){
    this.apple = "Apple"
    function print(){
        console.log(`Printed: ${this.apple}`)
    }
    print();
}

fun();
```

```
Printed: Apple
```

The function can be at any level, like the above `print` function is inside `fun`. `this` still points to the `window` object.

![[This-3.PNG]]

##### In Strict Mode

If calling `this` inside a function using strict mode, it would throw an error. 

```
Uncaught TypeError: Cannot set properties of undefined (setting 'apple')
    at fun (code.js:4:16)
    at code.js:11:1
```

The solution for this, is to use `call` method.
In the above error, `this` inside a function says `undefined`. So we will pass the `this` in `call` method's arguments.

```js
'use strict'

function fun() {
    this.apple = 'Apple';
    function print() {
        console.log(`Printed: ${this.apple}`);
    }
    print.call(this);
}

fun.call(this);
```

```
Printed: Apple
```

In the debugger, now the `this` inside the function points to the `window` object.

![[This-6.PNG]]

### this Inside a Constructor Function

Constructor functions return object and they need to be used with a `new` keyword. 

```js
function Person(name, age){
    this.name = name;
    this.age = age;
    this.getAge = function(){
        console.log(this.age);
    }
}

const John = new Person("John Doe", 20);
John.getAge();
```

```
20
```

In constructor function (when used with a `new` keyword), `this` refers to the object which the function is returning.

![[This-4.PNG]]

### this Inside a Class

In class, `this` behaves the same as constructor function, because class also needs a constructor to initialize an object. So, `this` refers to the object.

```js
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    
    getAge(){
        console.log(`Age of ${this.name} is ${this.age}`);
    }
}
const John = new Person("Jack", 30);
John.getAge();
```

```
Age of Jack is 30
```



>⏭️ **Up Next:**  [[📞 call, ✉️ apply, 🔗bind!]]
> 
>🔗 **Related:** 
>[[👀 window Object]]
