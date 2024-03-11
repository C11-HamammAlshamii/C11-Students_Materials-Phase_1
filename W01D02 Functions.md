# Functions In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- The definition of functions
- Creating a function and invoking it
- Understanding parameters and arguments
- Using the functions as values

## Functions

### What Are Functions

A function is a snippet of code (instructions to perform a specific action), that can be called (executed) by other code or by itself. In order to invoke (call) the function you will have to use the name of the function followed by parentheses `()`. There are also functions that are called `anonymous function` that do not have a specified name.

There are two ways of creating a function, `function declaration`, and `function expression`. For this lesson, we will focus on creating functions using function expressions.

Something to keep in mind, while naming functions, parameters, and variables in JS it is considered good practice to write the names using camel case. This means to always start the first word with a lowercase letter and for the rest of the following words use uppercase letters for the first letter of each word, `updateUser`, `calculateAgeInMinutes`, and `cube`.

### Define A Function

The basic syntax for creating functions:

```javascript
// an example for defining a function named "ourFunction" by using a function expression.
const ourFunction = function () {
  // Executable code
};

// an example for defining a function named "ourFunction" by using function declaration
function ourFunction() {
  // Executable code
}
```

You might have noticed the similarities with both ways but explain them in more detail.

`function`: is a reserved keyword that indicates the intent to define a function.

`parentheses ()`: contain the parameters that we will use in our function.

`curly brackets {}`: contains the executable code if any is present in the function.

When it comes to invoking the function both of the ways can be invoked in the same way which is by adding parentheses after the function name `ourFunction()`.

### Parameters And Arguments

In order to make our functions receive inputs we have to use parameters. We add parameters in between the parentheses
and use them in the code as placeholders for the input value. Whenever the value of the parameter is passed in as an argument to the function, the parameters will be replaced with the real value.

Let's create a function that prints out an introduction about yourself.

```javascript
// the function has two parameters the "name", and "age" that need to be provided as arguments when invoking the function
const introduction = function (name, age) {
  // console.log() is an invocation of a method (function) that will print the arguments passed to it to the console
  console.log("Hello my name is " + name + " and i am " + age + " years old");
};

// when invoking the function we pass in the arguments in between the parentheses
// make sure to use proper syntax, use the right value types, and to pass the arguments in the correct order
introduction("John", 20); // => Hello my name is John and i am 20 years old
introduction("Mark", 28); // => Hello my name is Mark and i am 28 years old
```

Let's create a function that squares the value passed to it.

```javascript
const square = function (number) {
  console.log(number * number);
};

square(2); // => 4
square(4); // => 16
```

### Functions As Values

In the previous examples we were printing out the result and that isn't helpful especially if we need to use the output of the function as a value somewhere else in the code, in order for the function to have a value we need to use the keyword `return` in the body of the function.

let's explore how functions can have values.

```javascript
const add = function (firstNumber, secondNumber) {
  return firstNumber + secondNumber;
};

const subtract = function (firstNumber, secondNumber) {
  return firstNumber - secondNumber;
};

// if we invoke the function it should return a value
add(10, 20); // => 30
subtract(10, 5); // => 5

// we can use the return value of a function in other parts of the code, like the following example
10 + add(5, 5) + subtract(10, 8); // => 22
add(add(5, 5), 5); // => 15

// what is the value of the function if we do not use the return keyword?
const multiply = function (numberOne, numberTwo) {
  numberOne * numberTwo;
};

multiply(5, 5); // => undefined

// undefined is a data type that represents not having a value assigned
// it is possible to mix other data types with undefined, the result will vary depending on the data types involved
```

### Built-in Functions

There is a lot of functionality available in JavaScript in the form of built-in functions that are used to perform various tasks.

```javascript
// console.log() would print out the arguments to the console
console.log(10);
// => 10

// Math.round() would round the number provided as an argument to the nearest number
Math.round(1.6); // => 2
Math.round(1.5); // => 2
Math.round(1.2); // => 1
```

### Pulse Check

1. Figure out the syntax errors in the following functions, and fix them.

   ```javascript
   const myFunction = function parameter) {}
   const my Second Function = function (parameter) {}
   const function = function (parameter) {}
   const functionName = function (paramOne paramTwo) {}
   ```

2. Write a function `sayHello` that returns `Hello` when executed.

   ```javascript
   const sayHello = function () {
     // TODO: Your code here
   };

   // an example of the output value when executing the function
   sayHello(); // => "Hello"
   ```

3. Write a function `myAge` that accepts one argument `age` and returns the age when executed.

   ```javascript
   const myAge = function (age) {
     // TODO: Your code here
   };

   // an example of the output value when executing the function
   myAge(20); // => 20
   myAge(30); // => 30
   ```

4. Write a function `incrementOne` that accepts one argument `number` and returns the number incremented by one when executed.

   ```javascript
   const incrementOne = function (number) {
     // TODO: Your code here
   };

   // an example of the output value when executing the function
   // add one to the the number that was passed in
   incrementOne(20); // => 21
   incrementOne(34); // => 35
   ```

5. Write a function `greet` that accepts one argument `name` and returns a string saying as shown below.

   ```javascript
   const greet = function (name) {
     // TODO: Your code here
   };

   // an example of the output value when executing the function
   greet("John"); // => "Hello John"
   greet("Mark"); // => "Hello Mark"
   ```

### Practice

1. Write a function `double` that accepts one argument `number` and returns the number doubled.

   ```javascript
   const double = function (number) {
     // TODO: Your code here
   };

   double(2); // => 4
   double(5); // => 10
   double(10); // => 20
   ```

