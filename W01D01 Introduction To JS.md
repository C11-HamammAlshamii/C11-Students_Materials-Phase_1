# Introduction To JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- The definition of JavaScript
- Knowing the basic JavaScript value types
- Using the console to create JavaScript expressions

## JavaScript

### What is JavaScript

JavaScript is mainly a client-side scripting or programming language that is used to implement dynamic features for the web, it can be run on most browsers and especially the mainstream browsers such as Google Chrome, Firefox, Internet Explorer, and Safari. To write and run JavaScript code on Google Chrome you can open the console by right-clicking the page and then choosing inspect or by opening the `Console` tab. You can also use the following shortcuts if you are on Windows `Ctrl + Shift + i` or `F12` and on macOS, you can use `Option + Command + i` or `F12`.

### What Is Syntax

In computer science, the syntax of a computer language is the set of rules that defines the combinations of symbols that are considered to be correctly structured statements or expressions in that language.

Try the following using the Console:

```javascript
// Using mathematical symbols it is possible to form a JavaScript expression
1 + 1;
9 - 5;
3 * 4;
8 / 2;
```

### Basic Value Types

Let's take a look at some of the value types in JavaScript.

```javascript
// 1- Strings: a JavaScript string stores a series of characters
// to create a string wrap the characters with double or single quotes  => "", ''
"This is an example of what a string looks like", "Another example";

// to create an expression to combine strings together use the `+` operator, known as string concatenation
"Hello " + "World"; // => "Hello World"

// 2- Numbers
120, 300, -56, 0, 1.3, 0.8;

// to perform mathematical operations in JS combine numbers and operators (+, -, *, /, %) in an expression,
// also in JS these operations will follow the Mathematical order of operations (PEMDAS)
100 + ((10 - 5) * 2) / 5; // => 102
10 % 2; // => 0
```

### Mixing Types

Since JavaScript isn't a strictly-typed language it is possible to mix different values of different types together.

Try the following:

```javascript
// an example of concatenating a string with a number
"I am " + 10 + " years old"; // => "I am 10 years old"

// in other strictly-typed languages it is not possible to add integers and float numbers together
10 + 5.5; // => 15.5

// an example of using arithmetic operators between numeric string and numeric values
"10" + 1; // => "101"
"10" - 5; // => 5
"10" / 5; // => 2
"10" * 5; // => 50
"10" % 2; // => 0
```

Mixing types makes the language a little bit beginner-friendly since errors will not be thrown when trying to mix types together which is a mistake usually done by beginners, but that doesn't mean that it doesn't have its downsides since when mixing types you might encounter unexpected behavior.

### Variables

Variables are containers used for storing values, they are similar to variables in mathematics.

There are three main ways to declare a variable in JavaScript using three different keywords, `var`, `let`, and `const`.

### Defining A Variable And Assignment

The basic syntax for defining a variable:

```javascript
// the difference between const and let is that when using const it won't allow a new value to be reassigned to the variable,
// while when using let, it allows the reassignment of values for the same variable
const ourVariable = "variable value";
let anotherVariable = 10;

// in order to reassign a value, you can just use the following syntax
ourVariable = 10; // => Uncaught TypeError: Assignment to constant variable.
anotherVariable = 20;

// to access the value of a variable just use it's name
anotherVariable; // => 20

// you can notice that the value of the variable stays the same even if the reference has changed (there are exceptions for this
// but it will be for a later lesson)
let a = 10;
let b = a;
a = 20;
a; // => 20
b; // => 10

// while reassigning you can use the current value of the variable to modify it and assign it back to the same variable
let c = 10;
c = c + 5;
c; // => 15

let string = "John";
string = string + " Doe";
string; // => "John Doe"

// if you do not assign a value to the variable it will be given a value of undefined
let anotherVariable;
anotherVariable; // => undefined

const ourVariable; //Uncaught SyntaxError: Missing initializer in const declaration

// using the keyword var was the old way of defining variables. You can still see it being used but it is better to
// work with let and const instead.
var variableName = "cat";
```

### Naming Variables

When naming variables keep in mind the following:

