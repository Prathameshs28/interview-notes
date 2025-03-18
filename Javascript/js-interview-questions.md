 # Javascript interview questions

### Basic: 



#### what are javascript data types: 

1.  Primitive Data Types: Number, String, Boolean, Undefined, Null, Symbol, BigInt.

2. Non-Primitive Data Types: Object, Array, Function.

---

#### JS is singlethred or multithreded why? 

JavaScript is single-threaded because it uses a single execution thread to process code. However, it can handle asynchronous tasks via event loops and Web APIs, allowing concurrent-like behavior without true multi-threading.

---

#### Scopes

- In JavaScript, scope refers to the context in which variables, functions, and objects are accessible or defined.

1. Global Scope: 

- It refers to the outermost level of the code. Variables and functions declared in the global scope are accessible from anywhere in the code.

- In a browser, variables declared in the global scope are attached to the window object.

```js
let globalVar = "I am global";

function showGlobalVar() {
    console.log(globalVar);  // Accessible from anywhere
}
showGlobalVar();  // "I am global"

```

2. Function Scope: 

- Variables declared inside a function are only accessible within that function. They are local variables.

- In JavaScript, before ES6, the var keyword created variables that were function-scoped.

```js
function myFunction() {
    let localVar = "I am local to the function";
    console.log(localVar);  // Accessible here
}
console.log(localVar);  // Error: localVar is not defined
myFunction();

```

3. Block Scope (Introduced in ES6 with let and const):

- Variables declared inside a block (like inside loops or conditionals) using let or const are limited to that block.
- This is different from var, which is function-scoped and ignores blocks like loops or if statements.

```js
if (true) {
    let blockVar = "I am inside a block";
    const blockConst = "I am also inside a block";
    console.log(blockVar);  // Accessible here
    console.log(blockConst);  // Accessible here
}
console.log(blockVar);  // Error: blockVar is not defined
console.log(blockConst);  // Error: blockConst is not defined

```

4. Lexical Scope (Static Scope):

- JavaScript uses lexical scoping, meaning a function’s scope is determined by where the function is defined, not where it is invoked.

- Inner functions have access to variables of their outer (enclosing) functions.

```js
function outer() {
    let outerVar = "I am from the outer function";
    
    function inner() {
        console.log(outerVar);  // Can access outerVar due to lexical scoping
    }
    
    inner();
}
outer();

```

5. Global Object Scope: 

- In a web browser, the global scope is represented by the window object, and any variable declared in the global scope can be accessed as a property of window

```js
let globalVariable = "I am a global variable";
console.log(window.globalVariable);  // "I am a global variable"

```
---


#### var, let const

1. var: 

- var is function-scoped, meaning it is accessible within the function where it is declared. If declared outside a function, it is globally scoped.

- var declarations are hoisted to the top of their scope, but only the declaration (not the initialization). The variable is initialized with undefined until it’s assigned a value.

- You can re-declare variables declared with var in the same scope

```js
var x = 10;
console.log(x); // 10

if (true) {
    var x = 20; // Re-declares the same x variable
    console.log(x); // 20
}

console.log(x); // 20 (global scope)


```

2. let:

- let is block-scoped, meaning it is only accessible within the block ({}) where it is declared, such as within loops or conditionals.

- let declarations are hoisted to the top of their block, but not initialized. Accessing them before the declaration results in a ReferenceError (temporal dead zone).

-  Variables declared with let cannot be re-declared in the same scope.

```js
let x = 10;
console.log(x); // 10

if (true) {
    let x = 20; // New x inside block
    console.log(x); // 20
}

console.log(x); // 10 (outer scope, unaffected by block)

```

3. const:

- const is also block-scoped like let.

- const is hoisted to the top of its block but is not initialized until the declaration is reached (similar to let), resulting in a temporal dead zone.

- You cannot re-declare or re-assign a const variable. Once a const is assigned a value, it cannot be reassigned. However, objects and arrays declared with const can still have their properties or elements modified.


```js
const y = 30;
console.log(y); // 30

// y = 40; // Error: Assignment to constant variable.

const person = { name: "Alice" };
person.name = "Bob"; // Works, modifying object properties
console.log(person); // { name: "Bob" }

```

---

#### Hoisting: 

- Hoisting is a JavaScript mechanism where variable and function declarations are moved (or "hoisted") to the top of their respective scopes during the compile phase, before the code execution starts. 


1. Variable Declarations with var

- Variables declared with var are hoisted to the top of their scope, but only the declaration (not the initialization). They are assigned undefined by default until the code execution. 


```js
console.log(a);  // undefined (not ReferenceError)
var a = 5;
console.log(a);  // 5

```

2. Variables Declared with let and const: 

- let and const are hoisted, but they do not get initialized until the code execution reaches the line of declaration. This leads to a "temporal dead zone" (TDZ), where you cannot access the variable before it’s declared, and doing so results in a ReferenceError


```js
console.log(b);  // ReferenceError: Cannot access 'b' before initialization
let b = 10;

```

3. Function Declarations:

- Function declarations are hoisted completely. You can call a function before its definition because both the function name and its body are hoisted to the top.


```js
greet();  // Outputs: "Hello!"

function greet() {
    console.log("Hello!");
}

```

4. Function Expressions: 

- Function expressions (including anonymous functions) are not hoisted in the same way that function declarations are. If you try to call a function before its definition, you’ll get an error.

