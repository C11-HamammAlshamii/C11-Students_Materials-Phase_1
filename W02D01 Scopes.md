# Scopes In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Defining a scope
- Global scope
- Local scope
- Closures

## Scopes

### What Are Scopes

Scopes represent the accessibility of `variables`, `functions`, etc. in the code depending on the location of these things. This means that depending on the scope, a variable might be visible in one region of the code but not in a different region.

There are two types of scopes in JavaScript, `Local Scope` and `Global Scope`. Local scope refers to the inside of the current scope, an example of that would be the inside of a function's code block where everything inside is considered the Local scope when executing the function meaning that all variables defined there will be accessible, and the Global scope will be the scope where the function is defined in.

When it comes to accessibility, Local scopes can access Global scopes, but not the other way around. This means that when trying to access a variable, it only goes outwards from the Local scope to other Global scopes.

Let's explore the Global scope.

```javascript
// Start of Global Scope

// an example of a Global variable used in the Local scope of a function
const person = "John";

const greet = function () {
  // start of Local Scope
  // the variable person doesn't exist in the Local scope of the function which will result in
  // the function looking for the variable in the outer scope that is considered Global to it
  return "Hello " + person;
  // End of Local Scope
};

greet(); // => "Hello John"
person; // => "John"

// an example to show that it is possible to reassign the value of a Global variable in the Local scope
let person = "Mark";

const updatePerson = function (newName) {
  // Start of Local Scope
  person = newName;
  return person;
  // End of Local Scope
};

updatePerson("Jane"); // => "Jane"
person; // => "Jane"
```

Let's explore the Local scope.

```javascript
// an example to show how the code is encapsulated within the function's scope and can't be accessed outside

const greeting = function (fName) {
  // Start of Local Scope
  // a Local scope variable is accessible inside the same scope but not from outside
  let firstName = fName;
  return "Hello " + firstName;
  // End of Local Scope
};

greeting("Mark"); // => "Hello Mark"
firstName; // =>  Uncaught ReferenceError: firstName is not defined
```

### Block Statements

Any Block statement that has its own code Block such as `if`, `else if`, and `else` doesn't create a Local scope by default, but by using `let` and `const` to define a variable inside it makes it act like a Local scope. Contrary to the old way of declaring variables with the `var` keyword that can be accessed from outside the Block statement.

```javascript
const example_1 = function () {
  // Local scope

  if (true) {
    // Block scope
    // these variables are only accessible inside the code Block
    const gender = "John";
    let age = 24;
  }

  console.log(gender); // ReferenceError: gender is not defined
  console.log(age); // ReferenceError: age is not defined
};

example_1();

const example_2 = function () {
  // Local scope
  if (true) {
    // Block scope
    // the variable can be accessed outside the Block scope since it was defined using `var`
    var isActive = true;
  }

  console.log(isActive); // true
};

example_2();
```

### Closures

A closure is the combination of a function bundled with references to its surrounding lexical environment. A closure gives you access to an outer function’s scope from an inner function.

Closures are used to persist data without having to define variables in the Global scope, and they are good for keeping some variables private.

```javascript
// an example of persisting data without using closures (using Global variables)
let lightSwitch_Global = "OFF";

const toggleLight = function () {
  if (lightSwitch_Global === "OFF") {
    lightSwitch_Global = "ON";
    return "the light is: " + lightSwitch_Global;
  } else {
    lightSwitch_Global = "OFF";
    return "the light is: " + lightSwitch_Global;
  }
};
// above we have a function that toggles a Global variable ON and OFF
//what if we had multiple functions that are controlling other light switches?
//they all would be using the same variable and that would result in a mess, so to solve that we could use closures

const toggle = function () {
  let lightSwitch_Local = "OFF";

  // this anonymous function is a closure function that has access to its own closure variable
  return function () {
    if (lightSwitch_Local === "OFF") {
      lightSwitch_Local = "ON";
      return "the light is: " + lightSwitch_Local;
    } else {
      lightSwitch_Local = "OFF";
      return "the light is: " + lightSwitch_Local;
    }
  };
};

// the variable will be equal to the return value of toggle so it will be equal to the closure function
const toggleLight_1 = toggle();
// we need a second invocation to be able to invoke the closure function
toggleLight_1(); // => 'the light is ON'
toggleLight_1(); // => 'the light is OFF'
toggleLight_1(); // => 'the light is ON'
// we can create another variable to control another light
const toggleLight_2 = toggle();
toggleLight_2(); // => 'the light is ON'
toggleLight_2(); // => 'the light is OFF'
toggleLight_1(); // => 'the light is OFF'
// now we have persisted data without using a Global variable
```

