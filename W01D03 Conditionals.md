# Conditionals In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Booleans
- Comparison operators
- Logical operators
- Conditional statements
- Truthy and falsy values

## Conditionals

### Booleans

A boolean is a data type in JavaScript that can be either `true` or `false`, booleans also have numeric values of `1` and `0` respectively when mixed with numbers.

### Comparison Operators

Comparison operators compare two values and return a boolean value that represents whether the expression is true or false.

Examples of comparison operators:

```javascript
// greater than
10 > 5; // => true

// less than
10 < 5; // => false

// greater than or equal
10 >= 10; // => true

// less than or equal
10 <= 5; // => false

// strictly equal operator `===` is used to compare if both values are equal and their types are the same,
"Hello" === "World"; // => false
5 === 5; // => true
5 === "5"; // => false

// you can use `!==` to check if the values aren't strictly equal to each other
"Hello" !== "World"; // => true
5 !== "5"; // => true

// loosely equal operator `==` is used to compare if both values are the same regardless of the type,
// it is not recommended to use this form of equality comparison because it may lead into unexpected results
5 == 5; // => true
5 == "5"; // => true
5 != "5"; // => false
```

### Logical Operators

Logical operators are used to evaluate an expression, even though logical operators are used to work with boolean values,
it is still possible to use them with other data types, but for this lesson, we will be using them to evaluate expressions that result in a boolean value.

Examples of logical operators:

```javascript
// the "AND" logical operator `&&` is used to evaluate if the whole statement is true or false, if both expressions/booleans are true
// then it will return true but if either of them is false it will return false
true && true; // => true
true && false; // => false
false && true; // => false
false && false; // => false
8 + 2 > 5 && "Hello" === "Hello"; // => true
8 + 2 > 5 && "Hello" === "World"; // => false

// the "OR" logical operator `||` is used to evaluate if the whole statement is true or false, if either or both of
// the expressions/booleans are true then it will return true and if both are false it will return false
true || true; // => true
true || false; // => true
false || true; // => true
false || false; // => false
1 > 5 || "Hello" === "Hello"; // => true

// the "NOT" Logical operator `!` is used to reverse the logical state of the value, as mentioned before
!true; // => false
!false; // => true
```

### Conditional Statements

Conditional Statements are used to execute blocks of code if certain conditions are met, it is possible to chain multiple statements altogether.

Examples of conditional statements:

```javascript
// using the keyword `if` we can create a conditional statement that executes a block of code if the condition is true
if (true) {
  // run this block of code
}

if (1 < 10) {
  // run this block of code
}
```

```javascript
// using the keyword `else` we specify a block of code to be executed if all previous conditions are false
if (false) {
  // since the condition is false, this block of code will be ignored
} else {
  // run this block of code
}

if (5 === 2) {
  // since the condition is false, this block of code will be ignored
} else {
  // run this block of code
}
```

```javascript
// using the keyword `else if` enables us to chain multiple conditions instead of just having an if/else statement
if (false) {
  // since the condition is false, this block of code will be ignored
} else if (true) {
  // run this block of code, because it was the first condition to succeed
} else if (true) {
  // even though this is also true it will not run since after executing the previous block of code it will stop checking
  // the other statements, which results in this one being ignored
} else {
  // since one of the previous conditions is true, this block of code will also be ignored
}

const name = "John";
if (name === "Mark") {
  // since the condition is false, this block of code will be ignored
} else if (name === "John") {
  // run this block of code
} else {
  // since one of the previous conditions is true, this block of code will be ignored
}
```

### Truthy and falsy values

```javascript
// in javaScript all values are considered truthy values (value is considered true in a boolean context) except
// falsy values which are considered false, some of the falsy values are `0`, `undefined`, `null`, `""` and `false`

if (1) {
  // run this block of code
}

if ("string") {
  // run this block of code
}

if (0) {
  // ignore this block of code
}

if (undefined) {
  // ignore this block of code
}
```

Example of what we have learned so far:

