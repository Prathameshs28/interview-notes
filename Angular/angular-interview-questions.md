#  Most Important & Latest Angular Questions

##### What directives and pipes ?

##### how to create dynamic component

##### Which form you use template driven or reactive forms

##### In case of multi-step forms, how will you use reactive form in it?

##### How to use shareable component

##### What is @INPUT & @OUTPUT decorators?

##### What is pipe? How to implement it?

##### What are validators in Angular? How to implement it?

##### How would you validate a form in angular?

##### How would you display the data in the frontend in angular?

##### What is directive? Types and syntax for ngif and ngfor

##### Had you created a custom directive? had you created a directive in the project that you had done before?

##### How to share the data between two component? or How we can communicate across(pass data from one component to another) the components? 

##### What is routing?

##### wild card route

##### What is router-outlet

##### What is lazy Loading ? how to implement?, advantages and disadvantage?

##### How to stop initial navigation until some condition is satisfied?

##### what are services? why it had introduced in angular?

##### how to create a service ?

##### dependency injection and why we used?

##### As we can also import the services in the components directly by creating the object of that services. So why we are using the dependency injection?

##### communication between modules?

##### how to share data between two modules in angular ? 

##### How to show grid in angular? And how to show data in grid?

##### How to use validation in search bar?

##### Types of event handler

##### How to handle error in angular? Syntax

##### If we want to search any data after entering 3 character How to implement that? 

##### How would you get the data from the api in angular?

##### Explain different types of event in angular?

##### If you have a huge data then how would you show in the frontend in angular?

##### How would you implement sorting and filtering if you have got a huge amount of data in your table or grid.

##### what is main.js polyfill.js vendor.js

##### what is -o in command ng s -o?

##### session storage VS local Storage?

##### I have one lack recode in our application, how to show in web page ?

##### Difference between JIT & AOT

##### Benefits of trackBy

##### What is a Change Detection Strategy? (https://www.xenonstack.com/blog/performance-optimization-in-angular)

##### How to manage state in Angular => ngrx

##### How to make http calls

##### Explain build process of angular application

##### Difference between Subject & Behavior subject & ReplaySubject & AsyncSubject (https://medium.com/@jaydeepvpatil225/observables-and-subjects-in-angular-a4d73dfa5bb)

##### What is View encapsulation in Angular

##### How to manage/handle session in ng

##### What is package.json & its need?

##### what are shared modules

##### callback promises observable

##### subject vs behaviouralSubject

##### app module - how to get other than app component as a home component

##### dependency and dev dependency - diff

##### infinite scrolling npm pacakage


##### Standalone Component


##### Optimizing angular app

##### Angular universal - SSR

##### Angular animation

##### Offline capabilities using service worker

##### Angular Schematics

##### ng Deploy

##### Managing Multiple Projects in One Folder

##### ActivatedRouteSnapshot, RouterStateSnapshot ActivatedRoute NavigationEnd NavigationStart ActivatedRoute, Data, Event, NavigationEnd, Router


##### angular logging and monitoring


##### cross component communication

##### Inter component communication?

##### How to easily make all properties of an interface optional?

##### is it possible to initialize variables in a constructor

##### typescript vs javascript? advantages of typescript?

##### app module - how to get other than app component as a home component


##### what are html selectors

##### what are css selectors

##### what is singleton class

##### explain two way binding

##### what is providers in angular ?

##### what is whitespaing ?
 
##### Transpiling?

##### web-socket?

##### web accessibility

##### Angular upgrade

##### Unit testing? describe different test cases for a 

##### Explain angular deployment, how is it done?

##### ngrx, flow: how state, actions, selectors, etc work

##### What is responsive design? what is mobile-first approach?

##### Multilanguage support?

##### How to select multiple data from drop-down



##### load and package size?? anything related to ng build? 
 (Ans: ng build with aot option, instead of default JIT compilation)

##### how to check bundle size of particular component in angular

- Webpack-bundle-analyzer, a freely available tool, to analyze the bundle size of an angular application. 

- Information from the bundle-size analysis will help you in making an informed decision in order to optimize application load time.


