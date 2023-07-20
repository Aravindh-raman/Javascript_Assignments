## 1. If we execute this Javascript, what will the browser's console show? 
```javascript
var text = 'outside'; 
function logIt()
{
    console.log(text); 
    var text = 'inside'; 
}; 
logIt();
```
Output:
```javascript
undefined
```
## 2. Write a regular expression to reverse the first and last name.
```javascript
const name = 'Aravindh Raman';
const regex = name.replace(/(\w+)\s+(\w+)/, '$2 $1');

console.log(regex);
```
Output:
```javascript
Raman Aravindh
```
## 3. Write a Regular expression to validate email address
([^\s@]+@[^\s@]+\.[a-zA-Z]+)
## 4. Find the Output 
```javascript
var x = 100; 
console.log(x); 
function test(){ 
    var x = 250; 
    console.log(x); 
    if (x > 100) { 
        let x = 350; 
        console.log(x); 
    } 
    console.log(x); 
} 
test(); 
console.log(x);
```
Output:
```javascript
100
250
350
250
100
```
## 5. What is the difference of output between these two expressions? Give your reasons for it: 
### a. 12 == “12”
```true``` 
#### The == operator will compare for equality after doing any necessary type conversions.
### b. 12 === “12” 
```false``` 
#### "===" is a strict equality comparision operator so it comapres the two operands in the same data type only, hence the output is false.
### c. Number(12) === 12
```true``` 
### Since Number(12) and 12 is equal and in same data type it returns true.
## 6. What is NaN?
In JavaScript, NaN stands for "Not a Number." It is a special value that represents the result of an operation that is mathematically undefined or cannot be represented as a valid number.

NaN is typically returned as a result when performing arithmetic operations or mathematical functions that involve non-numeric values. For example:
```javascript
const result = 0 / 0;
console.log(result); // Output: NaN
```
