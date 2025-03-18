
# Javascript: 


1. **block scope:**

```js
{
const a=5; // or let a = 5;
}
console.log(a);

```
**#Output:**

```
ReferenceError: a is not defined

Note:use var for avoid error (var is hoisted)

```

---

2. **shadowing:**

```js

 function test(){
        const a = "Hello";   // or let a = "Hello";
        if(true){
            const a = "hi";
            console.log(a);   //or use let a = "hi";
        }
        console.log(a)
    }
    
    test();

```

**#Output:**

```
hi
Hello

```
---

3. **shadowing with let to var:**


```js
  function test(){
        var a = "Hello";   
        let b = "Bye";
        if(true){
            let a = "hi";
            var b= "Goodbye"  // error already taken
            console.log(a);
            console.log(b);
        }
    }

 test();
```

**#Output:**

```
Uncaught SyntaxError: Identifier 'b' has already been declared 

```
--- 


4. **shadowing with var:**
   
```js
  function test(){
         var a=10;
         var a=20;          
         console.log(a)
    }

 test();
```

**#Output:**

```
20

```

---


5. **map:**
   
```js

 let arr = [1,2,3,4];
    
    let newArr = arr.map((num,i,arr) =>{
        return num * 10;
    
    })
    
    console.log(newArr);

```

**#Output:**

```
[10,20,30,40]

```

**PolyFill for map:**
```js
    Array.prototype.myMap = function(cb){
        let temp = [];
        for(let i=0;i<this.length;i++){
            temp.push(cb(this.[i],i,this));
        }
        return temp;
    }
```
---


6. **filter:**
   
```js

let arr = [1,2,3,4];
    
    let newArr = arr.filter((num) =>{
        return num%2==0;    
    })
    
    console.log(newArr) 

```

**#Output:**

```
 [2, 4]

```

**PolyFill for Filter:**
```js
 
     Array.prototype.myFilter = function(cb){
        let temp = [];
        for(let i=0;i<this.length;i++){
           if(cb(this[i],i,this))  temp.push(this[i]);
        }
        return temp;
    }

```
---


7. **reduce:**
   
```js

let arr = [1,2,3,4];
    
    let newArr = arr.reduce((acc,next,i,arr) => {
       return acc + next; 
    },0)
    
    console.log(newArr)

```

**#Output:**

```
 10

```

**PolyFill for Reduce:**
```js
 
    Array.prototype.myReduce = function(cb,initialValue){       
        var accumulator = initialValue;
        for(let i=0;i<this.length;i++){
          accumulator = accumulator ? cb(accumulator,this[i],i,this) :
          this[i];
        }
        return accumulator;
    }

```
---

 **example-1**
```js
const arr = [2,5,9,11,44];

const mapResult = arr.map((ar)=>{
    return ar + 2;
})

console.log(mapResult);
```

**#Output:**

```
[4, 7, 11, 13, 46]

```

```js
const arr = [2,5,9,11,44];
const forEachResult = arr.forEach((ar,i)=>{
    arr[i] = ar + 3;
})

console.log(forEachResult);
```

**#Output:**

```
undefined

```

---

**example-2**

Question: return total marks for students with marks greater than 60 after 20 marks have been
added to those who scored less than 60


```js
let students = [    
 {name:'abcd',rollNo:23,marks:90},
 {name:'xyz',rollNo:33,marks:70},
 {name:'pqr',rollNo:43,marks:30},
 {name:'lmn',rollNo:53,marks:63},
 {name:'mno',rollNo:63,marks:50}, 
]

const data = students.map((stu)=>{
        if(stu.marks < 60){
            stu.marks += 20;
        }
        return stu;
    }).filter((stu) => stu.marks > 60)
    .reduce((pre,stu) =>{
        return pre + stu.marks 
    },0)
    
  console.log(data)
```

**#Output:**

```
293

```
---

8. **First Class Function:**
  

```js
    function square(num){
        return num * num;
    }


    function displaySquare(fn){
        
        console.log("Square is: "+ fn(5));
    }
    
    displaySquare(square);

```

**#Output:**

```
Square is: 25

```
---

9. **IIFE:**

   IIFE (Immediatly Invoked Function Expression)

  ```js
        ((num)=>{
            console.log(num * num);        
        })(5);
  ``` 