```js
// install the webpack-bundle-analyzer package globally
npm install webpack-bundle-analyzer -g

// build anguar project
ng build --configuration production --stats-json

// see stats
npx webpack-bundle-analyzer dist/test-project/stats.json
```
---

##### how to minimize bundle size of angular build

##### api call before component re direct

##### charts library used or not?

##### event looping in angular
---

##### Explain latest features of the angular version you are working on ?

<p>

1. Built-in control flow (*ngFor, *ngIf, *ngSwitch)
2. improvement in lazy loading (@defer)
3. ssr package
4. new lifecycle hooks (afterrender, afternextrender)
5. vite + esBuild builder
6. DI dev tools
7. Standalone component

</p>

---

##### ng-container in angular


```js
   ng-container uses:

   1. avoid redundant elements
      e.g:

   <ng-container *ngIf="postsList" >   // instead of div use ng-container
   <div *ngFor="let post of postsList" >
      {{post.id}} : {{post.name}}
   </div>
   </ng-container>

   2. used in inline content:

   <div>
   <ng-container *ngIf="error">Oops: </ng-container> //instead of span use ng-container
   {{message}}
   </div>


   3. to Ensure Valid HTML Standards:

   <ul>
   <ng-container *ngFor="let todo of todos">   // instead of div use ng-container
      <li *ngIf="todo.content !== 'Done'">
         {{ todo.content }}
      </li>
   </ng-container>
   </ul>

```

---


##### ng-template, ng-container,ng-content, ngTemplateOutlet

```js

1. <ng-template></ng-template>:

<ng-template> Angular uses with structural directives ( *ngIf, *ngFor, [ngSwitch], and custom directives).

only work with structural directives
a template that doesn’t render anything by itself
It helps us create dynamic templates that can be customized and configured.

<div> 
   <div *ngIf=”false else showNgTemplateContent”> 
      Shouldn't be displayed 
   </div>
</div>
 
<ng-template #showNgTemplateContent> Should be displayed
</ng-template>



2. <ng-container></ng-container>


allows you to group elements in a template that doesn’t interfere with styles or layout because Angular doesn’t put it in the DOM

This is helpful if you don’t want any extra div on DOM,


For eg: If there are two structural directives being called on one div as below:

<div *ngIf="details" *ngFor="let info of details">
  {{ info.content }}
</div>

Error: Can't have multiple template bindings on one element. Use only one attribute prefixed with *

we can solve this using ng-container without adding any extra element in the DOM

<ng-container> *ngIf="details">
  <div *ngFor="let info of details">
    {{ info.content }}
  </div>
</<ng-container>



3. <ng-content></ng-content>


used to project content into Angular components.

Parent component html: 

<app-child>
  <div> Child Component Details </div>
</app-child>


In child componet
<ng-content></ng-content>


<ng-content> accepts a select attribute,


4. ngTemplateOutlet: (ngTemplateOutletContext)

ngTemplateOutlet is a structural directive
we can create customisable templates
Before we can use ngTemplateOutlet we must first define a template using <ng-template>



<ng-template #myTemplate> World! </ng-template>

Hello
<ng-container [ngTemplateOutlet]="myTemplate"></ng-container>


```

---

##### what the use of angular?

```
   angular is js ui binding framework which binds html ui and js model (view modal)

   mvvm / mvc / mvvm

   adding to it, it is also helps you to build SPA (Single page application) by
   using concept of routing it also has lot of other features like 
   HTTP, DI, Input output because of which you do not need other frameworks

```
 
---
 
##### Difference between angularjs vs angular
   
| Sr.no | angularjs | angular ts |
| ----------- | ----------- | ----------- |
| 1 | Written in TypeScript (also supports JavaScript) | Written in JavaScript |
| 2 | Supported by all popular mobile browsers | Does not support mobile |
| 3 | Uses Components and Directives | Follows Model-View-Controller design |
| 4 |A hierarchical DI system| use directives in place of DI | 
| 5 | CLI tool | not CLI tool |
| 6 | More SEO-friendly  | less  SEO-friendly|
| 7 | unit testing with Karma | Requires third-party tools for testing and error detection |


---
 
##### what are directives in Angular ?
 
```
   Directives changes the behavior of HTML DOM.
   
   e.g. ngModel, [hidden], {{anything}} 
```