```js
greet();  // TypeError: greet is not a function

var greet = function() {
    console.log("Hello!");
};

```

---

#### Features of ES6 (ECMAScript 2015): 

1. let and const for Variable Declaration
2. Arrow Functions
3. Template Literals (``` let res =  `test ${variable}` ```)
4. Destructuring Assignment (``` const { name, age } = person; ```)
5. Default Parameters (``` function greet(name = "Guest") {} ```)
6. Spread Operator (...)
7. Rest Parameter (``` function sum(...numbers) {} ```)
8. Classes
9. Modules (``` import { User } from './file1.js'; ```)
10. Promises
11. Iterators and Generators

- Iterators provide a way to iterate over data (such as arrays or objects).
- Generators are functions that can pause and resume execution, useful for working with asynchronous code or large data sets.


```js

function* myGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = myGenerator();
console.log(gen.next().value);  // 1
console.log(gen.next().value);  // 2
console.log(gen.next().value);  // 3

```

12. Map and Set:

- Map: A collection of key-value pairs where keys can be any type.
- Set: A collection of unique values.


```js

const map = new Map();
map.set("name", "Alice");
map.set("age", 30);
console.log(map.get("name"));  // Alice

const set = new Set([1, 2, 3, 3]);
console.log(set);  // Set {1, 2, 3}

```

#### Immediately Invoked Function Expression (IIFE): 

- An IIFE is a function that is executed immediately after it is defined. It is a common pattern used to create a local scope for variables to avoid polluting the global scope

```js

(function() {
    // code inside IIFE
})();

// or with arrow function 

(() => {
    // code inside IIFE
})();

```
---


#### Execution context in javascript:  


---
#### JS engine and Event loop in javascript:  


---
#### micro/ macro tasks: 


---

#### setTimeout vs setInterval:  


---

#### Normal Function Vs Arrow Function:


| **Feature**                | **Normal Function**                                      | **Arrow Function**                                      |
|----------------------------|----------------------------------------------------------|---------------------------------------------------------|
| **Syntax**                 | `function func() { ... }`                                | `const func = () => { ... }`                            |
| **`this` Binding**         | `this` is dynamically bound based on how the function is called. | `this` is lexically bound from the surrounding context. |
| **Constructor Function**   | Can be used as a constructor (with `new` keyword).       | Cannot be used as a constructor.                        |
| **Arguments Object**       | Has access to the `arguments` object (an array-like object). | Does not have an `arguments` object.                    |
| **Method Definition**      | Can be used to define methods in objects.                | Can be used, but arrow functions should not be used as object methods when referring to `this`. |
| **Return Statement**       | Requires `return` keyword to return a value.             | Implicit return if the function body has only one expression. |
| **Hoisting**               | Function declarations are hoisted (but not function expressions). | Not hoisted (like regular function expressions).        |
| **Use with Callbacks**     | Can be used in callbacks, but may require binding `this` explicitly. | Often preferred for callbacks because it automatically inherits `this`. |
| **Use Case**               | Suitable for traditional function definitions and methods. | Ideal for short functions, especially in array methods like `map()`, `filter()`, and `reduce()`. |

---

#### What  is anonunomous function & where we use that?

- An anonymous function is a function that is defined without a name. It is also sometimes called a function expression because it is typically assigned to a variable or passed as an argument to other functions.


```js

const functionName = function() {
    // function body
};


// or with Arrow Function (ES6)

const functionName = () => {
    // function body
};


```

##### Where Do We Use Anonymous Functions?

- As a Callback Function: Anonymous functions are often used as callbacks in functions like setTimeout, setInterval, or array methods like map(), filter(), and reduce().

- In Event Listeners

```js
button.addEventListener('click', function() {
    alert("Button clicked!");
});

```

- As Immediately Invoked Function Expressions (IIFE)

---


#### Highoreder function (HOF) in js:


A Higher-Order Function (HOF) is a function that:

- Takes one or more functions as arguments, or
- Returns a function as its result.
- e.g  Callbacks, Array Methods like map(), filter(), and reduce()

```js

function multiplyBy(factor) {
    return function(num) {
        return num * factor;
    };
}

const double = multiplyBy(2);  // Returns a function that doubles the number
console.log(double(5));  // 10

const triple = multiplyBy(3);  // Returns a function that triples the number
console.log(triple(5));  // 15

```

---

#### Currying: 

- In normal functions, you pass multiple arguments to the function at once. In currying, the function returns another function that accepts the next argument until all the arguments are provided.


```js
function add(a) {
    return function(b) {
        return function(c) {
            return a + b + c;
        };
    };
}

console.log(add(1)(2)(3));  // Output: 6


// with arrow function

const add = a => b => c => a + b + c;

console.log(add(1)(2)(3));  // Output: 6

```

---

#### Callbacks:

- A callback is a function that is passed as an argument to another function and is executed after a certain event or operation has completed. 

- Callbacks are used to handle asynchronous operations, such as reading files, fetching data, or interacting with APIs, where you don't know exactly when the operation will finish


```js

function fetchData(callback) {
    setTimeout(() => {
        console.log('Data fetched!');
        callback();  // Callback executed after data is fetched
    }, 2000);
}

function processData() {
    console.log('Processing data...');
}

fetchData(processData);  // Output:
// Data fetched!
// Processing data...


```
---

#### What is closure

- A closure is a function that retains access to its lexical environment (i.e., variables from the outer function) even after the outer function has finished executing. 

