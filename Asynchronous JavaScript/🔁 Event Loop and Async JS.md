
**Table of Contents**

- [[#What is an Event Listener?]]
- [[#Event Listeners with Closure]]

### Synchronous vs Asynchronous Functions

Synchronous functions are executed immediately after they are invoked. Which means in the call stack until the function is executed completely, any other function or cannot be executed. This means if the function is taking too long, further code after the invocation cannot be executed. This is called blocking the main thread.

Asynchronous functions do not block the main thread. Instead, they return a promise and the code executes further. When the promise resolves, then the operations on the return value of the async function can be performed. 

### Example: Working of setTimeout

The `setTimeout` function accepts two arguments. One is a callback function and second number of milliseconds