# Iteration In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Defining a while loop
- Defining a for loop
- Iterating over arrays and strings

## Iteration With While And For Loops

### What Are Loops

Loops execute a snippet of code repeatedly. Consisting of three parts, a starting point, a step, and a run condition, they are used to make our code dynamic and more readable.

There are multiple ways of creating loops. Here, we'll be learning the two most common types, for loops and while loops.

Example of defining a while loop:

```javascript
// create a starting point
let i = 0;
// define the while loop with the right condition
while (i < 5) {
  // code to execute
  console.log(i);

  // increment the i
  i++;
}
// => 0
// => 1
// => 2
// => 3
// => 4

// starting point doesn't have to be a number
let num = 0;
let notFound = true;
const randomNumber = Math.floor(Math.random() * 100);

// our start condition is a boolean and since the it's `true` it will run forever until it changes to `false`
while (notFound) {
  // our stop condition is inside the loop so we can change it our run condition to false so we exit the loop
  if (num === randomNumber) {
    notFound = false;
    console.log("The random number is: " + num);
  } else {
    // a step to get us closer to the random number and the random number is from 0-99 then we should increment the num variable to get closer to it
    num++;
  }
}
```

Examples on defining a for loop:

```javascript
// in the first section initialize the variables that will be used in the loop and separate it from the other sections by using a semicolon ";"
// in the middle part define the run condition, if the condition is true then the loop's code will be executed
// in the last part add a step that gets the loop to reach the endpoint (when the run condition is false)
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// => 0
// => 1
// => 2
// => 3
// => 4

// it is possible to use the keyword break to stop looping, it also works with while loops
for (let i = 0; true; i++) {
  if (i === 3) {
    console.log("Continue");
    continue;
  }
  if (i === 5) {
    console.log("Break");
    break;
  }

  console.log(i);
}
// => 0
// => 1
// => 2
// => "Continue"
// => 4
// => "Break"

// an example of defining a for loop with more than one variable
// it is possible to define multiple variables at the first section
// it is possible to have any expression that will result in a boolean value as a condition in the second section
// it is possible to add multiple expressions at the last section to help reach the condition
for (let i = 0, j = 10; i !== j; i++, j--) {
  console.log(i, j);
}
// => 0 10
// => 1 9
// => 2 8
// => 3 7
// => 4 6
```

### Iteration With Arrays

Since arrays are indexed then it makes sense that if we are trying to access all of its contents, we should create a loop with the starting point of zero since that is the starting index of the array, and the endpoint of the length of the array minus one.

Here is an example:

```javascript
// write a function that takes an array of numbers and returns a new array with the positive numbers only
const positiveOnly = function (numbers) {
  const result = [];
  // using for loop
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] >= 0) {
      result.push(numbers[i]);
    }
  }

  // using while loop
  // let index = 0
  // while(index < numbers.length){
  //     if (numbers[index] >= 0){
  //         result.push(numbers[index]);
  //     }
  //     index ++
  // }
  return result;
};
```

### Iteration With Strings

Since Strings are indexed like arrays we could also use the same method to iterate over them.

Here is an example:

```javascript
const logLetters = function (string) {
  for (let i = 0; i < string.length; i++) {
    console.log(string[i]);
  }

  // let index = 0;
  // while (index < string.length) {
  //   console.log(string[index]);
  //   index++;
  // }
};

logLetters("John");
// => J
// => o
// => h
// => n
```

### Common Mistakes While Using Loops

- Incorrect condition. The starting index does not correspond to the stated condition, resulting in the while block not being invoked.

```javascript
let index_1 = 0;
while (index_1 < -10) {
  console.log(index_1);
  index_1++;
}
```

- Incorrect or missing step. This will result in an infinite loop.

```javascript
let index_2 = 0;
while (index_2 < 10) {
  console.log(index)_2;
  index_2--;
}
```

- Modifying the index by other code outside of the while loop.

```javascript
let index_3 = 0;
while (index_3 < 10) {
  console.log(index_3);
  index_3++;
}

// since the first while loop ran, it modified the index value to be equal to 9
// and that would result in not executing the second while loop because the condition will be false
while (index_3 < 9) {
  console.log(index_3);
  index_3++;
}
```

### Troubleshooting Infinite Loops

In case of an infinite loop most likely the console or browser will not be responding (the effect varies depending on the specs of the CPU), and to solve that try the following:

- Close the use tab in your browser, if it wasn't responding try the below.
- For Windows, open the task manager `CTRL + SHIFT + ESC` then open the `processes` tab and find your browser then click on `End Task`.
- For MacOS open the activity monitor `CMD + OPTION + SHIFT + ESC` or by `CMD + Space` the search for it, and then click on the `CPU` tab and double click on the browser then click `Quit` when you get the popup if asked to `force quit` the app agree to that.