- In other words, closures allow a function to "remember" and access variables from the scope in which it was created, even when that function is executed outside of that scope.

- Closures enable data encapsulation, preserving state across function calls, and are commonly used in asynchronous code, event handlers, and function factories.


```js

function createCounter() {
    let count = 0;  // `count` is a private variable

    return {
        increment: function() {
            count++;
            console.log(count);
        },
        decrement: function() {
            count--;
            console.log(count);
        },
        getCount: function() {
            console.log(count);
        }
    };
}

const counter = createCounter();
counter.increment();  // Output: 1
counter.increment();  // Output: 2
counter.decrement();  // Output: 1
counter.getCount();   // Output: 1

// `count` cannot be accessed directly from outside
// console.log(counter.count); // Undefined


```

---

#### Memoization: 

- Memoization is an optimization technique used to improve the performance of functions by caching the results of expensive function calls and returning the cached result when the same inputs occur again

- Memoization is particularly useful for functions that are computationally expensive and are called repeatedly with the same arguments (e.g., recursive functions, calculations, or data processing).



```js
function memoizedFibonacci(n, cache = {}) {
    if (n in cache) {
        return cache[n];  // Return cached result
    }
    if (n <= 1) {
        return n;
    }
    // Compute and store the result in the cache
    cache[n] = memoizedFibonacci(n - 1, cache) + memoizedFibonacci(n - 2, cache);
    return cache[n];
}

console.log(memoizedFibonacci(35));  // Much faster due to memoization

```

---

####  Pure and Non-Pure Functions:

| **Aspect**        | **Pure Function**                                    | **Non-Pure (Impure) Function**                       |
|-------------------|------------------------------------------------------|-----------------------------------------------------|
| **Output**        | Always the same for the same input.                  | Can vary depending on external state or inputs.    |
| **Side Effects**  | No side effects. Does not alter any external state.  | Has side effects. Alters external state or performs I/O. |
| **State Dependency** | Only depends on its input arguments.              | May depend on external state or global variables.   |
| **Testability**   | Easier to test (predictable and isolated).           | Harder to test due to external dependencies and side effects. |
| **Examples**      | add(a, b), multiply(a, b)                           | console.log(), modifying global variables, I/O operations |


- Pure function example: 

```js

// Pure function that calculates the area of a rectangle
function calculateArea(length, width) {
    return length * width;
}

console.log(calculateArea(5, 10));  // Output: 50
console.log(calculateArea(5, 10));  // Output: 50 (same result every time)

```

- Non Pure function example: 

```js
let totalAmount = 1000;  // External state

// Non-pure function that modifies external state
function applyDiscount(discount) {
    totalAmount -= discount;
    console.log(`New total amount: ${totalAmount}`);
}

applyDiscount(100);  // Output: "New total amount: 900"
applyDiscount(200);  // Output: "New total amount: 700"

```
---

#### Promises:

- A Promise is a JavaScript object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value

- making it easier to work with asynchronous code and avoid "callback hell."

- States of a Promise

1. Pending: The initial state; the operation is ongoing and hasn't been completed yet.
2. Resolved (Fulfilled): The operation completed successfully, and the Promise has a result (the value it resolved with).
3. Rejected: The operation failed, and the Promise has an error (the reason it was rejected).


```js

const fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Data fetched successfully!");
    }, 1000);
});

fetchData
    .then(result => {
        console.log(result);  // Output: "Data fetched successfully!"
        return "Processing data...";  // Return new value to next .then()
    })
    .then(processedData => {
        console.log(processedData);  // Output: "Processing data..."
    })
    .catch(error => {
        console.log(error);  // Handle any errors that occur in the chain
    });

```

#### Methods of Promise:


1. **`Promise.resolve()`**

- Returns a `Promise` that is resolved with a given value.


```javascript
const resolvedPromise = Promise.resolve('Hello');
resolvedPromise.then(result => console.log(result)); // Output: "Hello"
```

2. **`Promise.reject()`**
- Returns a `Promise` that is immediately rejected with a given reason.
- Useful for rejecting a Promise with an error or any reason.

```javascript
const rejectedPromise = Promise.reject('Error occurred');
rejectedPromise.catch(error => console.log(error));  // Output: "Error occurred"
```


3. **`Promise.all()`**
- Takes an iterable (usually an array) of Promises and returns a new Promise that resolves when all the input Promises have resolved or rejects if any one of the input Promises rejects.
- Used when you need to run multiple asynchronous tasks in parallel and wait for all of them to finish.

```javascript
const p1 = Promise.resolve(3);
const p2 = new Promise(resolve => setTimeout(resolve, 1000, 'foo'));
const p3 = 42;  // A non-Promise value

Promise.all([p1, p2, p3])
  .then(values => {
    console.log(values);  // Output: [3, "foo", 42]
  })
  .catch(error => {
    console.log(error);  // Will trigger if any promise is rejected
  });
```

- If any Promise rejects, `Promise.all()` immediately rejects and passes that error to the `.catch()` handler.

4. **`Promise.allSettled()`**
- Takes an iterable of Promises and returns a Promise that resolves after all the given Promises have settled (i.e., they are either resolved or rejected).
- Useful when you need the result of all Promises regardless of whether they were fulfilled or rejected.