**#Output:**

```
25

```

```js

((num)=>{
  return (function(y){
     console.log(num);   
    })(10);
 })(5);

```

**#Output:**

```
5 

```

---

10. **What will be the output:**

```js
 for(var i=0;i<5;i++){
      setTimeout(() =>{
          console.log(i);
      },i*1000)
    }
```

**#Output:**

```
5 5 5 5 5

Note: instead of var if let used then output will be 0 1 2 3 4  
```

---

**Parameters   & Arguments:**

```js
    function fun(x,y){ // parameters
        console.log(x*y);
    }
    
    fun(5,10)  // arguments 
```

**#Output:**

```
50

```

---

**Rest and Spread Operator:**

```js

function fun(...nums){ // rest opeator
        console.log(nums);
    }
    
    let arr = [5,10];
    
    fun(...arr)    // spread operator

```

**#Output:**

```
[5, 10]

```
   
---    

**callback function:**

```js

     function printOp(op){
        console.log(op);
    }
    
    function takeIp(fn){
        let greet = 'Hi Good Morning!!!';
        fn(greet);
    }
    
    takeIp(printOp);

```

**#Output:**
```
Hi Good Morning!!!

```

---


**Arrow Function:**

```js

  function fun(){   // with normal function we can check arguments also
      console.log(arguments); // use arguments its inbuild keyword
  }
  
  fun(1,2,3,4,5)

```

**#Output:**

```
[1, 2, 3, 4, 5]

```

```js
  fun = () =>  console.log(arguments); // using arrow function
  
  fun(1,2,3,4,5)  // error arguments is not defined

```

**#Output:**

```
error arguments is not defined

```

---

**this keyword:**


```js
    let user = {
        userName:"Admin",
        arrowFun:()=>{
            console.log("User Name: "+this.userName);  // this refers to globaly
        },
        regFun(){
                    console.log("User Name: "+this.userName); // this referes to user object
        }
        
    }
    
    user.arrowFun();
    user.regFun();
```

**#Output:**

```
User Name: undefined
User Name: Admin

```

---


**closures:**

closure scope chain

```js
        function makeFun(){
            var name = "ABCD";
            function display(){
                console.log(name);
                function fun3(num){
                    console.log('this is fun 3, num= ',num);
                }
                return fun3;
            }

            return display;
        }

        makeFun()()(10);

```

**#Output:**

```

ABCD
this is fun 3, num=  10

```

---

```js

    var e = 10;

            function sum(a){
                return function(b){
                    return function(c){
                        return function(d){
                            return a + b + c+d+e;
                        }
                    }
                }
            }

    console.log(sum(20)(30)(40)(50)); 

```

**#Output:**

```
150

```

---

```js
   let count =0;
        (function print(){
            if(count ===0){
                let count =1; // shadowing
                console.log(count); 
            }
            console.log(count);
        })();

```

```
1
0

```

---

**time optimization**

```js
        let a = [];

        function find(){
            for(let i=0;i<1000000;i++){
                a[i] = i * i;
            }

            return function(index){
        
              console.log(a[index]);
            }
        }

  const closure = find();
  
  console.time("6");
  // find(6);      // without time optimization

  closure(6);       // with time optimization

  console.timeEnd("6");

  console.time("12");
  // find(12);     // without time optimization

  closure(12);     // with time optimization

  console.timeEnd("12");

```


```
with time optimization: 

36
6: 0.158935546875 ms
144
12: 0.052001953125 ms

---

without time optimization

36
6: 0.18408203125 ms
144
12: 0.080810546875 ms


```


---


```js
      for(var i=0;i<3;i++){
        setTimeout(function log(){
          console.log(i);   // if var : 3 3 3 
        },1000);            // if let : 0 1 2
       }

```

---


**print 0 1 2 without using let use var only**

**Problem Statement:**

```js

for (var i = 0; i < 3; i++) {
          setTimeout(() => {
            console.log(i);
          }, 1000);
      }
```

**Solution:**

```js
  for (var i = 0; i < 3; i++) {
        function inner(i) {
          setTimeout(() => {
            console.log(i);
          }, 1000);
        }
        inner(i);
      }

```

**#Output**

```
0 1 2
```

---

**How would you use a closure to create a private counter?**

