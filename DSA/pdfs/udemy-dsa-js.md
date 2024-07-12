https://www.youtube.com/watch?v=t4UNV4ncvRs


# Big O notation:



Time required for different two approaches:

```

function add(n){
        let total = 0;
        for(let i=1;i<=n;i++){
            total += i;
        }

        return total;
      }  

      let limit = 1000000000;
      let t1 = performance.now();
        //   add(limit); // Time elapsed: 1.214 seconds.
         nIntegerAddFormula(limit)  // Time elapsed: 0.00009999999776482581 seconds.
      let t2 = performance.now();

      console.log(`Time elapsed: ${(t2-t1)/1000} seconds.`)
    

      function nIntegerAddFormula(n){
        let total = 0;
        total = (n * (n+1)) /2;
        return total;
      }     

```


* The Problem with Time:

- Different machines will record different times

- THe same machine will record different times

- For fast algorithms speed measurements may not be precise enough?


If not time then what?

Rather than couting seconds, which are so variable...

Let's count the number of simple operations of simple operations the computer has to perform.



Big O notation is way to formalize fuzzy counting.


It allows us to talk formally about how the runtime of an algorithm grows as the inputs grow


We say that an algorithm is O(f(n)) if the number of simple operations the computer has to do is eventually less than a constat times f(n) as n increases.




- f(n) could be linear (f(n) = n)
- f(n) could be quadratic (f(n)= n^2)
- f(n) could be constant (f(n) =1 )
- f(n) could be something entirely different



## Simplifying Big O operations:


When determining the time complexity of an algorithm there are some helpful rule of thumbs for big O experessions.


These rules of thumb are consequences of definition of big O notation 


1. Constats don't matter

O(2n) ==> O(n)

O(500) ==> O(1)

O(13n^2) ==> O(n^2)


2. smaller terms don't matter

O(n+10) ==> O(n)

O(1000n+50) ==> O(n)

O(n^2+5n+7) ==> O(n^2)



## Big O shorthands

- Arithmetic operations are constats

- Variable assignment is constant

- Accessing elements in array (by index) or object (by key) is constant

- In a loop the complexity is the length of the loop times the complexity of whaterver happens inside of the loop.



## Space complexity:


We can also use big O notation to analyze space complexity

how much additional memory do we need to allocate in order to run the code in our algorithm?



Space complexity in JS

1. Most primitives (booleans, numbers, undefined, null) are constant space.

2. Strings require O(n) space (where n is the string length)

3. Reference types are generally O(n) where n is the length (for arrays) or the number of keys (for objects)


## Logarithms:


log 2 (8) = 3  ==> 2 ^3 = 8


log 2 (value) = exponent ==> 2^exponent = value




The logarithm of a number roughly measures the number of times you can divide that number by 2 before you get a value that's less than or equal to one.



Certain searching algorithms have logarithmic time complexity.

Efficient sorting algorithms involve logarithms.


Recursion sometimes involves logarithmic space complexity.



## OBjects

Big O of objects


Insertion - O(1)
Removal - O(1)
Searching - O(N)
Access - O(1)


when we don't need any ordering objects are an excellent choice.


Big O of Object methods

Object.keys - O(n)
Object.values - O(n)
Object.entries - O(n)
hasOwnProperty - O(1)



## Arrays


Big O of Arrays

Insertion - It depends 
Removal - It depends
Searching - O(n)
Access - O(1)



push - O(1)
pop - O(1)
shift - O(n)
unshift - O(n)
concat - O(n)
slice - O(n)
splice - O(n)
sort - O(n * log n)
forEach/map/filter/reduce - O(n)



## Algorithms and Problem Solving Patterns:

* What is an Algorithm?

A process of set of steps to accomplish a certain task.



## Problem solving stratergies:


- Understand the problem:

i. Can I restate the problem in my own words?

ii. What are the inputs that go into the problem?

iii. What are the outputs that should come from the solution to problem?

iv. Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problem? (you may not be able to answer this question until you set about solving the problem. That's okay it's still worth considering the question at this early stage).

v. How should I label the important pieces of data that are a part of the problem?



- Explore concrete examples:

i. start with simple examples

ii. Progress to more complex examples

iii. Explore e.g with empty inpts

iv. expore e.g with invalid inputs



- Break it down:

i. Explicitly write out the steps you need to take.


- Solve/Simplify:

i. Find the core difficulty in what you're trying to do

ii. Temporarily ignore that difficulty 

iii. Write a simplified solution

iv. Then incorporate that difficulty back in.


- Look back and refactor



 
2.32 hr 




































 





































 





































 





































 





































 





































 





































 





































 





































 





































 





































 





































 



