```javascript
const p1 = Promise.resolve(3);
const p2 = new Promise((_, reject) => setTimeout(reject, 1000, 'Error'));
const p3 = Promise.resolve(42);

Promise.allSettled([p1, p2, p3])
  .then(results => {
    results.forEach(result => {
      console.log(result.status);  // Output: "fulfilled", "rejected", "fulfilled"
      console.log(result.value || result.reason);  // Output: 3, "Error", 42
    });
  });
```

- The `result` object contains:
  - **`status`**: Either `'fulfilled'` or `'rejected'`.
  - **`value`**: The value when resolved.
  - **`reason`**: The error when rejected.

5. **`Promise.race()`**
- Takes an iterable of Promises and returns a Promise that resolves or rejects as soon as the first Promise in the iterable resolves or rejects.
- Useful when you want to act on the first completed operation, either success or failure.

```javascript
const p1 = new Promise(resolve => setTimeout(resolve, 500, 'First'));
const p2 = new Promise(resolve => setTimeout(resolve, 1000, 'Second'));

Promise.race([p1, p2])
  .then(value => {
    console.log(value);  // Output: "First" (as it resolves first)
  });
```

- The returned Promise resolves or rejects as soon as the first Promise resolves or rejects.

6. **`Promise.any()`**

- Takes an iterable of Promises and returns a Promise that resolves as soon as any of the Promises resolves, or rejects if all of them are rejected.
- Useful when you want the first successful result and don't care about the others.

```javascript
const p1 = new Promise((_, reject) => setTimeout(reject, 1000, 'Failed'));
const p2 = new Promise(resolve => setTimeout(resolve, 500, 'Success'));
const p3 = new Promise((_, reject) => setTimeout(reject, 2000, 'Failed'));

Promise.any([p1, p2, p3])
  .then(value => {
    console.log(value);  // Output: "Success" (first resolved promise)
  })
  .catch(error => {
    console.log(error);  // If all promises reject, this will trigger
  });
```

- If all Promises are rejected, `Promise.any()` will reject with an `AggregateError`, which contains all rejection reasons.

7. **`Promise.finally()`**

- Attaches a handler to be invoked when the Promise is settled (fulfilled or rejected), regardless of its outcome.
- Used for cleanup operations or logging, since it runs regardless of whether the Promise was fulfilled or rejected.

```javascript
const myPromise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Operation successful");
  } else {
    reject("Operation failed");
  }
});

myPromise
  .then(result => {
    console.log(result);  // "Operation successful"
  })
  .catch(error => {
    console.log(error);  // "Operation failed"
  })
  .finally(() => {
    console.log("Cleanup");  // Always runs
  });
```

- The `finally()` handler is always invoked, even if the Promise is rejected or fulfilled.

---

**Summary of Promise Methods:**

| **Method**            | **Description**                                                                                   |
|-----------------------|---------------------------------------------------------------------------------------------------|
| `Promise.resolve()`    | Returns a resolved Promise with a given value or another Promise.                                  |
| `Promise.reject()`     | Returns a rejected Promise with a given reason or error.                                           |
| `Promise.all()`        | Returns a Promise that resolves when all input Promises resolve, or rejects if any one fails.      |
| `Promise.allSettled()` | Returns a Promise that resolves when all input Promises have settled (either fulfilled or rejected). |
| `Promise.race()`       | Returns a Promise that resolves or rejects as soon as the first input Promise resolves or rejects. |
| `Promise.any()`        | Returns a Promise that resolves when any one of the input Promises resolves, or rejects if all fail. |
| `Promise.finally()`    | Attaches a handler that runs when the Promise is settled (fulfilled or rejected), regardless of outcome. |

---

#### Async-await: 

- It allow you to write asynchronous code in a way that looks and behaves like synchronous code, making it more readable and easier to understand

##### async Keyword: 

- The async keyword is used to declare a function as asynchronous

- An async function always returns a Promise. If the function explicitly returns a value, the returned value is wrapped in a resolved Promise

- If the function throws an error, the returned Promise is rejected.

##### await Keyword: 

- The await keyword can only be used inside an async function.

- It pauses the execution of the async function and waits for the Promise to resolve or reject.

- The result of the Promise is returned once it's resolved. If the Promise is rejected, the await expression throws an error.


```js
async function getData() {
    let result = await fetch('https://api.example.com/data');
    let data = await result.json();  // Resolves the response as JSON
    return data;
}

getData().then(data => {
    console.log(data);  // Output: { ...data from API ... }
});


```

##### How Async-Await Works

- async Function: When you declare a function as async, it always returns a Promise. Inside this function, you can use await to pause the function execution until the Promise is resolved.

- await Keyword: When you use await, JavaScript will pause execution of the async function until the Promise is resolved or rejected. After the Promise resolves, await returns the resolved value.


- Handling Errors with Async-Await

```js

async function getData() {
    try {
        let response = await fetch('https://api.example.com/data');
        if (!response.ok) {  // Check for HTTP errors
            throw new Error("Network response was not ok");
        }
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error:", error);  // Catching any error (fetch failure, invalid JSON, etc.)
    }
}

getData();


```

---


#### Various ways to create object in JS: 

1. Object Literal Syntax

```js
const obj = {
  name: 'John',
  age: 30
};

```

2. Using the new Object() Syntax

```js
const obj = new Object();
obj.name = 'John';
obj.age = 30;

```

3. Using a Constructor Function

- This method allows you to create multiple instances of the same object type.

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const john = new Person('John', 30);