### Pulse Check

1. Create a Global variable `myFavoriteFood` and return its value in the function's local scope.

   ```javascript
   // make sure that the variable is in the Global scope
   const favoriteFood = function () {
     // TODO: Your code here
   };

   favoriteFood(); // => the value of `myFavoriteFood` variable
   ```

2. Create a function `updateFavoriteFood` that updates the value of `myFavoriteFood`

   ```javascript
   const updateFavoriteFood = function (newValue) {
     // TODO: Your code here
   };

   updateFavoriteFood("Pizza");
   favoriteFood(); // => "Pizza"
   ```

3. Use the following closure function to create two separate counters

   ```javascript
   const createCounter_v01 = function () {
     let counter = 0;

     // this anonymous function is a closure function that has access to its own closure variable
     return function () {
       return (counter += 1);
     };
   };
   ```

4. Modify `createCounter_v01` to take a parameter that represents the starting point for the counter

   ```javascript
   // instead of counting from zero it will take count from the value provided
   const createCounter_v02 = function (start) {
     // TODO: Your code here
   };
   ```

### Practice

1. Predict the value of the following variables and explain why.

   ```javascript
   let age = 25;
   if (true) {
     age = 30;
   }
   age; // ?

   const myName = "John";
   if (true) {
     const myName = "Jane";
   }
   myName; // ?
   ```

2. Predict the value of the following function invocations.

   ```javascript
   let number = 10;
   const func1 = function () {
     let number = 15;

     if (true) {
       let number = 24;
     }

     return number;
   };

   func1(); // ?

   const func2 = function (age) {
     age = 10;
     if (true) {
       let age = 24;
       age = 20;
     }

     return age;
   };

   func2(26); // ?
   ```

3. Write a function `countDown` that returns a number representing a count down value. With each invocation the number should be lower by one and at zero it will no longer decrement and instead it will return `"count down is over"`.

   > **Hint:** create a new variable `counter` at the global scope to hold the value.

   ```javascript
   const countDown = function () {
     // TODO: Your code here
   };

   countDown(); // => 4
   countDown(); // => 3
   countDown(); // => 2
   countDown(); // => 1
   countDown(); // => 0
   countDown(); // => "count down is over"
   ```

4. Write a function `countUp` that should do the opposite of `countDown`. With every invocation, the count value should be incremented by one.

   > **Hint:** use the same `counter` variable from the previous question.

   ```javascript
   const countUp = function () {
     // TODO: Your code here
   };

   countUp(); // => 4
   countUp(); // => 5
   countUp(); // => 6
   countUp(); // => 7
   countUp(); // => 8
   ```

5. Write a function `resetCount` that accepts a number argument `start` and updates the count variable to equal the starting value and return a string implying that.

   > **Hint:** use the same `counter` variable from the previous question.

   ```javascript
   const resetCount = function (start) {
     // TODO: Your code here
   };

   resetCount(0); // => "the count has been reset"
   countUp(); // => 1
   resetCount(10); // => "the count has been reset"
   countUp(); // => 11
   ```

6. Write a function `addToList` that accepts a string argument `toDo` and returns the current list as a string. Every time we invoke the function it should return the old toDo item plus the new one.

   > **Hint:** create a new variable `allList` at the global scope to hold the value.

   ```javascript
   const addToList = function (toDo) {
     // TODO: Your code here
   };

   addToList("Eat"); // => 'Eat'
   addToList("Play"); // => 'Eat Play'
   addToList("Sleep"); // => 'Eat Play Sleep'
   addToList("repeat"); // => 'Eat Play Sleep repeat'
   ```

7. Write a function `createToDoList` that works similarly to `addToList` function but instead of a Global variable use a closure variable.

   ```javascript
   const createToDoList = function () {
     // TODO: Your code here
   };

   const toDoListOne = createToDoList();
   toDoListOne("Eat"); // => 'Eat'
   toDoListOne("Play"); // => 'Eat Play'
   toDoListOne("Sleep"); // => 'Eat Play Sleep'
   toDoListOne("repeat"); // => 'Eat Play Sleep repeat'
   ```

8. Write a function `deposit` that accepts a number argument `amount` and returns the current account balance after depositing the amount.

   > **Hint:** create a new variable `currentBalance` at the global scope to hold the value.

   ```javascript
   const deposit = function (amount) {
     // TODO: Your code here
   };

   deposit(100); // => 100
   deposit(50); // => 150
   ```