- The name must begin with a letter or `$` or `_`.
- You can't name a variable with a reserved keyword.
- The name can contain a combination of letters, `$`, `_`, and digits.
- The name is case sensitive which means you can create a variable with the same name but different capitalization.
- This isn't a rule but it is good practice to use camelCase while naming variables.
- Try to use descriptive names to make it easier to understand what the variable is supposed to hold by just reading the name.

```javascript
// valid variable names
let variable;
let $variable;
let _variable;
let variable10$$_1;

// invalid variable names (starting with digits or symbols other than $ and _)
let 10variable;
let #variable;

// invalid variable names (includes reserved keywords)
let var;
let let;
let function;
let const;
```

### Writing A Program

Something that you need to understand about coding is that computers will follow all of the instructions provided in detail. Unlike humans, computers aren't capable of performing intuitive leaps while reading instructions.

An example of an intuitive leap would be if you would ask another human to bring you a cup of tea. They will be able to intuitively understand a vague request so they will choose the right kind of tea (usually black if not specified or they can ask if they aren't sure) also they will bring sugar and choose the right kind of cup for it without you having to specify it, while computers on the other hand must have very detailed instructions in the right order to be able to fulfill the request.

Luckily, you are able to communicate with the machine by using a common language such as JavaScript. In summary, to create a program you will have to provide a series of detailed instructions with a language your machine understands.

The code is read from top to bottom and from left to right, if you would like to add a comment in the program to explain some code you could use `//`. Comments will be ignored while running the program.

An example of understandable language:

```javascript
// In JavaScript you will have some keywords or symbols to make the communication easier

// an example of reserved keywords  => function, if , else , console
// an example of reserved symbols   => {}, [], <, >, "

// An example of combining symbols and some keywords to enable us to log the word `Hello` in the console
console.log("Hello");
console.log(1 + 1);
```

### Practice

Open the console and solve the following questions

1. Predict the value of the following expressions then try them out in the console

   ```javascript
   9 + 1 * 5; // ?
   9 % 2; // ?
   (9 / 3) * (10 - 7); // ?
   21 / 3 + 3 * 9 * 9 + 5; // ?
   36 / 9 + 48 - 10 / 2; // ?
   ```

2. Figure out the syntax errors in the following variable declarations, and fix them.

   ```javascript
   const @name = 'John';
   const 'age' = 10;
   const const = "Constant";
   const variable 1 = "value";
   ```

3. Define the following variables.

   - Define a variable `color` containing your favorite color.

   - Define a variable `positiveNumber` containing any positive number.

   - Define a variable `food` containing your favorite food.

   - Define a variable `PhoneNumber` containing a phone number.

4. Before trying the following expressions try to predict the outcome.

   ```javascript
   10 + "10"; // ?
   "10" + "10"; // ?
   10 + 10 + "5"; // ?
   "Hello" + 1; // ?
   "10" + 5 + 5; // ?
   "20" - 10; // ?
   "9" - "5"; // ?
   "19" - "13" + 17; // ?
   5 + 6 + "4" + 9 - 4 - 2; // ?
   ```

5. Using string concatenation write an expression that represents your first name, last name, gender, and nationality.

6. Write an expression that represents the number of seconds in 30 days.

7. Reassign the value of `a` to make the following expression equal to nine.

   ```javascript
   let a;
   let b = 3;
   let c = 10;

   c - b * c + a;
   ```

8. Using the variables below write an expression that calculates the total amount for buying two coffee cups.

   ```javascript
   // tip and tax amounts are a percentage of the total billed amount
   const tip = 0.1;
   const taxRate = 0.08;
   const coffeeCupPrice = 6;
   ```

9. Write an expression that represents the average grade of an exam, knowing that in a class of ten students, five of them got 24/30, two of them got 16/30 and the remainder got 29/30.

10. Write expressions that calculate the area and the perimeter of a rectangle with a length of 10m and a width of 5m.

11. Write expressions that calculate the diameter and the circumference of a circle with a radius of 5m.

12. Write an expression that converts 30 degrees Celsius to Fahrenheit.