### Pulse Check

1. Fix the following loops so they work as intended.

   ```javascript
   for (const i = 0; i < 10; i++) {
     console.log(i);
   }

   for (let i = 0; i < 10; i--) {
     console.log(i);
   }
   ```

2. Create a while loop with a starting value of 0 and an end value of 5. Console log all numbers in between including the start and end.

3. Create a for loop with a starting value of 10 and an end value of 20. Console log all numbers in between including the start and end.

4. Create a for loop that works on the following array and console log both the index and values.

   ```javascript
   const galaxies = ["Andromeda", "Milky Way", "Magellanic Clouds"];
   ```

5. Create a for loop that works on the following string and console log all the letters that are not an `a`.

   ```javascript
   const randomString = "bwaxaawqaacasghwera";
   ```

### Practice

1. Write a function `sum` that accepts an array of numbers and returns the sum of the numbers.

   ```javascript
   const sum = function (numbers) {
     // TODO: Your code here
   };

   sum([1, 2, 3, 4, 5, 6]); // => 21
   sum([1, 2, 3]); // => 6
   ```

2. Write a function `login` that accepts two string arguments, `username` and `password`, and returns a message saying `"Login Successful"` or `"Login Failed"` depending on whether the login information matches the data in the given array.

   ```javascript
   const users = [
     { username: "Jane", password: "123456" },
     { username: "admin", password: "abc123" },
   ];

   const login = function (username, password) {
     // TODO: Your code here
   };

   login("Jane", "123456"); // => "Login Successful"
   login("Jane", "5321"); // => "Login Failed"
   login("Mark", "123456"); // => "Login Failed"
   login("admin", "abc123"); // => "Login Successful"
   login("admin", "aaabc123"); // => "Login Failed"
   ```

3. Write a function `onlyStrings` that accepts an array of strings, numbers, and booleans, and returns a new array with only the strings.

   ```javascript
   const onlyStrings = function (array) {
     // TODO: Your code here
   };

   onlyStrings([0, 1, "Hello", true, 4, "World", 6]); // => ["Hello", "World"]
   onlyStrings(["John", 87, true, 26, "Doe", false]); // => ["John", "Doe"]
   ```

4. Write a function `range` that accepts two number arguments and returns a string of all the numbers in between the two values in an acceding order, `start` and `end` are included and if only one value is provided then consider that the other value is zero.

   ```javascript
   const range = function (start, end) {
     // TODO: Your code here
   };

   range(5, 8); // => "5, 6, 7, 8"
   range(8, 5); // => "5, 6, 7, 8"
   range(5); // => "0, 1, 2, 3, 4, 5"
   range(-5); // => "-5, -4, -3, -2, -1, 0"
   ```

5. Write a function `onlyOddNumbers` that accepts an array of numbers and returns a new array with only the odd numbers.

   ```javascript
   const onlyOddNumbers = function (numbers) {
     // TODO: Your code here
   };

   onlyOddNumbers([0, 1, 2, 3, 4, 5, 6]); // => [1, 3, 5]
   onlyOddNumbers([0, 12, 6]); // => []
   ```

6. Write a function `maximumNumber` that accepts an array of numbers and returns the highest number in the array.

   ```javascript
   const maximumNumber = function (numbers) {
     // TODO: Your code here
   };

   maximumNumber([0, 5, 2, 10, 8, 6]); // => 10
   maximumNumber([0, 5, 6]); // => 6
   ```

7. Write a function `reversString` that accepts a string and returns the string reversed, don't use `.reverse()`.

   ```javascript
   const reversString = function (string) {
     // TODO: Your code here
   };

   reversString("Hello"); // => "olleH"
   reversString("John"); // => "nhoJ"
   ```

8. Write a function `onlyEven` that accepts an array of numbers and returns the same array with only the even numbers, make sure not to create a new array.

   ```javascript
   // make sure to use the same array
   const onlyEven = function (numbers) {
     // TODO: Your code here
   };

   onlyEven([0, 1, 2, 3, 4, 5, 6]); // => [0, 2, 4, 6]
   onlyEven([1, 9, 2, 3, 4]); // => [2, 4]
   ```

   HINT: check out how the method `splice` with arrays.

