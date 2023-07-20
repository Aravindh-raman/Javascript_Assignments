## 1) Create a Class AlertBox.
AlertBox:  
Constructor:  
take 1 variable(applicationName) and store it as an instance variable.  
Methods:  
showAlertBox(message) which shows an alert dialog with the message In format “{applicationName}: {message}”.
```js
class AlertBox
{
  constructor(applicationName)
  {
    this.applicationName = applicationName;
  }

  showAlertBox(message)
  {
    alert(`${this.applicationName} : ${message}`);
  }
}
```
ii) Create a new instance of AlertBox and show a message.
```js
var obj = new AlertBox("Javascript")
obj.showAlertBox("DONE")
```
## 2) Create a new class SuccessMessage which extends AlertBox. Override the showAlertBox method.
SuccessMessage <- AlertBox  
showAlertBox(message) - shows alert messages in this format. “{applicationName}:  
Success: {message}”.  
Create a new instance of SuccessMessage and call the showAlertBox method.
```js
class AlertBox
{
  constructor(applicationName)
  {
    this.applicationName = applicationName;
  }
  showAlertBox(message)
  {
    alert(`${this.applicationName} : ${message}`);
  }
}
class SuccessMessage extends AlertBox
{
  showAlertBox(message)
  {
    alert(`Success: ${message}`);
  }
}
var obj = new SuccessMessage()
obj.showAlertBox("Success")
```
## 3) What is inheritance and prototypes? Can you achieve inheritance using prototypes? If yes, how? ( Give examples )
In JavaScript, inheritance is a mechanism that allows an object (subclass) to inherit properties and behaviors from another object (superclass). Prototypes are a crucial part of JavaScript's inheritance model. Each object in JavaScript has an internal property called the prototype, which can be thought of as a reference to another object. When you access a property or method on an object, and it doesn't exist in the object itself, JavaScript looks for that property or method in its prototype chain until it finds it or reaches the top of the chain (usually `Object.prototype`).

Yes, you can achieve inheritance using prototypes in JavaScript. You can create a prototype chain where an object inherits properties and methods from another object, forming a hierarchical relationship between objects. Here's an example of how to achieve inheritance using prototypes:

```javascript
// Superclass (Parent)
function Animal(name) {
  this.name = name;
}

Animal.prototype.sayHello = function() {
  console.log(`Hello, I'm ${this.name}`);
};

// Subclass (Child) inheriting from Animal
function Dog(name, breed) {
  Animal.call(this, name); // Call the Animal constructor to initialize shared properties
  this.breed = breed;
}

// Set up the prototype chain: Dog.prototype inherits from Animal.prototype
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // Reset the constructor to Dog

Dog.prototype.bark = function() {
  console.log('Woof! Woof!');
};

// Creating instances of Dog
const dog1 = new Dog('Buddy', 'Golden Retriever');
const dog2 = new Dog('Max', 'Labrador');

dog1.sayHello(); // Output: Hello, I'm Buddy
dog1.bark();     // Output: Woof! Woof!

dog2.sayHello(); // Output: Hello, I'm Max
dog2.bark();     // Output: Woof! Woof!
```

In this example, we have a superclass `Animal`, which has a method `sayHello`, and a subclass `Dog`, which inherits from `Animal`. We use the `Object.create()` method to set up the prototype chain, linking `Dog.prototype` to `Animal.prototype`. By doing this, instances of `Dog` can access the methods defined in `Animal`, and also have their own methods, such as `bark`.
