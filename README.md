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