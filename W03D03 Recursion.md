# Recursion In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- The definition of recursion
- Using recursion

## Recursion

### What Is Recursion

Recursion is the process in which a function invokes itself. Recursion results in repetition so the same rules that apply to loops would apply to the recursive function, it must have a condition to stop invoking the function along with an action that leads towards that stop condition.

Example of recursion:

```javascript
const countDown_v01 = function (number) {
  console.log(number);
  if (number === 0) {
    return "Countdown is over";
  }
  return countDown_v01(number - 1);
};

countDown_v01(10);
// 10
// 9
// 8
// 7
// 6
// 5
// 4
// 3
// 2
// 1
// 0
// => "Countdown is over"
```

```javascript
const sum = function (number) {
  // a stop condition to enable the function to stop invoking it self
  if (number === 0) {
    return 0;
  }
  // the action that leads towards the stop condition `number-1` if the number is positive then this action will keep decreasing the number till it reaches zero
  return number + sum(number - 1);
};

// an example of what happens with every invocation
sum(5);
// 5 + sum(4)
//       4 + sum(3)
//            3 + sum(2)
//                 2 + sum(1)
//                      1 + sum(0)
//                           0
//                      1 + 0
//                 2 + 1
//            3 + 3
//       4 + 6
// 5 + 10
// => 15
```

### Why Do We Use Recursion?

You may have noticed that recursion is doing the same as other iteration methods such as `for` and `while` loops and that it should have worse performance (especially in non-optimized engines) since the whole function is being repeated rather than just a block of code but there is a really important argument to support using it in some cases and it all boils down into simply having more elegant, readable and maintainable code since it is usually not recommended to use variables with recursion (since they get redefined with every call) it makes it easier to read since it is mainly using the parameters so even with some complicated algorithms recursion can be used to reduce the time it needs to understand and modify the algorithm, and that sometimes is more important than saving a few milliseconds while executing the function.

### Recursion Common Mistakes

There are some common mistakes when dealing with recursion that could lead to crashing your application, since recursion is mainly repetition it is possible to do it infinitely, so in theory that should happen but there is a maximum call stack that differs depending on the browser/engine used so in case the call stack exceeded the maximum size it would throw an error that should crash the program.

An example of the common mistakes when dealing with recursion:

- Forgetting the stop condition:

  ```javascript
  // The absence of a stop condition will result in exceeding the maximum call stack
  const func_1 = function (num) {
    return func_1(num);
  };
  ```

- Not having a step to reach the stop condition:

  ```javascript
  // The function will be called with the same input and as long as it isn't zero it will keep calling till it exceeds the maximum call stack
  const func_2 = function (num) {
    if (num === 0) {
      return "done";
    }

    // assuming that we are counting down from the num till zero then we need to decrement the input by 1
    return func_2(num);
  };
  ```

- Forgetting the return:

  ```javascript
  // Without returning the same function the output will always be undefined
  const func_3 = function (num) {
    // even though the last call return `done`, it didn't go up the call stack to return at the first invocation
    if (num === 0) {
      return "done";
    }

    // must return the function if you are expecting a value, if not then it's fine not to return
    func_3(num - 1);
  };
  ```

### Pulse Check

1. Create a recursive function `recFunction` that keeps returning it self till it errors out `Uncaught RangeError: Maximum call stack size exceeded`.

   ```javascript
   const recFunction_v01 = function () {
     // TODO: Your code here
   };

   recFunction_v01(); //  Uncaught RangeError: Maximum call stack size exceeded
   ```

2. Modify `recFunction_v01` to accept a positive number argument and with each invocation decrement the number by 1.

   ```javascript
   const recFunction_v02 = function (number) {
     // TODO: Your code here
   };

   recFunction_v02(9); // => undefined
   ```

3. Modify `recFunction_v02` to have a stop condition and return `"0"` when the `number` is equal to zero.

   ```javascript
   const recFunction_v03 = function (number) {
     // TODO: Your code here
   };

   recFunction_v03(9); // => "0"
   ```

4. Modify `recFunction_v03` to concatenate all the numbers together and return a string of all the numbers.

   ```javascript
   const recFunction_v04 = function (number) {
     // TODO: Your code here
   };

   recFunction_v04(9); // => "9876543210"
   ```

5. Modify the `countDown_v01` function to return a string of each number separated by `-` till it reaches 0

   ```javascript
   const countDown_v02 = function (number) {
     console.log(number);
     if (number === 0) {
       return;
     }
     return countDown_v02(number - 1);
   };

   countDown_v02(10); // => "10-9-8-7-6-5-4-3-2-1-0"
   countDown_v02(3); // => "3-2-1-0"
   ```

### Practice

1. Write a function `factorial` that accepts a number argument, and returns the factorial of that number.

   ```javascript
   const factorial = function (number) {
     // TODO: Your code here
   };

   factorial(5); // 1 * 2 * 3 * 4 * 5 => 120
   factorial(3); // 1 * 2 * 3 => 6
   factorial(1); // => 1
   factorial(0); // => 1
   ```

