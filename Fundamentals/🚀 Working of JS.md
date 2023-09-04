
**Table of Contents**

- [[#Call Stack in JS]]
- [[#How is the code executed]]
	- [[#Creation of the execution context]]
- [[#Call Stack in JS]]

### What is JavaScript

JavaScript is a **Synchronous** and **Single Threaded** programming language.
- Synchronous: Code is executed sequentialy line by line
- Single Threaded: Only a single command can be run at a time

### How is the code executed

Everything is JS, is executed under **Execution Context**. It consists of two parts

|Variable Environment | Thread Environment| 
|------------ | ------------| 
|*var* x: 10 | Line 1| 
|*function* hello: {...} | Line 2|

**Variable Environment:** It contains all the variables and functions present inside the code
**Thread Environment:** Here the commands in the code are executed line by line such as logging, arithmatic operations, loops, function invokation etc.

##### Creation of the execution context

For every JavaScript file, a global execution context is created. The creation of this context happens in steps.

1. **Creation of Variable Environment**

This is the first phase, all the variables ie. var, let and const in the global scope (not in any block scope), are allocated memory. Also, they are initialized with *undefined*. 
Also, the functions (not the arrow functions), are allocated the memory and are initialized with the code inside the function itself. Which is the reason why we can invoke a function before the line where it is declared.

2. **Execution in Thread Environment**

This is the second phase of Execution Context. In this phase the following things takes place

- Initialize the variables with their original declared values in the code. ie. *undefined* is replaced by the actual value.
- Arithmatic operations are performed.
- Reassigning the variables.
- Loops, conditional statements, browser APIs etc.
- Function invocation

**Function Invocation and Execution Context**

Whenever a function is invoked, a new Exection Context is created inside the thread environment. All the local variables declared inside the function are allocated the memory in same way as Global Execution Context, but in the Function Execution Context. When the return statement is encountered, the value is returned (if any) and the FEC is removed and the control is handed over to the GEC again.

The picture below summarizes the GEC and FEC.

![[Working-1.png]]


### Call Stack in JS

The Execution Contexts, while executing are stored into a call stack. 
- First, GEC is pushed into the call stack. Whenever a function call is encountered the FEC is pushed into the stack. 
- At any given time, the EC at the top of the stack is currently executing. As soon as the function ends, the FEC is popped out. 
- Similarly when the global script ends, the GEC is also popped out of the stack.

![[Working-2.webp]]


> ⏭️ **Up Next:**  [[👽 Hoisting in JS]]
> 
>🔗 **Related:** 
>[[🔭 Scope Chaining and Lexical Environment]]



