---
 
 
##### Explain the different types of Angular Directives ?

```
   3 types SAC (S: Structural, A: Attribute, C: component)
   
   1. Structural Directive: change the DOM layout by adding and removing elements.      
      e.g *ngFor         

   2. Attribute Directive: change the appearance and behaviour of HTML elements      
      e.g [hidden] , [disable]
      
   3. Component Directive: Directives with templates. Itself directive.


```
 
 ---
 	
 
##### Explain the importance of NPM and node_modules folder?
 
 ```
      npm is package manager which makes installation of js framework easy.
      
      node_modules is the folder where all packages are installed. 
 
 ```

---

 
##### explain the importance of package.json file in angular ?

```
      it has all the js references needed for a project, so rather 
      than installing one package at a time we can install all 
      packages in one go

```
 	
---


##### what is typescript and why do we need it?

```
      	typescript superset of js, it added types to js.
      
         it gives a nice Object-Oriented programming environment
         which transpiles / converts to js.         
         
         so as its strongly typed, we will have less errors and because 
         we can do OOP with js our productivity and quality also 
         increases.

```

---
  
##### explain importance of angular CLI ?

```
       angular CLI is command line interface, by which 
       we can create initial angular project template.        
       We can install third party packages in our application.
       we can run application
       we can perform testing
       we can build our application for production

```

---     
  
##### Explain the importance of Component and modules ?
  
```
         component is where you write your binding code, 
         module is logically groups of components.
         
         
         view -- > component <-- modal
                     |		
                    css 

```

---
 
 
##### what is a decorator in Angular?

```
      Decorators are metadata in angular project.
      Decorator defines what kind of Angular class is it,
      for example if you decorate @Component then it says it's
      an angular component if you put @NgModule it becomes a Angular module

      1. Class Decorators: @Component and @NgModule
      2. Parameter Decorators:  @Inject, @Optional
      3. Property Decorators: @Output, @Input
      4. Method Decorators: : @HostListener, @HostBinding


```
 
---

  
##### what are annotations or metaData ?
  
```
      In Angular, an annotation refers to a type of metadata that is used to enhance and provide additional information about a class or its members. Annotations are commonly used in Angular to configure and decorate various parts of an application, including components, services, and modules

```
  
---


##### what is a template ?

```

         template is an HTML view of Angular in which we can write 
         directives. 
         
         there are two ways of defining template one is inline and 
         other is a separate HTML file

```

---

   
##### explain the four types of Data bindings in Angular?
   
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


 ##### explain the architecture of Angular ?
   
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


##### what is SPA in Angular ?

```
   In SPA all application's functions exist in a single HTML page. 
   As users access your application's features, the browser needs to render only the parts that matter to the user, instead of loading a new page. 
   This pattern can significantly improve your application's user experience &
   performance improvement

   When user accessing to new page or features angular will replace only specific 
   component or module. In angular we can achieve using routing, <router-outlet> and lazy loading.          

```

---
 	
##### How to implement SPA in Angular ?
 	
```
      In angular we can achieve using routing, <router-outlet> and lazy loading.          

```
---

##### How to implement routing in Angular ?
 
 ```
            routing is a simple collection which has two things URL
            and when this URL is called which component to load.

            In app.routing.module file we configure routing 
            if we implementing lazy loading then app.routing file we configure
            modules level root routing (loadchildren) and in sub-modules we configure
            component level child routing.
 
 ```
 
 ---

#####  Explain Lazy Loading ? 
 
 ```
            it means on demand loading, loading only the 
            necessary HTML, CSS and js files so that you 
            have better performance.

            for implementing lazy loading in app.routing file we configure
            modules level root routing (loadchildren) and in sub-modules we configure
            component level child routing.
  
 ```
     
---

#####  How to implement Lazy Loading in Angular ?
 
 ```
            divide your project in to modules
 
 	         use "loadChildren to load module"
 
 ```

---  
 
 
#####  Define Services ?
 
 ```
      services helps you to share common logic across angular projects
      services uses Dependency injections for sharing common logic throughout 
      application.

 ```  
 
---
 
##### What is Depedency Injection ?
 


