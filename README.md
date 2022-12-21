# Jelani's Notes

## Summary

This repository contains all of the notes taken by [Jelani](https://github.com/PlumScum) for the Lighthouse Labse Web Development Bootcamp.

## Table of Contents

* [Week 1](/Week_1/)
  * [Day 1](/Week_1/Day_1/)
  * [Day 3](/Week_1/Day_3/)

## Notes

### Module01 Week01 Day01- Dev Workflow

#### Git

GIT is a Version Control System (VCS) that lets us keep track of changes to our projects and collaborate with others on the work. Essentially, GIT acts as a check point save system for our files.

Git has four stages

1) git init - Initializes git in the folder of a brand new project. This lets git watch for file changes, add, and remove files.

2) untracked - a file is in your folder that's been modified but git is informing you, though ignoring it for now.

3) staged - Git has been used to add the file to the next commit. Staged files are in the commit index or staging area.

4) commited - the file is under version control

!! COMMIT AS OFTEN AS POSSIBLE!!


#### The Workflow:

gitclone/git init --> Work, Work, Work, Work, Work _>> git status (to see what files we worked on) --> git add . (to stage all files) --> git commit --> git push (so the work goes into Github)


#### How to Tackle a Problem

1) Understand what the question is asking - Break the problem down into a series of smaller (and easier to understand) steps.

2) Research the Unknowns - Small segments of code lets us easily see where errors and bugs are in our code.

3) Code incrementally! - Write, then execute the small amounts of code.

Don't Code Golf (attempt to do as much as possible with as few lines as possible). We're beginners and it's easy to lose sight of things we do, only to turn around and not recall what we've developed a program to do. No bueno.



```javascript 
const array = [1,2,3,4,5,6,7]

const addNumbers = (pineAppleArray) =>
  pineAppleArray.reduce(
    (acc, currValue) =>
      Number.isInteger(Number(currValue))
        ? Number(currValue) + Number(acc)
        : acc,
    0
  );

const fancyTotalSum = addNumbers(arguments);
```


Watch out for Logic-Syntax-Data (LSD) -
Logic: Have I told the computer exactly what to do?
Syntax: Am I missing a brace or bracket?
Data: Do I have the data I think I do in the format I expect?

Ask for Help - 
Google the error message or what you want to accomplish.
StackOverflow for multiple solutions to a problem.
Mozilla Developer Network (MDN)



### Module01 Week01 Day03 - Objects in JS


* JavaScript has 7 primitive types:
  * Boolean
  * Null
  * Undefined
  * Number
  * BigInt
  * String
  * Symbol

```javascript
const bool = false;
const nul = null;
const undef = undefined;
const num = 5;
const bigint = 9007199254740991n;
const str = 'This is a string';
const sym = Symbol('symbol');
```

* Primitive types are immutable; this means that they cannot be modified after they are created

```javascript
const myString = 'hello world';
const secondString = myString.replace('hello', 'goodbye'); // doesn't change myString
console.log(myString); // 'hello world'
```

### Objects!

   * Objects are data structures that allow us to store related data and functionality together
   * Objects are made up of key/value pairs
   * The key in an object is always a string
   * The value can be any valid JavaScript value (primitive, array, object, or function)
   * In arrays, you use the index to access a value:


```javascript
const arr = [1, 2, 3];
console.log(arr[1]); // 2
```

 * With objects, you use the key to access the value:

```javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum'
};

// we have two options for accessing values
// dot syntax
console.log(myObj.firstName); // Lorem

// square bracket syntax
console.log(myObj['lastName']); // Ipsum
```


  *  If you know the name of the property, use dot notation
  *  If the name of the property is dynamic (eg. stored in a variable), use square bracket syntax


### Passing Values to Functions

  *  Primitive types are passed to functions by value. This means that a copy is made and used by the function. The original value is unchanged.


```javascript
  const name = 'Murray';
const changeName = function (name) {
  name = 'Jane';
  console.log(name); // Jane
};

changeName(name);
console.log(name); // Murray
```
* Objects are passed to functions by reference. This means that the internal values of the object can be changed by the function, but the object itself cannot be reassigned.

```javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum'
};

const changeKey = function (obj) {
  obj.firstName = 'Jane'; // this does change the value of the firstName key
}

changeKey(myObj);
console.log(myObj.firstName); // Jane

const replaceObj = function (obj) {
  obj = {}; // this won't work
}

replaceObj(myObj);
console.log(myObj); // { firstName: 'Jane', lastName: 'Ipsum' }
```

### Functions Inside Objects

  *  Since objects are key/value pairs, and functions are values, we can store functions inside of an object

```javascript
const myObj = {
  firstName: 'Lorem',
  sayHello: function () {
    console.log('hello');
  }
};

myObj.sayHello(); // hello
console.log(myObj); // { firstName: 'Lorem', sayHello: [Function: sayHello] }
```

* We can make reference to the other properties in an object by using this to refer to the object itself


```javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum',
  sayFullName: function () {
    console.log(`My full name is ${this.firstName} ${this.lastName}`);
  }
};

myObj.sayFullName(); // My full name is Lorem Ipsum
```

* A function inside an object is often referred to as a `method`

### Object iteration with for..in

 *  JavaScript gives us an easy way to iterate through an object's keys: the for..in loop
 *  NOTE: We cannot use for..of to iterate through an object; it will result in an error

```javascript
const obj = { a: 1, b: 2, c: 3 };

for (const key in obj) {
  // we can use the key to access the value
  const value = obj[key];
}
```

Class Examples

```js
console.log('Hi! 👋');

// DATA TYPES
// Primitive / Inmutable values
const string = 'Hello!';
const number = 10;
const boolean = true;
const undef = undefined;
const nul = null;

// Mutable values
const array = [1, 2, 4];
const objects = { color: 'blue' };

// OBJECTS
// object = { key: value }
const user = {
  firstName: 'Pedro',
  lastName: 'González'
};

// dot notation
console.log('dot notation', user.firstName);

// bracket notation
console.log('brackets notation', user['firstName']);

const lastName = 'firstName';
console.log('29', user.lastName);
console.log('30', user[lastName]);

// arrays: we access to its values by a position index
const numbersArray = [1, 2, 3, 4];
console.log(numbersArray[1]); //2

// bonus! adding extra items to an array by its position with brackets notation
numbersArray[100] = 'im at position 100!';
numbersArray[50] = [1, 2, 3];
console.log(numbersArray.length);
console.log(numbersArray);

// objects: we access to its values by a key property
const numbersObject = { 1: 10, 2: 20, 3: 30 };

//accesing nested objects in an object
const mixObject = {
  1: 10,
  2: 20,
  3: 30,
  4: 40,
  myKey: 'red',
  otherKey: 30,
  100: {
    details: {
      color: 'red',
      name: 'Ferrari'
    }
  }
};

// we cannot use dot notation for numbers as keys
console.log(mixObject[1]);
console.log(mixObject['myKey']);

// we can use a mix of dot notation or brackets to access nested objects
console.log(mixObject[100]['details']['name']);
console.log(mixObject[100].details.name);

// bonus! adding extra key/value pairs by using dot or brackets notation
mixObject.title = 'My amazing title!';
mixObject['description'] = 'This is my awesome and super cool title!';

mixObject[100].details.engine = 'V12';

console.log(mixObject);

// PASSING OBJECTS AS ARGUMENTS IN FUNCTIONS
const carObject = {
  name: 'Ferrari',
  color: 'red'
};
console.log(carObject);

// Mutating an internal property
const paintCar = function(car) {
  car.color = 'blue';
};
paintCar(carObject);
console.log(carObject);

// Reassigning a full object
const changeCar = function(car) {
  car = {};
  console.log('inside changeCar!', car);
  return car;
};

changeCar(carObject);
console.log(carObject);

// adding extra properties within the object
const addSpeakers = function(car) {
  car.speakers = 'boom boOoOom!! 🔊';
};

addSpeakers(carObject);
console.log(carObject);

// FUNCTIONS INSIDE OBJECTS
// object {
//  key1: value1,
//  key2: value2,
//  method1(),
//  method2()
// }

const cat = {
  name: 'Garfield',
  color: 'orange',
  getFood: function() {
    console.log('Give me foood! 🍝');
  }
};

cat.getFood();

const person = {
  firstName: 'Nikko',
  lastName: 'Bansil',
  sayFullName: function() {
    console.log(${this.firstName} ${this.lastName});
    console.log(this);
  }
};

person.sayFullName();

// ITERATE THROUGH OBJECT KEY/VALUES
const fruit = {
  name: 'apple',
  color: 'green',
  emoji: '🍏'
};

// FOR OF
const fruitKeys = Object.keys(fruit);
console.log(fruitKeys);

for (const key of fruitKeys) {
  console.log(fruit[key]);
}

// FOR IN
for (const key in fruit) {
  console.log(fruit[key]);
}

// IN JS EVERYTHING IS INTERNALLY AN OBJECT! 🤯
const myString = 'hello!';
console.log(myString.proto);
```



### Module01 Week02 Day01 - Callbacks

### Functions as Values
- Just like everything else in JavaScript, functions are values
- As a result, they can be stored in variables just like any other value

```js
const myFunction = function() {
  // do something
};
```

- They can also be passed around just like any other variable

```js
const myFunction = function() {
  // do something
}
const myVar = myFunction;
myVar(); // equivalent to calling myFunction()
```
- And they can be passed to other functions as arguments

```js
const myFunction = function() {
  // do something
}
const myHigherOrderFunction = function(callback) {
  callback(); // equivalent to myFunction()
}
myHigherOrderFunction(myFunction);
```
### Callbacks and Higher Order Functions
- A callback is a function that gets passed to another function to be executed by that function
- Callback functions are used all over the place in JavaScript
- They encapsulate reusable code that can be passed around like any other JS variable
- We call the function that accepts another function as an argument a higher order function

### Anonymous Functions
- We can pass callback functions _inline_ to a higher order function rather than storing the callback in a variable first