```js
 function counter(){
        var _counter = 0;

        function add(increment){
          _counter += increment;
        }

        function getCounter(){
          return "Counter: "+ _counter;
        }

        return {
          add,
          getCounter
        }
       }

       const cnt= counter();

       cnt.add(10);
       cnt.add(20);
       console.log(cnt.getCounter());

```

---

**What is Module Pattern in js?**

```js
      var Module = (function(){
          function privateMethod(){
            console.log("Private");
          }

          return{
            publicMethod:function(){
              console.log('public');
              privateMethod();  // error
            }
          }
      })();

      Module.publicMethod();
      Module.privateMethod(); // cant access directly

```
**#Output**

```
public
Private
Uncaught TypeError: Module.privateMethod is not a function

```

---

**Make this run only once**

```js
      let view;
      function fun(){
          let cnt =0;
         return function one(){
          if(cnt === 0){
            view = "World!!!";
              console.log("Hello "+view);
              cnt++;
          }  
        } 
      }

    let one =fun();
    one();
    one();
    one();

```

**#Output**

```
Hello World!!!
```

---

**Once Polyfill**

```js

  function once(func,context){
          let ran;

          return function(){
            if(func){
              ran = func.apply(context || this, arguments);
              func = null;
            }

            return ran;
          }
        }

    const hello = once(() => console.log("hello"));
    
    hello();
    hello();
    hello();
    hello();

```

**#Output**

```
hello
```

---

**Implement Caching/Memoize Function**

```js

         function myMemoize(fn,context){
            const res = {};
            return function(...args){
              var argsChache = JSON.stringify(args);
              
              if(!res[argsChache]){
                res[argsChache] = fn.call(context || this, ...args);
              }
              return res[argsChache];
            };

         }

         const fun = (num1,num2) =>{
          for(let i=0;i<= 10000000;i++){

          }

          return num1 * num2;
         }
     
         const memoizedFun = myMemoize(fun);



         console.time("First call");
          console.log(memoizedFun(1000,2000));
          // console.log(fun(1000,2000));

         console.timeEnd("First call")

         console.time("Second call");
          console.log(memoizedFun(4000,9000));

          // console.log(fun(1000,2000));
          console.timeEnd("Second call");

```


**#Output:**

```
memoizedFun function call: 

2000000
First call: 12.7890625 ms
36000000
Second call: 8.85693359375 ms

---

fun function call: 

2000000
First call: 17.594970703125 ms
36000000
Second call: 9.3291015625 ms

```
---

**Difference between closure and scope**

**Currying:**

```js
    function fun(num1){
      return (num2)=>{
         console.log(num1 * num2)
        }
      }

      fun(5)(10);

```
**#Output:**

```
50
```

```js
      function fun(type){
 
        return (no1)=>{
          return (no2)=>{
     
              if(type){
                if(type === "sum"){
                  return no1 + no2;
                }else if(type === "sub"){
                  return no1 - no2;
                }else if(type === "mult"){
                  return no1 * no2;
                }else if(type === "div"){
                  return no1/no2;
                }else{
                  return "Not correct type";
                }
              }     
                     
          }
        }
      }

 
    //  console.log( fun("mult")(10)(2)); // 20

        const mul = fun("mult");
        console.log(mul(10)(20));
        console.log(mul(30)(20));
```

**#Output:**

```
200
600
```

---

**Infinite Currying:**

```js
      function add(a){
          return (b)=>{
            if(b) return add(a+b);
            return a;
          }
        }
      
       
      console.log(add(5)(2)(7)(8)(18)(10)(20)());

```

**#Output:**

```
70
``` 

---

**Currying VS Partial Application:**
  
**Manipulating DOM (use Currying):**

```html
<html>
<body>
 <h1 id="heading">Hello</h1>

    <script>
      function updateElementText(id){
        return function(content){
          document.querySelector("#" + id).textContent = content;
        }
      }
      
      const updateHeader = updateElementText("heading");
      updateHeader("Hi, Good Morning!!!");
    </script>

</body>
</html>
```

---


**Curry() implementation:**

 Converts f(a,b,c) into f(a)(b)(c)

