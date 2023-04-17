
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
