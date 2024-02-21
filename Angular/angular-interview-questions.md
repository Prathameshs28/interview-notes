# Most Important & Latest Angular Questions

Explain latest features of the angular version you are working on ?

ng-container in angular

```
         ng-container use:
         avoid redundant elements
            e.g
         <ng-container *ngIf="postsList" >       // div
         <div *ngFor="let post of postsList" >
            {{post.id}} : {{post.name}}
         </div>
         </ng-container>

         2. used on inline content
         e.g
         <div>
         <ng-container *ngIf="error">Oops: </ng-container> {{message}}   // span
         </div>


         3. to Ensure Valid HTML Standards
         <ul>
         <ng-container *ngFor="let todo of todos">   // div
            <li *ngIf="todo.content !== 'Done'">
               {{ todo.content }}
            </li>
         </ng-container>
         </ul>

```



 Dynamic Component
Standalone Component
Router protection
Optimizing angular app
Angular universal - SSR
Angular animation
Offline capabilities using service worker
Angular Schematics
ng Deploy
Managing Multiple Projects in One Folder





ActivatedRouteSnapshot
RouterStateSnapshot
ActivatedRoute
NavigationEnd
NavigationStart
ActivatedRoute, Data, Event, NavigationEnd, Router
resolver

useFactory useEffect
angular logging and monitoring

# Angular interview questions:



1. what the use of angular?

```
      angular is js ui binding framework which binds html ui and js model (view modal)

      mvvm / mvc / mvvm

      adding to it, it is also helps you to build SPA (Single page application) by
      using concept of routing it also has lot of other features like 
      HTTP, DI, Input output because of which you do not need other frameworks

```
 
---
 
 2. difference between angularjs vs angular
   
```
      1. Written in TypeScript (also supports JavaScript) *** Written in JavaScript
      
      2. Supported by all popular mobile browsers *** Does not support mobile
      
      3. Uses Components and Directives *** Follows Model-View-Controller design
      
      4. A hierarchical DI system *** use directives in place of DI

      5. CLI tool  ***	not CLI tool
      
      6. More SEO-friendly *** less  SEO-friendly
      
      7. unit testing with Karma	*** Requires third-party tools for testing and error detection
   
   
```
 ---
 
 3. what are directives in Angular ?
 
 ```
      Directives changes the behavior of HTML DOM.
      
      e.g. ngModel, [hidden], {{anything}} 
 ```

---
 
 
 4. explain the different types of Angular Directives ?

 ```
      3 types SAC (S: Structural, A: Attribute, C: component)
      
      1. Structural Directive: change the DOM layout by adding and removing elements.      
         e.g *ngFor         

      2. Attribute Directive: change the appearance and behaviour of HTML elements      
         e.g [hidden] , [disable]
         
      3. Component Directive: Directives with templates. Itself directive.
 
 
 ```
 
 ---
 	
 
 5. Explain the importance of NPM and node_modules folder?
 
 ```
      npm is package manager which makes installation of js framework easy.
      
      node_modules is the folder where all packages are installed. 
 
 ```

---

 
 6. explain the importance of package.json file in angular ?

```
      it has all the js references needed for a project, so rather 
      than installing one package at a time we can install all 
      packages in one go

```
 	
---


 7. what is typescript and why do we need it?

```
      	typescript superset of js, it added types to js.
      
         it gives a nice Object-Oriented programming environment
         which transpiles / converts to js.         
         
         so as its strongly typed, we will have less errors and because 
         we can do OOP with js our productivity and quality also 
         increases.

```

---
  
 8. explain importance of angular CLI ?

```
       angular CLI is command line interface, by which 
       we can create initial angular project template.        
       We can install third party packages in our application.
       we can run application
       we can perform testing
       we can build our application for production

```

---     
  
  9. Explain the importance of Component and modules ?
  
```
         component is where you write your binding code, 
         module is logically groups of components.
         
         
         view -- > component <-- modal
                     |		
               css 

```

---
 
 
 10. what is a decorator in Angular?

```
      Decorators are metadata in angular project.
      Decorator defines what kind of Angular class is it,
      for example if you decorate @Component then it says it's
      an angular component if you put @NgModule it becomes a Angular module

```
 
