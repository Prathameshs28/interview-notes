
# JS coding questions Questions



1. Given an integer array nums of unique elements, return all possible subsets. The solution set must not contain duplicate subsets. Return the solution in any order.
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

---

2. You are given a string s. You can convert s to a palindrome by adding characters in front of it.
Return the shortest palindrome you can find by performing this transformation.
Input: s = "aacecaaa"
Output: "aaacecaaa"

---

3. Given a string s that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.
Return a list of unique strings that are valid with the minimum number of removals. You may return the answer in any order.
Input: s = "()())()"
Output: ["(())()","()()()"]

---

4. Given an integer n, return the least number of perfect square numbers that sum to n.
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
SECTION 2 (Solve any 2)

---


5. Given an array of objects as following:
   const arr = [{id: 'AB',sum: 100,},
  {id: 'BC',sum: 200,},
  {id: 'CA',sum: 200,},
  {id: 'BC',sum: 500,},
  {id: 'AB',sum: 900,}];
Convert this array such that objects with same ids have one object and sum should be equal to sum of all objects of same id
[{id: 'AB',sum: 1000,},
  {id: 'BC',sum: 700,},
  {id: 'CA',sum: 200,}];
  

---

  3. how to find duplicate elements in given array ?
  
```js
    const arr = [10,20,30,40,20,60,70,10];
    
    const duplicate = arr.filter((el,index,array) => arr.indexOf(el) !== index );
    
    console.log('Duplicate: ',duplicate);


    const arr2 = [10,30,10,40,20,10];
    
    const unique = arr2.filter((el,index,arr2) => arr2.indexOf(el) == index) // or

      // const unique = Array.from(new Set(arr)) // easy way
    
    console.log('Unique: ',unique);  
    
```
  
**#Output:**

```
Duplicate: [20, 10]
Unique: [10, 30, 40, 20]
```

---

   4. How to find the count of duplicates in an array?
  
```js

const arr = [10,20,30,40,20,60,70,10,90,20];
    
const count = arr.reduce((obj,el) => {
    if(obj[el] == undefined){
        obj[el] =1;
        return obj;
    }else{
        obj[el]++;
        return obj;
    }
},{});

console.log(count);

```

**#Output:**

```
{10: 2, 20: 3, 30: 1, 40: 1, 60: 1, 70: 1, 90: 1}
```

---


  5. how to check if a given number is an integer ?
  
  ```js
  const no = 1;
    
  console.log(!isNaN(no));
  console.log(Number.isInteger(no))

  ```

**#Output:**

```
true
true  
```

---


  7. how to sort a number array?

  ```js
  const arr = [40,20,80,20,10,80,100];
    
    const sorted = arr.sort((a,b)=>{
        return a - b;
    });
    
    console.log(sorted)  
  
  ```

**#Output:**

```
[10, 20, 20, 40, 80, 80, 100]
```

---
  
  8. how to sort given string array ?

```js
    const arr = ['jan','feb','march','aug','may'];   
    
    console.log(arr.sort())

```
 
**#Output:**

```
['aug', 'feb', 'jan', 'march', 'may']
```
  
---
  
 
  9. How to find maximum value in a numbered array ?


  ```js
  let arr = [20,40,20,50,60,70,10,50];

    let max = arr.reduce((pre,next) => {
        return pre > next ? pre : next;
    })
    
    console.log(max);  
  ```
  
**#Output:**

```
70
```

---
  
  10. How to find minimum value in a numbered array ?

```js
  let arr = [20,40,20,50,60,70,10,50];
    
    let min = arr.reduce((pre,next) => {
        return pre < next ? pre : next;
    })
    
    console.log(min);
```

**#Output:**

```
10
```

---

  11. How to find the average of the numbers in the numbered array ?

```js
    let arr = [10,20,40,0,80,30,40];
    
    let total = arr.reduce( (pre,next) => pre +  next,0)
    
    
    console.log(total/arr.length);
```

**#Output:**

```
31.428571428571427
```
  