- Dependency Injection is a design pattern that helps achieve loose coupling between components by injecting their dependencies rather than creating them within the component.

- DI is an application design pattern where rather than creating object instances from within the component angular injects it via the constructor.

- Providers: Providers are responsible for creating instances of services and making them available for injection Components, services, or other Angular objects can receive their dependencies through constructor injection

1. @Injectable: Marks a class as a service that can be injected into other components, services, or directives

2. @Inject: Specifies a dependency explicitly when there are multiple providers for a given token

   constructor(@Inject(MY_MESSAGE) private message: string) {}

3. @Optional: Allows an injected dependency to be optional. If the dependency is not found, Angular will inject null instead of throwing an error.

```js
   constructor(@Optional() private myOptionalService: MyOptionalService) {
      this.message = myOptionalService
         ? myOptionalService.getMessage()
         : 'Optional service not available';
   }
```

4. @Self: The @Self decorator instructs Angular to look for the dependency only in the local injector. The local injector is the injector that is part of the current component or directive.

   Angular DI Framework to look for the Dependency attached to the current Component.


5. @SkipSelf: The @SkipSelf decorator instructs Angular to look for the dependency in the Parent Injector and upwards.

   not to look for the injector in the local injector, but start from the Parent.


6. @Host(): 

   @Host() decorator makes Angular to look for the injector on the component itself (similar to the @Self()). But if the injector is not found there, it looks for the injector up to its host component.


   we can do this as well:

   constructor (@Host() @SkipSelf() @Optional() toys: ToysService) {...}
  
---


##### How to implement Depedency Injection?
 
 ```
      1. create service
      2. add in provider (in app module)
      3. inject into your component where you need
      4. using injected variable use common function, variables in your code

 ```
 
 ---
 
##### Whats the benefit of Depedency Injection ?
 
 ```
 
            DI helps to decouple class dependencies,
            so that when you add new dependencies you do not have
            change everywhere.
         
            
            if we create object in every component without using DI
            then its becomes tightly coupled and if new changes 
            occure then have to change everywhere
 
 ```

---


#####  Differentiate between ng Serve and ng build ?
 
```
      "ng serve" builds in memory while,
         
      "ng build" builds on the hard disk. 
         
      so when you want to go for production "ng build" 
      command is used.

```

---


#####  Explain the --prod parameter in ng build ?
  

```
      ng build --prod flag creates build for production and
      compresses your JS file, removes 
      comments, creates GUIDs of your JS files and make
      your application ready for production.

```

---
  

##### More info about Angular component file 


```

   html: templateUrl has most preference than template,
        if we try to use both then templateUrl (external html file) has more preference.

   css: in styleUrls we can add external css file (other component css file) also. (in array)
   
   styleUrls and styles have same preference, but if we apply common properties then it will apply only from styles and not from styleUrls.

```  
  
---

##### Difference between Framework & library

```
      Both the framework vs library is precoded support programs to develop complex software applications. However, libraries target a specific functionality, while a framework tries to provide everything required to develop a complete application

      React is library and Angular it is framework.
```

---


##### What are Building blocks of angular

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

##### What are Component

- Components are the main building blocks for Angular applications. 
- Each component consists of: An HTML template that declares what renders on the page. 
- A TypeScript class that defines behavior. 
- A CSS selector that defines how the component is used in a template

---

##### What is Template

- In Angular, a template is a blueprint for a fragment of a user interface (UI). 
- Templates are written in HTML, and special syntax can be used within a template to build on many of Angular's features.

---


##### What is the difference bektween the Component and a directive?


|Sr.no| Component | Directive |
| --------- | --------- | --------- |
| 1 | @Directive annotation used for custom directive | @Component annotation used for component |
| 2| used in any existing DOM to add behavior  | template field is used to provide a View of component |
| 3 | Directives are not limited, comes with different types of directive such as Attribute, Directive and structural directive. | Only one Angular Component can be present for a particular view and this component can be used across angular application using the selector tag. |
| 4 | The directive should be used whenever you need to add/modify existing DOM behavior based on some action or event performed | Component can be accessed by any other Component within the application |

---

##### Difference between promise and observable ?  


