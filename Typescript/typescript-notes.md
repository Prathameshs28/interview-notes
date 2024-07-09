
question:

type vs interface
interface vs class



# Data types in Typescript:



1. Boolean
2. Number
3. String
4. Array 
5. Tuple
6. Enum
7. Unknown
8. Any
9. Void
10. Null and Undefined
11. Never
12. Object


# Type:

type User = {
    name:string;
    age:number;
    contact?:number
}


let user:User = {name:'abcd',age:10};

console.log(user);



OP:
{
  "name": "abcd",
  "age": 10
} 


----



type User = {
    name:string;
    age:number;
}


type Address = {
    line1:string;
    line2:string;
    pincode:number;
}

type Contact = {
    contact:number;
    email:string;
    socialProfile:string
}

type Candidate = User & Address & Contact & {
    isActive:boolean
}



let user:Candidate = {name:'abcd',age:10,
 line1:'x road',
    line2:'y',
    pincode:123,
    contact:9999,
    email:'abcd@g.com',
    socialProfile:'abcd@linkedin.com',
    isActive:true
};

console.log(user);

OP:

 {
  "name": "abcd",
  "age": 10,
  "line1": "x road",
  "line2": "y",
  "pincode": 123,
  "contact": 9999,
  "email": "abcd@g.com",
  "socialProfile": "abcd@linkedin.com",
  "isActive": true
} 


---


# Array:

const list:string[]=[];

const numsList : Array<number> = [];


---

# Union 

let temp : string | number = 10;

temp = "abcd";



e.g with type

type User = {
    id:number;
    name:string;
    type:string;
}

type Seller = {
    id:number;
    name:string;
    type:string;
    isSeller:boolean
}


let user : User | Seller  = {id:1,name:'abcd',type:'buyer'}

user = {
    id:100,
    name:'abcd',
    type:'seller',
    isSeller:true
}


const data : (string | number) [] = ["1","2",3,4];

console.log(typeof data)



let pi:3.14 = 3.14;

let MAX:100 = 100;


let seatAllotment:"aisle" | "middle" | "window";

seatAllotment = "aisle";

seatAllotment = "crew";   // got an error

---

# Tuple:


A tuple is a typed array with a pre-defined length and types for each index.

Tuples are great because they allow each element in the array to be a known type of value.


let user:[string,number,boolean];

user = ['abcd',10,true];

user = [false,'abcd',10]; // got an error


e.g with type

type User =  [number,string];

const newUser:User = [10,'abcd'];


newUser[1] = 'ram';

newUser.push(100);

console.log(newUser)


---

# Enum


enum SeatChoice{
    AISEL,
    MIDDLE,
    WINDOW
}

const hcSeat = SeatChoice.MIDDLE;


<!-- we can do as below to overcome too much js code creation -->

const enum SeatChoice{
    AISEL,
    MIDDLE,
    WINDOW
}


---

# Interface

```

interface User {
   readonly userId:number,
    fname:string,
    lname:string,
    age:number,
    greet?:()=> string,
    getValue?():number,
    getCoupon(name:string,value:number):number
}

const Emp:User = {
    userId:111,
    fname:'abcd',
    lname:'xyz',
    age:21,
    getValue:()=> 112,
    greet:()=> `Hello Good morning`,
    getCoupon(name:'abcd',off:10): => off
    
    }


console.log(Emp.getValue())

```

---

Reopening of interface:

``` 

interface User{
    name:string,
    age:number
}

interface User{     // re-opening of interface
    contact:number
}


const Emp:User = {
    name:'abcd',
    age:22,
    contact:123123
}

```


* Extend interface 

```

interface Admin extends User, Seller{
    role: "admin"
}

```


* Inteface vs Type:


1. We can extend interface using extend keyword

```

interface Bear extends Animal {
  isWild: boolean;
}

```


we can extend a type using intersections ( & )

``` 

type Animal = {
  name: string;
}

type Bear = Animal & { 
  isWild: boolean;

}

```


2. Adding new fields to an existing interface 

```

interface Window {
  title: string;
}

interface Window {
  ts: TypeScriptAPI;
}

```


A type cannot be changed after being created

```

type Window = {
  title: string;
}

type Window = {
  ts: TypeScriptAPI;
}

 // Error: Duplicate identifier 'Window'.

```


# Static keyword

Static class methods are defined on the class itself.

You cannot call a static method on an object, only on an object class.


