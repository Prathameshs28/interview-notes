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

 

## Some patterns:

1. Frequency counter
2. Multiple pointers
3. Sliding window
4. Divide and conquer
5. Dynamic programming
6. Greedy algorithm
7. Backtracking



1. Frequency counter:

This pattern uses objects or sets or collect values/frequencies of values.

This can often avoid the need for nested loops or O(N^2) operations with arrays / strings.


```

function checkSquares(arr1,arr2){
    if(arr1.length !== arr2.length){
        return false;
    }

    for(let i=0;i<arr1.length;i++){
        let currentIndex = arr2.indexOf(arr1[i] ** 2);
        if(currentIndex === -1){
          return false;
        }
            arr2.splice(currentIndex,1)
    }
        return true;

}

const result = checkSquares([1,2,3],[9,1,4]);

console.log(result)

```

Here time complexity will be O(n^2)

for loop * indexOf() 

indexOf internally works on top of loop.


```

function checkSquares(arr1,arr2){
    let arr1Obj = {};
    let arr2Obj = {};
    
    for(let i of arr1){
      arr1Obj[i] = ++arr1Obj[i] || 1;
    }

console.log(arr1Obj)

    for(let i of arr2){
      arr2Obj[i] = (arr2Obj[i] || 0) + 1;
    }
    
   
   for(let key in arr1Obj){
     if(arr2Obj[key ** 2] !== arr1Obj[key]){
        return false;
     }
     
     if(!(key **2 in arr2Obj)){
       return false;
     }
   }

  return true;
}

const result = checkSquares([1,2,3,2],[9,4,1,4]);

console.log(result)

```


using objects we can reduce time complexity to O(m+n)



* Example for anagram:

```
function checkAnagram(str1,str2){
  if(str1.length !== str2.length){
    return false;
  }
  
  let str1Obj = {};
  let str2Obj = {};
  
  for(let i of str1){
    str1Obj[i] = ++str1Obj[i] || 1;
  }
  

  for(let i=0;i<str2.length;i++){
    
   if(!str1Obj[str2[i]]){
     console.log(str1Obj)
     return false;
  }else{
      str1Obj[str2[i]] -= 1;
  }
  }
  

  return true;
  
}

console.log(checkAnagram('madam','amdma'))


```


* Multiple pointers

Creating pointers or values that correspond to an index or position and move towards the beginning, end or middle based on a cretain condition.


Very efficient for solving problems with minimal space complexity as well.


e.g 

```
sumZero([-3,-2,-1,0,1,2,3])

function sumZero(arr){
  
  let start = arr[0];
  let end = arr.length -1;
  
  while(start < end){
    let sum = arr[start] + arr[end];
    
    if(sum === 0){
      return [arr[start] , arr[end]]
    }else if(sum > 0){
      end--;
    }else{
      start++;
    }
    
  }
}


```

e.g Count unique values:

```
function findUniqueNumCount(arr){

  let i = 0;j=1;
  
  while(j < arr.length){
      if(arr[i] !== arr[j]){
        i++;
        arr[i] = arr[j];
      }
        j++;
  }
  
  return i+1;
  
}  


console.log(findUniqueNumCount([1,2,2,3,4,4,4,7,7,12,12,13]))

output: 7 

explaination: 1,2,3,4,7,12,13

```


### Sliding window


This pattern involves creating a window which can either be an array or number from one position to another


Depending on a certain condition the window either increases or closes (and a new window is created) very useful for keeping track of a subset of data in an array/string etc


```
Brut force soln:

function maxSubarrSum(arr,num){
  
  let max = -Infinity;
  
  for(let i=0;i< arr.length - num + 1;i++){
    let temp = 0;
    
    for(let j=0;j<num;j++){
      temp += arr[i+j];
    }
    
    if(max < temp){
      max = temp;
    }
    
  }
  
  return max;
  
}


console.log(maxSubarrSum([2,6,9,2,1,8,5,6,10,3],3)) 

output: 21

```



* using sliding window algorithm:


```


function maxSubarrSum(arr,num){
  
 if(num > arr.length) return null;
 
 let maxSum = 0;
 let tempSum = 0;
 
 for(let i=0;i<num;i++){
   maxSum += arr[i];
 }
 
 tempSum = maxSum;
 
 for(let i= num; i<arr.length;i++){
   
   tempSum = tempSum - arr[i - num] + arr[i];
   
   maxSum = Math.max(tempSum,maxSum)
   
 }
 
 return maxSum;
  
}


console.log(maxSubarrSum([2,6,9,2,1,8,5,6,3],3))


```



