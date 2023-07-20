## 1. Write a JavaScript program that adds a new item to the list whenever a user inputs a text into the input field and clicks the button.
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Add Item to List</title>
  </head>
  <body>
    <input type="text" id="itemInput" placeholder="Enter item">
    <button id="addItemBtn">Add Item</button>
    <ul id="itemList">
    </ul>
    <script>
      const itemList = document.getElementById('itemList');
      const addItemBtn = document.getElementById('addItemBtn');

      addItemBtn.addEventListener('click', () => {
        const newItem = itemInput.value.trim();
        if (newItem !== '') {
          itemList.innerHTML += `<li>${newItem}</li>`;
          itemInput.value = '';
        }
      });

      itemInput.addEventListener('keypress', event => {
        if (event.key === 'Enter') {
          addItemBtn.click();
        }
      });
    </script>
  </body>
</html>
```
## 2. Write a JS function to change the font size,bg-color, and font-family for the paragraph in the HTML snippet below on clicking the button.
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset=utf-8 />
    <title>JS DOM paragraph styling</title>
  </head>
  <body>
    <p id ='text'>It is a long established fact that a reader
    will be distracted by the readable content of a page when
    looking at its layout. </p>
    <div>
    <button id="jsstyle"> Style </button>
    </div>
  </body>
</html>
```
```js
const styler = document.getElementById("text")
const btn = document.getElementById("jsstyle")

btn.addEventListener('click', () => {
  styler.setAttribute("style", `background-color: aqua; font-family: Arial; font-size: 20px`);
});
```
## 3. Write a JavaScript program that calculates the area of a rectangle when the user inputs the width and height into two input fields and clicks a button.
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Rectangle Area Calculator</title>
</head>
<body>
  <h1>Rectangle Area Calculator</h1>
  <label for="length">Length:</label>
  <input type="number" step="any" id="length" placeholder="Enter length">

  <label for="breadth">Breadth:</label>
  <input type="number" step="any" id="breadth" placeholder="Enter breadth">

  <button id="calculate">Calculate Area</button>

  <p id="output"></p>

  <script>
    const button = document.getElementById("calculate");
    const length_input = document.getElementById("length");
    const breadth_input = document.getElementById("breadth");
    const area = document.getElementById("output");

    let length = 0;
    let breadth = 0;

    button.addEventListener('click', function() {
      length = parseFloat(length_input.value);
      breadth = parseFloat(breadth_input.value);

      if (!isNaN(length) && !isNaN(breadth)) {
        const rectangleArea = length * breadth;
        area.textContent = "The area of rectangle is " + rectangleArea;
      } else {
        area.textContent = "Please enter valid numbers for length and breadth.";
      }
    });
  </script>
</body>
</html>
```
## 4. Write a JavaScript program that displays an alert message to the user when they submit a form.
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <h1>Form</h1>
    <label for="name">Name</label>
    <input type="text" id="name" placeholder="Enter name">
    <br>
    <button id="submit" onclick="alert()">Submit</button>
    <script>
    function alert(){
      alert("This a an alert box");
    }
    </script>
  </body>
</html>
```
## 5. Write a JavaScript program that displays an alert message to the user when they resize the browser window.
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
</head>
<body>
  <script>
   function showAlert(){
    alert("You are resizing the window");
   }
   window.addEventListener("resize", showAlert);
  </script>
</body>
</html>
```
## 6. Write a JavaScript program that uses AJAX to fetch and display data from a text file when the user clicks on a button.
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
  </head>
  <body>
    <button id="fetch">Fetch Data</button>
    <p id="data"></p>
    <script>
      const button = document.getElementById("fetch");
      const dataParagraph = document.getElementById("data");

      button.addEventListener("click", () => {
        const xhr = new XMLHttpRequest();
        xhr.open("GET", "assignment_5.md", true);
        xhr.onload = () => {
          if (xhr.status === 200) {
            dataParagraph.textContent = xhr.responseText;
          } else {
            dataParagraph.textContent = "Error fetching data";
          }
        };
        xhr.send();
      });
    </script>
  </body>
</html>
```
## 7. Write a JavaScript program that uses AJAX to fetch and display an image from an API when the user clicks on a button.
```html
<!DOCTYPE html>
<html>
<head>
  <title>Fetch Image from API</title>
</head>
<body>
  <button id="fetchImageBtn">Fetch Image</button>
  <div id="imageContainer"></div>

  <script src="script.js">
    function fetchImageFromAPI() {
      const imageContainer = document.getElementById('imageContainer');
      fetch('https://www.rd.com/wp-content/uploads/2020/04/GettyImages-471926619-scaled.jpg?resize=768,512') 
        .then(response => {
          if (!response.ok) {
            throw new Error('Network response was not ok');
          }
          return response.blob();
        })
        .then(blob => {
          const imageUrl = URL.createObjectURL(blob);
          const imageElement = document.createElement('img');
          imageElement.src = imageUrl;
          imageContainer.appendChild(imageElement);
        })
        .catch(error => {
          console.error('Error fetching image:', error.message);
        });
    }
    const fetchImageBtn = document.getElementById('fetchImageBtn');
    fetchImageBtn.addEventListener('click', fetchImageFromAPI);
  </script>
</body>
</html>
```