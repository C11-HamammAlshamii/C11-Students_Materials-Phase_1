# Iteration With Objects In JavaScript

## High-Level Goals

By the end of this lesson, you will be familiar with the following:

- Defining a for-in loop
- Using a while loop with objects
- Iterating over objects

## Iteration With Objects

### Iteration With For In Loop

Since objects aren't indexed like arrays then the previous way of using the index to iterate will not work with objects. It is recommended to use the `for in loop` when dealing with objects.

Since ECMAScript 2015, objects have preserved the creation order for string and Symbol keys. In JavaScript engines that comply with the ECMAScript 2015 spec, iterating over an object with only string keys will yield the keys in order of insertion.

An example of a for-in loop:

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
};

// the const variable only exist within the statement block for one iteration each time.
for (const key in person) {
  console.log(key, person[key]);
}
// => firstName John
// => lastName Doe
// => age 50
```

```javascript
const people = {
  person1: { firstName: "John", lastName: "Doe" },
  person2: { firstName: "Mark", lastName: "Smith" },
};

const lookFor = function (first, last) {
  for (const key in people) {
    const person = people[key];
    if (person.firstName === first && person.lastName === last) {
      return first + " " + last + " is found";
    }
  }
  return first + " " + last + " is not found";
};

lookFor("John", "Doe"); // => "John Doe is found"
lookFor("Jane", "Doe"); // => "Jane Doe is not found"
```

### Iteration With While Loop

While loop can be used with objects but mainly for iterating vertically rather than horizontally.

An example of that would be:

```javascript
const nestedObjects = {
  nested: {
    nested: {
      nested: {},
    },
  },
};

const getDepth = function (nestedObjects) {
  // a counter to count how many levels are for the object
  let depth = 0;
  //
  // if there is a nested key then it should return a truthy value, en empty object `{}` is considered truthy also
  // it is possible to use nestedObjects.hasOwnProperty("nested") also to solve this question
  while (nestedObjects.nested) {
    depth++;

    // Our step is basically changing the object value to the next nested object
    nestedObjects = nestedObjects.nested;
  }

  return "The depth of this nested object is equal to " + depth;
};

getDepth(nestedObjects); // => "The depth of this nested object is equal to 3"
```

### Pulse Check

1. Create a for-in loop that works on the following object and console log the keys.

   ```javascript
   const object = {
     one: 1,
     two: 2,
     three: 3,
     four: 4,
   };
   ```

2. Create a for-in loop that works on the following object and console log the values.

   ```javascript
   const object = {
     one: 1,
     two: 2,
     three: 3,
     four: 4,
   };
   ```

### Practice

1. Write a function `keyValuePairs` that accepts an object and returns an array of arrays that contains both the key and value.

   ```javascript
   const keyValuePairs = function (object) {
     // TODO: Your code here
   };

   keyValuePairs({ name: "John", age: 24 }); // => [["name", "John"], ["age", 24]]
   keyValuePairs({ firstName: "John", lastName: "Doe" }); // => [["firstName", "John"], ["lastName", "Doe"]]
   keyValuePairs({
     name: "Mark",
     position: "Full-Stack Developer",
     salary: 600,
   }); // => [["name", "Mark"], ["position", "Full-Stack Developer"], ["salary", 600]]
   ```

2. Write a function `absoluteNumbers` that accepts an object of grades and changes all negative numbers to become positive then returns the object after checking all the values.

   ```javascript
   const absoluteNumbers = function (grades) {
     // TODO: Your code here
   };

   absoluteNumbers({ science: 50, art: 60 }); // => {science: 50, art: 60}
   absoluteNumbers({ science: -80, art: 75, english: 77 }); // => {science: 80, art: 75, english: 77}
   ```

3. Write a function `PassedOrFailed` that accepts an object of student grades and returns a string `The student have passed` if all of the grades are equal or above 50% of the material total grades otherwise return `The student have failed`.

   ```javascript
   const passedOrFailed = function (studentGrades) {
     // TODO: Your code here
   };

   const studentOne = {
     math: { grade: 70, total: 120 },
     english: { grade: 80, total: 100 },
     art: { grade: 90, total: 100 },
   };

   const studentTwo = {
     math: { grade: 59, total: 120 },
     english: { grade: 80, total: 100 },
     art: { grade: 90, total: 100 },
   };

   passedOrFailed(studentOne); // =>  "The student have passed"
   passedOrFailed(studentTwo); // =>  "The student have failed"
   ```

4. Write a function `convertToArray` that accepts an object with numerical keys and returns an array containing the values with the corresponding index `don't use push or unshift`.

   ```javascript
   const convertToArray = function (object) {
     // TODO: Your code here
   };

   convertToArray({ 0: "one", 1: "two", 2: "three" }); // => ["one", "two", "three"]
   convertToArray({ 0: "two", 1: "three", 2: "one" }); // => ["two", "three", "one"]
   convertToArray({ 0: "three", 1: "two", 2: "one" }); // => ["three", "two", "one"]
   ```