9. Write a function `createUser` that accepts two string arguments, `username` and `password`, and adds the new user to the `allUsers` array returning a message `"Registration successful"`. Make sure to check if the username of the new user matches any of the usernames from existing users, if it does, return a message saying `"That username is not available"` instead.

   ```javascript
   const allUsers = [
     { username: "Jane", password: "123456" },
     { username: "admin", password: "abc123" },
   ];

   const createUser = function (username, password) {
     // TODO: Your code here
   };

   createUser("James", "123456"); // => "Registration successful"
   allUsers; // => [{username: "Jane", password: "123456"}, {username: "admin", password: "abc123"}, {username: "James", password: "123456"}]

   createUser("Jane", "5321"); // => "That username is not available"
   allUsers; // => [{username: "Jane", password: "123456"}, {username: "admin", password: "abc123"}, {username: "James", password: "123456"}]

   createUser("Mark", "22222"); // => "Registration successful"
   allUsers; // => [{username: "Jane", password: "123456"}, {username: "admin", password: "abc123"}, {username: "James", password: "123456"}, {username: "Mark", password: "22222"}]

   createUser("admin", "abc123"); // => "That username is not available"
   allUsers; // => [{username: "Jane", password: "123456"}, {username: "admin", password: "abc123"}, {username: "James", password: "123456"}, {username: "Mark", password: "22222"}]
   ```

10. Write a function `convertToObject` that accepts an array and returns an object containing the values with the corresponding index as keys.

    ```javascript
    const convertToObject = function (array) {
      // TODO: Your code here
    };

    convertToObject(["one", "two", "three"]); // => { 0: "one", 1: "two", 2: "three" }
    convertToObject(["Hello", "World", "!!!"]); // => { 0: "Hello", 1: "World", 2: "!!!" }
    ```

### Advanced Practice

1. Write a function `sumArguments` that returns the sum of all arguments passed to the function. Make sure not to use parameters.

   ```javascript
   const sumArguments = function () {
     // TODO: Your code here
   };

   sumArguments(1, 2); // => 3
   sumArguments(1, 2, 3, 4); // => 10
   sumArguments(4, 5, 6, 7, 8); // => 30
   sumArguments(1); // => 1
   sumArguments(); // => 0
   ```

   HINT: read about `arguments`.

2. Write a function `sort` that accepts an unordered array of numbers and returns the same array in descending order. Do NOT use the built-in method `sort`.

   ```javascript
   // make sure to use the same array
   const sort = function (numbers) {
     // TODO: Your code here
   };

   sort([0, 1, 2, 3, 4, 5, 6]); // => [6, 5, 4, 3, 2, 1, 0]
   sort([3, 6, 2, 0, 4, 1, 5]); // => [6, 5, 4, 3, 2, 1, 0]
   ```

3. Write a function `compareArrays` that accepts two arrays, and returns true if all the array values are present in both arrays.

   ```javascript
   const compareArrays = function (arrayOne, arrayTwo) {
     // TODO: Your code here
   };

   compareArrays(["one", "two", "three"], ["one", "two", "three"]); // => true
   compareArrays(["one", "two", "three"], ["one", "three", "two"]); // => true
   compareArrays(["one", "two", "four"], ["one", "two", "three"]); // => false
   compareArrays(["one", "two"], ["one", "three", "two"]); // => false
   compareArrays(["one", "two", "three"], ["one", "two"]); // => false
   ```

4. Write a function `isPalindrome` that accepts a string and returns `true` or `false` depending on whether the string is a palindrome or not, before solving read below the criteria for the right way to solve it.

   ```javascript
   // - Must NOT use any string methods ( keep in mind `.length` is not a method, it is a property )
   // - Must NOT use any array methods ( keep in mind `.length` is not a method, it is a property )
   // - Must be solved with for loops
   // - Solve depending on the desired level below:
   //    - Basic: No special restrictions, ony the first three points mentioned above
   //    - Intermediate: Using only one for loop and no variables outside of it
   //    - Advanced: Using only one for loop and no variables outside of it and solution works on a string that has random empty spaces inside (not consecutive)
   //    - Master: Same as Advanced but works with consecutive empty spaces

   const isPalindrome = function (string) {
     // TODO: Your code here
   };

   isPalindrome("dad"); // => true
   isPalindrome("dads"); // => false

   // Advanced
   isPalindrome("a bcdcba"); // => true
   isPalindrome("abc d cb a"); // => true
   isPalindrome("was it a car or a cat i saw"); // => true
   isPalindrome("abc xd cb a"); // => false

   // Master
   isPalindrome("a                      bc d cb a"); // => true
   isPalindrome("abc cb                              a"); // => true
   isPalindrome("      abc  dx xd cb                         a"); // => true
   isPalindrome(
     "         a                      b              c d cb                      a"
   ); // => true
   ```