| Sr.no | Promises | Observable |
| ------- | ------- | ------- |
| 1 | Emit multiple values over a period of time. |  Emit a single value at a time. |
| 2 | Are lazy: they’re not executed until we subscribe to them using the subscribe() method. | Are not lazy: execute immediately after creation. |
| 3 | Can be cancellable using the unsubscribe() | Are not cancellable. |
| 4 | Provide the map for forEach, filter, reduce, retry, and retryWhen operators. | Don’t provide any operations |
| 5 | Deliver errors to the subscribers. | Push errors to the child promises. |

---


##### Hot & Cold observables

- When the data source is created inside the observable, it is considered cold. 

- Otherwise, if a data source is created outside, it is a hot observable.

- Cold observables are unicast, whereas hot observables are multicast.

- Cold observables start to emit values only when we subscribe to them. 

- Hot ones emit values always, even if there are no subscribers.


---

##### which is best promise or observable ?

- Promises are great for handling single asynchronous operations
- while Observables shine when dealing with multiple asynchronous events over time.

---


##### What is RxJs

- RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using observables that makes it easier to compose asynchronous or callback-based code.

---


##### rxjs operators

- map() operator: 
      
   transform the data emitted by an Observable into a new format

   perform operations such as modifying values, extracting specific properties, or even returning a completely new object

```js
   const source = from([1, 2, 3, 4, 5]);

   source.pipe( map (value => value * 2))
   .subscribe(result => console.log(result));

   // Output: 2, 4, 6, 8, 10

```

      
- filter() operator: 

   allows you to selectively filter the values emitted by an Observable based on a given condition.

```js

   const source = from([1, 2, 3, 4, 5]);

   source.pipe(filter(value => value % 2 === 0))
   .subscribe(result => console.log(result));

   // Output: 2, 4

```


- debounceTime() operator:

   used to control the frequency of emitted values from an Observable. It waits for a specified duration of inactivity before emitting the most recent value.

```js

   const searchInput = document.getElementById('search-input');

   fromEvent(searchInput, 'input').pipe(
   debounceTime(300))
   .subscribe(event => {
   // Perform search operation here
   });

```


-  switchMap() operator:

   often used for handling asynchronous operations, such as making HTTP requests in Angular. It transforms the values emitted by an Observable into a new Observable and automatically unsubscribes from the previous inner Observable when a new value arrives.

```js

   const button = document.getElementById('button');

   fromEvent(button, 'click')
   .pipe(switchMap(() => fetchData()))
   .subscribe(data => {
   // Handle fetched data here
   });

   function fetchData() {
   // Perform HTTP request and return an Observable
   }

```


- catchError() operator:

      allows you to gracefully handle errors emitted by an Observable. It intercepts an error, allowing you to recover from it, log it, or provide an alternative value or fallback behavior

```js

   const source = of(1, 2, 3, 'oops', 5);

   source.pipe(map(value => value * 2),
   catchError(error => {
      console.log('Error:', error);
      return of(0); // Fallback value
   }))
   .subscribe(result => console.log(result));

   // Output: 2, 4, 6, Error: oops, 0, 10

```


- tap() operator:

   allows you to perform side effects or actions on the emitted values of an Observable without modifying the values themselves. It is often used for debugging, logging, or triggering actions that do not affect the stream

```js

   const source = from([1, 2, 3, 4, 5]);

   source.pipe(tap(value => console.log('Value:', value)),
   map(value => value * 2))
   .subscribe(result => console.log(result));

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

```

- of() operator:

   used to create an Observable that emits a sequence of values. It takes any number of arguments and emits each argument as a separate value in the sequence

```js
   of(1, 2, 3, 4, 5)
   .subscribe(result => console.log(result));

   // Output: 1, 2, 3, 4, 5

```


 - forkJoin() operator:

   combines multiple Observables into a single Observable that emits an array of values from each source Observable, only when all the source Observables have completed. It waits for all the Observables to emit their final value and then emits an array of those values.

```js
   const source1 = of('Hello');
   const source2 = of('World');

   forkJoin([source1, source2]).subscribe(results => {
   console.log(results[0] + ' ' + results[1]);
   });

   // Output: Hello World

```


