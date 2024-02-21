 # Javascript interview questions


1. Event loop.
2. what is promises?
3. What is closure
4. hoisting?
5. what are javascript data types  
6. difference between let, const and var 
7. Difference between map, filter, reduce, find
8. splice method
9. Various ways to create object in JS
10. What is object literal in JS?
11. How to use OOP in JS 
12. What are classes in JS?
13. what is singleton class
14. How to implement singleton class?
15. What is object oriented concepts used in javascript
16. What is encapsulation , how to implement in javascript
17. what is inheritance  , how to implement in javascript 
18. Features of ES6 and what is ES6
19. implicit and explicit binding (apply, this,call,bind);
20. functions are first class object in js 
21. what is json ?
22. How to secure http cookies?
23. js is singlethred or multithreded why
24. highoreder function in js
25. what  is anonunomous function where we use that




**Find the OP:**


function f() {
    console.log('var', area);	
    console.log('let', name);
    let name = 'Bert';
    var area = 'Geology';
}
f();

function f2() {
    for (var i = 0; i < 3; i++) {
        setTimeout(function () {
            console.log(i)
        }, 1000 * i);
    }
}