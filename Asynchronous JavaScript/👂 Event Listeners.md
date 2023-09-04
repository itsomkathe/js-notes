
**Table of Contents**

- [[#What is an Event Listener?]]
- [[#Event Listeners with Closure]]

### What is an Event Listener?

Event listener is a special type of function, which takes two arguments, one being `event` and second a callback function. When that particular event occurs, the callback function is executed.

```js
document.getElementById("clickMe").addEventListener("click", function onClick(){
	console.log("Button Clicked");
});
```

When this script finishes, the button has an event listener attached. 

![[Event-1.PNG]]

### Event Listeners with Closure

If we want to log the count of how many times the button has been clicked, we can use one simple solution.

```js
let count = 0;

document.getElementById("clickMe").addEventListener("click", function onClick(){
	console.log("Button Clicked", ++count);
});

```

This would work, it's but not a good idea to add `count` as a global variable. So we can use closures to achieve this.

```js
function addEventListener(){
	let count = 0;
	
	document.getElementById("clickMe").addEventListener("click", function onClick(){
		console.log("Button Clicked", ++count);
	});
}

addEventListener();
```

![[Event-2.PNG]]

As expected, `onClick` function has a closure having a `count` variable. So on click, it increments that.

### Removing Event Listeners

As seen, event listeners also store the closures in the memory. Adding many of them will eventually make the website slow. So when not needed, remove the event listeners.

```js
function onClick(){
	console.log("Button Clicked");
};
document.getElementById("clickMe").addEventListener("click", onClick);
/*...*/
document.getElementById("clickMe").removeEventListener("click", onClick);
```

>⏭️ **Up Next:**  [[🔁 Event Loop and Async JS]]
