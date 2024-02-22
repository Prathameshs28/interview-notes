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
