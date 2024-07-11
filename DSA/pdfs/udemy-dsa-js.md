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



1 hr 10 min



















































