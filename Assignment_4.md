## 1. Given a string “Azad Ram Madiha Yash”. Return a string with the first letter of every word from the string. (Use built in methods).
```js
var a = "Azad Ram Madiha Yash"
var arr = a.split(" ")
for(var k of arr)
{
  console.log(k[0] + " ")
}
```
Output:
```js
A 
R 
M 
Y 
```
## 2. Given an array [1, -4, 12, 0, -3, 29, -150]. Calculate the sum of all positive numbers (use built in array methods).
```js
var arr = [1, -4, 12, 0, -3, 29, -150]
var ans = arr.reduce((a, b)=>{
  if(b > 0) a += b  
  return a
})

console.log(ans)
```
Output:
```js
42
```
## 3. Given an array [1, 2, 3, 4, 5]. Create a new array with the square of each element(use built in array methods).
```js
var arr = [1, 2, 3, 4, 5]
var res = arr.map(i => i*i)
console.log(res)
```
Output:
```js
[ 1, 4, 9, 16, 25 ]
```
## 4. Given an array [{ id: 2100, name: 'President Jacqueline' }, { id: 2114, name: 'Vice-president James' }, { id: 3016, name: 'House-captain Otis' }, { id: 4818, name: 'Prefect Finneas' }]. Create an array containing just the id of every individual. (write two solution one using iterator and another using built-in method
Solution using iterator (for loop):
```js
const arr = [
  { id: 2100, name: 'President Jacqueline' },
  { id: 2114, name: 'Vice-president James' },
  { id: 3016, name: 'House-captain Otis' },
  { id: 4818, name: 'Prefect Finneas' },
];
const idarr = [];
for (const i of arr) {
  idarr.push(i.id);
}
console.log(idarr);
```
Output:
```js
[2100, 2114, 3016, 4818]
```
Solution using built-in map method:
```js
const arr = [
  { id: 2100, name: 'President Jacqueline' },
  { id: 2114, name: 'Vice-president James' },
  { id: 3016, name: 'House-captain Otis' },
  { id: 4818, name: 'Prefect Finneas' },
];
const idarr = arr.map(i => i.id);
console.log(idarr);
```
Output:
```js
[2100, 2114, 3016, 4818]
```