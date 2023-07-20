## 1. Define ‘Asynchronous programming’.
Asynchronous programming in JavaScript refers to a programming paradigm where code execution does not follow the typical sequential flow from top to bottom. Instead, it allows tasks to be executed independently, and the program continues to execute other tasks without waiting for the completion of the previous tasks. Asynchronous programming is essential for handling time-consuming operations, such as network requests, file system operations, and other tasks that may take some time to complete.

In JavaScript, asynchronous programming is commonly achieved using callbacks, promises, and async/await syntax, which provide mechanisms to handle asynchronous tasks in a more organized and readable way.

Callbacks: Callback functions are functions passed as arguments to other functions. They are called once the asynchronous task is completed, allowing the program to continue execution without waiting for the task's completion.

Promises: Promises are objects that represent the eventual completion or failure of an asynchronous operation and can be used to handle the results once they are available. They provide a more structured way to handle asynchronous tasks compared to callbacks.

Async/Await: Introduced in ES2017, async/await is a syntactical improvement for handling asynchronous code. It allows you to write asynchronous code in a more synchronous style, making it easier to read and maintain.

Asynchronous programming in JavaScript is vital for building responsive and efficient web applications, as it allows tasks to be executed in the background without blocking the main thread, ensuring that the user interface remains smooth and interactive.
## 2. What are callbacks? Give an example.
Callbacks are functions passed as arguments to another function, and they are used in asynchronous programming to handle the result of an asynchronous operation once it is completed. When an asynchronous task finishes executing, it calls the provided callback function to notify the caller about the result or completion status.

Here's a simple example of using a callback in JavaScript to perform an asynchronous operation:
```js
function fetchDataFromServer(callback) {
  setTimeout(() => {
    const data = { name: 'Yash', age: 22 };
    callback(data);
  }, 2000);
}
function processData(data) {
  console.log('Data received:', data);
}
fetchDataFromServer(processData);

console.log('Fetching data...');
```
## 3. What is a promise? What are its different states? Also write the methods which change a promise to their corresponding states.
In JavaScript, a Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a more structured and easier-to-read way of dealing with asynchronous code compared to traditional callbacks. They are especially useful for handling asynchronous tasks, such as fetching data from a server, reading files, or making API calls.

Promises have three possible states:

1. **Pending**: The initial state when the Promise is created and the asynchronous operation is still in progress. The Promise is neither fulfilled nor rejected.

2. **Fulfilled (Resolved)**: The Promise has successfully completed the asynchronous operation, and a result is available. The `then()` method is used to handle the fulfilled state.

3. **Rejected**: The Promise failed to complete the asynchronous operation, and an error is available. The `catch()` method is used to handle the rejected state.

Methods that change a Promise to their corresponding states:

1. **`resolve()`**: This method is used to change a Promise from the pending state to the fulfilled state. It is typically called when the asynchronous operation is successful and has a result to be returned.

2. **`reject()`**: This method is used to change a Promise from the pending state to the rejected state. It is called when the asynchronous operation encounters an error or fails.

Now, let's see how to create a Promise and change it to the fulfilled or rejected states using `resolve()` and `reject()`:

```javascript
// Example: Creating a Promise that resolves after a delay
const delay = (ms) => new Promise((resolve, reject) => {
  if (ms < 0) {
    reject(new Error('Delay time cannot be negative'));
  } else {
    setTimeout(() => {
      resolve(`Resolved after ${ms} milliseconds`);
    }, ms);
  }
});

// Using the created Promise
delay(2000) // Resolves after 2 seconds
  .then((result) => {
    console.log(result); // Output: Resolved after 2000 milliseconds
  })
  .catch((error) => {
    console.error(error.message);
  });

delay(-1000) // Rejects with an error
  .then((result) => {
    console.log(result); // This block will not be executed
  })
  .catch((error) => {
    console.error(error.message); // Output: Delay time cannot be negative
  });
```

