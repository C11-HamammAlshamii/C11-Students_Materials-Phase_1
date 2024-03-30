# Callbacks and Higher Order Functions

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- The definition of Callbacks
- Using Callbacks
- The definition of higher-order functions
- Using forEach, map, reduce, and filter

## Callbacks

### What Is A Callback Function

Functions that are passed in as an argument for another function are called callback functions. Callbacks are mostly used with asynchronous code, but more on that in a later lesson.

Examples of callbacks:

```javascript
// here we specify a parameter for our callback function and then execute it inside the function. At the moment, the callback function is not
// defined and it will be defined when it is passed in as an argument
const exampleFunc = function (callback) {
  callback();
};

// you can define the function inside the invocation parentheses
exampleFunc(function () {
  console.log("Hello World");
}); // => Hello World

// you can also use a function name instead of the way above
const hello = function () {
  console.log("Hello World");
};

exampleFunc(hello); // => Hello World

// it is possible to pass arguments to the callback function
const exampleFunction = function (x, y, callback) {
  return callback(x, y);
};

exampleFunction(10, 20, function (x, y) {
  return x + y;
}); // => 30

// an example of using callbacks with asynchronous code
setTimeout(function () {
  console.log("logs once after one second");
}, 1000);

setInterval(function () {
  console.log("logs every one second");
}, 1000);
```

## Higher Order Functions

### What Is A Higher Order Function

A higher-order function is a function that can take another function as an argument.

Examples of some built-in higher-order functions:

- `forEach`: is used to iterate over arrays, it is possible to access every element inside the callback function.

  ```javascript
  const array = [1, 2, 3];
  // `forEach` will loop over the array above and give access to every number and index
  // there is no return value for `forEach`
  array.forEach(function (element, index) {
    console.log(element);
  });
  // 1
  // 2
  // 3

  array.forEach(function (element, index) {
    if (index === 1) {
      console.log(element);
    }
  });
  // 2
  ```

- `map`: is used to iterate and modify the array elements

  ```javascript
  const numbers = [1, 2, 3];
  // `map` will iterate and perform an action on every element of the array
  // map returns a new array with the modified values
  numbers.map(function (element, index) {
    // return an expression to change the element, in this case, it will increment the element by 1
    return element + 1;
  }); // => [2, 3, 4]

  const strings = ["Hello", "World"];
  strings.map(function (element, index) {
    return element + "!!!";
  }); // => ["Hello!!!", "World!!!"]
  ```

- `filter`: is used to iterate and filter the array elements depending on a condition

  ```javascript
  // `filter` will iterate over an array to filter out values depending on a condition
  // it returns a new array of the elements that passed the condition
  const numbers = [1, 2, 3];
  numbers.filter(function (element, index) {
    // return an expression that results in a boolean value
    return element > 1;
  }); // => [2, 3]

  numbers.filter(function (element, index) {
    return true;
  }); // => [1, 2, 3]
  ```

- `reduce`: is used to reduce all the elements of the array into a single value.

  ```javascript
  // reduce will reduce the array values into one value, like summing them all together
  // it returns a single value
  const numbers = [1, 2, 3];
  numbers.reduce(function (accumulator, number, index) {
    // accumulator is basically the total amount
    // return an expression that would modify the accumulator
    return accumulator + number;
  }); // => 6

  numbers.reduce(function (accumulator, number, index) {
    // return an expression that would modify the accumulator
    return accumulator + number;
    // you can specify the starting value of the accumulator
  }, 10);
  // 16
  ```

### Pulse Check

1. Write a function that accepts two arguments, `number` and `callback`, and using the callback return the number squared.

2. Using forEach iterate over the following arrays and console log all the indexes.

   ```javascript
   const numbers = [1, 2, 3, 4];
   const animals = ["Cat", "Dog", "Bear", "Bat"];
   ```

3. Using map iterate over the following array and decrement all elements by 1.

   ```javascript
   const numbers = [1, 2, 3, 4];
   ```

4. Using filter iterate over the following array and return all `string` values.

   ```javascript
   const array = [1, "two", "three", 4];
   ```

