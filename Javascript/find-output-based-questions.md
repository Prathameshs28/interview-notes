
async function asyncDemo(x,y){
   let promise = new Promise((resolve,reject)=>{
       setTimeout(()=>resolve("Output: "+(x+y)),5000);
       setTimeout(()=>resolve("Output: "+(x-y)),3000);
   });
   console.log(x+y);
   let result = await promise;
   console.log(result);
}
asyncDemo(20,15);

---

console.log('a')
setTimeout(()=>{
    console.log("b")
    setTimeout(function() {
        console.log("c")
    }, 1000);
},3000)
console.log("d")
setTimeout(()=>{
    console.log('e')
},0)
setTimeout(()=>{
    console.log('f')
},5000)

---

function a(x){
  var x = 10
 function b(){
    x++
    console.log(x)
    var x = 20
  }
  b()
}
a(5)

---


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

---


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

// console.log(num)

var num = 8;
var num = 10;

console.log(num)

---

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

---

var variable = 10;
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

---



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

---


console.log(a)
console.log(b)
var a = b = 5; 

---

console.log(1 < 2 < 3) // true
console.log(3 > 2 > 1) // false 

---

const foo = ()=> {
    console.log(this.age);
}

foo.call({age:'john'})

---





const foo = function(){
    console.log(this.age);

    const bar = ()=>{
        console.log(this.age)
    }
    bar()
}

foo.call({age:'john'}) 

---


// make id only freeze not others

 let obj = {
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
  
  console.log(obj) 

  ---


class A{
  constructor(){
    this.foo = 30;
  }

  bar(){
    console.log(this.foo)
  }
}

let obj = new A();

console.log(typeof A)

---



function fn(){
  this.foo = 10;
}

fn.prototype.bar = function(){
  console.log(this.foo)
}

let obj = new fn();
console.log(obj.foo)
obj.bar()

---

let resPromise;
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

---

var a1 = 10;
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

---

console.log(foo());

var foo = function(){
    return 9;
}

---

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

---

3 Ways to convert String to Numbers
.
+, Number and parseInt.  these three Number() and Unary Plus(+) works exactly same.

Below are the major differences between Number constructor function and parseInt.
1. Number(x) does type coercion to number, while parseInt(x) does parsing.

2.Number works well with Scientific Numbers
Number("83e4"); // 830000
Number("2e2"); // 200

parseInt('4e3'); // 4

3. Empty, Nullish value handling is different.
Number(""); // 0
Number(false); // 0
Number(null); // 0
Number([]); // 0

Number(true); // 1

parseInt(""); // NaN
parseInt(null); // NaN
parseInt(false); // NaN
parseInt([]); // NaN

parseInt(true); // NaN

parseInt(undefined); // NaN
parseInt({}); // NaN

Number({}); // NaN

4. Number() can’t differentiate different Number System, but parseInt can with radix argument.
parseInt(10,8)// Octal conversion - output 8
parseInt(101,2)// Binary conversion - output 5

Similarity:
They both also ignore whitespace:
const foo = "    6  ";
console.log(parseInt(foo)); // 6
console.log(Number(foo)); // 6