```
class Car{
    private name!:string;

    constructor(cName:string){
        this.name = cName;
    }

    static getCarName(){
        return this.name;
    }   

}

let carObj = new Car('Tata punch');

console.log(carObj?.getCarName());

// error: Property 'getCarName' does not exist on type 'Car'

```


If you want to use the myCar object inside the static method, you can send it as a parameter:


```

class Car{
    private name!:string;

    constructor(cName:string){
        this.name = cName;
    }

    static getCarName(x:any){
        return x.name;
    }  

}


let carObj = new Car('Tata punch');

let carName = Car.getCarName(carObj);

console.log(carName);

```

---


# Getters and Setters


```

class Car{
    private name!:string;

    constructor(cName:string){
        this.name = cName;
    }

    set cname(name:string){
        this.name = 'Car - ' + name;  
    }

    get cname():string{
        return this.name;
    }
  

}

let carObj = new Car('Tata punch');

carObj.cname = 'ford';

console.log(carObj.cname);


```


# Protected access specifier


```


class Car{
    protected name!:string;

    constructor(cName:string){
        this.name = cName;
    }   
  
}

class Model extends Car{
    
      changeModel(){
       return this.name = 'ford 123 ';
    }
}

let carObj = new Model('Tata punch');

console.log(carObj.changeModel());


```


* Why interface is required:


```

interface TakePhoto{
    cameraMode:string,
    filter:string,
    burst:number,
    postStory:() => string
}

class Instagram implements TakePhoto{
cameraMode!: string;
filter!: string;
burst!: number;

// or we can create in constructor

constructor(cameraMode:string,
    filter:string,
    burst:number){}

    postStory = () => 'Post story';

}

```



# Abstract class

Define an abstract class in Typescript using the abstract keyword. Abstract classes are mainly for inheritance where other classes may derive from them. We cannot create an instance of an abstract class.

The class which implements an abstract class must call super() in the constructor.


```


abstract class TakePhoto{
    constructor(
        public cameraMode:string,
        public filter:string
    ){}

   abstract showPics():void;

   getReelTime():number{
    return 10;
   }
}


class Instagram extends TakePhoto{

    constructor(
        public cameraMode:string,
        public filter:string
    ){
    super(cameraMode,filter);
    }

    showPics(){
        console.log('show all pics');
    }

}

// let takePhotoObj = new TakePhoto("test","test");

// error : Cannot create an instance of an abstract class


let instagramObj = new Instagram("test","test");

let reelTime = instagramObj.getReelTime();

console.log(reelTime);



```


* The abstract class can also include an abstract property, as shown below



```

abstract class Person {
    abstract name: string;

    display(): void{
        console.log(this.name);
    }
}

class Employee extends Person { 
    name: string;
    empCode: number;
    
    constructor(name: string, code: number) { 
        super(); // must call super()
        
        this.empCode = code;
        this.name = name;
    }
}

let emp: Person = new Employee("James", 100);
emp.display(); //James


```

# Generics

need to specifiy function type, parameters and return type as well

```

function fun<J>(val1:J):J{
   // if(typeof val1 === "boolean") return false as J;
    
    return val1;
}

let result = fun(true);

console.log(result)

```


Generics with array parameters:

```

function getSearchProducts<T>(products:T[]):T{
   
    return products[1];
}

```

With arrow functon:

```

const getSearchProductsList = <T>(products:T[]):T => {
    return products[0];
}

```



// Generic classes

```
function fun<T,U>(numOne:T,numTwo:U):objct{
    return {
        numOne,
        numTwo
    }
}

console.log(fun(3,'test'))


OP:

{
  "numOne": 3,
  "numTwo": "test"
} 


```


if we extend value as boolean then get error


```

// Generic classes

function fun<T,U extends boolean>(numOne:T,numTwo:U):objct{
    return {
        numOne,
        numTwo
    }
}

console.log(fun(3,'test'))

// error: Argument of type 'string' is not assignable to parameter of type 'boolean'


```


example with interface:


```
interface Database{
    connectionUrl:string,
    username:string,
    password:string
}


function fun<T,U extends Database>(numOne:T,numTwo:U):U{
    return numTwo;
}

console.log(fun(3,{
    connectionUrl:'test123',
    username:'123',
    password:'test123'
}))



```


other e.g

```



interface Quiz{
    qType:string,
    name:string,
    time:number
}

interface Course{
    name:string,
    author:string,
    subject:string
}

class Sellable<T>{
    public cart:T[] = [];

    addToCart(product:T){
        this.cart.push(product);
    }
}


let quizObj = new Sellable();

let quiz:Quiz = {
     qType:'history',
    name:'Q-1',
    time:60
}

quizObj.addToCart(quiz)


let courseObj = new Sellable();

let course:Course = {
     name:'Java',
    author:"abcd",
    subject:'xyz'
}

quizObj.addToCart(course)

```