5. Write a function `safeToConsume` that accepts an object of some of the chemicals compounds of the object, and returns a string `Safe to consume` if none of the chemical compounds is poisonous and if it does then return `Poisonous do not consume`, check the object bellow for more information on the poisonous compounds.

   ```javascript
   const poisonousCompounds = {
     daphnetoxin: true,
     mercury: true,
     cyanide: true,
   };

   const safeToConsume = function (object) {
     // TODO: Your code here
   };

   safeToConsume({ h2o: "10.0g" }); // => "Safe to consume"
   safeToConsume({ pyridoxine: "0.4mg", choline: "9.8mg", vitaminC: "8.7mg" }); // => "Safe to consume"
   safeToConsume({
     genkwanin: "3.1mg",
     mezerein: "2.7mg",
     daphnetoxin: "7.3mg",
   }); // => "Poisonous do not consume"
   safeToConsume({ h2o: "5.2mg", glucose: "1.3mg", cyanide: "4.0mg" }); // => "Poisonous do not consume"
   ```

6. Write a function `toString` that accepts an object and return all of its values in a string, solving it using `for in` loop.

   ```javascript
   const toString = function (object) {
     // TODO: Your code here
   };

   toString({ name: "John", age: 24 }); // => "John, 24"
   toString({ firstName: "John", lastName: "Doe" }); // => "John, Doe"
   toString({ name: "Mark", position: "Full-Stack Developer", salary: 600 }); // => "Mark, Full-Stack Developer, 600"
   ```

7. Write a function `totalBill` that accepts an object representing separate bills and returns the sum of all bills.

   ```javascript
   // Make sure to loop over the bills object
   const billsForJanuary = {
     waterBill: 25,
     electricityBill: 50,
     hospitalBill: 1000,
   };

   const billsForFebruary = {
     waterBill: 30,
     electricityBill: 45,
     insurance: 300,
   };

   const totalBill = function (billsObject) {
     // TODO: Your code here
   };

   totalBill(billsForJanuary); // => 1075
   totalBill(billsForFebruary); // => 375
   ```

8. Write a function `login` that accepts two string arguments, `username` and `password`, and returns a message saying `"Login Successful"` or `"Login Failed"` depending on whether the login information matches the data in the given object.

   ```javascript
   const users = {
     userOne: { username: "Jane", password: "123456" },
     userTwo: { username: "admin", password: "abc123" },
   };

   const login = function (username, password) {
     // TODO: Your code here
   };

   login("Jane", "123456"); // => "Login Successful"
   login("Jane", "5321"); // => "Login Failed"
   login("Mark", "123456"); // => "Login Failed"
   login("admin", "abc123"); // => "Login Successful"
   login("admin", "aaabc123"); // => "Login Failed"
   ```