- finalize() operator:

   allows you to perform a specified action when an Observable completes or errors, regardless of whether it emits values or not. It is often used to release resources or perform cleanup operations.

```js

   const source = of(1, 2, 3);

   source.pipe(
   finalize(() => {
      // Cleanup or final action
      console.log('Observable completed.');
   })
   ).subscribe(result => console.log(result));

   // Output: 1, 2, 3
   // Observable completed.

```


- retry() operator:

   allows you to retry the emission of values from an Observable when it encounters an error. It takes the number of retry attempts as a parameter and resubscribes to the source Observable.

```js

   const source = interval(1000);

   source.pipe(retry(3))
   .subscribe(
   result => console.log(result),
   error => console.error('Error:', error));      

```
      
- take() operator:

   allows you to take a specified number of values emitted by an Observable and then complete. It limits the stream to emit only the desired number of values.

```js
   const source = interval(1000);

   source.pipe(take(5))
   .subscribe(result => console.log(result));

   // Output: 0, 1, 2, 3, 4

```



- distinctUntilChanged() operator:

   filters out consecutive duplicate values emitted by an Observable. It ensures that only unique values are propagated downstream

```js

   const source = from([1, 1, 2, 2, 3, 3, 3, 4, 5]);

   source.pipe(distinctUntilChanged())
   .subscribe(result => console.log(result));

   // Output: 1, 2, 3, 4, 5

```

- merge() operator:

   The RxJS merge() operator is a join operator that is used to turn multiple observables into a single observable. It creates an output Observable, which concurrently emits all values from every given input Observables.


```js
   const source1 = interval(1000);
   const source2 = interval(500);

   merge(source1, source2).subscribe(result => console.log(result));

   // Output: 0, 0, 1, 1, 2, 0, 3, 2, 4, 1, 5, 3, ...
```


- scan() operator:

   applies an accumulator function over the values emitted by an Observable and emits the accumulated result after each emission. It is similar to the Array.reduce() method

```js

   const source = from([1, 2, 3, 4, 5]);

   source.pipe(scan((acc, value) => acc + value, 0))
   .subscribe(result => console.log(result));

   // Output: 1, 3, 6, 10, 15

```

---


##### Event emmiter

```js
   EventEmitter in Angular is utilized for communication between components. Custom events are emitted from a child component to its parent component through the use of EventEmitter. For instance, when a button on a child component is clicked, the child component employs an EventEmitter to inform the parent component of the button click.

   It can be implement it with the utilization of the @Output() decorator and the EventEmitter class

   @Output() eventName = new EventEmitter<Type>();

   this.eventName.emit(value)

```
---

##### Decorator

```
   Decorators are design patterns used to isolate the modification or decoration of a class without modifying the source code.

   Class decorators, such as @Component and @NgModule
   Property decorators for properties inside classes, such as @Input and @Output
   Method decorators for methods inside classes, such as @HostListener
   Parameter decorators for parameters inside class constructors, such as @Inject

```


##### custom pipe

```js

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

##### What is async pipe


```
      In Angular, the async pipe is a pipe that essentially does these three tasks:

      1. It subscribes to an observable or a promise and returns the last emitted value.
      
      2. Whenever a new value is emitted, it marks the component to be checked. That means Angular will run Change Detector for that component in the next cycle.
      
      3. It unsubscribes from the observable when the component gets destroyed.

      Also, as a best practice, it is advisable to try to use a component on onPush change detection strategy with async pipe to subscribe to observables.
      
```
---

##### Life cycle hooks

1. ngOnChanges : @Input property binding and every change in @Input property
<br>

2. ngOnInIt : component initialization 
<br>

3. ngDoCheck :  fires every change detection
<br>

4. ngAfterContentInit : <ng-content> projection done
<br>

5. ngAfterContentDochecked : <ng-content> projection changes
<br>

6. ngAfterViewInit : view finished it's initialization
<br>

7. ngAfterViewChecked : change detection occure in view
<br>

8. ngOnDestroy : component destroyed

---

##### what is http interceptor:

```js
An interceptor is a middleware service that can intercept HTTP requests and responses from the application to the server. 

The interceptor can modify the requests or responses, add headers or tokens, handle errors, or perform any other necessary actions.