---

  
  11. what are annotations or metaData ?
  
```
      In Angular, an annotation refers to a type of metadata that is used to enhance and provide additional information about a class or its members. Annotations are commonly used in Angular to configure and decorate various parts of an application, including components, services, and modules

```
  
---


   12. what is a template ?

```

         template is an HTML view of Angular in which we can write 
         directives. 
         
         there are two ways of defining template one is inline and 
         other is a separate HTML file

```

---

   
   13. explain the four types of Data bindings in Angular?
   
```
      data binds means how view (html) and component communicate with each other
 
       1) interpolation / expression binding --> {{}}

        data flows from component to the view and we can mix
          the same with HTML tags.
       	   
       2) property binding --> []
        
       data flows from component to view
       
       3) event binding --> click, keypress, keyup --> ()
        
       when you want to send event from the view to component
       
       4) two way binding --> [()] 
 	    
       Data flows from component to the view and vice versa.


```
 
---


   14. explain the architecture of Angular ?
   
```
      Angular MVC architecture follows,
      
      a group of components present in module
   
      view (template)  <-------->  Controller (Component) <--------> Model (Service)
             
     		         
      
      Points should be discuss: 
      
      1. Template : HTML view of Angular
      2. Component : Binds the view and Model
      3. Modules : Groups components logically
      4. Binding : Defines how view and component communicate
      5. Directives : changes the HTML DOM behaviour
      6. Service : Helps to share common logic across the project
      7. DI (Dependancy Injector) : it helps to inject instance across constructor

```
  
---


  15. what is SPA in Angular ?

```
         In SPA all application's functions exist in a single HTML page. 
         As users access your application's features, the browser needs to render only the parts that matter to the user, instead of loading a new page. 
         This pattern can significantly improve your application's user experience &
         performance improvement
    	
         When user accessing to new page or features angular will replace only specific 
         component or module. In angular we can achieve using routing, <router-outlet> and lazy loading.          

```

---
 	
 16.  How to implement SPA in Angular ?
 	
```
      In angular we can achieve using routing, <router-outlet> and lazy loading.          

```
---

 17. How to implement routing in Angular ?
 
 ```
            routing is a simple collection which has two things URL
            and when this URL is called which component to load.

            In app.routing.module file we configure routing 
            if we implementing lazy loading then app.routing file we configure
            modules level root routing (loadchildren) and in sub-modules we configure
            component level child routing.
 
 ```
 
 ---

 18.  Explain Lazy Loading ? 
 
 ```
            it means on demand loading, loading only the 
            necessary HTML, CSS and js files so that you 
            have better performance.

            for implementing lazy loading in app.routing file we configure
            modules level root routing (loadchildren) and in sub-modules we configure
            component level child routing.
  
 ```
     
---

 19.  How to implement Lazy Loading in Angular ?
 
 ```
            divide your project in to modules
 
 	         use "loadChildren to load module"
 
 ```

---  
 
 
 20.  Define Services ?
 
 ```
      services helps you to share common logic across angular projects
      services uses Dependency injections for sharing common logic throughout 
      application.

 ```  
 
---
 
 21.  What is Depedency Injection ?
 
```

         DI is an application design pattern where rather than
         creating object instances from within the component
         angular injects it via the constructor.

```
   
---


 22.  How to implement Depedency Injection?
 
 ```
      1. create service
      2. add in provider (in app module)
      3. inject into your component where you need
      4. using injected variable use common function, variables in your code

 ```
 
 ---
 
 23.  Whats the benefit of Depedency Injection ?
 
 ```
 
            DI helps to decouple class dependencies,
            so that when you add new dependencies you do not have
            change everywhere.
         
            
            if we create object in every component without using DI
            then its becomes tightly coupled and if new changes 
            occure then have to change everywhere
 
 ```

---

 24.  Differentiate between ng Serve and ng build ?
 
```
      "ng serve" builds in memory while,
         
      "ng build" builds on the hard disk. 
         
      so when you want to go for production "ng build" 
      command is used.

```

---

 25.  Explain the --prod parameter in ng build ?
  

```
      ng build --prod flag creates build for production and
      compresses your JS file, removes 
      comments, creates GUIDs of your JS files and make
      your application ready for production.

```

