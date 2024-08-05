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


