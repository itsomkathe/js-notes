
**Table of Contents**

-  [[#What is a Block in JS]]
- [[#Block Scope]]
- [[#Block Shadowing]]
	- [[#Illegal Block Shadowing]]
	- [[#Block Shadowing in Functions?]]

### What is a Block in JS

Block is a group of statements combined, which is used where JavaScript expects one statement. For example, conditional statements, loops, functions expect some statement after them. So instead of writing all statements on one line, a block is used to combine the statements.
A block is defined by curly brackets

```js
{...} //A plain block

if(true){...} //Block used with if statement
```

### Block Scope

Block scope is, the variables which can be accessed inside a block. 
See the code below

```js
{
    var a = 10;
    let b = 15;
    const c = 20;
    
    console.log(`a inside: ${a}`);
    console.log(`b inside: ${b}`);
    console.log(`c inside: ${c}`);
}

console.log(`a Outside: ${a}`);
console.log(`b Outside: ${b}`);
console.log(`c Outside: ${c}`);
```

```
a inside: 10
b inside: 15
c inside: 20

a Outside: 10
Uncaught ReferenceError: b is not defined
```

As we can see, `let` and `const` cannot be accessed outside of the block. Because they are block scoped.

![[Block-1.PNG]]

In the variable space, `let` and `const` variables are not stored in the `global` object, but in a `block` object. As soon as the block ends, `block` scope is no longer available.
Contrary to this, `var` is stored `global` object. Which is why `var` is accessible outside the block.

### Block Shadowing

When same variables with same data type are inside and outside the block, it is called as block shadowing. See the code below

```js
var a = 100;
let b = 150;
const c = 200;

{
    var a = 10;
    let b = 15;
    const c = 20;
}

console.log(`a Outside: ${a}`);
console.log(`b Outside: ${b}`);
console.log(`c Outside: ${c}`);
```

```
a Outside: 10
b Outside: 150
c Outside: 200
```

See when we log ouside of the block, how `var` has been updated but `let` and `const` are not.
When the execution of block starts, see the debugger

![[Block-2.PNG]]

`b` and `c` in the block are defined in a seperate `block` scope and `a` is defined in the `global` scope only.
So when the block executes, `a` is updated in `global` and `b` and `c` are updated in the block scope.
As the execution of block ends,

![[Block-3.PNG]]

the `block` scope has been removed and the initial `b` and `c` are present in `script` scope, which remained untouched! That is the reason the output is like this.

##### Illegal Block Shadowing

If we declare `var` (which is having greater scope) and with the same name declare `let` or `const`, it is not allowed and straight up throw a syntax error.

```js
let a = 10;
{
    var a = 50;
}
```

```
Uncaught SyntaxError: Identifier 'a' has already been declared
```

This is because, `a` will be in both `script` and `block` scope which is not allowed.

But vice-versa will not throw an error. ie.

```js
var a = 10;
{
    let a = 50;
}
```

```js
let a = 10;
{
    let a = 50;
}
```

This is completely valid code. Because `var` is in `global` scope and `let` is in `block` scope.

In the second case, first `a` is in `script` scope and second `a` is in `block` scope.


##### Block Shadowing in Functions?

When a function is created, a seperate FEC is created. All the local variables including `var` are stored in this FEC only. So redeclaring any value won't update any value in it's parent's scope. 

>⏭️ **Up Next:**  [[🔒 Closures Demystified]]
> 
>🔗 **Related:** 
>[[👀 window Object]]