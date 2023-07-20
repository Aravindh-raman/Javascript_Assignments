## 1. What is the difference in hoisting behaviour between a function created using function declaration syntax and that created using a function expression syntax? Give an example.
The main difference in hoisting behavior between a function created using function declaration syntax and one created using a function expression syntax lies in when they are accessible in the code.

### Function Declaration Syntax:

With function declaration syntax, the entire function is hoisted to the top of its scope. This means that you can call the function before its actual declaration in the code.

```javascript
// Function declaration
hoistedFunction();

function hoistedFunction() {
  console.log("This is a hoisted function.");
}
```
### Function Expression Syntax:
With function expression syntax, only the variable declaration is hoisted to the top of its scope, not the function itself. Therefore, if you try to call the function before the actual assignment, you'll get an error because the function is not yet defined.
```javascript
// Function expression
// Trying to call the function before the assignment (will result in an error)
notHoistedFunction(); // Error: notHoistedFunction is not a function

var notHoistedFunction = function() {
  console.log("This is not a hoisted function.");
};
```
In the second example, although the variable `notHoistedFunction` is hoisted, it is still `undefined` at the point of calling it, leading to the error. To avoid this, you should call the function after the function expression assignment.
```javascript
var notHoistedFunction = function() {
  console.log("This is not a hoisted function.");
};

// Now, the function can be called without any errors
notHoistedFunction(); // Output: "This is not a hoisted function."
```
the key distinction is that function declarations are hoisted entirely, allowing them to be called before their actual definition, while function expressions are not fully hoisted, and trying to call them before assignment results in an error.
## 2. Write the usage of following functions / operators and give an example.
### a. Date.now()
`Date.now()` is a static method of the `Date` object that returns the current timestamp in milliseconds since the Unix Epoch (January 1, 1970, 00:00:00 UTC). It provides a quick and simple way to get the current time in milliseconds, which is often used for measuring performance, calculating time differences, or setting timestamps for various operations.

Usage of `Date.now()`:
```javascript
const currentTime = Date.now();
console.log(currentTime); // Output: Current timestamp in milliseconds (e.g., 1626636691648)
```
### b. ?? (nullish coalescing operator)
The `??` (nullish coalescing operator) is a JavaScript operator used to provide a default value when dealing with null or undefined values. It allows you to choose the right-hand side value if the left-hand side value is null or undefined.

Usage of `??`:
```javascript
const result = value1 ?? value2;
```
In the above example, if `value1` is null or undefined, the `result` will be assigned the value of `value2`. However, if `value1` is not null or undefined, `result` will be assigned the value of `value1`.
### c. ?. (optional chaining operator)
The `?.` (optional chaining operator) is a JavaScript feature that allows you to safely access properties or call methods on nested objects without causing an error if any of the intermediate properties are null or undefined. It provides a concise way to handle optional properties and method calls, avoiding the need for excessive null checks.

Usage of `?.`:
```javascript
const value = object?.property?.nestedProperty;
```
In the above example, if any of the properties (`property` or `nestedProperty`) is null or undefined, the `value` will be set to undefined. The code won't throw an error, making it safer to access nested properties.
## 3. Write 2 JS statements, where:
### a. 1st one will split the words of the sentence "I love going walkies" into an array.
```javascript
let s="I love going walkies";
let arr=s.split(' ');
console.log(arr);
```
Output:
```javascript
[ 'I', 'love', 'going', 'walkies' ]
```
### b. 2nd one will assign the elements of the resultant array into 4 variables (in a single statement).
```javascript
const[a,b,c,d]=arr;
console.log(a+' '+b+' '+c+' '+d);
```
Output:
```javascript
I love going walkies
```
## << Given object for Questions 4, 5 (and possibly 6)>>
```javascript
const myObject = {
    x1: "Samba",
    x2: {
        x3: {
            x4: {},
            x5: "Rails",
        },
        x6: {
            x7: -1,
            x8: [25, 8, 4, 10]
        },
    }
};
```
## 4. For the given object, write a single line destructuring assignment to get these values:
### a. x3 (store result in variable name y)
```javascript
const y=myObject.x2.x3;
console.log(y);
```
Output:
```javascript
{ x4: {}, x5: 'Rails' }
```
### b. 2nd element of x8 (use any variable name for result)
```javascript
const a=myObject.x2.x6.x8[1];
console.log(a);
```
Output:
```javascript
8
```
## 5. Write JS code to create another object (named newObject), which contains all attributes from the given objects, and the following key value pairs:
### a. Key: x20 Value: “Shinko”
### b. Key: x21 Value: [5, 40, 73, 19]
```javascript
const myObject = {
  x1: "Samba",
  x2: {
    x3: {
      x4: {},
      x5: "Rails",
    },
    x6: {
      x7: -1,
      x8: [25, 8, 4, 10],
    },
  },
};

const newObject = {
  ...myObject,
  x20: "Shinko",
  x21: [5, 40, 73, 19],
};
console.log(newObject);
```
## 6. Create a new array newArray , which combines elements from arrays stored inside attributes x8 and x21 of the object created in Q5.
```javascript
const myObject = {
  x1: "Samba",
  x2: {
    x3: {
      x4: {},
      x5: "Rails",
    },
    x6: {
      x7: -1,
      x8: [25, 8, 4, 10],
    },
  },
};

const newObject = {
  ...myObject,
  x20: "Shinko",
  x21: [5, 40, 73, 19],
};
const newArray = newObject.x2.x6.x8.concat(newObject.x21);
console.log(newArray);
```
## 7. For the given JS program:
```js
let aRandomNum = 37;
function f1(num) {
console.log(num * 3);
}
function f2() {
aRandomNum *= 3;
console.log(aRandomNum);
}
f1(aRandomNum);
f2();
f1(aRandomNum);
```
### a. Out of the 2 functions f1 and f2, which one is pure and which one is impure? Give reasons for the conclusion.
f1 is a pure function because its output depends solely on its input parameter and it has no side effects. f2 is an impure function because it modifies external state (the global variable aRandomNum).
### b. What will be the output of the program (the 3 output values)?
```js
111 
111 
333 
```
## 8. In case of arrow functions, in which case the parenthesis for function parameters can be omitted? Give an example.
In arrow functions, the parentheses for function parameters can be omitted when there is exactly one parameter. If there are zero or multiple parameters, the parentheses should be used. This is a syntactical shorthand that allows for more concise function definitions.

Example with one parameter (parentheses omitted):

```javascript
// Arrow function with one parameter, parentheses omitted
const square = num => num * num;

console.log(square(5)); // Output: 25
```

Example with multiple parameters (parentheses required):

```javascript
// Arrow function with multiple parameters, parentheses required
const addNumbers = (num1, num2) => num1 + num2;

console.log(addNumbers(3, 7)); // Output: 10
```

Example with zero parameters (parentheses required):

```javascript
// Arrow function with zero parameters, parentheses required
const getRandomNumber = () => Math.random();

console.log(getRandomNumber()); // Output: a random number between 0 and 1
```
## 9. Can arrow functions be used as object methods? Why or why not?
Arrow functions can not be used as object methods. This is because arrow functions do not have their own this binding. The this binding in an arrow function is the same as the this binding in the enclosing lexical scope. In the case of an object method, the this binding should be the object itself. For example
```js
const myObject = {
    value:"I am value",
  firstMethod: () => {
    console.log(this.value);
  },
  secondMethod () {
    console.log(this.value);
  },
};
console.log(myObject.firstMethod()); // I am value
console.log(myObject.secondMethod()); // undefined
```
