Question:- "this" keyword

Answer:-

In JavaScript, the this keyword refers to the current execution context, which can vary depending on how a function is called. Understanding the value of this is important for writing maintainable and reusable code, as it allows you to reference the appropriate object or context in different scenarios.

1.Global context
In the global context, this refers to the global object. In a web browser environment, this would be the window object.

code:-

```javascript
console.log(this); // logs the window object in a web browser environment
```

2.Function context
In the context of a function, the value of "this" can vary depending on how the function is called. If the function is called with no context, "this" will default to the global object. If the function is called on an object, "this" will refer to that object.

```javascript
function sayHello() {
  console.log(this);
}

sayHello(); // logs the window object in non strict mode else undefined

const person = {
  name: "John",
  sayName: function () {
    console.log(this.name);
  },
};

person.sayName(); // logs "John"
```

3.Object context
When a method is called on an object, this refers to the object itself. "this" is often used to access or modify properties of the object.

```javascript
const person = {
  name: "John",
  age: 30,
  sayHello: function () {
    console.log(
      `Hello, my name is ${this.name} and I am ${this.age} years old.`
    );
  },
};

person.sayHello(); // logs "Hello, my name is John and I am 30 years old."
```

4.Constructor context
When a function is used as a constructor to create new objects, "this" refers to the new object being created. This is often used to set initial values for properties of the new object.

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const john = new Person("John", 30);

console.log(john.name); // logs "John"
console.log(john.age); // logs 30
```

5.Event listener context
In an event listener, "this" refers to the element that triggered the event. This can be useful for accessing properties of the element or modifying its appearance.

```javascript
const button = document.querySelector("button");

button.addEventListener("click", function () {
  console.log(this); // logs the button element
  this.classList.add("clicked");
});
```

# "this" keyword in NON_STRICT mode

1. If this is used in a function that is called with no context, it will default to the global object (e.g. window in a web browser).

2. If this is used in a function that is called on an object, it will refer to that object.

3. If this is used in a function that is called as a constructor with the new keyword, it will refer to the new object being created.

4. If this is used in an event listener, it will refer to the element that triggered the event.

# "this" keyword in STRICT mode

1. If "this" is used in a function that is called with no context, it will be undefined instead of defaulting to the global object.

2. If "this" is used in a function that is called on an object, it will still refer to that object.

3. If "this" is used in a function that is called as a constructor with the new keyword, it will still refer to the new object being created.

4. If "this" is used in an event listener, it will still refer to the element that triggered the event.

```javascript
"use strict";

function Person(name) {
  this.name = name;
}

const john = Person("John"); // Throws an error in strict mode

console.log(name); // undefined in strict mode, "John" in non-strict mode
```

In this example, the Person function is called without the new keyword, so this defaults to the global object in non-strict mode. However, in strict mode, this is undefined, so the attempt to set the name property on it throws an error.

In general, using strict mode can help catch errors like this and make your code more predictable and maintainable.

# Tricky Example of "this" keywoard

```javascript
const obj = {
  fullName: "Pranav Nandane",
  greet() {
    console.log(this); // undefined in strict else window
    console.log(this.fullName); // TypeError: Cannot read properties of undefined (reading 'fullName') error in strict undefined in non-strict
  },
};

const { greet } = obj;
greet(); // this will point to undefined in strict mode else window obj
```

```javascript
const person = {
  name: "Alice",
  sayName: function () {
    console.log(`My name is ${this.name}.`);
  },
};

person.sayName(); // logs "My name is Alice."

const greet = person.sayName;
greet(); // logs "My name is undefined."
```

```javascript
const obj1 = {
  name: "Alice",
  greet: function () {
    console.log(`Hi, my name is ${this.name}.`);
  },
};

const obj2 = {
  name: "Bob",
};

obj1.greet(); // logs "Hi, my name is Alice."
obj1.greet.call(obj2); // logs "Hi, my name is Bob."
```

```javascript
function Dog(name) {
  this.name = name;
  this.bark = function () {
    console.log(`Woof! My name is ${this.name}.`);
  };
}

const fido = new Dog("Fido");
fido.bark(); // logs "Woof! My name is Fido."

const bark = fido.bark;
bark(); // logs "Woof! My name is undefined."
```

```html
<button id="my-button">Click me!</button>
```

```javascript
const button = document.querySelector("#my-button");
button.addEventListener("click", function () {
  console.log(`You clicked the ${this.textContent} button.`);
});
```

Inside the event listener function, the "this" keyword refers to the button element that triggered the event. This allows us to access properties of the button (like its "textContent" property) using this.

# Important Point

However, if we use an arrow function instead of a regular function for the event listener, the value of "this" changes. Arrow functions don't bind their own "this" value, so "this" inside the arrow function would refer to the value of "this" in the parent scope (which might not be what we want). So it's important to be aware of how the "this" keyword behaves when using different types of functions.

```javascript
const button = document.querySelector("#my-button");
button.addEventListener("click", () => {
  console.log(this); // Pointing to the window object
  console.log(`You clicked the ${this.textContent} button.`); // You clicked the undefined button.
});
```