---
  

26. More info about Angular component file 


```

   html: templateUrl has most preference than template,
        if we try to use both then templateUrl (external html file) has more preference.

   css: in styleUrls we can add external css file (other component css file) also. (in array)
   
   styleUrls and styles have same preference, but if we apply common properties then it will apply only from styles and not from styleUrls.

```  
  
---

27. Difference between Framework & library

```
      Both the framework vs library is precoded support programs to develop complex software applications. However, libraries target a specific functionality, while a framework tries to provide everything required to develop a complete application

      React is library and Angular it is framework.
```

---


28. What are Building blocks of angular

```
         component
         modules
         services
         directives
         pipes
         DI
         Template
         Data binding
         Metadata
         Routing         
```

---

29. What are Component

```
      Components are the main building blocks for Angular applications. Each component consists of: An HTML template that declares what renders on the page. A TypeScript class that defines behavior. A CSS selector that defines how the component is used in a template
```

---

30. What is Template

```
         In Angular, a template is a blueprint for a fragment of a user interface (UI). Templates are written in HTML, and special syntax can be used within a template to build on many of Angular's features.
```

---


31. What is the difference bektween the Component and a directive?

```
   1. @Directive annotation used for custom directive 
   
                     *** 
   
      @Component annotation used for component


   2. used in any existing DOM to add behavior 

                     *** 
      
      template field is used to provide a View of component


   3.  Directives are not limited, comes with different types of directive such 
       as Attribute, Directive and structural directive.

                     ***

      Only one Angular Component can be present for a particular view and this component 
      can be used across angular application using the selector tag.
   
   4. The directive should be used whenever you need to add/modify existing DOM behavior 
      based on some action or event performed

                     ***

      Component can be accessed by any other Component within the application


```


32. Difference between promise and observable ?  
```
      1. Emit multiple values over a period of time.
               ***
         Emit a single value at a time.

      2. Are lazy: they’re not executed until we subscribe to them 
         using the subscribe() method.	
               ***
         Are not lazy: execute immediately after creation.

      3. Have subscriptions that are cancellable using the unsubscribe() method, 
         which stops the listener from receiving further values.	
               ***
         Are not cancellable.

      4. Provide the map for forEach, filter, reduce, retry, and retryWhen operators.	
               ***
         Don’t provide any operations.

      5. Deliver errors to the subscribers.	
               ***
         Push errors to the child promises.

```


---

33. hot vs cold observables

```
      When the data source is created inside the observable, it is considered cold. 

      Otherwise, if a data source is created outside, it is a hot observable.
      
      Cold observables are unicast, whereas hot observables are multicast.
      
      Cold observables start to emit values only when we subscribe to them. 
      
      Hot ones emit values always, even if there are no subscribers.

```

---

34. which is best promise or observable ?

```
      Promises are great for handling single asynchronous operations, while Observables shine when dealing with multiple asynchronous events over time.
```
---


35. What is RxJs

```
      RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using observables that makes it easier to compose asynchronous or callback-based code.
```
---


36. rxjs operators