```js
      function curry(func){
        return function curriedFunc(...args){
            if(args.length >= func.length){
              return func(...args);
            }else{
              return function(...next){
                return curriedFunc(...args,...next);
              }
            }

        }
      }

      const sum = (a,b,c,d) => a + b + c + d;
      const totalSum = curry(sum);

      console.log(totalSum(1)(5)(6)(7))

```

**#Output:**

```
19
```

---

**Objects in Javascript:**

```js

  const user = {
    name:"Abcd",
    age:29
  }

  user.name = "Ram";

//  delete user.age // {name: 'Ram'}

  console.log(user)

```
**#Output:**

```
{name: 'Ram', age: 29}
```

---

```js
 const fun = (function (a){
          delete a; // delete only object property not local variable
          return a;
      })(10);
 
      console.log(fun);
```

**#Output:**

```
10
```
---

```js
      const porperty = "firstName";
      const name = "RAM TM"; 
      
      const user ={
        [porperty]:name
      }

      console.log(user.firstName);

```

**#Output:**

```
RAM TM
```

---

```js
   const user ={
      name:'ABCD',
      age:20,
      sal:20000,
      status:'single'
     }

     for(key in user){
        console.log(key+" : "+user[key]);
     }
```

**#Output:**

```
name : ABCD
age : 20
sal : 20000
status : single
```

---

**Check length of object:**

```js
 const user ={
      name:'ABCD',
      age:20,
      sal:20000,
      status:'single'
     }

let len = Object.keys(user).length;
console.log(len)
```
**#Output:**

```
4
```

---

```js
const a = {};

const b = {key:"b"};
const c = {key:"c"};

a[b] = 123;   // a["[object Object]"]  means "[object Object]" = 123

a[c] = 456;  // a["[object Object]"] (overlap to) "[object Object]" = 456 


console.log(a[b]);

```

**#Output:**

```
456
```

---

```js
console.log([..."abcdefghijklm"]);   //  it spread values and create an array
```

**#Output:**

```
['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm']
```

---

```js

  let obj = {
          name:'abcd',
          age:30,
          no:101010101,
          address:'pune'
        }
        
        let admin = {
          ...obj,
          admin:true,
        }

        console.log(admin)

```

**#Output:**

```
{name: 'abcd', age: 30, no: 101010101, address: 'pune', admin: true}
```

---

```js
      const user ={
        name:'abcd',
        age:20,
        sal:30000
      }

      const data = JSON.stringify(user,["age","sal"]);

      console.log(data); // only age and sal will be strinify

```
 
**#Output:**

```
{"age":20,"sal":30000}   
```
     
---


```js
   const shape = {
        radius:10,
        diameter(){
          return this.radius * 2; // reference to shape object
        },
        perimeter: ()=>  2 * Math.PI * this.radius // arrow fun refer to window object

      }

      console.log(shape.diameter());
      console.log(shape.perimeter())

```

**#Output:**

```
 20
 NaN 
```

---

**what is destructuring in objects ?**

```js
      let user = {
        name:'ABCD',
        age:24,
        address:{
          street:'xyz road',
          city:'pune',
          pin:202020
        }
      };

      // const name = "XYZ" // if any other name is there
      // const {name:myName} = user;
      // console.log(myName);

      const { address: {city}} = user

      console.log(city)

```

**#Output:**

```
pune
```
---

```js
  // function getItems(fruitList,...args,favFruit){   // error code line
      function getItems(fruitList,favFruit, ...args){ // ...args is the rest parameter must be last as parameter
        return [...fruitList,...args,favFruit];  // this ...args is spread operator
      }

     console.log( getItems(["banana","apple"],"pear","orange"));

```

**#Output:**

```
['banana', 'apple', 'orange', 'pear']
```

---

**Object reference**

```js

  let c = {geeting:"hi"};
  let d;
  d = c;

  c.geeting = "hello";
  console.log(d.geeting);

```

**#Output:**
```
hello
```

---------------------------------------------------------------
  
```js

console.log({a:1} == {a:1});  
console.log({a:1} === {a:1});

```

**#Output:**
```
false
false
```

---

```js
 let person = {name:"ram"};
 const members = [person];
 person= null;
      
 console.log(members) // array with 0th position person obj

```

**#Output:**
```
[name:"ram"]
```

---

```js

let person = {name:"ram"};
const members = [person];

person.name = null;

console.log(members);

```

**#Output:**
```
[name:null]
```

---

