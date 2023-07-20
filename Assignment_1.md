## 1. Write a program that declares a variable using var, let, and const and prints the value to the console.
```javascript
var a="Hi";
const b=121;
let c=3.14;
console.log(a+" "+b+" "+c);
```
Output
```javascript
Hi 121 3.14
```
## 2. Write a program that reassigns a value to a variable declared with let and prints the new value to the console.
```javascript
let a=100;
a=500;
console.log(a);
```
Output
```javascript
500
```
## 3. Write a program that tries to reassign a value to a variable declared with const and prints the message to the console.
```javascript
const a=100;
a=500;
console.log(a);
```
Output
```javascript
ERROR!
/tmp/QdyGgZ2ySs.js:2
a=500;
 ^

TypeError: Assignment to constant variable.
    at Object.<anonymous> (/tmp/QdyGgZ2ySs.js:2:2)
    at Module._compile (node:internal/modules/cjs/loader:1256:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1310:10)
    at Module.load (node:internal/modules/cjs/loader:1119:32)
    at Module._load (node:internal/modules/cjs/loader:960:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:23:47
```
## 4. Write a program to declare a const, let, var variable within an if statement and try to access the variable outside the if block, what is the result?
var declaration:
```javascript
if(true)
{
  var a = 1
}
console.log(a)
```
Output:
```javascript
1
```
let declaration:
```javascript
if(true)
{
  let a = 1
}
console.log(a)
```
Output:
```javascript
ERROR!
/tmp/QdyGgZ2ySs.js:7
console.log(a)
            ^

ReferenceError: a is not defined
    at Object.<anonymous> (/tmp/QdyGgZ2ySs.js:7:13)
    at Module._compile (node:internal/modules/cjs/loader:1256:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1310:10)
    at Module.load (node:internal/modules/cjs/loader:1119:32)
    at Module._load (node:internal/modules/cjs/loader:960:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:23:47
```
const declaration:
```javascript
if(true)
{
  const a = 1
}
console.log(a)
```
Output:
```javascript
ERROR!
/tmp/QdyGgZ2ySs.js:7
console.log(a)
            ^

ReferenceError: a is not defined
    at Object.<anonymous> (/tmp/QdyGgZ2ySs.js:7:13)
    at Module._compile (node:internal/modules/cjs/loader:1256:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1310:10)
    at Module.load (node:internal/modules/cjs/loader:1119:32)
    at Module._load (node:internal/modules/cjs/loader:960:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:81:12)
    at node:internal/main/run_main_module:23:47
```
## 5. Write a program that concatenates two or more strings and prints the result to the console.
```javascript
let s1 = "Aravindh";
let s2 = "Raman";
let s3=s1+" "+s2;
console.log(s3);
```
Output:
```javascript
Aravindh Raman
```
## 6. Write a program that takes a string as input and prints the length of the string to the console.
```javascript
let s = "Hello";
console.log(s.length);
```
Output:
```javascript
5
```
## 7. Write a program that converts a string to uppercase and prints the result to the console.
```javascript
let s = "hello";
console.log(s.toUpperCase());
```
Output:
```javascript
HELLO
```