---

  
  12. how can you uppercase the first character in string array ?

 ```js
   const days = ['sun','mon','tue','wed','thu','fri','sat'];
  let newDay = [];
  days.forEach( (el) => {
    el = el.charAt(0).toUpperCase() + el.substring(1);
    newDay.push(el);
  } )
  
  console.log(newDay);
 
 ```

**#Output:**

```
['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']
```

---


  13. How to make sentence out of a given array?

  ```js

  let arr = ['Welcome','to','Computer','World','!!!'];

  // let sen ='';
  // arr.forEach((el) =>{
  //     sen += el + ' ';
  // })

  let sen = arr.join(" ");
  console.log(sen);

  ```

**#Output:**

```
Welcome to Computer World !!! 
```

---

  14. How to check if an array contains any element of another array?

```js
  let arr1 = [1,2,3,4,5,6,7,8,9,10];

  let arr2 = [12];

  let ans = arr1.some( el => arr2.includes(el))

  console.log(ans)

```

**#Output:**

```
false
```

--- 
  
  15. Given two strings how can you check if the strings are anagram 
  for each other ?

  ```js
    let str1 = 'abc';
    let str2 = 'cbd';
    
    //let str2 = 'cba';  // true
    
    function checkAnagram(s1,s2){
    let a = str1.toLowerCase();
    let b=str2.toLowerCase();
    
    a=a.split("").sort().join("");
    b=b.split("").sort().join("");
    
    return a===b;
    }
    
    console.log(checkAnagram(str1,str2));  
  ```

**#Output:**

```
false
```

---
  
  16. How can you extract a few fields from the given JSON object
  and form a new array ?

```js
    const data = {
    "emp": [
      {
        name:'abcd',
        id:101,
        sal:1000
      },
       {
        name:'xyz',
        id:102,
        sal:2000
      },
       {
        name:'pqrs',
        id:103,
        sal:3000
      },
       {
        name:'lmno',
        id:104,
        sal:4000
      }
    ]
  }
  
let result = data.emp.map((el) =>{
   
    let newData = {
        name:el.name,
        sal:el.sal + 500
    }
    
    return newData
    
});

console.log(result);
```

**#Output:**

```
[
    { "name": "abcd", "sal": 1500 },
    { "name": "xyz",  "sal": 2500 },
    { "name": "pqrs", "sal": 3500 },
    { "name": "lmno", "sal": 4500 }
]
```

---
---



  **String Questions:** 


  1. How do you check whether a string contains a substring?

```js

      // using includes (ES6):

      let str = 'hello';
      let substr='ell';

      console.log(str.includes(substr))
  
  
       // using indexOf (ES5):

        let str2 = 'hello';
        let substr2='ell';

        console.log(str2.indexOf(substr2) !== -1)
  

      //using regex


```

**#Output:**

```
true
true
```

---

- what will be output: 
```js
console.log("[743,31]" > "[89]") // 7 > 8 false

console.log("[3]" > "[2]") // 3 > 2 // true

```

- Ans-> It compares numbers and if it's returns false then ans will be false

---


**Find the OP:**

```js
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

```

---

1. Reverse an Array
2. Find the maximum Element
3. Remove duplicates
4. Array sumRotate an Array
5. Merge two sorted arrays
6. Array intersection
7. Subarray with given sum
8. Two sum
9. Move Zeros to the end


Objects:

1. write a function to extract keys and
values from an object and return them as separate arrays

2. Implement a function to deeply compare two objects 
and determine if they are equal 

3. write a function to transform an object by adding a prefix to all its keys

4. implement a function to filter an object based on a given condition

5. write a function to flatten a nested object into single-level object

6. Implement a funciton to merge two objects, with second 
object's values precendence in case of key conflicts

7. Write a function to convert an objects into a JSON string

8. Implement a function to create a deep copy of object

9. Write a funciton to check if a specific key exists in an object

10. write a function to convert an array of objects into 
an object, using a specified property as 
the key.