5. Using reduce iterate over the following array and return the sum of all the numbers doubled.

   ```javascript
   const numbers = [1, 2, 3, 4];
   ```

### Practice

1. Write a function `convertToString` that accepts an array of letters and returns all the letters combined.

   ```javascript
   // Make sure to use the correct higher-order function
   const convertToString = function (array) {
     // TODO: Your code here
   };

   convertToString(["c", "a", "t"]); // => "cat"
   convertToString(["h", "e", "l", "l", "o"]); // => "hello"
   ```

2. Write a function `averageGrade` that accepts an array of student grades as values and returns the average grade. If an empty array was passed in return `"Please enter at least one grade"`.

   ```javascript
   // Make sure to use the correct higher-order function
   const averageGrade = function (grades) {
     // TODO: Your code here
   };

   averageGrade([100, 80, 95, 67, 74]); // => 83.2
   averageGrade([100, 90, 80, 70]); // => 85
   averageGrade([]); // => "Please enter at least one grade"
   ```

3. Write a function `evenLengthOddIndex` that accepts an array of strings and returns a new array of only the even-length words that are in an odd index.

   ```javascript
   const evenLengthOddIndex = function (strings) {
     // TODO: Your code here
   };

   evenLengthOddIndex(["word", "care", "car", "food", "cast", "cat"]); // => ["care", "food"]
   evenLengthOddIndex(["word", "care", "food", "car", "cast", "cat"]); // => ["care"].
   evenLengthOddIndex(["word", "cat", "food"]); // => []
   ```

4. Write a function `incrementByIndex` that accepts an array of nested arrays that hold numbers as values, and returns an array where each element of the nested arrays is incremented by the index of that nested array.

   ```javascript
   // Make sure to use the correct higher-order functions
   const incrementByIndex = function (array) {
     // TODO: Your code here
   };

   // the first nested array's values were incremented by 0 since it is the first index, second nested array was
   // incremented by 1 and so on.
   incrementByIndex([
     [6, 1, 5],
     [1, 5, 49],
   ]); // => [[6, 1, 5], [2, 6, 50]]
   incrementByIndex([
     [1, 2, 3],
     [2, 7, 9],
     [10, 3, 44],
   ]); // => [[1, 2, 3], [3, 8, 10], [12, 5, 46]]
   ```

5. Write a function `countWords` that accepts a string and returns an object that has all of the unique words from the string as keys, and the number of times a word was found in the string is shown as the value of that key.

   ```javascript
   // Make sure to use the correct higher-order function
   const countWords = function (string) {
     // TODO: Your code here
   };

   countWords("hello hello world"); // => { hello: 2, world: 1 }
   countWords("hello"); // => { hello: 1 }
   countWords(""); // => {}
   ```