###  Divide and conquer:

This pattern involves dividing a data set into smaller chunks and then repeating a process with subset of data.

this pattern can tremendously decrease time complexity.



```

function search(arr,val){
  for(let i=0;i< arr.length;i++){
    if(arr[i] === val) return i;
  }
}

Lenear search

Time comp: O(N)

```

```

function search(array,val){
  let min = 0;
  let max = array.length -1;

  while(min <= max){
    let middle = Math.floor((min + max) / 2);

  if(array[middle] < val){
    min = middle + 1;
  }else if(array[middle] > val){
    max = middle -1;
  }else{
    return middle;
  }
  }

  return -1;
}

TC: log(N) Binary search

```


### Recursion:


* What is recursion?

A process (a function in our case) that calls itself


- JSON.parse / JSON.stringify

- document.getElementById and DOM traversal algorithms

- Object traversal


Functions:

In almost all programs languages, there is a built in data structure that manages what happens when functions are invoked.


* The Call Stack


- It's a stack data structure

- Any time a function is invoked it is placed (pushed) on the top of the call stack

- When javascript sees the return keyword or when the function ends, the compiler will remove (pop)




- you're used to functions being pushed on the call stack and popped off when they are done

- When we write recursive functions, we keep pushing new functions onto the call stack



* Helper method Recursion


```

function findOddNumbers(arr){
  
  let result = [];
  
  function helper(inputArr){
    
    let len = inputArr.length;
    if(len === 0) return;
    
    if(inputArr[0] % 2 !== 0){
      result.push(inputArr[0]);
    }
    
    return helper(inputArr.slice(1))
  }
  
  
  helper(arr);
  
  return result;
  
}


let result = findOddNumbers([1,2,3,4,5,6,7,8,9,11]);

console.log(result)


```


* Pured recursion:


```

function findOddNumbers(arr){
  
  let result = [];
  

    let len = arr.length;
    if(len === 0) return result;
    
    if(arr[0] % 2 !== 0){
      result.push(arr[0]);
    }
   
    result = result.concat(findOddNumbers(arr.slice(1)));
   
  return result;
  
}


let result = findOddNumbers([1,2,3,4,5,6,7,8,9,11]);

console.log(result)

```

- For arrays, use methods like slice, the spread operator and concat that make copies of arryas so you do not mutate them.


- Remember that strings are immutable so you will need to use methods like slice, substr or substring to make copies of strings.

- To make copies of objects use Object.assign or the spread operator.



### Searching algorithms:


* JS Search


There are many different search methods on arrays in js:

- indexOf
- includes
- find
- findIndex


## Linear Search


```

function linearSearch(arr,item){
    
    for(let i=0;i<arr.length;i++){
      if(arr[i] === item) return i;
    }
    
    return -1;
}

let result= linearSearch([10,40,70,10,90,20,80], 900);

console.log(result);

```

Big O for linear search

Best- O(1)
Average- O(N)
Worst- O(N)



## Binary Search:

- Binary search only works on sorted array.


* Divide and Conquer:




```


function binarySearch(arr,item){
  
  let start = 0;
  let end = arr.length -1 ;
  
  while(start <= end){
    let middle = Math.floor((start + end ) /2);
    
    if(arr[middle] < item){
        start = middle + 1;
    }else if(arr[middle] > item){
      end = middle - 1;
    }else{
      return middle;
    }
    
  }
  
  return -1;   
}



let result= binarySearch([10,20,30,40,50,60,70,80], 40);

console.log(result)

```


Big O for Binary Search

Wrost and Average case: O(log n)

Best case: O(1)



#### Naive String Search



```

function naiveSearch(long, short){
  let count = 0;

  for(let i=0;i< long.length;i++){
    for(let j=0;j< short.length;j++){
      if(short[j] !== long[i+j]){
        break;
      }

      if(j === short.length - 1){
        count++;
      }
    }
  }
  return count;
}

let result = naiveSearch("lorie loled","lol");

console.log(result);

```

## Sorting Algorithms:


Sorting is the process of rearranging the items in a collection (e.g an array) so that the items are in some kind of order.

In JS for sort, Firefox uses merge sort, while Chrome and Safari use Tim-sort.

Tim Sort is a hybrid sorting algorithm derived from merge sort and insertion sort.


* Bubble sort:


A sorting algorithm where the largest values bubble up to the top.







6.22 hr 
























 





































 





































 





































 





































 





































 





































 





































 





































 





































 





































 



































