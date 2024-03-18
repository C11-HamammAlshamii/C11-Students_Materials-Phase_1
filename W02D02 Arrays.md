# Arrays In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Defining an array
- Accessing array values
- Assigning values to arrays
- Array methods

## Arrays

### What are Arrays

An array is an ordered collection of related values. There are no restrictions on the types of data that can be present in an array, although, usually it is preferred to hold values of the same data type.

How to define an array (with examples):

```javascript
const array = []; // => empty array

// in between the square brackets `[]` add comma-separated values
// the values of an array could be of any data type
const fruits = ["Apple", "Banana", "Strawberry", "Mango"];
const oddNumbers = [1, 5, 7, 3, 11];
const someArrayValues = [
  100,
  "Hello",
  true,
  [1, 2, 3, 4],
  function () {
    console.log("Hello");
  },
];

// it is possible to use other variables inside the array
let nameOne = "John";
let nameTwo = "Doe";
const names = [nameOne, nameTwo];

names; // => ["John", "Doe"]

nameOne = "Jane";
nameTwo = "Smith";

names; // => ["John", "Doe"]
```

### Accessing and Assigning values

In order to access a value in the array, we need to reference its location in the array. Since arrays are indexed, we will need to reference the index of the element to access its value.

Here is an example:

```javascript
// the array indexes start at 0 so the first item in the array will always have the index of 0
const numbers = [40, 30, 90, 45];

// to access a value we need to reference the array and then add the index number in between square brackets
numbers[0]; // => 40
numbers[1]; // => 30
numbers[2]; // => 90
numbers[3]; // => 45
numbers[4]; // => undefined

// arrays come with a property called `length` that is used to get the length of the array
// it could be used to access the last element of an array
numbers.length; // => 4
numbers[numbers.length - 1]; // => 45

// accessing nested arrays
const nestedArrays = [
  [1, 2, 3],
  [4, 5, 6],
];

nestedArrays[0]; // => [1,2,3]
nestedArrays[0][1]; // => 2
nestedArrays[1][0] === 4; // => true

// since we can access a specific location in the array, we can use the assignment operator to update or add values
const nums = [5, 2, 3];

nums[0] = 1;
nums; // => [1, 2, 3]
nums[3] = 4;
nums; // => [1, 2, 3, 4]
```

### Array Methods

Arrays have some built-in methods that we can use to manipulate the array, some of them are `push`, `pop`, `shift`, and `unshift`

An example of array methods:

```javascript
// the push method is used to add one or more elements  to the end of the array
const numbers = [1, 2];
numbers.push(3); // this expression will return the length of the array after adding the element
numbers; // => [1, 2, 3]
numbers.push(4, 5);
numbers; // => [1, 2, 3, 4, 5]

// the `pop` method is used to remove the last element of the array
numbers.pop(); // this expression will return the removed element
numbers; // => [1, 2, 3, 4]

// the `shift` method is used to remove the first element of the array
numbers.shift(); // this expression will return the removed element
numbers; // => [2, 3, 4]

// the `unshift` method is used to add one or more elements to the start of the array
numbers.unshift(1); // this expression will return the length of the array after adding the element
numbers; // => [1, 2, 3, 4]
numbers.unshift(-1, 0);
numbers; // => [-1, 0, 1, 2, 3, 4]

// the `join` method is used to combine the array values together depending on what is passed to it
const letters = ["H", "e", "l", "l", "o"];
// since an empty string got passed in the join method, an empty string replaced all of the commas when creating the string
letters.join(""); // => "Hello"
// since a hyphen got passed in the join method, a hyphen replaced all of the commas when creating the string
letters.join("-"); // => "H-e-l-l-o"

// the `reverse` method is used to reverse the order of items in the array
const orderedArray = [1, 2, 3, 4, 5, 6];
orderedArray.reverse();
// notice how the original array got mutated (changed)
orderedArray; // => [6, 5, 4, 3, 2, 1]
```

### Pulse Check

1. Define the following arrays.

   - Define an array `colors` containing your favorite three colors.

   - Define an array `negativeNumbers` containing five negative numbers.

   - Define an array `food` containing three of your favorite foods.

   - Define an array `numbers` containing two arrays, the first array contains three odd numbers and the second array contains four even numbers.

2. Access the following values.

   - Access the value `Mars` of the following arrays using the index.

   ```javascript
   const orderedPlanets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter"];
   const unorderedPlanets = ["Mars", "Earth", "Mercury", "Jupiter", "Venus"];
   ```

   - Access the `Koala` value of the following arrays using the `length` property.

   ```javascript
   const animals = ["Cat", "Dog", "Dolphin", "Squirrel", "Koala"];
   ```