6. Write a function `orderByType` that accepts an array of mixed type values and returns a new array with the same values but ordered by type, meaning all the strings first, then all the numbers, and all the booleans last.

   ```javascript
   // Make sure to use the correct higher-order function
   const orderByType = function (array) {
     // TODO: Your code here
   };

   orderByType([1, true, 10, "hello", "world", false, 90, "cat"]); // => ["hello", "world", "cat", 1, 10, 90, true, false]
   orderByType(["hello", "world", 90, "cat"]); // => ["hello", "world", "cat", 90]
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     Search for `concat` on MDN
   </details>

7. Write a function `gradeExam` that accepts an array of objects and return an array of only the passed subjects with modified value, instead of the grade saying `passed`, the passing grade is 50 or above.

   ```javascript
   // Make sure to use the correct higher-order function
   const gradeExam = function (array) {
     // TODO: Your code here
   };

   gradeExam([
     { subject: "art", grade: 90 },
     { subject: "math", grade: 48 },
   ]); // => [{ subject: "art", grade: "passed" }]
   gradeExam([
     { subject: "english", grade: 74 },
     { subject: "math", grade: 64 },
   ]); // => [{ subject: "english", grade: "passed" },{ subject: "math", grade: "passed" }]
   gradeExam([
     { subject: "english", grade: 41 },
     { subject: "art", grade: 30 },
   ]); // => []
   ```

8. Write a function `allNumbers` that accepts an array and returns `true` if all the values are numbers and returns `false` if it is not.

   ```javascript
   // Make sure to use the correct higher-order function
   const allNumbers = function (array) {
     // TODO: Your code here
   };

   allNumbers([1, 2, 3, 4]); // => true
   allNumbers([10, 4, -1, 0]); // => true
   allNumbers([1, 2, "three", 1]); // => false
   allNumbers([41, 27, true]); // => false
   ```

9. Write a function `convertToObject` that accepts an array of key-value pairs arrays, and return an array of objects with the corresponding keys and values.

   ```javascript
   // Make sure to use the correct higher-order function
   const convertToObject = function (array) {
     // TODO: Your code here
   };

   convertToObject([["name", "Jane"]]); // => [{ name: "Jane" }]
   convertToObject([
     ["name", "John"],
     ["age", 24],
   ]); // => [{ name: "John"}, {age: 24 }]
   ```

10. Write a function `fibonacci` that accepts a number argument, and returns an array that it's indices are Fibonacci numbers (from zero to the number) and its values are the values of the sequence at that index, you may use the helper function `range` to help you solve the question.

    ```javascript
    // Make sure to use the correct higher-order function

    // find the relation between the fibonacci number and the value of the sequence at that number
    // Fibonacci numbers: | F0 | F1 | F2 | F3 | F4 | F5 | F6 | F7 | F8 | F9 | F10 |
    // Value of sequence: | 0  | 1  |  1 | 2  | 3  | 5  | 8  | 13 | 21 | 34 | 55  |

    const range = function (number) {
      const array = [];
      for (let i = 0; i <= number; i++) {
        array.push(i);
      }
      return array;
    };

    const fibonacci = function (fibNumber) {
      // TODO: Your code here
    };

    fibonacci(4); // => [0, 1, 1, 2, 3]
    fibonacci(7); // => [0, 1, 1, 2, 3, 5, 8, 13]
    fibonacci(10); // => [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
    ```

### Advanced Practice

1. Write a function `loop` that accepts two arguments an array and a callback function. The function `loop` should enable us to access all the values in the array and give us the ability to modify the elements by using the callback function (Just like forEach).

   ```javascript
   // DO NOT USE ANY ARRAY METHODS (forEach, reduce, map, filter)
   const loop = function (array, callback) {
     // TODO: Your code here
   };

   loop([1, 2, 3], function (number) {
     console.log(number);
   });
   // 1
   // 2
   // 3
   ```

2. By using the function `loop`, write a function `filter` that accepts two arguments, `array` and `callback`, and iterates over the array returning a new array of all the elements that passed the filter condition that was returned by the callback function (Just like filter).

   ```javascript
   // DO NOT USE ANY ARRAY METHODS (forEach, reduce, map, filter)
   const filter = function (array, callback) {
     // TODO: Your code here
   };

   filter([1, 2, 3], function (number) {
     return number > 1;
   }); // => [2, 3]
   ```

3. By using the function `loop`, write a function `map` that accepts two arguments, `array` and `callback`, and iterates over the array returning a new array after modifying every element from the original array by using the callback function (Just like map).

   ```javascript
   // DO NOT USE ANY ARRAY METHODS (forEach, reduce, map, filter)
   const map = function (array, callback) {
     // TODO: Your code here
   };

   map([1, 2, 3], function (number) {
     return number * 10;
   }); // => [10, 20, 30]
   ```

4. By using the function `loop`, write a function `reduce` that accepts two arguments, `array` and `callback`, and iterates over the array returning an accumulated value depending on what is returned in the callback function (Just like reduce).

   ```javascript
   // DO NOT USE ANY ARRAY METHODS (forEach, reduce, map, filter)
   const reduce = function (array, callback) {
     // TODO: Your code here
   };

   reduce([1, 2, 3], function (accumulator, number) {
     return accumulator + number;
   }); // 1 + 2 + 3 => 6
   ```

5. Modify the `loop`, `filter`, `map`, and `reduce` functions you just made to work with objects. If the input is an object then iterate over it and return an object instead of an array.