```javascript
// Write a function `getGrade` that accepts a number argument and returns a string representing the grade
// 0  - 49  =>  F
// 50 - 59  =>  D
// 60 - 69  =>  C
// 70 - 79  =>  B
// 80 - 100  =>  A

const getGrade = function (grade) {
  if (grade >= 80) {
    return "A";
  } else if (grade >= 70) {
    return "B";
  } else if (grade >= 60) {
    return "C";
  } else if (grade >= 50) {
    return "D";
  } else {
    return "F";
  }
};

getGrade(90); // => A
getGrade(51); // => D
```

### Pulse Check

1. Figure out the syntax errors in the following, and fix them.

   ```javascript
  
   // 1
   if (10 =< 10){
   }
   
   // 2
   if 5 > 3 {
   }
   
   // 3
   if (5 > 10){
   }
   else(true){
   }
   
   // 4
   if (2 < 3 && 7 > 10)
   }
   
   // 5
   if ("hello" = "hello"){
   }
 
   ```

2. Predict the value of the following expressions and explain why.

   ```javascript
   true && true && false;

   true || (true && false);

   5 === 2 || 1 < 10;

   (!false && true) || (!true && true);
   ```

3. Write a function `legalAge` that accepts one argument `age` and returns `true` if the age is over or equal to eighteen and `false` if it is below that.

   ```javascript
   const legalAge = function (age) {
     // TODO: Your code here
   };

   legalAge(20); // => true
   legalAge(18); // => true
   legalAge(17); // => false
   ```

4. Write a function `isItMyName` that accepts one argument `name` and returns `true` if the `name` is the same as your name and return `false` if it is not.

   ```javascript
   const isItMyName = function (name) {
     // TODO: Your code here
   };

   // the following output depends on the assumption that your name is `John`
   isItMyName("Mark"); // => false
   isItMyName("Sarah"); // => false
   isItMyName("John"); // => true
   ```

5. Write a function `positiveOrNegative` that accepts one argument `number` and returns a string saying whether the number is positive, negative, or if it is neutral number like zero.

   ```javascript
   const positiveOrNegative = function (number) {
     // TODO: Your code here
   };

   positiveOrNegative(10); // => 10 is positive
   positiveOrNegative(-10); // => -10 is negative
   positiveOrNegative(0); // => 0 is neither positive nor negative
   ```

### Practice

1. Write a function `toLowerOrUpperCase` that accepts two arguments, `string` and `strCase`, and returns the string in lower case or upper case depending on what was specified in the second parameter. Check out the following built-in methods then solve the question.

   ```javascript
   // you could use the `toLowerCase` string methods to convert a string into lower case
   "HeLlO wOrlD".toLowerCase(); // => "hello world"

   // you could use the `toUpperCase`string methods to convert a string into upper case
   "HeLlO wOrlD".toUpperCase(); // => "HELLO WORLD"

   const toLowerOrUpperCase = function (string, strCase) {
     // TODO: Your code here
   };

   toLowerOrUpperCase("HELLO WORLD", "lower"); // => "hello world"
   toLowerOrUpperCase("my name is john", "upper"); // => "MY NAME IS JOHN"
   toLowerOrUpperCase("my name is john", "mixed"); // => "String case must be lower or upper"
   ```

2. Write a function `howLong` that accepts one argument `word` and returns whether the word is `short`, `medium`, `long`, or `very long`. Check out the following examples about the length property then answer the question.

   ```javascript
   // one handy string property `length` is used to return the length of a string
   "hello".length; // => 5
   "hello world".length; // => 11 (notice how the space in between the words counted as a character)

   // - words less than 5 are considered short words
   // - words in between 5 and 8 are considered medium words
   // - words in between 9 and 13 are considered long words
   // - words more than 13 are considered very long words

   const howLong = function (word) {
     // TODO: Your code here
   };

   howLong("and"); // => "short"
   howLong("function"); // => "medium"
   howLong("corresponding"); // => "long"
   howLong("Supercalifragilisticexpialidocious"); // => "very long"
   ```

