
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


* Using class constructor:

```
class Employee{
  name: string;
  age: number;
  constructor(n: string, a: number){
    this.name= n;
    this.age=a;
  }
}

let emp = new Employee("John", 24);
console.log(emp.name);
console.log(emp.age);


```


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

function person(first_name:string, last_name:string) {
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



### Inheritance:

It is the mechanism through which a class inherits or acquires properties of another class.

The class from which properties are inherited is called the base/super/parent class and the class which acquires the property is called the derived/child/sub class.


note: ‘super’ is a keyword used to call the parent constructor and its value.


```


// Base class
class Manager{               
  firstName : string;
  lastName : string;
  salary: number
  email: string;

  constructor(firstName: string, lastName: string, salary: number, email: string){
    this.firstName= firstName;
    this.lastName= lastName;
    this.email= email;
    this.salary= salary;
  }
}

//Derived class
class AreaManager extends Manager{ 
  area: string;
  constructor(firstName: string, lastName: string, salary: number, email: string, area: string){
    super(firstName, lastName, salary, email);
    this.area= area;
  }
}

const manager = new Manager("John", "Doe", 25000, "john@xyz.com");  
const areaManager = new AreaManager("Chun", "Li", 35000, "chun@xyz.com", "Los Angeles");

console.log(`Manager's name: ${manager.firstName} ${manager.lastName}`);
console.log(`Manager's salary: ${manager.salary}`);
console.log(`Area Manager's name: ${areaManager.firstName} ${areaManager.lastName}`);
console.log(`Area Manager's salary: ${areaManager.salary}`);
console.log(`Area Manager's area of duty: ${areaManager.area}`);


```

* Types of Inheritance:


- Single inheritance
- Multilevel Inheritance
- Multiple Inheritance
- Hierarchical inheritance
- Hybrid inheritance


* Single Inheritance:

When a single class inherits another single class

Class A (Parent) ----> Class B (Child)

Above eg. for sigle inheritance.



* Multilevel Inheritance:

When there is a single chain of inheritance then it is called as multilevel inheritance.

Class A (Parent of B & C) ----> Class B (Child for A but Parent for C) ----> Class C (Child of A,B)



* Multiple Inheritance:


When a sub class inherits from more than one base class. Typescript does not support multiple inheritance.

Class A (Parent) &  Class B (Parent) ----> Class C (Child of A & C)



* Hierarchical Inheritance:

When more than one sub classes are inherited from a single base class.

```
                Class A (Parent) 
                      ||
                      \/
 Class B (Child of A)     Class C (Child of A)


```

* Hybrid Inheritance:


Combination of more than one type of inheritance is called hybrid inheritance. To reduce complexity typescript does not support hybrid inheritance.



```
                Class A (Parent) 
                     / \
                    /   \
 Class B (Child of A)     Class C (Child of A)
              \             /
               \           /
             Class A (Child of B & C)

```


### Polymorphism:


Poly signifies many and meaning of morph is shape, so polymorphism is basically executing a function in many ways. Polymorphism is another way after inheritance to achieve code reusability.



*Polymorphism can be achieved by:

- Method Overloading
- Method Overriding



1. Method Overloading


In typescript we can have multiple function with the same name using different parameter types and return types. Unlike java, in typescript the number of parameters must be same. 

Let’s understand this with two examples:


```

class Example{
  

// function declaration
  
  add(a:string, b:string): string;
  add(a:number, b:number): number; 
  
  // method add is overloaded by providinng different parameter type and return type
  
  // function definition

  add(a:any, b:any):any{
    return a+b;
  }  
}

let object= new Example();

console.log(object.add("Hello ","John"));
console.log(object.add(1,1));

OP:

"Hello John"
2

```

we are trying to overload the function add by changing the parameter type and return type to number.



Now let’s try providing different number of parameters:




```

class Example{
  mult(a: number, b:number){
    return a*b;
  }
  mult(a:number, b:number, c:number){
    return a*b*c;
  }
}


Output:

Error: Duplicate function implementation

```


2. Method Overriding:



To implement method overriding we must use inheritance and in the child class we provide different definition of functions that have been previously declared in the base class. 

Let’s take an example:


```

class Laptop{
  getOS(){
    console.log("Operatiing System");
  }
}

class Macbook extends Laptop{
  getOS(){
    console.log("MacOS");
  }
}

class DellLaptop extends Laptop{
  getOS(){
    console.log("Windows");
  }
}

let obj1 = new Laptop();
let obj2 = new Macbook();
let obj3 = new DellLaptop();

obj1.getOS();
obj2.getOS();
obj3.getOS();


Output:

"Operatiing System"
"MacOS"
"Windows"

```


In the above example subclass Macbook and subclass DellLaptop both extends base class Laptop. Laptop has a method getOS(). We are overriding this method in both the subclasses by simply defining it uniquely in each time.




### Abstraction


Abstraction is simply hiding internal details and showing functionalities. It lets us focus on what an object does instead of how it does.


It reduces the duplication of the code.


Abstraction can be achieved by two ways:

- Using abstract class
- Using interface


* Abstract Method: 

- A type of method that is only declared and has no implementation or “function body” is known as the Abstract method. 

- The abstract method must be declared inside the Abstract Class. Where its definition can be added in its subclass.



* Abstract Class: 

- We define an abstract class in typescript using an abstract keyword before the class keyword.

- Instance of an abstract class cannot be created. But other classes can be derived from it and must contain at least one abstract method inside it.

- The class which extends an abstract class must define all the abstract methods or properties.


- The class which extends abstract class must call super in the constructor.


```

abstract class Children {
    name: string;
    
    constructor(name: string) {
        this.name = name;
    }

    display(): void{
        console.log(this.name);
    }

    abstract find(rollNo: number): Children;
}

class Student extends Children { 
    rollNo: number;
    
    constructor(name: string, rollNo: number) { 
        super(name); // must call super()
        this.rollNo = rollNo;
    }

    find(rollNo:number): Children { 
        let roll: number=101;
        let name: string = "ABCD";
        return new Student(name, roll);
    }
}

let emp: Children = new Student("John", 100);
emp.display(); 

let emp2: Children = emp.find(101);
emp2.display();

```


Looking at the above example, we can outline the need for abstraction.

- We cannot instantiate the Abstract class which means this class can only be used by inheritance.

- The Abstract method definition can be given in its subclass.

- Extracting the unnecessary information and keeping it inside the Abstraction class, means it ignores the implementation details and only shows the functionality to the user.



### Interface:


- It is a syntax for a class.

- It contains only the declaration of methods and properties. Classes implementing an interface must implement all its members and methods.

- It cannot be instantiated.

- It is used to type-check an object, whether it is followed by a specific structure or not .

- Interfaces can be inherited from other interfaces by using extends key word.

- Classes use implements keyword to implement an interface.


```

interface IUser{
  name: string;
  email: string;
}

interface IEmployee extends IUser{
  employeeId: number;
}

class Employee implements IEmployee{
  name: string;
  email: string;
  employeeId: number;
  constructor(name: string, email: string, employeeId: number){
    this.name= name;
    this.email= email;
    this.employeeId= employeeId;
  }
}

```


In the above example interface IEmployee extends interface IUser, shows interfaces can be inherited from other interfaces. Again class Employee implements interface IEmployee.



### Access Modifiers



To understand encapsulation we must first understand the access modifiers. There are three types of access modifiers in typescript:

- Public
- Private
- Protected


* Public

By default all the members of a class are public in typescript that means we can access and modify them outside of the class. Let’s take an example:



```
class Employee{
    name:string;
    public age:number;

    constructor(name:string,age:number){
        this.name = name;
        this.age = age;
    }
}

let emp = new Employee("John",24);

console.log(emp.name + "age is " + emp.age)

emp.name = "abcd"
emp.age = 30;

console.log(emp.name + "age is " + emp.age)


Output:

John age is 24
abcd age is 30

```

* Private:

Private members are allowed to access or modify inside the class but not allowed outside of the class. Let’s take an example:



```
class Employee{
    name:string;
    private age:number;

    constructor(name:string,age:number){
        this.name = name;
        this.age = age;
    }

    display(){
        console.log(this.age)
    }
}

let emp = new Employee("John",24);

emp.display();

// emp.age = 30; // not allowed


```

* Protected:

Protected members can be accessed or modified within the class as well as within its child classes. For example:


```
class Employee{
    name:string;
    protected age:number;

    constructor(name:string,age:number){
        this.name = name;
        this.age = age;
    }
}

class Manager extends Employee{
    designation:string;

    construction(name:string,age:number,designation:string){
        super(name,age);
        this.designation = designation;
    }

    display(){
        console.log(this.age);
    }

    modify(num:number){
        this.age = num;
    }
}

let emp = new Manager("John",24,"Manager");

emp.display();
emp.modify(40);
emp.display();

OP:

24
40

```

* Encapsulation:


Wrapping codes and data into a single unit is called encapsulation. We can achieve it by using the access modifiers. For example we can create a fully encapsulated class by making all its members private.


```



class Employee {
    private name!:string;
    private salary!:number;
    private empId!:number;

    constructor(empName:string, empSalary:number, empId:number){
        this.empId = empId;
        this.salary = empSalary;
        this.name = empName;
    }

    set setEmpSalary(sal:number){
        this.salary = sal;
    }

    get getEmpSalary():number{
        return this.salary;
    }

}

let empObj = new Employee('ram',50000,101);

console.log(empObj);

empObj.setEmpSalary = 100000;
let newSal = empObj.getEmpSalary;

console.log(newSal);


OP:

 Employee: {
  "empId": 101,
  "salary": 50000,
  "name": "ram"
} 

100000 

```


