In this example, the `delay()` function returns a Promise that resolves after the specified delay (in milliseconds). If the delay time is negative, the Promise is rejected with an error. We use `resolve()` to change the Promise to the fulfilled state and provide the result. On the other hand, we use `reject()` to change the Promise to the rejected state and provide an error when necessary. We handle the fulfilled state using the `then()` method and the rejected state using the `catch()` method.
## 4. Write a JS promise which resolves after 5s, with a value of “Hello Javascript”. Also, write code to print the length of this string after resolving.
```js
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Hello Javascript");
  }, 5000);
});

myPromise.then((resolvedValue) => {
  console.log("Length of the resolved string:", resolvedValue.length);
});
```
Output:
```js
Length of the resolved string: 16
```
## 5. What is ‘callback hell’ problem? How does the use of promises help in reducing this?
Callback hell, also known as the "pyramid of doom" or "callback spaghetti," is a common problem in asynchronous programming, especially when dealing with multiple nested callbacks. It arises when multiple asynchronous operations are dependent on each other or when sequential operations are required. As a result, the code becomes deeply nested and challenging to read and maintain.

The callback hell problem occurs due to the nature of asynchronous operations. In traditional callback-based asynchronous code, one operation initiates another operation, and so on. This nesting of callbacks makes the code structure complicated, difficult to follow, and error-prone. 

Each nested callback represents an additional level of indentation, making the code harder to read and maintain as the number of asynchronous operations increases.

Promises, on the other hand, provide a solution to the callback hell problem by introducing a more structured and sequential approach to handle asynchronous tasks. Promises allow us to chain multiple asynchronous operations together in a more elegant and readable way, without nesting callbacks.

## 6. What is the difference between Promise.all() and Promise.allSettled()? Give an example.
Both `Promise.all()` and `Promise.allSettled()` are methods in JavaScript that deal with multiple promises. However, they have different behaviors and outcomes:

1. `Promise.all()`:
- `Promise.all()` takes an array of promises as input and returns a single promise.
- It waits for all the promises in the input array to either resolve or reject.
- If all the promises resolve successfully, it returns an array of resolved values in the same order as the input promises.
- If any of the promises reject, the whole `Promise.all()` call is rejected, and it returns the rejection reason of the first promise that rejects.

2. `Promise.allSettled()`:
- `Promise.allSettled()` also takes an array of promises as input and returns a single promise.
- It waits for all the promises in the input array to settle (resolve or reject), regardless of their outcome.
- It returns an array of objects with a `status` property indicating whether the promise was fulfilled or rejected, and a `value` or `reason` property representing the resolved value or rejection reason, respectively.

Let's see an example to illustrate the differences:

```javascript
const promise1 = new Promise((resolve) => setTimeout(() => resolve("Resolved 1"), 1000));
const promise2 = new Promise((resolve, reject) => setTimeout(() => reject("Rejected 2"), 2000));
const promise3 = new Promise((resolve) => setTimeout(() => resolve("Resolved 3"), 1500));

// Example using Promise.all()
Promise.all([promise1, promise2, promise3])
  .then((results) => console.log("Promise.all - All resolved:", results))
  .catch((error) => console.error("Promise.all - Rejected:", error));

// Example using Promise.allSettled()
Promise.allSettled([promise1, promise2, promise3])
  .then((results) => console.log("Promise.allSettled - All settled:", results));
```

In this example, we have three promises (`promise1`, `promise2`, and `promise3`) that resolve or reject after different delays. Here's the output:

As you can see, with `Promise.all()`, the entire promise call is rejected as soon as the first promise (`promise2`) rejects, and the catch block is executed with the rejection reason of `promise2`.

On the other hand, `Promise.allSettled()` waits for all promises to either resolve or reject, and it returns an array with information about each promise's status and value/reason. In this case, it shows that `promise1` and `promise3` have been fulfilled, while `promise2` has been rejected.

## 7. Write a JS function that throws a SyntaxError if the value age (passed as parameter of the function) is greater than 80. The error message will be “You are too old.”
```javascript
function checkAge(age) {
  if (age > 80) {
    throw new SyntaxError("You are too old.");
  }
}

// Example usage
try {
  checkAge(85);
} catch (error) {
  console.error(error.message); // Output: "You are too old."
}

```