```

4. Using Object.create()

```js
const proto = { greet: function() { console.log('Hello!'); } };
const obj = Object.create(proto);
obj.greet(); // Output: Hello!

```

5. Using a Class (ES6+)

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const john = new Person('John', 30);

```

6. Using Object.assign()

```js
const obj1 = { name: 'John' };
const obj2 = { age: 30 };

const combinedObj = Object.assign({}, obj1, obj2);
console.log(combinedObj); // { name: 'John', age: 30 }

```

7. Using a Factory Function

- A factory function is a function that returns a new object. This allows for creating multiple objects with the same structure but different properties.

```js
function createPerson(name, age) {
  return {
    name: name,
    age: age
  };
}

const john = createPerson('John', 30);

```

8. Using JSON.parse() with JSON.stringify()

```js
const obj = JSON.parse('{}'); // Creates an empty object

```

---

#### Object methods: 


1. **`Object.keys()`**
Returns an array of a given object's property names (keys).

```javascript
const obj = { name: 'John', age: 30, city: 'New York' };
console.log(Object.keys(obj)); // Output: ['name', 'age', 'city']
```

2. **`Object.values()`**
Returns an array of a given object's property values.

```javascript
const obj = { name: 'John', age: 30, city: 'New York' };
console.log(Object.values(obj)); // Output: ['John', 30, 'New York']
```

3. **`Object.entries()`**
Returns an array of a given object's own enumerable string-keyed property `[key, value]` pairs.

```javascript
const obj = { name: 'John', age: 30, city: 'New York' };
console.log(Object.entries(obj)); 
// Output: [['name', 'John'], ['age', 30], ['city', 'New York']]
```

4. **`Object.assign()`**
Copies all enumerable own properties from one or more source objects to a target object.

```javascript
const obj1 = { name: 'John' };
const obj2 = { age: 30 };
const mergedObj = Object.assign({}, obj1, obj2);
console.log(mergedObj); // Output: { name: 'John', age: 30 }
```

5. **`Object.create()`**
Creates a new object with the specified prototype object and properties.

```javascript
const proto = { greet() { console.log('Hello!'); } };
const obj = Object.create(proto);
obj.greet(); // Output: Hello!
```

6. **`Object.freeze()`**
Freezes an object, making it immutable. New properties cannot be added, and existing properties cannot be modified or deleted.

```javascript
const obj = { name: 'John', age: 30 };
Object.freeze(obj);
obj.age = 40; // This will not change the age
console.log(obj.age); // Output: 30
```

7. **`Object.seal()`**
Seals an object, preventing new properties from being added and marking all existing properties as non-configurable.

```javascript
const obj = { name: 'John', age: 30 };
Object.seal(obj);
obj.age = 40; // This will modify the age
delete obj.name; // This will fail silently
console.log(obj); // Output: { name: 'John', age: 40 }
```

8. **`Object.getPrototypeOf()`**
Returns the prototype (internal `[[Prototype]]`) of an object.

```javascript
const obj = {};
console.log(Object.getPrototypeOf(obj)); // Output: {}
```

9. **`Object.setPrototypeOf()`**
Sets the prototype (internal `[[Prototype]]`) of an object.

```javascript
const obj = {};
const newProto = { greet() { console.log('Hello!'); } };
Object.setPrototypeOf(obj, newProto);
obj.greet(); // Output: Hello!
```

10. **`Object.is()`**
Compares two values for strict equality (similar to `===`, but with a few differences, like handling `NaN` and `-0`).

```javascript
console.log(Object.is(10, 10)); // Output: true
console.log(Object.is(10, '10')); // Output: false
console.log(Object.is(NaN, NaN)); // Output: true
console.log(Object.is(-0, +0)); // Output: false
```

11. **`Object.hasOwnProperty()`**
Returns a boolean indicating whether the object has the specified property as its own (not inherited) property.

```javascript
const obj = { name: 'John' };
console.log(obj.hasOwnProperty('name')); // Output: true
console.log(obj.hasOwnProperty('age'));  // Output: false
```

12. **`Object.defineProperty()`**
Defines a new property on an object or modifies an existing property.

```javascript
const obj = {};
Object.defineProperty(obj, 'name', {
  value: 'John',
  writable: false,
  enumerable: true,
  configurable: false
});
console.log(obj.name); // Output: John
obj.name = 'Doe'; // This will not change the name
console.log(obj.name); // Output: John
```

13. **`Object.defineProperties()`**
Defines multiple properties on an object.

```javascript
const obj = {};
Object.defineProperties(obj, {
  'name': { value: 'John', writable: false },
  'age': { value: 30, writable: true }
});
console.log(obj.name); // Output: John
obj.name = 'Doe'; // This will not change the name
console.log(obj.name); // Output: John
```

14. **`Object.fromEntries()`** (ES10)
Converts a list of key-value pairs into an object. This is the reverse of `Object.entries()`.

```javascript
const entries = [['name', 'John'], ['age', 30]];
const obj = Object.fromEntries(entries);
console.log(obj); // Output: { name: 'John', age: 30 }
```

15. **`Object.isExtensible()`**
Checks if new properties can be added to an object. Returns `true` if the object is extensible, and `false` if it's not.

```javascript
const obj = {};
console.log(Object.isExtensible(obj)); // Output: true
Object.preventExtensions(obj);
console.log(Object.isExtensible(obj)); // Output: false
```