```js
const myHigherOrderFunction = function(callback) {
  callback();
}
// the function we pass as an argument has no name
myHigherOrderFunction(function() {});
```

- Anonymous functions are simply functions that do not have a name
- [Naming things is hard](https://martinfowler.com/bliki/TwoHardThings.html)

### Arrow Functions
- Arrow functions give us a syntactic alternative to using the function keyword

```js
// function keyword
const myFunc = function() {
  // do something
};
// arrow function
const myArrowFunc = () => {
  // do something
};
```
- There are some _gotchas_ around using the this keyword inside an arrow function, but if you aren't using this, arrow functions can be used interchangeably with "regular" functions
- Arrow functions are often used as callbacks because they are shorter/cleaner to type

js
arr.forEach(function(element) {});
// vs
arr.forEach((element) => {});

### Useful Links
* [Wikipedia: Callbacks](https://en.wikipedia.org/wiki/Callback_(computer_programming))
* [MDN: Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

Functions as Values Example -

```js
// function sayHello() {
//   console.log('hello there');
// }

const sayHello = function() {
  console.log('hello there');
};

const funcs = [sayHello];

// funcs.push(sayHello);

console.log(funcs);

funcs[0]();

// sayHello.secretMessage = 'does this work?';

// console.log(sayHello);

// const copy1 = sayHello();
// const copy2 = sayHello;

// copy2();

// console.log(sayHello.toString());
// console.log();
// console.log(copy2.toString());

// const a = 5;
// const b = a;
```

Passing Functions Example -

```js
// function sayHello() {
//   console.log('hello there');
// }

const sayHello = function() {
  console.log('hello there');
};

const funcs = [sayHello];

// funcs.push(sayHello);

console.log(funcs);

funcs[0]();

// sayHello.secretMessage = 'does this work?';

// console.log(sayHello);

// const copy1 = sayHello();
// const copy2 = sayHello;

// copy2();

// console.log(sayHello.toString());
// console.log();
// console.log(copy2.toString());

// const a = 5;
// const b = a;
```

Anonymous Function Example - 

```js
// naming things is hard

// const username = 'alice';
// console.log(username);

// console.log('bob');
// sayHello('carol');

const runMyFunc = function(anotherFunc) {
  anotherFunc('Carol');
};

// anotherFunc();

const sayHello = function(name) {
  console.log(hello there ${name});
};

runMyFunc(function(name) {
  console.log(hello there ${name});
});

runMyFunc(sayHello);
```

Justification Example

```js
const names = ['alice', 'bob', 'carol', 'dean', 'elise'];

// for (const name of names) {
//   console.log(Hello ${name}, welcome to our website!);
// }


const loopingArray = function(arr, callback) {
  for (const element of arr) {
    // console.log('element', element);
    callback(element);
  }
};

const whatToDoOnEachIteration = function(name) {
  console.log(We got this ${name} from the higher order function);
};

loopingArray(names, whatToDoOnEachIteration);
console.log();
names.forEach(whatToDoOnEachIteration);
// loopingArray([1, 2, 3]);

// for (const index in names) {
//   console.log(names[index]);
// }

// for (let i = 0; i < names.length; i += 2) {
//   console.log(names[i]);
// }

// console.log('i', i);
```

Arrow Function Example -

```js
// added in 2015 with ES6
// advantages
// 1. no function keyword needed
// 2. if only one argument, no parens needed
// 3. if only one line of code, no curly braces needed
// 4. if no curly braces, the line of code is implicitly returned
// 5. arrow funcs do not create this

const myFunc1 = () => {}
const myFunc2 = name => console.log('hello');

// function sayHello() {}
// sayHello() => {};

const sayHello1 = function(name) {
  return hello there ${name};
};

const sayHello2 = name => hello there ${name};

const returnVal = sayHello2('alice');
console.log('returnVal', returnVal);
```

Array Map Example - 


```js
const names = ['alice', 'bob', 'carol', 'dean', 'elise'];

const ourMap = (arr, callback) => {
  // create the output array
  const output = [];

  // loop through the provided array
  for (const element of arr) {
    // call the provided callback with each element AND capture the return value
    const returnVal = callback(element);

    // add the returnVal to the output array
    output.push(returnVal);

    // output.push(callback(element));
  }

  // return the output array
  return output;
};

const doOnEachLoop = (name) => {
  return hello there ${name};
};

const outputArray = ourMap(names, doOnEachLoop);
console.log('names', names);
console.log('outputArray', outputArray);

console.log();

const outputArray2 = names.map(doOnEachLoop);
console.log('built-in map', outputArray2);
```

Nested For-Of Example -

```js
const myObj = {
  nestedArrays: [
    ['a', 'b', 'c'],
    [1, 2, 3]
  ]
};

console.log(myObj);

// const nestedArrays = myObj.nestedArrays;

for (const subArray of myObj.nestedArrays) {
  console.log('subArray', subArray);
  for (const subElement of subArray) {
    console.log('subElement', subElement);
  }
}
```