3. Check out the following examples and solve the question.

   ```javascript
   // since strings store a series of characters in an ordered way
   // we could use the index of the character to access the character in the string
   // each character in the string has its own unique identifying number (index)
   // the index value starts at zero and for every letter that is added after the first one, the index will be incremented by one

   "hello"[0]; // => h
   "hello"[1]; // => e
   "hello"[2]; // => l
   "hello"[3]; // => l
   "hello"[4]; // => o

   // write a function `startsWith` that accept two string arguments `string`, `character` and returns true if the string
   // starts with that character. It doesn't matter if it's lowercase or uppercase

   const startsWith = function (string, character) {
     // TODO: Your code here
   };
   startsWith("Hello", "h"); // => true
   startsWith("hello", "h"); // => true
   startsWith("hello", "a"); // => false
   startsWith("World", "h"); // => false
   startsWith("World", "a"); // => false
   ```

4. Write a function `endsWith` that accepts two string arguments, `string` and `character`, and returns true if the string ends with that character.

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

5. Write a function `deposit` that accepts an argument `amount` and returns the deposited amount. The function should only accept positive number arguments otherwise return `"Please enter a positive number"` if it is not positive and return `"Please enter a number"` if the type of the argument is not a number.

   ```javascript
   const deposit = function (amount) {
     // TODO: Your code here
   };

   deposit(100); // => 100
   deposit(250); // => 250
   deposit(-100); // => "Please enter a positive number"
   deposit("100"); // => "Please enter a number"
   ```

   HINT: read about how to use `typeof` on MDN.

6. Write a function `oddOrEven` that accepts a number argument `number` and returns a string stating if the `number` is odd or even.

   ```javascript
   const oddOrEven = function (number) {
     // TODO: Your code here
   };

   oddOrEven(1); // => "1 is odd"
   oddOrEven(2); // => "2 is even"
   oddOrEven(5); // => "5 is odd"
   oddOrEven(10); // => "10 is even"
   ```

   HINT: think about how to use `%` to solve the question.

7. Write a function `stringCase` that accepts a string argument `string` and returns whether the string is `all upper case` or `all lower case` or `mix case`.

   ```javascript
   const stringCase = function (string) {
     // TODO: Your code here
   };

   stringCase("JOHN"); // => "all upper case"
   stringCase("john"); // => "all lower case"
   stringCase("joHN"); // => "mix case"
   ```

8. Write a function `isLeapYear` that accepts a number argument `year` and returns true if the year is a leap year. Leap years are divisible by 4 but non-leap years are divisible by 100 with the exception of 400 (leap years are also divisible by 400).

   ```javascript
   const isLeapYear = function (year) {
     // TODO: Your code here
   };

   isLeapYear(2000); // => true
   isLeapYear(2004); // => true
   isLeapYear(2020); // => true
   isLeapYear(2096); // => true

   isLeapYear(1603); // => false
   isLeapYear(2021); // => false
   isLeapYear(2200); // => false
   isLeapYear(2500); // => false
   isLeapYear(2600); // => false
   isLeapYear(3000); // => false
   ```

9. Write a function `login_v01` that accepts two string arguments, `username` and `password`, and returns a string `login successful` if the username length is more than 6 and the password length is more than or equal to 8 otherwise return `login failed`.

   ```javascript
   const login_v01 = function (username, password) {
     // TODO: Your code here
   };

   login_v01("John", "1234"); // => "login failed"
   login_v01("John", "12345678"); // => "login failed"
   login_v01("john_doe", "123456"); // => "login failed"
   login_v01("john_doe", "12345678"); // => "login successful"
   ```

10. Modify `login_v01` to check whether the username and password match the corresponding values from the account list below. Make sure not to remove the length validation from the previous question and check the examples below for more information.

    ```javascript
    // accounts:
    // 1- username: "john_doe", password: "koljgwEA"
    // 2- username: "jane_doe", password: "12345678"

    const login_v02 = function (username, password) {
      // TODO: Your code here
    };

    // usernames are not case sensitive but passwords are
    login_v02("JOHN_DOE", "koljgwEA"); // => "login successful"
    login_v02("john_doe", "KOLJGWEA"); // => "login failed"
    // both information need to be true to return a success message
    login_v02("john_doe", "12345678"); // => "login failed"
    login_v02("jane_doe", "koljgwEA"); // => "login failed"
    login_v02("jane_doe", "12345678"); // => "login successful"
    ```