16. **`Object.preventExtensions()`**
Prevents new properties from being added to an object.

```javascript
const obj = { name: 'John' };
Object.preventExtensions(obj);
obj.age = 30; // This will not add the new property
console.log(obj); // Output: { name: 'John' }
```

17. Object..groupBy()

- The .groupBy() method groups items according to the value returned by a callback function. The return value of the .groupBy() method is a null-prototype object that doesn’t inherit any object methods.

```js
const subs = [
  { userName: 'Lisa', yearSub: 2022 },
  { userName: 'Akim', yearSub: 2020 },
  { userName: 'Lola', yearSub: 2020 },
];

const subsByYear = Object.groupBy(subs, (user) => {
  return user.yearSub;
});



// output:

{
  '2020': [
    { userName: 'Akim', yearSub: 2020 },
    { userName: 'Lola', yearSub: 2020 }
  ],
  '2022': [ { userName: 'Lisa', yearSub: 2022 } ]
}


```

---


prototype inheritance




How to use OOP in JS 

What are classes in JS?
this keyword

what is singleton class
How to implement singleton class?
What is object oriented concepts used in javascript
What is encapsulation , how to implement in javascript
what is inheritance  , how to implement in javascript 
implicit and explicit binding (apply, this,call,bind);
functions are first class object in js 
what is json ?


How to secure http cookies?

Debouncing
Throttling



event bubbling, capturing, delegation
async and defer
math and Date obj


pollyfills
Weakmap is es6

how to create global variable in js

How to call function which is in IIFE?

on call on some condition

flatMap use

JS modules


// js visualizer https://www.jsv9000.app/

----

- call :
Call is a function that helps to change the context of the invoking function.  it helps to replace the value of this inside a function with whatever value you want.

- Apply:
Apply is very similar to the call function. The only difference is that in apply you can pass an array as an argument list

- Bind:
Bind is a function that helps you create another function that you can execute later with the new context of this that is provided.
The call() method takes arguments separately.
The apply() method takes arguments as an array

bind() method, an object can borrow a method from another object.

```
const person1 = {
        fname: "Rahul",
        lname: "patil",
      };
      const person2 = {
        fname: "Virat",
        lname: "Reddy",
      };
      const person = {
        fullname: function (city, country) {
          return this.fname + " " + this.lname + ", " + city + ", " + country;
        },
      };
      //   let name = person.fullname.call(person2, "pune", "India");
      //   let name = person.fullname.apply(person2, ["pune", "India"]);
      //   console.log(name);
      // bind
      const createPerson = {
        firstname: "Ram",
        lastname: "Savant",
        fullname: function () {
          return this.firstname + " " + this.lastname;
        },
      };
      const member = {
        firstname: "Sham",
        lastname: "Kadam",
      };
      let user = createPerson.fullname.bind(member);
      console.log(user());

```

*** Singleton design pattern :
 
The singleton is one of the most well-known design patterns. There are times when you need to have only one instance of a class and no more than that.

Singletons are used to create an instance of a class if it does not exist or else return the reference of the existing one. This means that 

singletons are created exactly once during the runtime of the application in the global scope.

Several other patterns, such as, Factory, Prototype, and Façade are frequently implemented as Singletons when only one instance is needed.

```
var myInstance = {
  method1: function () {
    // ...
  },
  method2: function () {
    // ...
  }
};
 class car {
        constructor(name, price) {
          this.name = name;
          this.price = price;
        }
        getDetails() {
          return `${this.name} ${this.price} `;
        }
      }
      class Suzuki extends car {
        constructor(name, price, colour) {
          super(name, price);
          this.colour = colour;
        }
        getColour() {
          return this.colour;
        }
      }
      let suzuki = new Suzuki("suzuki 1 ", 10000, "red");
      console.log(suzuki.getColour());
      console.log(suzuki.getDetails());
```

 Abstraction:

```
// abstraction
      function person(name, age) {
        let Uname = name;
        let Uage = age;
        let private = function () {
          return ` ${Uname} + ${Uage} `;
        };
        this.public = function getDetails() {
          return ` ${Uname}  ${Uage} `;
        };
      }
      let user1 = new person("ram", 10);
      console.log(user1.private); // undefined
      console.log(user1.public()); // ram 10
 Various ways to create object in JS (object literal (normal way), new Object(),  Object.create(), constructor())

```

---


Global execution context

2 phases there 

1st is Memory phase
2nd is Code phase

In memory phase code checks any 
variables from top to bottom 
and store variables without any 
value (e.g undefined).

Note: variable initialization not 
a part of memory phase

In Code phase code run line by line

and value initialize to variables as 
per code execution line by line.

---

<span>
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Obcaecati, laudantium dolorum soluta ullam repudiandae, eaque magnam corrupti esse illo, atque aut. Necessitatibus, animi obcaecati cum mollitia 
</span>
<button onclick="check()">Check</button>
<button id="btn" >Click</button>

<script src="./app.js" type="module"></script> 

---

 

1. How Javascript works and Execution Context ?

 ```
			- Execution context is an 2 component - memory or variable envioronment 
			- contains variable and function as the key value pair. code or thread of execution - it is an whole code is executed one line at a time 2 types of JS Context
			- Global and Function(Local).
			- Javascript is a Synchronous single threaded language.
 
 ```
 					
---

2. For Each, For in, For of		