9. Write a function `withdraw` that accepts a number argument `amount` and returns the current account balance after withdrawing the amount.

   > **Hint:** use the same `currentBalance` variable from the previous question.

   ```javascript
   const withdraw = function (amount) {
     // TODO: Your code here
   };

   deposit(100); // => 100
   deposit(50); // => 150
   withdraw(70); // => 80
   deposit(50); // => 130
   withdraw(100); // => 30
   withdraw(100); // => "insufficient funds, current balance: 30"
   ```

10. Write a closure function `createAccount` that accepts a number argument `initialValue` that represents the starting value of the account balance and return a closure function with two parameters, `transactionType` and `amount` that deposit or withdraw from the account balance depending on the `transactionType`and returns the total balance amount. Make sure to prevent transactions that withdraw more than the total balance.

    ```javascript
    const createAccount = function (initialValue) {
      // TODO: Your code here
    };

    const accountOne = createAccount(0);
    accountOne("withdraw", 10); // => "insufficient funds, current balance: 0"
    accountOne("deposit", 50); // => 50
    accountOne("deposit", 70); // => 120
    accountOne("withdraw", 10); // => 110

    const accountTwo = createAccount(500);
    accountTwo("withdraw", 100); // => 400
    accountTwo("withdraw", 100); // => 300
    accountTwo("deposit", 50); // => 350
    accountTwo("withdraw", 500); // => "insufficient funds, current balance: 350"
    ```

### Advanced Practice

1. Write a function `minMax` that accepts a number argument `number` and returns a string representing the maximum and the minimum numbers. Read the comments for more information.

   ```javascript
   // every time the function is called it must check if the passed argument is the maximum number, minimum number, or
   // both, and preserve the result for later invocations
   const minMax = function (number) {
     // TODO: Your code here
   };

   minMax(5); // => "the maximum number is: 5 and the minimum number is 5"
   minMax(2); // => "the maximum number is: 5 and the minimum number is 2"
   minMax(3); // => "the maximum number is: 5 and the minimum number is 2"
   minMax(7); // => "the maximum number is: 7 and the minimum number is 2"
   minMax(0); // => "the maximum number is: 7 and the minimum number is 0"
   ```

   HINT search for NEGATIVE_INFINITY and POSITIVE_INFINITY on [MDN](https://developer.mozilla.org/en-US/).

2. Modify the `rockPaperScissors_v02` function from the previous lesson to save the score of how many times the user has won and how many the user has lost. Return the score with every invocation.

   ```javascript
   // use your previous solution for `randomMove`
   const randomMove = function () {
     // TODO: Your code here
   };

   const rockPaperScissors_v03 = function (move) {
     // TODO: Your code here
   };

   rockPaperScissors_v03("rock"); // => "Won: 1, Lost:0"
   rockPaperScissors_v03("rock"); // => "Won: 1, Lost:1"
   rockPaperScissors_v03("paper"); // => "Won: 1, Lost:2"
   ```

3. Modify the `rockPaperScissors_v03` function to have a score limit such as winning five times then resetting the score back to zero.

   ```javascript
   // let's assume that the score limit is set to three
   rockPaperScissors_v04("rock"); // => "Won: 2, Lost:2"
   rockPaperScissors_v04("rock"); // => "Won: 2, Lost:3"
   rockPaperScissors_v04("rock"); // => "Won: 1, Lost:0"
   ```

4. Modify the `rockPaperScissors_v04` function to have an optional second boolean parameter `reset` that when true will reset the game score back to zero.

   ```javascript
   const rockPaperScissors_v05 = function (move, reset) {
     // TODO: Your code here
   };

   rockPaperScissors_v05("rock"); // => "Won: 1, Lost:0"
   rockPaperScissors_v05("", true); // => "the game has been reset"
   rockPaperScissors_v05("scissors"); // => "Won: 0, Lost:1"
   ```

5. Modify the `rockPaperScissors_v05` function to keep track of the last winner and modify the `randomMove` function to have a 25% chance of picking the same move if the user has lost the previous round, otherwise, it picks a random move.

   ```javascript
   rockPaperScissors_v06("rock"); // => "Won: 0, Lost:1"
   //let's assume that the same random move was picked because of the 25% chance
   rockPaperScissors_v06("rock"); // => "Won: 0, Lost:2"
   rockPaperScissors_v06("rock"); // => "Won: 1, Lost:0"
   ```
