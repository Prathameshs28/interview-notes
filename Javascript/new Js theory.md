
#### Deep cloning in js:

We can deep clone in js using, 

1. JSON Stringify and Parse
2. structuredClone()
3. loadash library
4. custom recursive function


### 1. JSON Stringify and Parse

- JSON.stringify: Converts a JavaScript object into a JSON string.
- JSON.parse: Parses a JSON string and constructs a JavaScript object from it.


```
const original = { a: 1, b: { c: 2 } };
const cloned = JSON.parse(JSON.stringify(original));

```

##### Limitations:

1. Loss of Functions:

   ```
    const original = { a: 1, b: function() { return this.a; } };
    const cloned = JSON.parse(JSON.stringify(original));
    console.log(cloned.b); // undefined
   
   ```

2. Non-Serializable Properties:
   Properties that are not serializable by JSON, such as undefined, symbol, or function, will be lost.
   They won't appear in the cloned object.


 ```
  const original = { a: undefined, b: Symbol('sym') };
  const cloned = JSON.parse(JSON.stringify(original));
  console.log(cloned); // { }
 ```

3. Date Objects:

Date objects will be converted to strings. You’ll lose the date functionality and need to manually convert them back if required.


```
const original = { date: new Date() };
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.date); // ISO date string, not a Date object

```

4. Prototype Chain:

This approach does not preserve the prototype chain. The cloned object will have the default Object prototype.


```
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function() {
  return `Hello, ${this.name}!`;
};

const original = new Person('Alice');
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.greet); // undefined

```

5. RegExp Objects

RegExp objects are converted to plain objects. Their properties and functionality are lost in the cloning process.


```
const original = { pattern: /abc/ };
const cloned = JSON.parse(JSON.stringify(original));
console.log(cloned.pattern); // {}

```

6. Map & Set Objects
JSON.stringify does not handle Map & Set objects directly. When you try to stringify a Map, it will be converted to an empty object {}.

```
const map = new Map([[1, 'one'], [2, 'two']]);
const jsonString = JSON.stringify(map);
console.log(jsonString); // "{}"


```


```
const set = new Set([1, 2, 3]);
const jsonString = JSON.stringify(set);
console.log(jsonString); // "{}"

```



### 2. structuredClone()


```
let clone = structuredClone(value);

```

- While structuredClone is robust and versatile, it has limitations:

1. Does not clone functions or Symbol properties.
2. Does not preserve prototypes.



### 3. loadash library

- Lodash: _.cloneDeep handles many of the complexities associated with deep cloning

```
const _ = require('lodash');
const original = { a: new Date(), b: /abc/, c: function() {} };
const cloned = _.cloneDeep(original);

```

- Rambda: The R.clone function from Ramda also provides deep cloning functionality

```
const R = require('ramda');
const original = { a: new Date(), b: /abc/, c: function() {} };
const cloned = R.clone(original);

```


#### 4. Custom recursive function

```

let obj = {
  name:'ram',
  age:undefined,
  add:{
    line:'abcd',
    loc:'pune',
    pin:12345
  },
  size:[10,20,30,40]
}

let result = cloneObject(obj);

console.log(result)



function cloneObject(obj){
  
  if(obj === null || typeof obj !== 'object') return obj;
  
  if(Array.isArray(obj)){
    return obj.map((item)=> cloneObject(item) );
  }
  
  
  
  let resultObj = {};
  
  for(let key in obj){
    if(obj.hasOwnProperty(key)){
      resultObj[key] = cloneObject(obj[key]);
    }
  }
  
  
  return resultObj;
  
}

```

* Note: for custom function need to handle for Symbol, Map, Set.