## 8. For this code, answer the following:
```js
const p1 = Promise.any([
    new Promise((resolve, reject) => setTimeout(() => reject(“Part 1 is rejected.”), 2000)),
    new Promise((resolve, reject) => setTimeout(() => resolve(“Part 2 is resolved.”), 5000)),
]);
p1.then((res) => console.log(res))
```
a. Write the output of this code. Briefly explain the reasoning.
```
Part 2 is resolved.
```

Explanation:
The `Promise.any()` method takes an array of promises as input and returns a new promise that is fulfilled when any of the input promises are fulfilled. It will be rejected only if all the input promises are rejected.

In the given code, `Promise.any()` is called with two promises. The first promise rejects after a delay of 2 seconds, and the second promise resolves after a delay of 5 seconds. Since `Promise.any()` fulfills when any of the promises fulfill, it will resolve as soon as the second promise resolves (Part 2). The rejection of the first promise (Part 1) does not affect the overall outcome.

b. What will be the output of this code if Promise.any() is replaced by Promise.race()? Is the output for this case generated faster or slower? Give reasons.
```
Part 1 is rejected.
```

Explanation:
The `Promise.race()` method takes an array of promises as input and returns a new promise that is fulfilled or rejected as soon as any of the input promises are fulfilled or rejected.

In this case, if we replace `Promise.any()` with `Promise.race()`, the output will be determined by the first promise that settles, either fulfills or rejects. Since the first promise to settle is the one that rejects after 2 seconds (Part 1), the `Promise.race()` will immediately be rejected with the rejection reason of Part 1.

The output for this case is generated faster when using `Promise.race()` because it resolves or rejects as soon as any of the input promises settles, whereas `Promise.any()` waits for at least one promise to fulfill. In this scenario, the rejection of Part 1 happens before Part 2 is resolved, so the output is generated faster.

## 9. Given is a code snippet
```js
const p = new Promise((resolve, reject) => {
resolve(“Part a”);
resolve(“Part b”);
})
p.then((res)=>console.log(res));
```
a. What will be the output of the above? Justify your answer.
```
Part a
```

Justification:
In a Promise constructor, once the `resolve()` or `reject()` method is called, the Promise is considered settled, and only the first call to `resolve()` or `reject()` takes effect. Any subsequent calls to `resolve()` or `reject()` after the first one are ignored.

In the given code snippet, the Promise `p` is created with a `resolve()` call twice in a row. However, only the first `resolve()` call is effective, and the Promise will be resolved with the value "Part a". The second `resolve()` call is ignored, and "Part b" will not be considered as the resolved value for the Promise.

b. What code should we write to get both the resolved results  

To get both resolved results, you can use an array to store the resolved values and then use `Promise.all()` to wait for all the promises to resolve. Here's how you can modify the code:

```javascript
const p = new Promise((resolve, reject) => {
  resolve("Part a");
  // resolve("Part b"); // Remove this line to avoid settling the Promise immediately.
});

p.then((res) => {
  console.log(res); // Output: "Part a"
  return "Part b"; // Return the second value to chain another .then() handler.
})
.then((res) => {
  console.log(res); // Output: "Part b"
})
.catch((error) => {
  console.error(error);
});
```

In this modified code, we remove the second `resolve("Part b")` line to avoid settling the Promise immediately. Instead, we use a single `then()` block to handle the first resolved value "Part a". We then return "Part b" in the first `then()` block to chain another `then()` handler. This way, we can handle the second resolved value "Part b" and print it to the console.

By chaining `then()` handlers, you can access multiple resolved values in the order they are resolved and perform further actions accordingly.

## 10. Using async / await syntax, and fetch(), make an API request to https://official-joke-api.appspot.com/random_joke and console the results. Also handle errors if any.
```javascript
async function fetchJoke() {
  try {
    const response = await fetch("https://official-joke-api.appspot.com/random_joke");
    if (!response.ok) {
      throw new Error("Network response was not ok.");
    }
    const data = await response.json();
    console.log("Joke:", data);
  } catch (error) {
    console.error("Error:", error.message);
  }
}
fetchJoke();
```