#  Narrowing 

* in operator:

```
  
  interface User{
    name:string,
    email:string
  }


  interface Admin{
    name:string,
    email:string,
    isAdmin:boolean
  }

  function isAdmin(account: User | Admin){
    
    if("isAdmin" in account){
        return account.isAdmin;
    }

    return false;

  }

```


# keyof


keyof is a keyword in TypeScript which is used to extract the key type from an object type.

* keyof with explicit keys:

When used on an object type with explicit keys, keyof creates a union type with those keys.


```
interface Person{
    name:string,
    age:number
}

function printPersonProperty(person:Person, property: keyof Person){
    console.log(person[property])
}

let person = {
  name: "Max",
  age: 27
};

printPersonProperty(person,"name")

```

* keyof with index signatures:

keyof can also be used with index signatures to extract the index type.

```
type StringMap = { [key: string]: unknown };
// `keyof StringMap` resolves to `string` here
function createStringPair(property: keyof StringMap, value: string): StringMap {
  return { [property]: value };
}

let result = createStringPair("name","prathamesh");

console.log(result)

```


# OOPs Concept in TS/JS

i. Object	
ii. Classes	
iii. Encapsulation
iv. Abstraction	
v. Inheritance	
vi. Polymorphism



i. Objects:

An Object is an instance of a class. An Object is a unique entity that contains properties and methods.


### Way to create objects:

* Using an Object Literal:

```

let person = {
    first_name: 'Mukul',
    last_name: 'Latiyan',
    getPersonDetails:function(){ }

}

```


*  Using an Object Constructor:

```

function person(first_name, last_name) {
    this.first_name = first_name;
    this.last_name = last_name;
}

let person1 = new person('Mukul', 'Latiyan');
let person2 = new person('Rahul', 'Avasthi');

```

* Using Object.create() Method 


```

const coder = {
    isStudying: false,
}

const me = Object.create(coder);
me.isStudying = true;

```



ii. Classes:

Classes are blueprints of an Object.


Note: 

To be more precise, JavaScript is a prototype-based Object Oriented Language, which means it doesn’t have classes, rather it defines behaviors using a constructor function and then reuses it using the prototype. 


```

class Vehicle {
    constructor(name, maker, engine) {
        this.name = name;
        this.maker = maker;
        this.engine = engine;
    }
    getDetails() {
        return (`The name of the bike is ${this.name}.`)
    }
}

let bike1 = new Vehicle('Hayabusa', 'Suzuki', '1340cc');

```


* Traditional Way of defining an Object and simulating them as classes.

```

function Vehicle(name, maker, engine) {
    this.name = name,
        this.maker = maker,
        this.engine = engine
};
 
Vehicle.prototype.getDetails = function () {
    console.log('The name of the bike is ' + this.name);
}
 
let bike1 = new Vehicle('Hayabusa', 'Suzuki', '1340cc');

```


iii. Abstraction


Abstraction means displaying only essential information and hiding the details. Data abstraction refers to providing only essential information about the data to the outside world, hiding the background details or implementation. 


Abstract Method: A type of method that is only declared and has no implementation or “function body” is known as the Abstract method. The abstract method must be declared inside the Abstract Class. Where its definition can be added in its subclass.

Abstract Class: Abstract class is a type of class for which we can not create the instance and must contain at least one abstract method inside it.

It reduces the duplication of the code.

```

abstract class Person{
    username:string = '';
    constructor(name:string){
        this.username = name;
    }

    abstract info():void;
}

class User extends Person{
    
    constructor(name:string){
        super(name);
    }

    info(){
        return this.username;
    }
}

let obj = new User('ram');

console.log(obj.info())

```


Looking at the above example, we can outline the need for abstraction.

- We cannot instantiate the Abstract class which means this class can only be used by inheritance.
- The Abstract method definition can be given in its subclass.
- Extracting the unnecessary information and keeping it inside the Abstraction class, means it ignores the implementation details and only shows the functionality to the user.
- If we have to create a Person kind of object, we don’t have to bother about the properties of the Person. It's already given in abstract class, you just have to inherit in your class and use it.




note for me: https://medium.com/@baruahd5/object-oriented-programming-oops-using-typescript-cdbffd7d0cf5

create notes from above in ts