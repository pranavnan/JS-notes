
# Scope

Scope is a certain region of a program where a defined variable exist

# Variable Shadowing
## Example 1: its legal
```javascript
function hello() {
  let a = 10;

  if (true) {
    let a = 20;
    console.log(a)
  }

  console.log(a)
}

hello();
```
## Example 2: its legal
```javascript
function hello() {
  var a = 10;

  if (true) {
    let a = 20;
    console.log(a)
  }

  console.log(a)
}

hello();
```
## Example 3: its illegal

```javascript
function hello() {
  let a = 10;

  if (true) {
    var a = 20;
    console.log(a)
  }

  console.log(a)
}

hello();
```

we get an error on above code :- Cannot assign to read only property 'message' of object 'SyntaxError: /src/index.js: Identifier 'a' has already been declared. (5:8)

# execution context

Execution contacts have two phases, creation, phase and execution phase.
During creation phase, JavaScript, engine moves our variables, and function declaration to the top of their scope, this is know as hoisting

# TDZ

Temporal Dead Zone. In JavaScript, TDZ is a period between the creation of a variable and its initialization, 

# Currying 
Currying is a function that takes one argument at a time and returns a new function expecting the next argument.
Basically Currying doesn’t call a function. It just transforms a function. They are constructed by chaining closures by immediately returning their inner functions simultaneously.

# Lexical scope
Lexical scope in JavaScript refers to the ability of a function to access variables and parameters that are declared outside of its own scope. In other words, a function can access variables that are in its outer scope, but not vice versa.

A scope refers to the current context of our code it can be either globally or locally defined.
A lexical scope in JavaScript means that a variable defined outside function can be accessible inside of another function define after variable declaration

```javascript
let count = 0;
(function f() {
  if (count === 0) {
    var count = 1;
    console.log(count);
  }
  console.log(count);
})();
```
output=> undefined
This is because of variable hoisting in JavaScript. When the function f is called, the variable count is declared with the keyword var, which means that its declaration is hoisted to the top of the function scope. However, the assignment of the value 1 to count is not hoisted, so at the time the if condition is evaluated, the value of count is undefined.

Therefore, the output of the first console.log statement is undefined, and the output of the second console.log statement is also undefined, because count has not been assigned any value in the function scope.