```js

  const value = {number:10};

  const multiply = (x = {...value}) => {  // ...value --> its clone of object value
    console.log(x.number *= 2);
  }

  multiply();  
  multiply(); 
  multiply(value); // passing actual obj ref and it will copied into x and then it 
                   // will change value of x = 10 to x =20 
  multiply(value);

```

**#Output:**
```
20
20
20
40
```

---   

```js

   function fun(obj1){
        obj1.age = 25;

        obj1 = {
          name:'John',
          age:50
        }

        return obj1;

      }

      const obj1 = {
        name:'Alex',
        age:30
      }

      const obj2= fun(obj1);

      console.log(obj1); 
      console.log(obj2); 
```

**#Output:**
```
{name: 'Alex', age: 25}
{name: 'John', age: 50}
```

---

**What's shallow Copy and Deep Copy?**

**shallow Copy : one object hold the reference of another object**

```js
      let obj = {
        name:'ram',
        age:20
      }

      newObj = obj;      
      newObj.age = 50;     
      console.log("Old Obj: "+ obj.age +"\nNew Obj: "+ newObj.age);

```

**#Output:**
```
Old Obj: 50
New Obj: 50
```

---


**Deep Copy: one obj cloned with another obj variable**
    
```js

  let obj = {
    name:'ram',
    age:20
  }

  let newObj = {...obj};  // (destructuring) copy obj to newObj & not ref

  // let newObj = Object.assign({},obj); // 2nd way copy object
  
  // let newObj = JSON.parse(JSON.stringify(obj)); // 3rd way copy object
  
  newObj.age = 55;
  
  console.log(newObj.age);    // 55   
  console.log(obj.age);  // 20


```

**#Output:**
```
55
20

Note: If you are sure your deeply nested data only includes strings, numbers, boolean and null, then you can use json parse and stringify but if there is nested object then destructuring & Object.assing will not work. 

JSON.stringify works but there are some limitations

1. Any internal getters and setters will be lost.
2. Destruction of date objects. (Dates will be parsed as Strings, not as Dates)
3. Class prototypes will be lost. 

For deep cloning use lodash library or (2023 update) Use the structuredClone() or
you can write your own deep cloning function using recursion
```

---

**This keyword**

```
implicit binding & explicit binding

implicit binding usually this keyword use with . operator

explicit binding includes call, bind, apply 


a = 10;   // for var and only a show op but let & const not shows
console.log(this.a) // output- 10 

```

---

```js
      a = 10;

     function fun(){
      console.log(this.a); // var a and only a works but 
     }                     // let and const (op: undefined) not works because its not global

     fun();

```

**#Output:**
```
10
```

---


```js

 this.a = 5;

 const fun = () =>{
   console.log(this.a);
 }

  fun();  
```

**#Output:**
```
5
```

---

 **this with normal function VS arrow Function:**


  *** using  normal function ***

```js

    let data  = {
      name:"abcd",
      age: 30,
      getData(){
        console.log(this.name);
      }
    }

  data.getData();
    
```

**#Output:**
```
abcd
```


```js
    let data  = {
      name:"abcd",
      age: 30,
      childObj:{
        newName: "ram",
        getData(){
          console.log("Child: ",this.newName,"\nParent: ",this.name);
        }

      }


    }

   data.childObj.getData();
 

```

**#Output:**
```
Child:  ram 
Parent:  undefined
```

---


**using  arrow function**

```js

 let data  = {
      name:"abcd",
      age: 30,
      getData: ()=> {
          console.log(this) // undefined its pointing to window obj
          // arrow function take reference from its parent function
          // and parent function must be normal function ow its refer to window      
        }
    }

    data.getData();

```

**#Output:**
```
{window: Window, self: Window, document: document}.... (window object print)
```

```js

    let data  = {
      name:"abcd",
      age: 30,
      getData(){
          const nestedArrow = () => {
            console.log(this.name);
          }     
          nestedArrow(); 
        }
      }

    data.getData(); 
```

**#Output:**
```
abcd
```
---

**Class in JS**

```js

      class user {
          constructor(n){
            this.name = n;
          }  
        
          getName(){
              console.log(this.name)
          }
     
      }

      let obj = new user('ram');
      obj.getName();

```

**#Output:**
```
ram
```
---