```
      1. map() operator: 
      
      transform the data emitted by an Observable into a new format

      perform operations such as modifying values, extracting specific properties, or even returning a completely new object

      e.g:

      const source = from([1, 2, 3, 4, 5]);

      source.pipe(
      map(value => value * 2)
      ).subscribe(result => console.log(result));

      // Output: 2, 4, 6, 8, 10

      
      2. filter() operator: 

      allows you to selectively filter the values emitted by an Observable based on a given condition.

      e.g:

      const source = from([1, 2, 3, 4, 5]);

      source.pipe(
      filter(value => value % 2 === 0)
      ).subscribe(result => console.log(result));

      // Output: 2, 4


      3. debounceTime() operator:

      used to control the frequency of emitted values from an Observable. It waits for a specified duration of inactivity before emitting the most recent value.


      const searchInput = document.getElementById('search-input');

      fromEvent(searchInput, 'input').pipe(
      debounceTime(300)
      ).subscribe(event => {
      // Perform search operation here
      });


      4. switchMap() operator:

      often used for handling asynchronous operations, such as making HTTP requests in Angular. It transforms the values emitted by an Observable into a new Observable and automatically unsubscribes from the previous inner Observable when a new value arrives.

      const button = document.getElementById('button');

      fromEvent(button, 'click').pipe(
      switchMap(() => fetchData())
      ).subscribe(data => {
      // Handle fetched data here
      });

      function fetchData() {
      // Perform HTTP request and return an Observable
      }


      5. catchError() operator:

      allows you to gracefully handle errors emitted by an Observable. It intercepts an error, allowing you to recover from it, log it, or provide an alternative value or fallback behavior

      const source = of(1, 2, 3, 'oops', 5);

      source.pipe(
      map(value => value * 2),
      catchError(error => {
         console.log('Error:', error);
         return of(0); // Fallback value
      })
      ).subscribe(result => console.log(result));

      // Output: 2, 4, 6, Error: oops, 0, 10


      6. tap() operator:

      allows you to perform side effects or actions on the emitted values of an Observable without modifying the values themselves. It is often used for debugging, logging, or triggering actions that do not affect the stream

      const source = from([1, 2, 3, 4, 5]);

         source.pipe(
         tap(value => console.log('Value:', value)),
         map(value => value * 2)
         ).subscribe(result => console.log(result));

         // Output:
         // Value: 1
         // 2
         // Value: 2
         // 4
         // Value: 3
         // 6
         // Value: 4
         // 8
         // Value: 5
         // 10

      7. of() operator:

      used to create an Observable that emits a sequence of values. It takes any number of arguments and emits each argument as a separate value in the sequence

      of(1, 2, 3, 4, 5).subscribe(result => console.log(result));

      // Output: 1, 2, 3, 4, 5


      8. forkJoin() operator:

      combines multiple Observables into a single Observable that emits an array of values from each source Observable, only when all the source Observables have completed. It waits for all the Observables to emit their final value and then emits an array of those values.

      const source1 = of('Hello');
      const source2 = of('World');

      forkJoin([source1, source2]).subscribe(results => {
      console.log(results[0] + ' ' + results[1]);
      });

      // Output: Hello World


      9. finalize() operator:

      allows you to perform a specified action when an Observable completes or errors, regardless of whether it emits values or not. It is often used to release resources or perform cleanup operations.

      const source = of(1, 2, 3);

      source.pipe(
      finalize(() => {
         // Cleanup or final action
         console.log('Observable completed.');
      })
      ).subscribe(result => console.log(result));

      // Output: 1, 2, 3
      //         Observable completed.


      10. retry() operator:

      allows you to retry the emission of values from an Observable when it encounters an error. It takes the number of retry attempts as a parameter and resubscribes to the source Observable.

      const source = interval(1000);

      source.pipe(
      retry(3)
      ).subscribe(
      result => console.log(result),
      error => console.error('Error:', error)
      );
      
      
      11. take() operator:

      allows you to take a specified number of values emitted by an Observable and then complete. It limits the stream to emit only the desired number of values.


      const source = interval(1000);

      source.pipe(
      take(5)
      ).subscribe(result => console.log(result));

      // Output: 0, 1, 2, 3, 4


      12. distinctUntilChanged() operator:

      filters out consecutive duplicate values emitted by an Observable. It ensures that only unique values are propagated downstream

      const source = from([1, 1, 2, 2, 3, 3, 3, 4, 5]);

      source.pipe(
      distinctUntilChanged()
      ).subscribe(result => console.log(result));

      // Output: 1, 2, 3, 4, 5

      13. merge() operator:

      const source1 = interval(1000);
      const source2 = interval(500);

      merge(source1, source2).subscribe(result => console.log(result));

      // Output: 0, 0, 1, 1, 2, 0, 3, 2, 4, 1, 5, 3, ...


      14. scan() operator:

      applies an accumulator function over the values emitted by an Observable and emits the accumulated result after each emission. It is similar to the Array.reduce() method

      const source = from([1, 2, 3, 4, 5]);

      source.pipe(
      scan((acc, value) => acc + value, 0)
      ).subscribe(result => console.log(result));

      // Output: 1, 3, 6, 10, 15

```
---


37. event emmiter