```
			** For each() -> Simply calls a provided function on each elements in your array and here doesn't return anything.

				Syntax- arr.forEach(callback (curent value[index[array]]){
					//execution
					}[thisArg]);
					
				eg- const cities= ['pune', 'mumbai','nag'];

					cities.forEach(function(city){
						c.log (	city + " => " + city.length);
					})  // pune=>4  mumbai=>6  nag=>3
					
			** for in=> Iterate and return indexes for all elements of an array.

						for(var city in cities){
							c.log(city + " => " + city.length);
						} // 0 => 1 1=>1 2=>1
						
			** for of => return element of an array; 

						for(var city of cities){
							c.log(city + " => " + city.length);
						} // pune=> 4 mumbai=>6 nag=>3
```
				  
---
		  

 4. Synchronous and Asynchronous in js ?
Ans-  Js is a Synchronous and single threaded language.
		Synchronous code is executed in sequence- each statement waits for the previous statement to finish before executing.
		Synchronous operation block instructions until the task is completed.
		
	  Js execution envioronment is Asynchronous.
		  Asynchronous code doesn't have to wait - your program can continue to run.
		  Asynchronous operation can execute without blocking other operations.
		  

---
			



6. SetTimeOut with Closuers in js?
Ans- SetTimeOut is take a callback function nd stores into some place and attach to the timer do it.
		Its run only once after the code execution . it is timer show in milisecond (1000).Its not wait for anythings.
		
		ex- after every seconds print value-
				function x(){
				  for(let i=1; i<=5; i++){
					setTimeout(function () {
					console.log(i);
					},i * 1000);
				  }
				  console.log("Hello");
				}
				x();
				
				
		ex- function x(){
				  for(let i=1; i<=5; i++){
					function close(x){
					setTimeout(function () {
					console.log(x);   
					},x * 1000);
					}
					close(i);
				  }
				  console.log("Hello");
				}
				x();
				
				
				
*** - Lexical Environment ?
Ans-  The Scope which is maintain a copy of outer scope variable to be used inside the nested/inner function.
		Parameter and variable of outer scope can be accessed from nested (inner) function.
		Parameter and variable of inner function can not be accessed in outer function.
		Lexical Environment that means the local memory along with lexical envioronment of the parent.(hirachy).
		
		Ex-   function f1(a){
				function f2(b){
					function f3(c){
						console.log(a,b,c);
					}
				   console.log(a,b)	;
				}
				  console,log(a);
			  }
			  

****- SetTimeOut in js?
Ans- Allow us to run the function once after interval of time .


	SetInterval : - Allow us to run a function repeatedly starting after the interval of time , then repeating continously 
					at that interval.
					
			eg- let timers = setInterval (()=> alert('tick'),2000); // repeat show alert afetr every 2 sec
			
				setTimeout (()=>{
					clearInterval(timers);
					alert('stop');
				},5000) // after 5sec auto stop.
				


***- Local storage and Session Storage  ?
Ans-Local storage-  This read-only interface property provides access to the Document’s local storage object,
		the stored data is stored across browser sessions.
	localStorage data for a document loaded in a private browsing or incognito session.
	localStorage data does not expire.
	You can keep the data store in that browser as you want long time.
		
		**Methods-   1. setItem() Method -  It is used to store the value in a particular location with the name of the key.
											localStorage.setItem(key, value)
											
					2. getItem() Method – This method  which is used to get the value stored with a particular key name.
											localStorage.getItem(key)
											
					3. removeItem() Method– This is method is used to remove the value stored in the memory in reference to key.
											localStorage.removeItem(key)
											
					4.clear() Method – This method is used to clear all the values stored in localstorage.
											localStorage.clear()						
		
	
	sessionStorage, except that sessionStorage data gets cleared when the page session ends – that is when the page is closed.
	 It is cleared when the last “private” tab of a browser is closed .
	 sessionStorage data is cleared when the page session ends.
	
	same method use in sessionStorage-  setItem(), getItem(),removeItem(), clear().
	
	
	




****- SET  in JavaScript ?
Ans- The Set object lets you store unique values of any type, Set objects are collections of values.
		A value in the Set may only occur once; it is unique in the Set's collection. 
		The Set has method checks if a value is in a Set object.
		

****- Array methods ?
Ans- Push() - Add one or more element to the end of an  array and return the new length of the array.
	
	UnShift()- Push and unshift both are same, but in the push() add element to the end and unshift() add element to start 
			in the array.
			
	Pop() - Removes the last element from an array.
	
	Shift() - Removes the starting element from an array.
	
	Splice()- 
	
	flat() - The flat() method creates a new array with all sub-array elements concatenated into
				it recursively up to the specified depth.  Flat() methos it is used for multiple inside array converted 
				into single array. [[[]]] => [][][] like.
				
	indexOf() - The indexOf() method returns the first index at which a given element can be found in the array, 
				or -1 if it is not present.
				ex- const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

						console.log(beasts.indexOf('bison'));
						// Expected output: 1

						// Start from index 2
						console.log(beasts.indexOf('bison', 2));
						// Expected output: 4

						console.log(beasts.indexOf('giraffe'));
						// Expected output: -1

	
	