```js
  const user = {
      firstName:'ram',
      getName(){
        const firstName = "Virat";
        return this.firstName;
      }
    }

    console.log(user.getName()); 

```

**#Output:**
```
ram
```
---

```js
      function makeUser(){
        return {
          name:'Ram',
          ref:this,          
        }
      }

      let user = makeUser(); // pointing to parent obj which is window obj
      console.log(user.ref.name);
      console.log(user.ref);

```

**#Output:**
```
nothing will be print
{window: Window, self: Window, document: document}.... (window object print)
```


 
 **for fix above problem:**

```js

  function makeUser(){
        return {
          name:'Ram',
         ref(){
          return this;
         }          
        }
      }

 let user = makeUser(); 

 console.log(user.ref().name);

```

**#Output:**
```
ram
```

---

```js

  const user = {
      name:"ram",
      logMsg(){
        console.log(this.name); 
      }
     }

// setTimeout(user.logMsg,1000); // prints undefine or nothing
 
setTimeout(()=>{  // to solve problem call method in func
  user.logMsg();
},1000);

```

**#Output:**
```
nothing will be print
ram
```

---

```js

     const user = {
        name:"ram",
        greet(){
          return `Hello ${this.name}`
        },

        farewell:()=>{
          return `Goodbye, ${this.name}`
        }        
      }

      console.log(user.greet());
      console.log(user.farewell());  // to solve problem make farewell normal 
                                     // function or put in normal function
```

**#Output:**
```
Hello ram
index.html:25 Goodbye, 
```

---

```js
   let calculator = {
            read(){
              this.a = +prompt("a = ",0);
              this.b = +prompt("b = ",0);              
            },
            sum(){
              return this.a + this.b; 
            },
            mul(){
              return this.a * this.b;
            }
        }

        calculator.read();
        console.log(calculator.sum());
        console.log(calculator.mul());

// work without this also throughout program
```

---

```js

        var length = 4;

        function callback(){
          console.log(this.length);
        }

        const object = {
          length:5,
          method(fn){
            fn();
          }
        }

        object.method(callback);
        
```

**#Output:**
```
4
```

---

```js
    var length = 4;

        function callback(){
          console.log(this.length); // length of array 3
        }

        const object = {
          length:5,
          method(){        // arguments = [callback,2,3]
            arguments[0]();
          }
        }

        object.method(callback,2,3);
```

**#Output:**
```
3
```

---


```js
   let calc = {
        total: 0,
        add(no){
          this.total += no;
          return this;
        },
        mult(no){
          this.total *= no;
          return this;
        },
        sub(no){
          this.total -= no;
          return this;
        }            
      }
      
      const result = calc.add(10).mult(5).sub(30).add(10);
      console.log(result.total);
```

**#Output:**
```
30
```

---
---


**Explicit binding (call,apply,bind)**

**1.call:**

```
Call is a function that helps you change the context of the invoking function. In layperson's terms, it helps you replace the value of this inside a function with whatever value you want.

```

```js

      var obj = {name:'ABCD'};

        function sayHello(){
          return "Hi" + this.name;
        }

        console.log(sayHello()); 

```

**#Output:**
```
Hi
```

```js

    var obj = {name:'ABCD'};

        function sayHello(age,add){
          return "Hi, My name is " + this.name  + " I am " + age + " old"
        }

        console.log(sayHello.call(obj,30,'pune'));

```

**#Output:**
```
Hi, My name is ABCD I am 30 old
```

---

**2.apply:**

```
Apply is very similar to the call function. The only difference is that in apply you can pass an array as an argument list.

```

```js

      var obj = {name:'ABCD'};

        function sayHello(age,add){
          return "Hi, My name is " + this.name  + " I am " + age + " old"
        }

      //  console.log(sayHello.apply(obj,new Array(30,'pune'))); // or
      
       console.log(sayHello.apply(obj,[30,'pune']));


```

**#Output:**
```
Hi, My name is ABCD I am 30 old
```

---

**3.bind:**

```
Bind is a function that helps you create another function that you can execute later with the new context of this that is provided.

The bind function creates a copy of a function with a new value to the this present inside the calling function.

```

```js
    var obj = {name:'ABCD'};

        function sayHello(age){
          return "Hi, My name is " + this.name  + " I am " + age + " old"
        }

        const bindFun = sayHello.bind(obj);
        console.log(bindFun(30));
```

