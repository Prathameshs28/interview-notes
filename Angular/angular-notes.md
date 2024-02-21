# Angular Interview notes

### 1. Model, class and interface:

<!-- **Definition:** -->

*   **Model** : It represents the data structure and business logic of an application.
                It encapsulates the properties and methods related to a specific entity or concept
                It used to organize and manage data, making it easier to manipulate and interact with in different parts of the application.

**Example:**

```js
// User Model
export class User {
  id: number;
  username: string;
  email: string;

  constructor(id: number, username: string, email: string) {
    this.id = id;
    this.username = username;
    this.email = email;
  }
}
```

In this example, the User model defines the structure of a user, including properties like id, username, and email. It also has a constructor to initialize these properties when creating a new user instance.


*   **Class** : In object-oriented programming, a class is a blueprint for creating objects. It defines the properties and methods that objects of the class will have. In Angular, classes are commonly used to represent models, services, components, and other building blocks of the application.

**Example:**

```js
// User Class
export class User {
  id: number;
  username: string;
  email: string;

  constructor(id: number, username: string, email: string) {
    this.id = id;
    this.username = username;
    this.email = email;
  }

  getFullName(): string {
    return `${this.username} (${this.email})`;
  }
}
```

Now, the User class not only includes properties but also a method (getFullName()) to retrieve the full name of the user. This demonstrates how a class can encapsulate both data and behavior.



*   **Interface** : It defines the structure of an object. It specifies the properties and their types, but it doesn’t provide an implementation. Interfaces are used for enforcing a certain shape of objects, promoting code consistency and adherence to predefined structures.

**Example:**

```js
// User Interface
export interface User {
  id: number;
  username: string;
  email: string;
}
```

In this case, the User interface outlines the expected properties of a user without defining how they should be implemented. Interfaces are especially useful when multiple classes or components need to adhere to the same structure.


---


Angular Cold and Hot Observable:

When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable


Cold Observables:

An Observable “cold” when the data is produced inside the Observable.Observables are lazy, it means they only execute values when something subscribes to it. For each subscriber the Observable starts a new execution, resulting in the fact that the data is not shared. 

If your Observable produces a lot of different values it can happen that two Observables that subscribe at more or less the same receive two different values. We call this behaviour “unicasting”. To demonstrate this:

```js

import * as Rx from "rxjs";

const observable = Rx.Observable.create((observer) => {
    observer.next(Math.random());
});

// subscription 1
observable.subscribe((data) => {
  console.log(data); // 0.24957144215097515 (random number)
});

// subscription 2
observable.subscribe((data) => {
   console.log(data); // 0.004617340049055896 (random number)
});

```


As you see the data is produced inside the Observable, making it cold.

Of course this behaviour is not always desirable. Luckily it’s easy to change this behaviour:

```js

import * as Rx from "rxjs";

const random = Math.random()

const observable = Rx.Observable.create((observer) => {
    observer.next(random);
});

// subscription 1
observable.subscribe((data) => {
  console.log(data); // 0.11208711666917925 (random number)
});

// subscription 2
observable.subscribe((data) => {
   console.log(data); // 0.11208711666917925 (random number)
});

```


Hot Observables

 Observable is hot when the data is produced outside the Observable. As we just saw the hot Observable is able to share data between multiple subscribers. We call this behaviour “multicasting”.


 Let’s say we’re tracking clicking behaviour and have multiple subscribers do something with the coordinates:

 ```js
 
import * as Rx from "rxjs";

const observable = Rx.Observable.fromEvent(document, 'click');

// subscription 1
observable.subscribe((event) => {
  console.log(event.clientX); // x position of click
});

// subscription 2
observable.subscribe((event) => {
   console.log(event.clientY); // y position of click
});
 
 ```


 The data is produced outside of the Observable itself. Which makes it hot, because the data is being created regardless of if there is a subscriber or not. If there is no subscriber when the data is being produced, the data is simply lost.

Is one better than the other?
Well, that depends on the usecase. A cold Observable is usually fine, unless:

1. You want to make sure multiple subscribers get the same data.

2. Your creating a new instance of something on each Observable execution, let’s say a websocket connection. You don’t want to create a new connection for each subscriber, but instead just share it to all the subscribers. Moving the instantiation of the connection outside the Observable will make it hot and fixes this.

---