*********JWT - JSON Web Token ?
 
 Ans- A JSON web token(JWT) is JSON Object which is used to securely transfer information over the web(between two parties). 
	 It can be used for an authentication system and can also be used for information exchange.
	 The token is mainly composed of header, payload, signature. These three parts are separated by dots(.).
	 
	 JWT defines the structure of information we are sending from one party to the another, and it comes in two forms
	 – Serialized, Deserialized.
	 The Serialized approach is mainly used to transfer the data through the network with each request and response. 
	 While the deserialized approach is used to read and write data to the web token.
	 
	 **Deserialized

	JWT in the deserialized form contains only the header and the payload.Both of them are plain JSON objects.

	** Serialized
JWT in the serialized form represents a string . all these three components make up the serialized JWT [header.payload.signature]. 
			
			
---


#### Deep cloning in js:

We can deep clone in js using, 

1. JSON Stringify and Parse
2. structuredClone()
3. loadash library
4. custom recursive function


### 1. JSON Stringify and Parse

- JSON.stringify: Converts a JavaScript object into a JSON string.
- JSON.parse: Parses a JSON string and constructs a JavaScript object from it.


```
const original = { a: 1, b: { c: 2 } };
const cloned = JSON.parse(JSON.stringify(original));

```

##### Limitations:

1. Loss of Functions:

   ```
    const original = { a: 1, b: function() { return this.a; } };
    const cloned = JSON.parse(JSON.stringify(original));
    console.log(cloned.b); // undefined
   
   ```

2. Non-Serializable Properties:
   Properties that are not serializable by JSON, such as undefined, symbol, or function, will be lost.
   They won't appear in the cloned object.


 ```
  const original = { a: undefined, b: Symbol('sym') };
  const cloned = JSON.parse(JSON.stringify(original));
  console.log(cloned); // { }
 ```

3. Date Objects:

Date objects will be converted to strings. You’ll lose the date functionality and need to manually convert them back if required.


```
const original = { date: new Date() };
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.date); // ISO date string, not a Date object

```

4. Prototype Chain:

This approach does not preserve the prototype chain. The cloned object will have the default Object prototype.


```
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function() {
  return `Hello, ${this.name}!`;
};

const original = new Person('Alice');
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.greet); // undefined

```

5. RegExp Objects

RegExp objects are converted to plain objects. Their properties and functionality are lost in the cloning process.


```
const original = { pattern: /abc/ };
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.pattern); // {}

```

6. Map & Set Objects
JSON.stringify does not handle Map & Set objects directly. When you try to stringify a Map, it will be converted to an empty object {}.

```
const map = new Map([[1, 'one'], [2, 'two']]);
const jsonString = JSON.stringify(map);
console.log(jsonString); // "{}"


```


```
const set = new Set([1, 2, 3]);
const jsonString = JSON.stringify(set);
console.log(jsonString); // "{}"

```



### 2. structuredClone()


```
let clone = structuredClone(value);

```

- While structuredClone is robust and versatile, it has limitations:

1. Does not clone functions or Symbol properties.
2. Does not preserve prototypes.



### 3. loadash library

- Lodash: _.cloneDeep handles many of the complexities associated with deep cloning

```
const _ = require('lodash');
const original = { a: new Date(), b: /abc/, c: function() {} };
const cloned = _.cloneDeep(original);

```

- Rambda: The R.clone function from Ramda also provides deep cloning functionality

```
const R = require('ramda');
const original = { a: new Date(), b: /abc/, c: function() {} };
const cloned = R.clone(original);

```


#### 4. Custom recursive function

```

let obj = {
  name:'ram',
  age:undefined,
  add:{
    line:'abcd',
    loc:'pune',
    pin:12345
  },
  size:[10,20,30,40]
}

let result = cloneObject(obj);

console.log(result)



function cloneObject(obj){
  
  if(obj === null || typeof obj !== 'object') return obj;
  
  if(Array.isArray(obj)){
    return obj.map((item)=> cloneObject(item) );
  }
  
  
  
  let resultObj = {};
  
  for(let key in obj){
    if(obj.hasOwnProperty(key)){
      resultObj[key] = cloneObject(obj[key]);
    }
  }
  
  
  return resultObj;
  
}

```

* Note: for custom function need to handle for Symbol, Map, Set.

---
---

# Web API in javascript: 

A **Web API** (Application Programming Interface) in JavaScript refers to a set of functions and protocols that allow web browsers and other applications to interact with web services or the browser's built-in features. These APIs are built into the browser and enable developers to access and manipulate various aspects of a web page or web application.

Some common Web APIs in JavaScript include:

1. **DOM (Document Object Model) API**: Allows interaction with HTML and XML documents, enabling you to manipulate elements, structure, and styles of a web page.

2. **Fetch API**: Provides a way to make HTTP requests to interact with remote resources, such as REST APIs. It allows you to send GET, POST, PUT, and DELETE requests to servers.

3. **Geolocation API**: Provides the ability to get a user's geographic location (latitude, longitude) based on GPS or network signals.

4. **LocalStorage and SessionStorage APIs**: Allow web applications to store data on a user's device (in the browser) persistently (LocalStorage) or temporarily (SessionStorage).

5. **Canvas API**: Used to draw graphics, animations, and images directly on a web page.

6. **WebSockets API**: Provides a way to open a persistent, real-time connection between the client and server for two-way communication.

7. **Notification API**: Allows web applications to send notifications to the user, even when the web page is not open.

8. **Audio API**: Provides functionality to play and control audio directly within a web page.

9. **WebRTC API**: Enables real-time communication (like video chat, voice calls) between browsers.

10. Promise API

11. setTimeout & setInterval

12.  File API

---

