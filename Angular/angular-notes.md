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




suppose I've one angular application and one of the component having grid, if I click on any grid the new window will open and after close that window I want to perform event on grid component how we can do this.
@HostListener('document:visibilitychange', ['$event'])
  visibilitychange() {
      if (document.hidden){
            console.log("Page is hidden",document);
      } else {
            console.log("Page is visible",document);
      }
  }
  
****************************************************************
how to check bundle size of particular component in angular
how to minimize bundle size of angular build
api call before component re direct
charts library used or not?
event looping in angular


visibility
gridElement.scrollIntoView({  block: 'center' });

****************************************************************
Please complete the story point addition and task breakdown for your main story if anyone has not yet been added.
 Jira should be perfect before starting the sprint.
 * Branch creation should be discussed with your own team members to avoid duplicate branches.
 * Take the latest from fh-dev and create a branch like fh-dev-2400
 * Every push from your local branch to the main branch, which means into fh-dev, should be through a Pull Request.
 * Add reviewers and verify it was reviewed on time and deployed.
 * Any doubts in anything contact your own team leads.
 * Auto generated files should not be committed or pushed to the local or cloud.
 * If you are adding any kind of library files or something new, please have a call or discuss it with your leads and inform us here to avoid last-minute struggles in case of deployment or build issues.
 * Tasks should be completed on time. Concentrate on the task delivery on time.


 ****************************************************************


What are the best practices for handling user authentication and authorization in web applications, including techniques like OAuth and JWT?
Handling user authentication and authorization is crucial for securing web applications and protecting user data. There are several best practices and techniques, including OAuth and JWT, that developers can use to implement robust authentication and authorization systems. Here are the key best practices:
**1. Use Strong Password Policies:**
- Implement strong password policies that require users to create complex passwords with a combination of letters, numbers, and special characters. Enforce password length and expiration rules.
**2. Hash and Salt Passwords:**
- Always hash and salt user passwords before storing them in the database. Use secure cryptographic hashing algorithms like bcrypt or Argon2. Salting helps defend against rainbow table attacks.
**3. Implement Multi-Factor Authentication (MFA):**
- Encourage or require users to enable MFA whenever possible. MFA adds an extra layer of security by requiring users to provide two or more authentication factors, such as a password and a one-time code from a mobile app.
**4. Secure Authentication Endpoints:**
- Protect authentication endpoints (e.g., login and registration) against common attacks like brute force, account enumeration, and account lockout. Implement rate limiting and CAPTCHA challenges if needed.
**5. Use HTTPS:**
- Always use HTTPS to encrypt data in transit, especially during login and registration. This prevents eavesdropping and man-in-the-middle attacks.
**6. Session Management:**
- Implement secure session management to create and manage user sessions. Use a secure session identifier, and expire sessions after a reasonable idle time or upon user logout.
**7. Implement Role-Based Access Control (RBAC):**
- Assign roles (e.g., admin, user, guest) to users and enforce access control based on these roles. Restrict access to sensitive functionality and data based on the user's role.
**8. OAuth for Third-Party Authentication:**
- If your application integrates with third-party services, use OAuth for secure and standardized authentication. OAuth allows users to grant limited access to their data without sharing their credentials.
**9. JSON Web Tokens (JWT):**
- Use JWTs to securely transmit user claims and authentication information between the client and server. JWTs are stateless, compact, and can be used for both authentication and authorization.
**10. Token-Based Authentication:**
- Implement token-based authentication mechanisms, where users receive an authentication token (e.g., JWT) upon successful login. The token is included in subsequent requests to authenticate the user.
**11. Token Validation and Revocation:**
- Validate tokens on the server-side for each incoming request. Implement token expiration and, if necessary, token revocation mechanisms (e.g., token blacklisting).
**12. Proper Error Handling:**
- Handle authentication and authorization errors gracefully. Avoid exposing sensitive information in error messages that could aid attackers.
**13. Secure Cookies:**
- When using cookies for session management or token storage, make sure they are marked as secure and HttpOnly to prevent cross-site scripting (XSS) and data theft.
**14. Regularly Audit and Monitor:**
- Continuously monitor and audit user authentication and authorization systems. Implement logging and alerting for suspicious activities or access attempts.
**15. Keep Software and Libraries Updated:**
- Regularly update your authentication libraries, frameworks, and dependencies to patch security vulnerabilities. Vulnerable components can be exploited by attackers.
**16. Implement Cross-Origin Resource Sharing (CORS) Safely:**
- Configure CORS headers to control which domains can access your API. Use appropriate CORS policies to prevent unauthorized access while allowing necessary interactions.
**17. Educate Users:**
- Educate users about best practices for secure authentication, such as the importance of choosing strong passwords, enabling MFA, and recognizing phishing attempts.



