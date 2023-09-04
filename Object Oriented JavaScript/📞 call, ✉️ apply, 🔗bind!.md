
**Table of Contents**

-  [[#call Method]]
- [[#apply Method]]
- [[#bind Method]]

### call Method

Say we have an object having a function. Another second object wants to use this method but it does not have it. So we use call to achieve this. 

```js
const person1 = {
    firstName: "Om",
    lastName: "Kathe",
    printFullName: function (){
        console.log(`${this.firstName} ${this.lastName}`);
    }
}

const person2 = {
    firstName: "John",
    lastName: "Doe"
}

//this of printFullName will point to person2
person1.printFullName.call(person2);
```

```
John Doe
```

As we can see, it calls the method on `person2` successfully. 
`call` function applied on a function means that, the `this` keyword in that function points to the object which is passed to `call` method.

![[Call-1.PNG]]

`call` can be in global scope also. In this case by default `this` of the function will be pointing to `window` object. After passing object in the `call`, `this` will be pointing to the object.

```js
const person1 = {
    firstName: "Om",
    lastName: "Kathe",
}

function printFullName(city){
    console.log(`${this.firstName} ${this.lastName} from ${city}`);
}

printFullName.call(person1, "Nashik");
```

### apply Method

`apply` method does exactly what `call` does. The difference is that, it takes argument inside an array unlike 
`call` which takes arguments seperately.

```js
function printFullName(city, state){
    console.log(`${this.firstName} ${this.lastName} from ${city}, ${state}`);
}

printFullName.call(person1, ["Nashik", "Maharashtra"]);
```

### bind Method

`bind` method takes an object and returns a method who's `this` points to the object. We need to explicitly call the returned method.

```js
const person1 = {
    firstName: "Om",
    lastName: "Kathe",
}

function printFullName(city){
    console.log(`${this.firstName} ${this.lastName} from ${city}`);
}

//printMyName's this would point to person1
const printMyName =  printFullName.bind(person1, "Nashik");
printMyName();
```

Bind takes the arguments same as `call` takes.