3. Assign the following values to the corresponding array.

   - Assign the value `Mars` to the end of the following arrays (don't replace `Jupiter` and `Mercury`).

   ```javascript
   // a- use the `length` property
   const orderedPlanets = ["Mercury", "Venus", "Earth", "Jupiter"];
   // b- don't use the `length` property (use the index)
   const unorderedPlanets = ["Neptune", "Earth", "Mercury"];
   ```

   - Assign the `Koala` to the start of the following array using the index (replace `Cat`).

   ```javascript
   const animals = ["Cat", "Dog", "Dolphin", "Squirrel"];
   ```

4. Solve the following questions using array methods.

   - Add the value `Dinosaur` to the end of the array using the correct array method.

   ```javascript
   const reptiles = ["Snake", "Lizard", "Turtle"];
   ```

   - Add the value `Goldfish` to the start of the array using the correct array method.

   ```javascript
   const fish = ["Swordfish", "Clownfish", "Shark"];
   ```

   - Remove the first value of `reptiles`.

   - Remove the last value of `fish`.

5. Solve the following questions using the correct array methods.

   - Create the following string `1993` from the array below.

   ```javascript
   [1, 9, 9, 3];
   ```

   - Create the following string `John Doe The Third` from the array below.

   ```javascript
   ["John", "Doe", "The Third"];
   ```

   - Create the following array ['world', 'hello'] from the array below.

   ```javascript
   ["hello", "world"];
   ```

   - Create the following string `4-3-2-1` from the array below.

   ```javascript
   [1, 2, 3, 4];
   ```

### Practice

1. Write a function `addToArray` that accepts two arguments, `array` and `string`, and returns the same array after adding the string element to the end of it.

   ```javascript
   const addToArray = function (array, string) {
     // TODO: Your code here
   };

   addToArray(["Hello", "i", "am"], "John"); // => ["Hello", "i", "am", "John"]
   addToArray(["Hello", "John", "i", "am"], "Jane"); // => ["Hello", "John", "i", "am", "Jane"]
   ```

2. Write a function `convertToString` that accepts an array of strings and returns a string made out of the array values.

   ```javascript
   const convertToString = function (array) {
     // TODO: Your code here
   };

   convertToString(["Hello", "i", "am", "John"]); // => "Hello i am John"
   convertToString(["Hello", "John", "i", "am", "Jane"]); // => "Hello John i am Jane"
   ```

3. Write a function `accessElement` that accepts two arguments, `array` and `index`, and returns the corresponding array element depending on the passed index.

   ```javascript
   const accessElement = function (array, index) {
     // TODO: Your code here
   };

   accessElement([1, 2, 3, 4, 5], 0); // => 1
   accessElement([1, 2, 3, 4, 5], 3); // => 4
   accessElement([1, 2, 3, 4, 5], 10); // => "No element at index 10"
   ```

4. Write a function `isInArray` that accepts two arguments, `array` and `string`, and returns `true` or `false` depending on whether the string is an element in the array or not.

   ```javascript
   const isInArray = function (array, string) {
     // TODO: Your code here
   };

   isInArray(["John", "Jane", "Mark"], "Jane"); // => true
   isInArray(["John", "Jane", "Mark"], "Mark"); // => true
   isInArray(["John", "Jane", "Mark"], "Smith"); // => false
   isInArray(["John", "Jane", "Mark"], "Doe"); // => false
   ```

   HINT: search for `indexOf` on [MDN](https://developer.mozilla.org/en-US/).

5. Write a function `reverseWords` that accepts a string argument and returns the same string if only one word was passed in. If more than one word is passed, it will return a string of the words in the reverse order. Check out the comments below before solving the question.

   ```javascript
   // split: is a string method that is used to convert a string into an array and the values will be separated depending on the
   // argument passed into the split method (opposite of join)
   const word = "Hello";
   // if an empty string is passed as an argument then the string will be split on every character
   word.split(""); // => ["H", "e", "l", "l", "o"]
   // if we pass the letter "e" as an argument, it will split the string on every "e" in that string. Since there is only one "e", the string has split into an array with two elements
   word.split("e"); // => ["H", "llo"]
   // if an empty space (" ") is passed as an argument, the string will be split on every empty space
   const words = "This is a string that contains words";
   words.split(" "); // => ["This", "is", "a", "string", "that", "contains", "words"]

   const reverseWords = function (string) {
     // TODO: Your code here
   };

   reverseWords("Hello"); // => "Hello"
   reverseWords("Hello World"); // => "World Hello"
   ```

6. Write a function `addToLast` that accepts two arguments, `array` and `value`, and returns an array with the value added to the end of the array. Use `unshift` instead of push.

   ```javascript
   // do not use `push` or array assignments, only `unshift`
   const addToLast = function (array, value) {
     // TODO: Your code here
   };

   addToLast([1, 2, 3], 4); // => [1, 2, 3, 4]
   addToLast([10, 6], 1); // => [10, 6, 1]
   ```

7. Solve the following.

   ```javascript
   // write a function `getLength` that accepts an array and returns the
   // length of the array without using the array's attribute `length`
   const getLength = function (array) {
     // do not use array.length
     // TODO: Your code here
   };

   getLength([1, 2, 3, 4]); // => 4
   getLength([10, 22, 30]); // => 3

   // write a function `getFirstVal` that accepts an array and returns the
   // first value of the array without using the index to access the value
   const getFirstVal = function (array) {
     // do not use array[0]
     // TODO: Your code here
   };

   getFirstVal([1, 2, 3, 4]); // => 1
   getFirstVal([51, 3, 3, 4]); // => 51
   ```

8. Write a function `updateOrCreate` that accepts three arguments, `array`, `value`, and `index`, and returns an updated array. Check the output for more information on the updated array.

   ```javascript
   const updateOrCreate = function (array, value, index) {
     // TODO: Your code here
   };

   updateOrCreate([10, 20, 30], 50, 1); // => [10, 50, 30]
   updateOrCreate([10, 20, 30], 40, 3); // => [10, 20, 30, 40]
   updateOrCreate([10, 20, 30], 100, 10); // => [10, 20, 30, empty * 7, 100]
   ```

9. Write a function `sliceArray` that accepts three arguments, an ordered numeric `array` (unique numbers), `startVal`, and `endVal`, and returns an array starting at the `startVal` and ending at the `endVal`.

   ```javascript
   const sliceArray = function (array, startVal, endVal) {
     // TODO: Your code here
   };
   sliceArray([10, 20, 30, 40, 50, 60], 10, 60); // => [10, 20, 30, 40, 50, 60]
   sliceArray([10, 20, 30, 40, 50, 60], 20, 40); // => [20, 30, 40]
   sliceArray([10, 20, 30, 40, 50, 60], 20, 20); // => []
   sliceArray([10, 20, 30, 40, 50, 60], 50, 20); // => []
   ```

   HINT: search for `slice` on [MDN](https://developer.mozilla.org/en-US/).

10. Write a function `randomFruit` that accepts an array of fruits and returns a random element from that array.

    ```javascript
    const randomFruit = function (array) {
      // TODO: Your code here
    };

    const fruits = ["Apple", "Banana", "Strawberry", "Mango"];

    randomFruit(fruits); // => "Apple"
    randomFruit(fruits); // => "Apple"
    randomFruit(fruits); // => "Strawberry"
    randomFruit(fruits); // => "Banana"
    ```

### Advanced Practice

1. Write a function `isPalindrome` that accepts a string argument and returns whether the string is a palindrome or not.

   ```javascript
   // a palindrome is when a string is read the same backwards
   const isPalindrome = function (string) {
     // TODO: Your code here
   };

   isPalindrome("dad"); // => true
   isPalindrome("was it a car or a cat i saw"); // => true
   isPalindrome("a santa at nasa"); // => true
   isPalindrome("John doe"); // => false
   ```

2. Write a function `arrayMiddle` that accepts an array and returns the middle element of the array. If the array's length is even then return the average of both of the middle elements.

   ```javascript
   const arrayMiddle = function (array) {
     // TODO: Your code here
   };

   arrayMiddle([1, 2, 3, 4, 5]); // => 3
   arrayMiddle([1, 2, 3, 4, 5, 6]); // => 3.5
   arrayMiddle([10, 52, 2, 10, 31]); // => 2
   arrayMiddle([10, 52, 2, 10, 31, 7]); // => 6
   ```

3. Write a function `removeElement` that accepts two arguments, `array` and `index`, and returns an array after removing the element that corresponds to that index.

   ```javascript
   const removeElement = function (array, index) {
     // TODO: Your code here
   };

   removeElement([1, 2, 3], 1); // => [1, 3]
   removeElement(["Hello", "John", "how", "are", "you"], 0); // => ["John", "how", "are", "you"]
   ```

   HINT: search for the right array method to use, on [MDN](https://developer.mozilla.org/en-US/).

4. Write a function `combineArrays` that accepts two arrays, `arrayOne` and `arrayTwo`, and returns a new array holding all the elements of both arrays.

   ```javascript
   const combineArrays = function (arrayOne, arrayTwo) {
     // TODO: Your code here
   };

   combineArrays([1, 2, 3], [4, 5]); // => [1, 2, 3, 4, 5]
   combineArrays([1, 1], [1, 1]); // => [1, 1, 1, 1]
   ```

   HINT: search for the right array method to use, on [MDN](https://developer.mozilla.org/en-US/).

5. Write a function `hasNestedArray` that accepts an array that contains nested arrays of at least two elements and returns whether the array contains nested arrays or not.

   ```javascript
   const hasNestedArray = function (array) {
     // TODO: Your code here
   };

   hasNestedArray([1, 2, 3, 4, 5]); // => false
   hasNestedArray([1, 2, 3, [4, 5]]); // => true
   hasNestedArray([1, 2, 3, 4, 5, 6, 7]); // => false
   hasNestedArray([1, 2, 3, [4, 5, [6, 7]]]); // => true
   ```

   HINT: search for the right array method to use, on [MDN](https://developer.mozilla.org/en-US/).
