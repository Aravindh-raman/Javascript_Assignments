## 1. What is an IIFE (Immediately Invoked Function Expression) and why would you use it in JavaScript? Give an example of IIFE.
An IIFE (Immediately Invoked Function Expression) is a JavaScript design pattern where a function is defined and executed immediately after its creation. It involves wrapping a function expression inside parentheses and then immediately invoking it using an additional set of parentheses. This pattern allows you to create a private scope for variables and avoid polluting the global namespace.

Why use IIFE in JavaScript:

1. **Encapsulation**: IIFEs create a new scope, which helps avoid naming collisions and keeps variables and functions encapsulated, preventing them from affecting the global scope or interfering with other parts of the code.

2. **Module Pattern**: IIFEs are commonly used to implement the module pattern in JavaScript, where certain variables and functions are kept private, and only selected parts are exposed for interaction with the outside world.

3. **Avoid Global Pollution**: By using IIFEs, you can limit the number of variables and functions added to the global scope, making your code more maintainable and less likely to cause conflicts with other scripts or libraries.

Example of IIFE:

```javascript
(function () {
  const message = "Hello, I am inside an IIFE!";
  console.log(message);
})();
```

In this example, we have an anonymous function expression wrapped inside parentheses. The outer parentheses indicate that this is an expression, and the final set of parentheses `()` immediately invokes the function. As a result, the function is executed immediately, and you'll see the message "Hello, I am inside an IIFE!" printed in the console.

The variables declared inside the IIFE, such as `message` in this case, will not be accessible from outside the function due to the scope isolation provided by the IIFE. This helps prevent variable name collisions and provides a clean way to create private variables and functions in your code.
## 2. What is the purpose of using the bind() method in JavaScript and how is it different from call() and apply()?
The `bind()`, `call()`, and `apply()` are methods in JavaScript used to manage the execution context (the value of the `this` keyword) of a function. They are often used when you want to control the context in which a function is invoked. Each method serves a slightly different purpose:

1. **bind() method**:
The `bind()` method returns a new function with the specified context (`this` value) and partially applied arguments. It does not immediately invoke the function but allows you to create a new function that, when executed, will have the desired context. It is commonly used to ensure that a function always has a specific `this` value, regardless of how it is called.

Example of using `bind()`:

```javascript
const person = {
  name: 'John',
  greet: function() {
    console.log(`Hello, my name is ${this.name}`);
  },
};
const boundGreet = person.greet.bind(person); 
boundGreet(); // Output: Hello, my name is John
```

2. **call() method**:
The `call()` method is used to immediately invoke a function, explicitly specifying the context (`this` value) and passing arguments individually. Unlike `bind()`, `call()` executes the function right away.

Example of using `call()`:

```javascript
const person1 = { name: 'Alice' };
const person2 = { name: 'Bob' };

function greet() {
  console.log(`Hello, my name is ${this.name}`);
}
greet.call(person1); // Output: Hello, my name is Alice
greet.call(person2); // Output: Hello, my name is Bob
```

3. **apply() method**:
The `apply()` method is similar to `call()`, but it takes the context (`this` value) as the first argument and an array (or array-like object) of arguments to pass to the function. It is primarily used when the number of arguments is unknown or when you have an array of arguments that you want to pass to the function.

Example of using `apply()`:

```javascript
const person = { name: 'Grace' };
function greet(phrase1, phrase2) {
  console.log(`${phrase1}, my name is ${this.name}. ${phrase2}`);
}
const phrases = ['Hi', 'Nice to meet you'];
greet.apply(person, phrases); // Output: Hi, my name is Grace. Nice to meet you
```
## 3. What is a Higher-Order Function (HOF) in JavaScript and how is it different from regular functions? Explain with an example.
In JavaScript, a Higher-Order Function (HOF) is a function that takes one or more functions as arguments or returns a new function as its result. In other words, it treats functions as first-class citizens, allowing them to be manipulated and passed around just like any other values (e.g., numbers, strings, objects).

Regular functions, on the other hand, are functions that don't take other functions as arguments or return functions as their results. They are the typical functions we define to perform specific tasks.

Example of a Higher-Order Function:

```javascript
// Higher-Order Function: map()
function map(arr, callback) {
  const mappedArray = [];
  for (let i = 0; i < arr.length; i++) {
    mappedArray.push(callback(arr[i]));
  }
  return mappedArray;
}

// Regular function: multiplyByTwo
function multiplyByTwo(num) {
  return num * 2;
}

const numbers = [1, 2, 3, 4, 5];

// Using the map() higher-order function with the multiplyByTwo regular function as the callback
const result = map(numbers, multiplyByTwo);

console.log(result); // Output: [2, 4, 6, 8, 10]
```

In this example, `map()` is a higher-order function because it takes the `numbers` array and a callback function (`multiplyByTwo`) as arguments. The `map()` function then iterates over each element of the `numbers` array and applies the `multiplyByTwo` callback function to each element, creating a new array `[2, 4, 6, 8, 10]`.

The distinction between higher-order functions and regular functions is essential in functional programming paradigms, where functions are treated as first-class citizens, enabling powerful techniques such as function composition, currying, and more. Higher-order functions provide a flexible way to abstract and generalize logic, promoting code reusability and maintainability.

## 4. Write a function called multiplyBy that takes a number as input and returns a new function that multiplies any number passed into it by the original number.
```js
function multiplyBy(a)
{
  return function(b)
  {
    return a*b;
  }
}

const m_by2 = multiplyBy(2)
console.log(m_by2(5))
```
Output:
```js
10
```
## 5. Write a function named sortArray that takes in two parameters:                                                                                                                            1. An array of numbers                                                                                                                                                                           2. A boolean value ascending that indicates whether the array should be sorted in ascending or descending order.                                                                               The sortArray function should return the sorted array. Use an anonymous function to do the actual sorting, rather than using the built-in sort method.
```js
function sortArray(numbers, ascending)
{
  return ((arr) => 
  {
    var n = arr.length
    for(var i=0; i<n; i++)
    {
      for(var j=i+1; j<n; j++)
      {
        if((ascending && arr[j] < arr[i]) || (!ascending && arr[j] > arr[i]))
        {
          var temp = arr[j];
          arr[j] = arr[i]
          arr[i] = temp
        }
      }
    }
    return arr
  })(numbers)
}

var nums = [1,2,2,7,4,2]

console.log(sortArray(nums, true))
console.log(sortArray(nums, false))
```
Output:
```js
[ 1, 2, 2, 2, 4, 7 ]
[ 7, 4, 2, 2, 2, 1 ]
```