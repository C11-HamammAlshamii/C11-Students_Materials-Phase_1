# Introduction to ES6

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- The definition of ES6
- Different helpful ES6 syntax

## ES6

### What is ES6

ES6 refers to version 6 of the ECMA Script programming language. ECMA Script is the standardized name for JavaScript, and version 6 is a significant enhancement to the JavaScript language, and adds many more features intended to make large-scale software development easier.

Examples of some ES6 features:

<details>
  <summary>
    1. Variables:
  </summary>

```javascript
// constant variables
const x = 10;

// block-scoped variables
if (true) {
  const a = 1;
  let b = 2;
}

a; // => Uncaught ReferenceError: a is not defined
b; // => Uncaught ReferenceError: b is not defined
```

</details>

<details>
  <summary>
    2. Template Literals:
  </summary>

```javascript
// string interpolation
const name = "john";
const string = `hello this is ${name}`;

string; // => hello this is john

//multi-line strings
const multiLineString = `This
is a

multiline
String`;
```

</details>

<details>
  <summary>
    3. Arrow Functions:
  </summary>

```javascript
// used for multi-line functions
const functionOne = (a, b) => {
  const c = a + b;
  return c;
};

functionOne(1, 2); // => 3

// used for single line functions
const functionTwo = (a, b) => a + b;

functionTwo(1, 2); // => 3

// used with one parameter, works with both multi-line and single-line arrow functions
const functionThree = (a) => a + 1;
const functionFour = (a) => {
  const c = a + 1;
  return c;
};

functionThree(1); // => 2
functionFour(1); // => 2
```

</details>

<details>
  <summary>
    4. Destructuring:
  </summary>

```javascript
// array destructuring
const array = [1, 2, 3];
const [x, y, z] = array;

x; //=> 1
y; //=> 2
z; //=> 3

const [a, , c] = array;
a; //=> 1
c; //=> 3

const functionFive = ([a, b, c]) => {
  return a + b + c;
};

functionFive([1, 2, 3]); // => 6

// object destructuring
const person = {
  name: "John",
  age: 24,
};

// the name of the variable must match the name of the property
const { name, age } = person;

name; // => "John"
age; // => 24

const functionSix = ({ name, age }) => {
  return `${name} is ${age} years old`;
};

functionSix(person); //'John is 24 years old'
```

</details>

<details>
  <summary>
    5. Default Function Parameters:
  </summary>

```javascript
// default function parameters
const functionSeven = (a = 10, b = 12) => a + b;

functionSeven(1, 2); // => 3
functionSeven(1); // => 13
functionSeven(); // => 22
```

</details>

<details>
  <summary>
    6. Rest Parameters:
  </summary>

```javascript
const functionEight = (x, ...y) => x * y.length;

functionEight(5, "hello", "world"); // 5 * ["hello", "world"].length => 10
functionEight(5, 5, 10, 20); // 5 * [5, 10, 20].length => 15
```

</details>

<details>
  <summary>
    7. Spread Operator:
  </summary>

```javascript
// spread operator on arrays
// copying arrays
const arrOne = [1, 2, 3];
const arrOneCopy = [...arrOne];

arrOneCopy; // => [1, 2, 3]

// passing each element of the array as an argument
const functionNine = (x, y, z) => x + y + z;

//Pass each elem of the array as an argument
functionNine(...[1, 2, 3]); // 1 + 2 + 3 => 6

arrOne.push(...arrOneCopy);
arrOne; // => [1, 2, 3, 1, 2, 3]

const max = Math.max(...[10, 50, 70, 90, 1]);
max; // => 90

// combining arrays
const numbersOne = [4, 5, 6];
const numbersTwo = [1, 2, 3, ...numbersOne];

numbersTwo; // => [1, 2, 3, 4, 5, 6]

// it is possible to use destructuring and spread operators together
const [a, b, ...c] = [1, 2, 3, 4, 5, 6];
a; // => 1
b; // => 2
c; // => [3, 4, 5, 6]

// spread operator on objects
const objectOne = { a: 1, b: 2, c: 3 };
const objectTwo = { a: 5, d: 4 };

const objectThree = { ...objectOne, ...objectTwo };
objectThree; // => { a: 5, b: 2, c: 3, d: 4 }
```

