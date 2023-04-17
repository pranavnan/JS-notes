
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
