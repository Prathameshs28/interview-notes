# Angular Machin Test or Coding questions:

1. Suppose you have shown grid in angular template and if you scroll down at 400 user's id and you clicked on user's profile then you will navigate to user's profiles page, when you back from that page you have to scrolled down at that user's id automatically.  


```js

// grid component code:


 gotoChild(index:any){
    this.myService.setIndex(index);
    this.router.navigate(['child']);
  }

 ngAfterViewChecked(){  
    let index = this.myService.getIndex();  
      const gridElement = this.elementRef.nativeElement.querySelector(`#row-${index}`);
      if (gridElement) {
        if (gridElement) {
          gridElement.scrollIntoView({  block: 'center' });
        }
      }
  }



  // service file code: 


    index:any;
  setIndex(value:any){
    this.index = value;
  }

  getIndex(){
    return this.index;
  }

```


2. content projection in angular using <ng-content>


```js

child component:


<p>child works!</p>


<ng-content select="div"></ng-content> // only div content will show not p 

******************************************************************************

Parent component:


<app-child >

    <p>this is msg from parent</p>
    <div>this is div</div>

</app-child>



```

---


3. suppose I've one angular application and one of the component having grid, if I click on any grid the new window will open and after close that window I want to perform event on grid component how we can do this.


```js
@HostListener('document:visibilitychange', ['$event'])
  visibilitychange() {
      if (document.hidden){
            console.log("Page is hidden",document);
      } else {
            console.log("Page is visible",document);
      }
  }

```





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

On click of button focus in input 

<input #inpVariable type="text" class="inp">
<button (click)="setFocus()">Click here</button>


@ViewChild('inpVariable') inpVariable!: ElementRef;
setFocus() {
  this.inpVariable.nativeElement.focus();
}

