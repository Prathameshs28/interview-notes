# Javascript Notes:


 call :
Call is a function that helps to change the context of the invoking function.  it helps to replace the value of this inside a function with whatever value you want.
Apply:
Apply is very similar to the call function. The only difference is that in apply you can pass an array as an argument list
Bind:
Bind is a function that helps you create another function that you can execute later with the new context of this that is provided.
The call() method takes arguments separately.
The apply() method takes arguments as an array
bind() method, an object can borrow a method from another object.
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
*** Singleton design pattern :
 The singleton is one of the most well-known design patterns. There are times when you need to have only one instance of a class and no more than that.
Singletons are used to create an instance of a class if it does not exist or else return the reference of the existing one. This means that singletons are created exactly once during the runtime of the application in the global scope.
Several other patterns, such as, Factory, Prototype, and Façade are frequently implemented as Singletons when only one instance is needed.
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
 Abstraction:
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



 **************************************************************