2. Write a function `fullName` that accepts string arguments, firstName and lastName then returns a string containing your full name combined.

   ```javascript
   const fullName = function (firstName, lastName) {
     // TODO: Your code here
   };

   fullName("John", "Doe"); // => "John Doe"
   fullName("Mark", "Smith"); // => "Mark Smith"
   ```

3. Write a function `average` that accepts two number arguments and returns the average of these numbers.

   ```javascript
   const average = function (a, b) {
     // TODO: Your code here
   };

   average(20, 25); // => 22.5
   average(15, 7); // => 11
   ```

4. Using the defined functions below and your average function try to guess the output of the following expressions without executing the functions.

   ```javascript
   const square = function (number) {
     return number * number;
   };

   const cube = function (number) {
     return number * number * number;
   };

   // guess the following before trying it in the console
   cube(25) + 20; // => ?
   square(5) + cube(2); // => ?
   square(10 / 5) + cube(2 + 1); // => ?
   average(square(average(6, 2)), cube(4)); // => ?
   ```

5. Write a function `totalBill` that accepts three arguments `total`, `taxPercentage`, `tip`, and returns the total after adding the tax and the tip.

   ```javascript
   const totalBill = function (total, taxPercentage, tip) {
     // TODO: Your code here
   };

   totalBill(40, 0.16, 2); // => 48.4
   totalBill(10, 0.16, 0); // => 11.6
   ```

6. Write a function `ageInHours` that accepts a number argument `ageInYears` and returns the age in hours (ignore leap years).

   ```javascript
   const ageInHours = function (ageInYears) {
     // TODO: Your code here
   };

   ageInHours(10); // => 87600
   ageInHours(19); // => 166440
   ```

7. Write a function `calculateProfit` that accepts three arguments `unitsSold`, `unitCost`, `unitPrice`, and returns the net profit.

   ```javascript
   const calculateProfit = function (unitsSold, unitCost, unitPrice) {
     // TODO: Your code here
   };

   calculateProfit(1, 3, 5); // => 2
   calculateProfit(4, 2, 5); // => 12
   calculateProfit(10, 5, 15); // => 100
   ```

8. Write a function `floor` that accepts one number argument, `number`, and returns the number as an integer.

   ```javascript
   const floor = function (number) {
     // TODO: Your code here
   };

   // the rounding is to the smallest number
   floor(5); // => 5
   floor(2.4); // => 2
   floor(0.2); // => 0
   floor(1.7); // => 1
   ```

   HINT: Look up `Math.floor()` on [MDN](https://developer.mozilla.org/en-US/).

9. Write a function `toThePowerOf` that accepts two number arguments, `base` and `exponent`, and returns the base to the exponent power.

   ```javascript
   const toThePowerOf = function (base, exponent) {
     // TODO: Your code here
   };

   toThePowerOf(2, 2); // => 4
   toThePowerOf(2, 3); // => 8
   toThePowerOf(4, 2); // => 16
   ```

   HINT: Look up `Math.pow()` on [MDN](https://developer.mozilla.org/en-US/).

10. Write a function `upperCase` that accepts a string argument `string` and returns the same string in upper case.

    ```javascript
    const upperCase = function (string) {
      // TODO: Your code here
    };

    upperCase("john"); // => "JOHN"
    upperCase("cat"); // => "CAT"
    upperCase("DOG"); // => "DOG"
    ```

    HINT: Look up `toUpperCase()` on [MDN](https://developer.mozilla.org/en-US/).

### Advanced Practice

1. Write a function `randomNumber` that returns a random value between zero and one (includes 0 but not 1).

   ```javascript
   const randomNumber = function () {
     // TODO: Your code here
   };

   randomNumber(); // => 0.5052417714491793
   randomNumber(); // => 0.32678224417562673
   randomNumber(); // => 0.43265697184952523
   ```

   HINT: Search for the right method to use on [MDN](https://developer.mozilla.org/en-US/).

2. Write a function `oneOrZero` that uses `randomNumber` to return either the number zero or one.

   ```javascript
   const oneOrZero = function () {
     // TODO: Your code here
   };

   oneOrZero(); // => 1
   oneOrZero(); // => 1
   oneOrZero(); // => 0
   ```

3. Write a function `randomRange` that accepts a positive number and returns a random number between zero and the passed in argument.

   ```javascript
   const randomRange = function (number) {
     // TODO: Your code here
   };

   // 10 and 0 are included
   randomRange(10); // => 10
   randomRange(10); // => 7
   randomRange(10); // => 1
   randomRange(10); // => 0
   ```

4. write a function `fromTo` that accepts two positive number arguments, `start` and `end`, returning a random number in between the `start` and the `end` value.

   ```javascript
   const fromTo = function (start, end) {
     // TODO: Your code here
   };

   // start is included but end is excluded
   fromTo(10, 20); // => 19
   fromTo(10, 20); // => 17
   fromTo(10, 20); // => 11
   fromTo(10, 20); // => 10
   ```

5. write a function `randomCharacter` that accepts a string argument `string` and returns a random character from that string.

   ```javascript
   const randomCharacter = function (string) {
     // TODO: Your code here
   };

   randomCharacter("John"); // => "h"
   randomCharacter("John"); // => "J"
   randomCharacter("John"); // => "o"
   randomCharacter("Cat"); // => "t"
   randomCharacter("Cat"); // => "a"
   randomCharacter("Cat"); // => "a"
   ```

HINT: Look up the following on MDN [character_access](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#character_access), [string_length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length#basic_usage).
