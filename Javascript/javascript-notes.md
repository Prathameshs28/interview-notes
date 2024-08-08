# Javascript Notes:


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


function resolveAfterTwoSec(){
    return new Promise((resolve)=>{
        setTimeout(()=>{
            resolve('resolved')
        },2000);
    })
}

async function asyncCall(){
    console.log('calling');
    const result = await resolveAfterTwoSec();
    console.log(result);
}


// -------------------------------

console.log(foo());

var foo = function(){
    return 9;
}

// -------------------------------


 const add = {
    city:"Delhi",
    street: "abc"
 }

 console.log(add.pincode)


// -------------------------------



humanize('contact_details_are_not_found')


function humanize(str){
  
  let st = str.split('_');
  let tempStr = '';
 st.map((x)=> x.charAt(0).toUpperCase()+x.substr(1)).forEach((val)=> tempStr+= val + ' ');
 console.log(tempStr)
  
}


// -------------------------------


// console.log(num)

var num = 8;
var num = 10;

console.log(num)



// -------------------------------


what is _ _ prototype
pollyfills
Weakmap is es6

how to create global variable in js

How to call function which is in IIFE?

on call on some condition

flatMap use

JS modules


// -------------------------------

console.log('1...');

for(var i=0;i<2;i++){
    setTimeout(console.log(i),100);
}

console.log('2...');

// -----------------

{
    var a = 10;
    console.log(a);
}

var a = 20;
console.log(a);

// -----------------


function abc(){
    {
      var a = 10;
      console.log(a)
    }
    
    {
      let a = 200;
      console.log(a)
    }
    
    console.log(a)
  }
  
  abc();

// -----------------


function foo(a,b){
    console.log(arguments[1]);
}

foo(3)



// custome directive for change background color 
// of cell basis on age condition



const compose = (f,g) => (x) => f(g(x));

const g = (num) => num + 1;
const f = (num) => num * 2;

const h = compose(f,g);

console.log(h(20));


//  ----------------
// js visualizer https://www.jsv9000.app/


console.log(1)

setTimeout(()=> console.log(2),0)
Promise.resolve().then(()=>console.log(3));
setTimeout(()=> console.log(4),1);

console.log(5)


1 
5
3
2
4


//  ----------------





/*

Array:

1. Reverse an Array
2. Find the maximum Element
3. Remove duplicates
4. Array sumRotate an Array
5. Merge two sorted arrays
6. Array intersection
7. Subarray with given sum
8. Two sum
9. Move Zeros to the end

Objects:

1. write a function to extract keys and
values from an object and return them as separate arrays

2. Implement a function to deeply compare two objects 
and determine if they are equal 

3. write a function to transform an object by adding a prefix to all its keys

4. implement a function to filter an object based on a given condition

5. write a function to flatten a nested object into single-level object

6. Implement a funciton to merge two objects, with second 
object's values precendence in case of key conflicts

7. Write a function to convert an objects into a JSON string

8. Implement a function to create a deep copy of object

9. Write a funciton to check if a specific key exists in an object

10. write a function to convert an array of objects into 
an object, using a specified property as 
the key.

*/




/* 


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


*/



/* 

myFun();

var myFun = function(){
    console.log("First");
}

myFun();

function myFun(){
    console.log('Second');
}

myFun(); 

OP:

Second
First
First

*/




/* var variable = 10;
(()=>{
    console.log(variable);

     variable = 20;
    
    console.log(variable)

})();

console.log(variable);

var variable = 30;


OP:

10 
20
20

if in function there is somthing 

var variable = 20;

then we get op as

undefined 
20
10

*/


/*
 variable = 10;

(()=>{
    foo = 100;
    console.log(variable);
    var foo = 100;
    variable = 20;
  
    console.log(variable);
})();

console.log(foo);
console.log(variable);
var variable = 30;

op:

10
20
error foo not defined

 */



/* 

console.log(a)
console.log(b)
var a = b = 5; 

*/


/* 

console.log(1 < 2 < 3) // true
console.log(3 > 2 > 1) // false 

*/



/* 

const foo = ()=> {
    console.log(this.age);
}

foo.call({age:'john'})

*/



/* const foo = function(){
    console.log(this.age);

    const bar = ()=>{
        console.log(this.age)
    }
    bar()
}

foo.call({age:'john'}) */



// make id only freeze not others

/* let obj = {
    id:1,
    name:'ram'
  }
  
  Object.freeze(obj);
  
  obj.id = 100;
  obj.name = 'abcd';
  
  console.log(obj)



  Answer:

  let obj = {
    id:1,
    name:'ram',
    age:20
  }
  
  // Object.freeze(obj);
  

  // for single property

  Object.defineProperty(obj,'id',{
    writable:false
  })

  // for multiple
  Object.defineProperties(obj,{
   id: {
    writable:false
  },
  age:{
    writable:false
  }
  })
  
  obj.id = 100;
  obj.name = 'abcd';
  obj.age = 300;
  
  console.log(obj) */

  

/* 

if we give these properites then 

backdrop-filter: blur(4px);

transform
perspective
click path property


position:fixed element will be related to its parent
it will not be related to viewport

*/ 



/* 

defer 
async  attribute for load script file



replaced inline elements
non replaced inline elements

images are inline then how we 
can give width and height to it?


for replaced inline elements 
are comes from external source 
so we can give height and width

e.g <img>


non replaced inline elements
are by default inline so we can't 
give height and width

e.g span, a, b, i 


inline elements don't follow
box model

 */




/* class A{
  constructor(){
    this.foo = 30;
  }

  bar(){
    console.log(this.foo)
  }
}

let obj = new A();

console.log(typeof A)
 */



/* 
function fn(){
  this.foo = 10;
}

fn.prototype.bar = function(){
  console.log(this.foo)
}

let obj = new fn();
console.log(obj.foo)
obj.bar()
 */


/* let resPromise;
let rejPromise;
const p = new Promise((resolve,reject)=>{
  resPromise = resolve;
});


function check(){
  console.log(p)
}

function resolvePromise(){
  
  if(resPromise){
    resPromise();
  }

  p.then(()=>{
    console.log('promise resolved')
  }).catch((err)=>console.log('err'));
}
 */


{/* <button onclick="check()">Check</button> */}
{/* <button id="btn" >Click</button> */}

/* let resPromise;
let rejPromise;
const p = new Promise((resolve,reject)=>{
  document.getElementById('btn').addEventListener('click',()=>{
    resolve();
  })
});

p.then(()=>{
  console.log('promise resolved')
}).catch((err)=>console.log('err'));


function check(){
  console.log(p)
} */

//  javascript file module
//  type = "module"

 


/* var a1 = 10;
{
  var a2 = 20;
}

function fn(){
  var a3 = 100;
}

fn();

if(true){
  var a4 = 200;
}
 */


/* 
<span>
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Obcaecati, laudantium dolorum soluta ullam repudiandae, eaque magnam corrupti esse illo, atque aut. Necessitatibus, animi obcaecati cum mollitia 
</span>
<button onclick="check()">Check</button>
<button id="btn" >Click</button>

<script src="./app.js" type="module"></script> */