</details>

### Practice

**Note:** All Practice should be solved using `ES6`.

1. Write a function `average` that accepts two number arguments and returns the average of these numbers.

   ```javascript
   const average = function (a, b) {
     // TODO: Your code here
   };

   average(20, 25); // => 22.5
   average(15, 7); // => 11
   ```

2. Write a function `endsWith` that accept two string arguments, `string` and `character`, and returns true if the string ends with that character.

   ```javascript
   const endsWith = function (string, character) {
     // TODO: Your code here
   };

   endsWith("Hello", "o"); // => true
   endsWith("Hello", "O"); // => true
   endsWith("hellO", "o"); // => true
   endsWith("World", "h"); // => false
   endsWith("World", "a"); // => false
   endsWith("World", "c"); // => false
   ```

3. Write a function `addToList` that accepts a string argument `toDo` and returns the current list as a string. Every time we invoke the function it should return the old toDo item plus the new one.

   ```javascript
   const addToList = function (toDo) {
     // TODO: Your code here
   };

   addToList("Eat"); // => 'Eat'
   addToList("Play"); // => 'Eat Play'
   addToList("Sleep"); // => 'Eat Play Sleep'
   addToList("repeat"); // => 'Eat Play Sleep repeat'
   ```

4. Write a function `addToArray` that accepts two arguments, `array` and `string`, and returns the same array after adding the string element to the end of it.

   ```javascript
   const addToArray = function (array, string) {
     // TODO: Your code here
   };

   addToArray(["Hello", "i", "am"], "John"); // => ["Hello", "i", "am", "John"]
   addToArray(["Hello", "John", "i", "am"], "Jane"); // => ["Hello", "John", "i",  "am", "Jane"]
   ```

5. Write a factory function `createUser` that accepts two string arguments, `firstName` and `lastName`, returning an object representing the user.

   ```javascript
   const createUser = function (firstName, lastName) {
     // TODO: Your code here
   };

   createUser("John", "Doe"); // => {firstName: "John", lastName: "Doe"}
   createUser("Peter", "Brown"); // => {firstName: "Peter", lastName: "Brown"}
   ```

6. Write a function `onlyStrings` that accepts an array of strings, numbers, and booleans, and returns a new array with only the strings.

   ```javascript
   const onlyStrings = function (array) {
     // TODO: Your code here
   };

   onlyStrings([0, 1, "Hello", true, 4, "World", 6]); // => ["Hello", "World"]
   onlyStrings(["John", 87, true, 26, "Doe", false]); // => ["John", "Doe"]
   ```

7. Write a function `convertToArray` that accepts an object with numerical keys and returns an array containing the values with the corresponding index.

   ```javascript
   const convertToArray = function (object) {
     // TODO: Your code here
   };

   convertToArray({ 0: "one", 1: "two", 2: "three" }); // => ["one", "two", "three"]
   convertToArray({ 1: "two", 0: "one", 2: "three" }); // => ["one", "two", "three"]
   convertToArray({ 2: "two", 1: "one", 0: "three" }); // => ["three", "one", "two"]
   ```

8. Write a function `factorial` that accepts a number argument, and returns the factorial of that number.

   ```javascript
   const factorial = function (number) {
     // TODO: Your code here
   };

   factorial(5); // 1 * 2 * 3 * 4 * 5 => 120
   factorial(3); // 1 * 2 * 3 => 6
   factorial(1); // => 1
   factorial(0); // => 1
   ```

9. Write a function `averageGrade` that accepts an array of student grades as values and returns the average grade. If an empty array was passed in return `"Please enter at least one grade"`.

   ```javascript
   // Make sure to use the correct higher-order function
   const averageGrade = function (grades) {
     // TODO: Your code here
   };

   averageGrade([100, 80, 95, 67, 74]); // => 83.2
   averageGrade([100, 90, 80, 70]); // => 85
   averageGrade([]); // => "Please enter at least one grade"
   ```