******************************************


Angular 17 features:
Built-in control flow (*ngFor, *ngIf, *ngSwitch)
improvement in lazy loading (@defer)
ssr package
new lifecycle hooks (afterrender, afternextrender)
vite + esBuild builder
DI dev tools
Standalone component


******************************************

usevalue useclass use-existing usefactory
most important  





***************************************

determine how the dependencies will be provided to our classes
4 different ways of creating dependencies: useValue, useFactory, useClass and useExisting
1. useValue
Lets you inject a value or a function.
Often used to set the initial configuration.
export const RACE_CARS_CONFIG: CARS_CONFIG= {
  domain: 'api.race-cars.com',
};providers: [CarsService,
 { provide: CARS_CONFIG, useValue: RACE_CARS_CONFIG}
]



-------------------------------------------------

2. useClass:

Returns another class, specified by "useClass" when component asks for class specified in "provide".
It is useful, for example, when unit testing components. We don't have to provide the full service then, 
but we can create a separate class that will be able to implement the methods in a different way. 
Thanks to this, we will only test the component itself and not its interaction with the service.

providers: [{ provide: UserService, useClass: mockUserService}]

In case the provide and useClass values are the same

providers: [{ provide: UserService, useClass: UserService}]
we can use a shorter write

providers: [UserService]

---------------------------------------------------------


useExisting
Creates two ways to access the same service object with two different tokens.
It works well, e.g. when we have many methods on the service, and we only want to use a few of them. This helps in reducing the size of the interface.
Sample service:

class CarService {
  getWeight(): number {...}
  getColor(): string {...}
  getName(): string {...}
  getWidth(): number {...}
  getHeight(): number { … }
  getModel(): string {...}
  getYear(): number {...}
  ...
}
Reduced implementation:

export abstract class CarSizeService {
  abstract getHeight: number;
  abstract getWidth: number;
}
Providers array:

providers: [{ provide: CarSizeService, useExisting: CarService}]

----------------------------------------------------------------------
useFactory
Specifies the function that is called and injects its return value.
It is useful when we want to get some value from the information that is not available before the run application, e.g. load some data from another page.
If it has dependencies, put them in the "deps" array.
It may include a "multi" property that allows multiple providers spread across many files to provide configuration information to a common token.
Function implementation:

function configUrlFactory (configUrl: ConfigUrlService) { return () => configUrl.load(); }
Providers array:

providers: [{
  provide: APP_INIT,
  useFactory: configUrlFactory,
  deps: [ConfigUrlService],
  multi: true
}]
Example service:

@Injectable() export class ConfigUrlService{
constructor(private http: HttpClient){}
  load(): Promise<any> {
    return http.get('https://exampleConfigUrl.com').toPromise();
  }
}


----------------------------------------------------------------------


Angular DI:
Dependency Injection is a design pattern that helps achieve loose coupling between components by injecting their dependencies rather than creating them within the component.
Providers: Providers are responsible for creating instances of services and making them available for injection
Components, services, or other Angular objects can receive their dependencies through constructor injection
@Injectable: Marks a class as a service that can be injected into other components, services, or directives
@Inject: Specifies a dependency explicitly when there are multiple providers for a given token
constructor(@Inject(MY_MESSAGE) private message: string) {}
@Optional: Allows an injected dependency to be optional. If the dependency is not found, Angular will inject null instead of throwing an error.
constructor(@Optional() private myOptionalService: MyOptionalService) {
    this.message = myOptionalService
      ? myOptionalService.getMessage()
      : 'Optional service not available';
  }



  _________________________


  localeCompare
moment
toLocaleString
enum use
toString
number conversion
interface use
type in ts
parseFloat
parseInt()
window.location.href
import jwtDecode from 'jwt-decode'; in angular
toISOString()
tofixed()
charAt
map, mergeMap, forkJoin, of
constructor(@Inject(Injector) private readonly injector: Injector, private readonly zone: NgZone) {
    // no code required here
  }
Inject, Injectable, Injector, NgZone
ng build --configuration=production --output-hashing=all


MVC:
Systems like Node JS are currently operated on an MVC (Model View Controller) architecture. It’s a design pattern. The idea is that it helps to focus on a specific part of the application and build it on a modular basis. The components are:
Model: It represents the structure and constraints of the data stored in the database.
View: It is the way the required data is presented to the user as per the need of the user.
Controller: This section controls the requests of the user and generates the appropriate response which is fed to the user.