```
      EventEmitter in Angular is utilized for communication between components. Custom events are emitted from a child component to its parent component through the use of EventEmitter. For instance, when a button on a child component is clicked, the child component employs an EventEmitter to inform the parent component of the button click.

      It can be implement it with the utilization of the @Output() decorator and the EventEmitter class

      @Output() eventName = new EventEmitter<Type>();

      this.eventName.emit(value)

```
---

38. decorator

```
      Decorators are design patterns used to isolate the modification or decoration of a class without modifying the source code.

      Class decorators, such as @Component and @NgModule
      Property decorators for properties inside classes, such as @Input and @Output
      Method decorators for methods inside classes, such as @HostListener
      Parameter decorators for parameters inside class constructors, such as @Inject

```


39. custom pipe

```
   pipes are simple functions designed to accept an input value, process, and return a transformed value as the output

   Angular Pipes are TypeScript classes with the @Pipe decorator. 

   CLI Command: ng g p pipe-name

         @Pipe({
            name: 'demopipe',
            pure:true
         })

      export class DemopipePipe implements PipeTransform {

         transform(value: unknown, ...args: unknown[]): unknown {

         return null;
      } }

   here PipeTransform is interface which provide transform method.

   in module or components we can use as==> declarations: [DemopipePipe]


   and in html we can use as ==>  <p>Super power boost: {{2 | demopipe: 10}}</p>

```

---

40. What is async pipe


```
      In Angular, the async pipe is a pipe that essentially does these three tasks:

      1. It subscribes to an observable or a promise and returns the last emitted value.
      
      2. Whenever a new value is emitted, it marks the component to be checked. That means Angular will run Change Detector for that component in the next cycle.
      
      3. It unsubscribes from the observable when the component gets destroyed.

      Also, as a best practice, it is advisable to try to use a component on onPush change detection strategy with async pipe to subscribe to observables.
      
```
---



23. What directives and pipes

24. how to create dynamic component

25. Which form you use template driven or reactive forms

In case of multi-step forms, how will you use reactive form in it?

26. How to use shareable component

27. What is @INPUT & @OUTPUT decorators?

28. What is pipe? How to implement it?

29. What are validators in Angular? How to implement it?

30. How would you validate a form in angular?

31. How would you display the data in the frontend in angular?

32. Life cycle hooks

```
         ngOnChanges : @Input property binding and every change in @Input property
         ngOnInIt : component initialization
         ngDoCheck :  fires every change detection
         ngAfterContentInit : <ng-content> projection done
         ngAfterContentDochecked : <ng-content> projection changes
         ngAfterViewInit : view finished it's initialization
         ngAfterViewChecked : change detection occure in view
         ngOnDestroy : component destroyed

```

33. What is directive? Types and syntax for ngif and ngfor

34. Had you created a custom directive? had you created a directive in the project that you had done before?


35. How to share the data between two component? or How we can communicate across(pass data from one component to another) the components? 



36. What is routing?

37. wild card route

38. What is router-outlet

39. How to protect the routes?

40. What is lazy Loading ? how to implement?, advantages and disadvantage?

41. How to stop initial navigation until some condition is satisfied?

42. what are services? why it had introduced in angular?

43. how to create a service ?

44. dependency injection and why we used?

45. As we can also import the services in the components directly by creating the object of that services. So why we are using the dependency injection?


46. communication between modules?

47. how to share data between two modules in angular ? 

48. How to show grid in angular? And how to show data in grid?

49. How to use validation in search bar?

50. Types of event handler

51. How to handle error in angular? Syntax

52. If we want to search any data after entering 3 character How to implement that? 

53. How would you get the data from the api in angular?

54. Explain different types of event in angular?

55. If you have a huge data then how would you show in the frontend in angular?

56. How would you implement sorting and filtering if you have got a huge amount of data in your table or grid.


57. what is main.js polyfill.js vendor.js

58. what is -o in command ng s -o?

59. what is single sign on? sso?

60. session storage VS local Storage?
61. I have one lack recode in our application, how to show in web page ?


62. Difference between JIT & AOT

63. Benefits of trackBy