9. Write a function `createDog` that accepts three string arguments, `name`, `dogBreed`, and `furColor`, and adds a new dog to the `uniqueDogs` object then returns a string `Added the dog successfully` if there is no other dog with the same name otherwise return `The dog isn't unique enough :(`

   ```javascript
   const uniqueDogs = {
     max: { breed: "Labrador Retriever", color: "blond" },
     rex: { breed: "German Shepherd", color: "black and brown" },
     lucy: { breed: "Bulldog", color: "white" },
     lucifer: { breed: "Chihuahua", color: "brown" },
   };

   const createDog = function (name, dogBreed, furColor) {
     // TODO: Your code here
   };

   createDog("luna", "Husky", "black and white"); // => "Added the dog successfully"
   createDog("rex", "Golden Retriever", "blond"); // => "The dog isn't unique enough :("
   ```

10. Write a function `validateMessage` that accepts an object representing a message and returns the object if it is valid and after removing any Advanced keys. The message will consist of three keys, `username`, `message`, and `date`, with all of their values as strings. Return the object only if all three keys are strings. If the number of keys is more than three then delete the Advanced keys, and if the message doesn't have the right data type then return `invalid message`.

    ```javascript
    const messageOne = {
      username: "John",
      message: "Hello",
      date: "01/01/2020",
      someKey: "someValue",
    };

    const messageTwo = {
      username: 10,
      message: "Hello",
      date: "01/01/2020",
    };

    const validateMessage = function (message) {
      // TODO: Your code here
    };
    validateMessage(messageOne); // => {username: "John", message: "Hello", date:"01/01/2020"}
    validateMessage(messageTwo); // => invalid message
    ```

### Advanced Practice

1. Write a function `compare` that accepts an array and an object, and returns true if all the array values are present as object values.

   ```javascript
   const compare = function (array, object) {
     // TODO: Your code here
   };

   compare(["one", "two", "three"], { 0: "one", 1: "two", 2: "three" }); // => true
   compare(["one", "two", "four"], { 0: "one", 1: "two", 2: "three" }); // => false
   compare(["one", "two"], { foo: "one", bar: "two", baz: "three" }); // => true
   compare(["one", "two", "three"], { foo: "one", bar: "two" }); // => false
   ```

2. Write a function `sumValues` that accepts an object of nested objects, and returns the sum of all the numerical values in all the levels.

   ```javascript
   const nestedObject = {
     value1: 10,
     value2: 20,
     nextObj: {
       value3: 11,
       value4: "hello",
       nextObj: {
         value5: "12",
         value6: 8,
         nextObj: {
           value7: 19,
           nextObj: {},
         },
       },
     },
   };

   const sumValues = function (object) {
     // TODO: Your code here
   };

   sumValues(nestedObject); // => 68
   ```

3. Write a function `deleteKeys` that accepts two objects and deletes all the keys from the first object that are not present in the second object then return the first object.

   ```javascript
   const deleteKeys = function (firstObj, secondObj) {
     // TODO: Your code here
   };

   deleteKeys({ c: 1, d: 2, b: 10 }, { a: 1, b: 2, c: 3 }); // => { c: 1, b: 10 }
   deleteKeys({ b: 1, c: 2, d: 10 }, { a: 1 }); // => {}
   deleteKeys({ c: 1 }, { a: 1, b: 2, c: 3 }); // => { c: 1 }
   ```

4. Write a function `sameKeys` that accepts two objects and checks if all the keys from both objects are present in both objects then return the `true` if all keys are present or return `false` if not all keys are present in both objects.

   ```javascript
   const sameKeys = function (firstObj, secondObj) {
     // TODO: Your code here
   };

   sameKeys({ c: 14, b: 2 }, { b: 5, c: 3 }); // => true
   sameKeys({ c: 14, b: 2, a: 5 }, { a: 12, b: 5, c: 3 }); // => true
   sameKeys({ c: 1, b: 2, d: 10 }, { a: 1, b: 2, c: 3 }); // => false
   sameKeys({ c: 1, b: 2, d: 10 }, { a: 1, b: 2, c: 3, d: 1 }); // => false
   sameKeys({ c: 1, b: 2, d: 10 }, { a: 1 }); // => false
   sameKeys({ c: 1 }, { a: 1, b: 2, c: 3 }); // => false
   ```