Interceptors are defined as services in Angular, they can be added to the application by providing them in the HTTP_INTERCEPTORS multi-provider token.



import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler } from '@angular/common/http';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  intercept(request: HttpRequest<any>, next: HttpHandler) {
    const token = localStorage.getItem('auth_token');
    if (token) {
      const authRequest = request.clone({
        headers: request.headers.set('Authorization', `Bearer ${token}`)
      });
      return next.handle(authRequest);
    }
    return next.handle(request);
  }
}



AuthInterceptor class implements the HttpInterceptor interface and provides the intercept() method.

 The intercept() method receives the incoming request and the HttpHandler object that allows us to pass the request to the next interceptor or the final HTTP handler.


 To use this interceptor in your application, you need to provide it in the HTTP_INTERCEPTORS multi-provider token.


 @NgModule({
  imports: [HttpClientModule],
  providers: [
    { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true }
  ]
})


In this example, the AuthInterceptor is provided in the HTTP_INTERCEPTORS token as a multi-provider, which means that it can be combined with other interceptors if needed.


Interceptors in Angular have several use cases:

1. Authentication and authorization: add authentication tokens or authorization headers to outgoing requests.

2. Error handling: handle global errors that occur during HTTP requests. This can be useful for handling network, timeouts, or server-side errors.

3.Caching: to cache responses from the server, which can improve the performance of your application.

4. Logging: to log HTTP requests and responses. This can be useful for debugging and monitoring your application's performance.

5. Transformation of requests and responses.


```

##### What is authguard /routeGuard / guards
// or 
##### How to protect the routes?

```
Auth Guards is a technique used to protect our routes based on user authentication status.

It will manage different access levels between authenticated and non-authenticated users.


1. CanActivate:

 It determines if a user is allowed to navigate a particular route and returns a Boolean value (true or false) or an observable/promise that resolves to a Boolean.

 If the returned value is true, the route is activated; if it’s false, the route is blocked,



2.CanActivateChild:

same as CanActivate
specifically used to protect child routes of a particular route.


3. CanDeactivate:

allows us to control whether a user is allowed to leave a particular route

use case:

prompt the user for confirmation when navigating away from a route that may have unsaved changes or to perform other checks before allowing the user to leave.


4. CanLoad:

used when you want to prevent the lazy-loaded modules from being loaded for users who are not authenticated.

It checks if the user can load the module asynchronously or not.


5. Resolve:

This guard is used to resolve data for a route before it is activated. It can be used to fetch data from a backend API and make it available to a component.