64. What is a Change Detection Strategy? (https://www.xenonstack.com/blog/performance-optimization-in-angular)

65. How to manage state in Angular => ngrx

66. How to make http calls

67. Explain build process of angular application

68. Difference between Subject & Behavior subject & ReplaySubject & AsyncSubject (https://medium.com/@jaydeepvpatil225/observables-and-subjects-in-angular-a4d73dfa5bb)



69. What is View encapsulation in Angular

70. How to manage/handle session in ng

71. What is package.json & its need?

72. what are shared modules

73. what is http interceptor

74. What is authguard /routeGuard / guards

75. callback promises observable

76. subject vs behaviouralSubject

77. app module - how to get other than app component as a home component

78. dependency and dev dependency - diff



81. infinite scrolling npm pacakage

82. What are HTTPIntercepters & why used??



-------------------------------

new





Explain angular deployment, how is it done?
ngrx, flow: how state, actions, selectors, etc work
What is responsive design? what is mobile-first approach?
Multilanguage support?
How to select multiple data from drop-down


what are different ways to optimize a given project to minimize the rendering 
load and package size?? anything related to ng build? 
(Ans: ng build with aot option, instead of default JIT compilation)




**********************


**explain following code:
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
@NgModule({
  imports:     [ BrowserModule ],
  providers:   [ Logger ],
  declarations: [ AppComponent ],
  exports:     [ AppComponent ],
  bootstrap:   [ AppComponent ]
})
export class AppModule { }


how to show reverse order in js? like 12345 - 54321 & also can show in typescript ?


*******************************************************


Performance optimization?
cross component communication
Inter component communication?
How to easily make all properties of an interface optional?

is it possible to initialize variables in a constructor


typescript vs javascript? advantages of typescript?

app module - how to get other than app component as a home component

dependency and dev dependency - diff


Types of event handler

How to handle error in angular? Syntax

Explain different types of events in angular?


How to manage/handle session in ng

What is package.json & its need?

what are html selectors
what are css selectors
what is singleton class

explain two way binding

what is providers in angular ?
what is whitespaing ?


Transpiling?
web-socket?
web accessibility
Angular upgrade
unit testing? describe different test cases for a 

login component with 2 input fields, submit button & cancel button



Coding & Scenario:

Q. coding question using notepad, show result on a browser:- 
create a button using html, change its style, show alert on click


prime number program



Scenario 1:- 

You have a dropdown in that you have options of cities. 
If you click on the city you would get the data as name and category. 
So how would you display the data in of the categories and name in a card.


Scenario 2:- 

In a project, If you have three modules:- AppModule,ModuleA,ModuleB. 
and If you run the application the AppModule would be loaded and if i go to Module A, 
the module A would be loaded. After that i clear the cache memory and reload the application. 
Then if go directly on ModuleB. It would load moduleA and ModuleB. So what would be the mistake 
that had might done by the developer.

* If API returns random string which contains "Click Here" .
 Display that string and also display the "Click Here" in link format. 
 (without using javascript functions, just logic)


* CSS= If there are 4 Div's in a row eg:(Div 1, Div 2, Div 3, Div 4).... 
Display Div 4 before Div 1, just using CSS.


* css=>there is div inside there is two div's =>display:flex=> what is the output

* justify-content-center=>what is the output

const a=[1,2,3] a.map(x=>x*3) and a.filter(x=>x*3) output?ans=>for map=[3,6,9],filter=[1,2,3]

const a={x:3,y:2,z:4}=>get z value by spread or destructure  methods=>ans=>const {z}=a

there is a button and and a table with 7 columns. I am fetching 7 APIs onclick how to 
render them immediately without wait.


respons of fetched api is either paragraph or single line or empty. 
If it's not empty and it has click here show it as a link .

 change order of 4 divs using css.

config dependencies? if there is a conflict in the dependecy library? how you can overcome that



------------------------------------------------------
 
----------Practical/Scenario questions-------------

1. create two different modules and components inside them. communicate in between with the help of subject.

2. Scenario: In a project, If you have three modules:- AppModule,ModuleA,ModuleB. and If you run the application the AppModule would be loaded and if i go to Module A, the module A would be loaded. After that i clear the cache memory and reload the application. Then if go directly on ModuleB. It would load moduleA and ModuleB. So what would be the mistake that had might done by the developer.


3. Scenario: 3api call- if get response from all , then only page should be load

-----------------------