**#Output:**
```
Hi, My name is ABCD I am 30 old
```

---

**#Find the op**
1. 

```js
  const person = {name:'ram'};

    function fun(age){
      return `name is ${this.name} & age is ${age}`;
    }

    console.log(fun.call(person,23));
    console.log(fun.apply(person,[23]));
    console.log(fun.bind(person,23));
```

**#Output:**

```
name is ram & age is 23
name is ram & age is 23
Function
```

---

2. 
```js

        const age = 10;

        var person = {
          name:"ram",
          age:20,
          getAge:function () {
            return this.age;
          }
        }

        var person2 = {age:24};
       console.log( person.getAge.call(person2));

```

**#Output:**

```
24
```

---

3. 
```js

      var status = 'a';

        setTimeout(()=>{
            const status = 'b';
           const data = {
            status:'c', 
            getStatus(){
                return this.status;
             }
           };

           console.log(data.getStatus()); 
           console.log(data.getStatus.call(this)); 
      },0)  

```

**#Output:**

```
c
a

```

---

4. 

```js
       const animals =[
          {species:"lion",name:"king"},
          {species:"whale",name:"Queen"},
        ]

        function printAnimals(i){
          this.print = function(){
            console.log("#"+i+" "+this.species+": "+this.name);
          };
          this.print();
        }

        for(let i=0;i<animals.length;i++){
          printAnimals.call(animals[i],i);
        }

```

**#Output:**

```
#0 lion: king
#1 whale: Queen
```

---

5. 

```js
  const arr = ["a","b"];
  const ele = [0,1,2];

  arr.push.apply(arr,ele);
  console.log(arr);
```

**#Output:**

```
['a', 'b', 0, 1, 2]
```
     
---

6. 

```js
        const num = [5,9,2,17,1];
        console.log(Math.max.apply(null,num));
        console.log(Math.min.apply(null,num));
```

**#Output:**

```
17
1
```

---

7. 

```js
        function f(){
          console.log(this);
        }

        let user = {
          g: f.bind(null)
        }
       
        user.g(); // pointing to window object
```

**#Output:**

```
{window: Window, self: Window, document: document....}
```

---

8. 

```js
 function f(){
          console.log(this.name);
        }

        f = f.bind({name:"ABCD"}).bind({name:"XYZ"}); 
        
        // bind chaining not working only once it will bind with object

        f();

```

**#Output:**

```
ABCD
```

---

9. 

```js
    
      function checkPassword(success,failed){
        let password = prompt("Password?","");
        if(password == "ABCD") success();
        else failed();
       }

       let user = {
        name:"RAM",
        loginSuccess(){
          console.log(`${this.name} logged in`);
        },
        loginFailed(){
          console.log(`${this.name} failed to log in`);
        }
       }

       checkPassword(user.loginSuccess.bind(user),user.loginFailed(user));
       
```


---

**javascript coding quetion**

**callback method**


 1. how to define a class with properties and methods in js

 ```js
          class car{
            constructor(model,name){
               this.model = model;
               this.name = name;
            }
            
            start(){
               console.log(`car name is ${this.name}`);
            }
         }

         bmw = new car('2016','BMW');

         bmw.start();
```

**#Output:**

```
car name is BMW
```

---

 2. how to implement class inheritance in js?


```js

class Car{
    constructor(model,name){
        this.model = model;
        this.name = name;
    }
    
    start(){
        console.log(`car name is: ${this.name}`);
    }
}

class BMW extends Car{
    dashboard(){
        console.log('child function');
    }
    call(){
        super.start();
        this.dashboard();
    }
}

bmw = new BMW('bmw2016','BMW');

bmw.call();

```

**#Output:**

```
car name is: BMW
child function
```

---

 

6. explain the difference between Object.freeze() vs const ?

```js
// for variable

const month = 'July';

month = 'feb';

console.log(month);  // it will give an error


// for object

let person = {
   name:'abcd'
}

Object.freeze(person);

person.name = 'xzy';

console.log(person.name); 

```
**#Output:**

```
error
abcd

print abcd not xyz, and no shows any error if not using normal functionn strict mode
but in strict mode it will also give an error (cannto assign value to readonly property)  

```

---