```
---

##### what is single sign on? sso?


- Single sign-on is an authentication method where a user can log in with one set of username and password across multiple applications. There can be a single point of authentication via any Identity Access Manager (IAM) of your choice.

- Google, Facebook, LinkedIn are some of the most popular SSO services available, and they allow users to register and login in no time.

- For implementing single sign-on for Angular applications we can use AWS Cognito and Amplify.

---

##### Localstorage, SessionStorage, Cookie

Localstorage: 5 mb
session storage: 5mb
coockies: 4 kb (4096 bytes) per coockie

| Sr.no | Local Storage | Session Storage | Cookies | 
| ----- | ----- | ----- | ----- |
| 1 | capacity:  5MB/10MB | capacity:  5MB | capacity: 4KB |
| 2 | it must be deleted via javascript or manually | It’s session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed | Cookies expire based on the setting and working per tab and window |
| 3 | The client  can only read local storage | The client can only read local storage | Both clients and servers (httpOnly Flag true) can read and write the cookies  |
| 4 | There is no transfer of data to the server | There is no transfer of data to the server | Data transfer to the server is exist |
| 5 | No Auto-expire | Auto-expired | Auto-expired |
---


##### What is Tree-Shaking?

- Tree-shaking, also known as dead code elimination, is a technique used to eliminate unused or “dead” code from your JavaScript bundle during the build process. 

- This process is crucial for reducing the size of your application’s JavaScript files, leading to faster load times and improved overall performance.

- Tree-shaking helps to removing unused code, resulting in smaller bundle sizes. Smaller bundles mean faster loading times, which can significantly enhance your application’s performance. Additionally, smaller bundles are beneficial for mobile users with limited bandwidth and slower devices.

**How Tree-Shaking Works in Angular?**

1. Dependency Injection: 

   Angular encounters a service that is not used anywhere in your application, it can safely remove the associated code during the build process.
<br>

2. Module Optimization: 

   During tree-shaking, Angular can analyze the module dependency graph to identify modules that are not used in your application and the associated code is removed from the bundle
<br>

3. AOT Compilation:

   AOT compilation enables more aggressive tree-shaking because it performs the analysis and elimination of dead code at compile-time.

   Enabling AOT compilation in your Angular application is a fundamental step towards achieving effective tree-shaking.

---

##### Model, class and interface in angular:

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


##### Angular Cold and Hot Observable:

When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable


**Cold Observables:**

- An Observable “cold” when the data is produced inside the Observable.Observables are lazy, it means they only execute values when something subscribes to it. For each subscriber the Observable starts a new execution, resulting in the fact that the data is not shared. 
<br>
- If your Observable produces a lot of different values it can happen that two Observables that subscribe at more or less the same receive two different values. We call this behaviour “unicasting”. To demonstrate this:

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


**Hot Observables:**

- Observable is hot when the data is produced outside the Observable. As we just saw the hot Observable is able to share data between multiple subscribers. We call this behaviour “multicasting”.
<br>
- Let’s say we’re tracking clicking behaviour and have multiple subscribers do something with the coordinates:

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

**Which one better than the other?**

Well, that depends on the usecase. A cold Observable is usually fine, unless:

1. You want to make sure multiple subscribers get the same data.

2. Your creating a new instance of something on each Observable execution, let’s say a websocket connection. You don’t want to create a new connection for each subscriber, but instead just share it to all the subscribers. Moving the instantiation of the connection outside the Observable will make it hot and fixes this.

---

##### What are the best practices for handling user authentication and authorization in web applications, including techniques like OAuth and JWT?

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

---


##### How to determine the dependencies will be provided to our classes

***4 different ways of creating dependencies: useValue, useFactory, useClass and useExisting***

**1. useValue:**

- Lets you inject a value or a function.
- Often used to set the initial configuration.

```js
   export const RACE_CARS_CONFIG: CARS_CONFIG= {
      domain: 'api.race-cars.com',
   };
   
   providers: [CarsService,
   { provide: CARS_CONFIG, useValue: RACE_CARS_CONFIG}
   ]

```
<br>

**2. useClass:**

- Returns another class, specified by "useClass" when component asks for class specified in "provide".

- It is useful, for example, when unit testing components. We don't have to provide the full service then, but we can create a separate class that will be able to implement the methods in a different way. 

- So we will only test the component itself and not its interaction with the service.

```js
providers: [{ provide: UserService, useClass: mockUserService}]
```

In case the provide and useClass values are the same

```js
providers: [{ provide: UserService, useClass: UserService}]
```
we can use a shorter write

```js
providers: [UserService]
```
<br>

**3. useExisting:**

- Creates two ways to access the same service object with two different tokens.

- It works well, e.g. when we have many methods in the service, and we only want to use a few of them. This helps in reducing the size of the interface.

```js
// Sample service:

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

// Reduced implementation:

export abstract class CarSizeService {
  abstract getHeight: number;
  abstract getWidth: number;
}
Providers array:

providers: [{ provide: CarSizeService, useExisting: CarService}]

```
<br>

**4. useFactory:**


- Specifies the function that is called and injects its return value.

- It is useful when we want to get some value from the information that is not available before the run application, e.g. load some data from another page.
If it has dependencies, put them in the "deps" array.

- It may include a "multi" property that allows multiple providers spread across many files to provide configuration information to a common token.

```js
// Function implementation:

function configUrlFactory (configUrl: ConfigUrlService) { 
   return () => configUrl.load(); 
   }

// Providers array:

providers: [{
  provide: APP_INIT,
  useFactory: configUrlFactory,
  deps: [ConfigUrlService],
  multi: true
}]

// Example service:

@Injectable() export class ConfigUrlService{
constructor(private http: HttpClient){}
  load(): Promise<any> {
    return http.get('https://exampleConfigUrl.com').toPromise();
  }
}

```

---