2. Write a function `sumCubes` that accepts an array and returns the sum of the cubed numbers.

   ```javascript
   const sumCubes = function (numbers) {
     // TODO: Your code here
   };

   sumCubes([1, 2]); // => 9
   sumCubes([1, 2, 3]); // => 36
   sumCubes([5, 3, 3]); // => 179
   sumCubes([]); // => 0
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     You could use `slice()` to iterate using recursion.
   </details>

3. Write a function `getLength` that accepts a string argument, and returns the length of the string. Do not use the length property.

   ```javascript
   const getLength = function (string) {
     // TODO: Your code here
   };

   getLength("Hello"); // => 5
   getLength("John"); // => 4
   getLength(""); // => 0
   ```

4. Write a function `reverseString` that accepts a string argument, and returns a string in a reversed order.

   ```javascript
   const reverseString = function (string) {
     // TODO: Your code here
   };

   reverseString("Hello World"); // => "dlroW olleH"
   reverseString("John Doe"); // => "eoD nhoJ"
   reverseString(""); // => ""
   ```

5. Write a function `countCharacter` that accepts a string, and a character and returns the number of times the character was repeated.

   ```javascript
   const countCharacter = function (string, character) {
     // TODO: Your code here
   };

   countCharacter("hello", "l"); // => 2
   countCharacter("hello", "e"); // => 1
   countCharacter("hello", "z"); // => 0
   ```

6. Write a function `oddOrEven` that accepts a number and returns a string `"The number is even"` or `"The number is odd"` depending on whether the number is odd or even. Do not use the modulo operator `%`.

   ```javascript
   const oddOrEven = function (number) {
     // TODO: Your code here
   };

   oddOrEven(8); // => "The number is even"
   oddOrEven(1); // => "The number is odd"
   ```

7. Write a function `multiply` that accepts two number arguments and returns the multiple of both numbers without using the `*` operator.

   ```javascript
   const multiply = function (numberOne, numberTwo) {
     // TODO: Your code here
   };

   multiply(2, 3); // => 6
   multiply(4, 5); // => 20
   ```

8. Write a function `isPalindrome` that accepts a string argument and returns `true` if the string is a palindrome and `false` if it is not.

   ```javascript
   const isPalindrome = function (string) {
     // TODO: Your code here
   };

   isPalindrome("dad"); // => true
   isPalindrome("dads"); // => false
   isPalindrome("John doe"); // => false
   isPalindrome("a bcdcba"); // => true
   isPalindrome("a santa at nasa"); // => true
   isPalindrome("was it a car or a cat i saw"); // => true
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     You could use `replaceAll()` to get rid of the spaces.
   </details>

9. Write a function `remainder` that accepts two number arguments and returns the remainder of the division of both numbers, do not use `%` to solve this question.

   ```javascript
   const remainder = function (numberOne, numberTwo) {
     // TODO: Your code here
   };

   remainder(5, 1); // => 0
   remainder(7, 2); // => 1
   remainder(7, 4); // => 3
   remainder(8, 2); // => 0
   remainder(4, 6); // => 4
   remainder(1, 8); // => 1
   ```

10. Write a function `fibonacci` that accepts a number argument, and returns the value of the Fibonacci sequence at that value, check below for more information about the Fibonacci sequence.

    ```javascript
    // find the relation between the fibonacci number and the value of the sequence at that number
    // Fibonacci numbers: | F0 | F1 | F2 | F3 | F4 | F5 | F6 | F7 | F8 | F9 | F10 |
    // Value of sequence: | 0  | 1  |  1 | 2  | 3  | 5  | 8  | 13 | 21 | 34 | 55  |

    const fibonacci = function (fibNumber) {
      // TODO: Your code here
    };

    fibonacci(4); // => 3
    fibonacci(7); // => 13
    fibonacci(13); // => 233
    ```

### Advanced Practice

1. Write a function `maximumNumber` that accepts an array of numbers and returns the max number in the array.

   ```javascript
   const maximumNumber = function (numbers) {
     // TODO: Your code here
   };

   maximumNumber([0, 5, 2, 10, 8, 6]); // => 10
   maximumNumber([0, 5, 6]); // => 6
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     You could use `splice()` to iterate.
   </details>

2. Write a function `familyTree` that accepts an object representing a family tree and returns a string containing all names in the tree from top to bottom.

   ```javascript
   const family = {
     name: "John",
     child: {
       name: "Bill",
       child: {
         name: "Mark",
         child: {
           name: "Terry",
           child: null,
         },
       },
     },
   };

   const familyTree = function (family) {
     // TODO: Your code here
   };

   familyTree(family); // => "John Bill Mark Terry"
   ```

3. Write a function `flattenArray` that accepts a nested array and returns a one-dimensional array, do not use an array method called `flat`.

   ```javascript
   const flattenArray = function (array) {
     // TODO: Your code here
   };

   flattenArray([1, 2, 3, [4, 5, [6, 7]]]); // => [1, 2, 3, 4, 5, 6, 7]
   flattenArray([[1, 2, [3, 4]]]); // => [1, 2, 3, 4]
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     Read about `Array.isArray()` and `concat()`.
   </details>

4. Write a function `sumTreeValues` that accepts a tree-structured object (similar to how a family tree would look like) and return the sum of all the values for all the objects inside the tree.

   ```javascript
   // in thee first object there are three children that some of them have their own children
   const tree = {
     value: 1,
     children: [
       {
         value: 2,
         children: [
           {
             value: 5,
             children: [],
           },
           {
             value: 6,
             children: [],
           },
         ],
       },
       {
         value: 3,
         children: [],
       },
       {
         value: 4,
         children: [
           {
             value: 7,
             children: [
               {
                 value: 8,
                 children: [],
               },
               {
                 value: 9,
                 children: [],
               },
             ],
           },
         ],
       },
     ],
   };

   const sumTreeValues = function (tree) {
     // TODO: Your code here
   };

   sumTreeValues(tree); // => 45
   ```

   <details>
     <summary>
       Click here for HINT.
     </summary>
     Try drawing the tree first, it will help out a lot.
   </details>
