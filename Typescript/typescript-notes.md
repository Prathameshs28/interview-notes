
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