11. Modify `login_v02` to return the appropriate reason for failed login attempts. Check below for more information on the failure messages and keep the validation from the previous questions.

    ```javascript
    // 1- `username must be more than 6 characters long`
    // 2- `password must be at least 8 characters long`
    // 3- `username doesn't exist`.
    // 4- `wrong password`.

    // accounts:
    // 1- username: "john_doe", password: "koljgwEA"
    // 2- username: "jane_doe", password: "12345678"

    const login_v03 = function (username, password) {
      // TODO: Your code here
    };

    login_v03("john_doe", "koljgwEA"); // => "login successful"
    login_v03("jane_doe", "12345678"); // => "login successful"

    login_v03("john", "12345678"); // => "username must be more than 6 characters long"
    login_v03("jane_doe", "123456"); // => "password must be at least 8 characters long"

    login_v03("MrPotato", "12345678"); // => "username doesn't exist"
    login_v03("jane_doe", "123456789"); // => "wrong password"
    ```

### Advanced Practice

1. Write a function `letterInString` that accepts two string arguments, `string` and `letter`, and returns `true` if the letter is inside the string and returns `false` if it doesn't.

   ```javascript
   const letterInString = function (string, letter) {
     // TODO: Your code here
   };

   letterInString("Hello", "E"); // => true
   letterInString("Hello", "Z"); // => false
   ```

   HINT: search for the correct method to use on [MDN](https://developer.mozilla.org/en-US/).

2. Write a function `guessTheSquareRoot` that accepts two number arguments, `number` and `squareRoot`, and returns a string `"correct"` if the guess is correct and returns `"incorrect"` if the guess is incorrect.

   ```javascript
   const guessTheSquareRoot = function (number, squareRoot) {
     // TODO: Your code here
   };

   guessTheSquareRoot(4, 2); // => "correct"
   guessTheSquareRoot(4, 3); // => "incorrect"
   ```

   HINT: search for the correct method to use on [MDN](https://developer.mozilla.org/en-US/).

3. Write a function `randomMove` that when invoked would return a string `"rock"` or `"paper"` or `"scissors"` randomly.

   ```javascript
   const randomMove = function () {
     // TODO: Your code here
   };

   randomMove(); // => "rock"
   randomMove(); // => "rock"
   randomMove(); // => "paper"
   randomMove(); // => "scissors"
   ```

4. Write a function `rockPaperScissors_v01` that accepts a string argument with only the following values, `"rock"`, `"paper"`, `"scissors"` and returns `"invalid move"` if anything else is passed in. Otherwise, return `"valid move"`.

   ```javascript
   const rockPaperScissors_v01 = function (move) {
     // TODO: Your code here
   };

   rockPaperScissors_v01("rock"); // => "valid move"
   rockPaperScissors_v01("paper"); // => "valid move"
   rockPaperScissors_v01("scissors"); // "valid move"
   rockPaperScissors_v01("knife"); // => "invalid move"
   ```

5. Modify `rockPaperScissors_v01` to return `"you win"`, `"you lose"`, and `"it is a draw"` depending on the user input and the randomly selected move. Read the comments for more explanation.

   ```javascript
   // game rules:
   // 1- rock beats scissors
   // 2- paper beats rock
   // 3- scissors beats paper

   // important:
   // use the `randomMove` function that you have created previously (it must be working correctly)
   // read the comments inside the function to know how to get the random value and save it in a variable to use it
   // if the user input would beat the random input then return `you win`
   // if the user input would lose against the random input then return `you lose`
   // if the user input is the same as the random input then return `it is a draw`
   // keep the move validation from the previous question

   const rockPaperScissors_v02 = function (move) {
     // use randomMove to get the value of the random move
     const randomMoveForComputer = randomMove();
     // randomMoveForComputer; => rock (use it by referencing it's name, the random value should stay the same)
     // TODO: Your code here
   };

   rockPaperScissors_v02("rock"); // => "you win"
   rockPaperScissors_v02("paper"); // => "you win"
   rockPaperScissors_v02("rock"); // => "you lose"
   rockPaperScissors_v02("scissors"); // => "you win"
   rockPaperScissors_v02("paper"); // => "it is a draw"
   ```
