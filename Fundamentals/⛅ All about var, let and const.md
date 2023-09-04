
**Table of Contents**

- [[#About var]]
- [[#About let]]
- [[#About const]]

### About var

`var` was the first data type  in JavaScript. 

##### Properties of `var`:

- Whenever `var` is created, it is assigned to the `global` object of that execution context.
- If declared in blocks like conditional statements, loop or block, it can be accessed outside of the block.
- If declared within function it is not accessible outside of the function, because it is store inside the FEC.
- It can be redeclarea and reassigned.

### About let

`let` is one of the data type in JavaScript introduced in ES6. 

##### Properties of `let`:

- It is block scoped and is not attached to the `global` object.
- It cannot be accessed ouside the block.
- It cannot be reinitialized
- It can be reassigned.
- It can be declared and get its value assigned later.

### About const

`const` is one of the data type in JavaScript introduced in ES6. It is the strictest among three.

##### Properties of `const`:

- It is block scoped and is not attached to the `global` object.
- It cannot be accessed ouside the block.
- It can neither be reinitialized nor be reassigned
- It should be initialized at the time of declaration.


### Hoisting let and const?

`let` and `const` are also hoisted, but not the way `var` does it. The code below tries to access the `let` type before initializing it. 

```js
console.log(a);
let a = 5;
```

```
Uncaught ReferenceError: Cannot access 'a' before initialization
```

This error statement, shows that `a` cannot be accessed. Which means `a` has been allocated the memory. Let's se in the debugger

![[LetConst-1.PNG]]

As said, `a` has been given memory and it is initialized as `undefined`. But it is stored in the `script` object and not in `global`. 

>`let` and `const` are stored in the `script` object and not in `global`.
> The variables in `script` cannot be accessed before they are initialized. 

##### Temporal Dead Zone

The time between, memory allocation and initialization of `let` and `const` is known as Temporal Dead Zone. 
In short, lines before the declaration of `let` and `const` come under this zone. 

>⏭️ **Up Next:**  [[🧊 Block Scope and Shadowing in JS]]
