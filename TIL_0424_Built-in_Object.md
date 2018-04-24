# 0424 Built-in Object

## Built-in Object

- JavaScript's standard, built-in objects

- These objects are Date, Math, String, Array, and Object


* [What is Built-in Object](https://www.ibm.com/developerworks/library/wa-objectsinjs-v1b/index.html)
for reference, All programming languages have intrinsic (or built-in) objects that create the essential functionality of the language. Intrinsic objects are the foundation of the language in which you write custom code that powers custom functionality based on your imagination. JavaScript has many intrinsic objects that define it as a language. 



## JSON

- **JSON**: JavaScript Object Notation. For Web. 

- JSON is a syntax for storing and exchanging data.

- When exchanging data between a browser and a server, the data can only be text.

- We can also convert any JSON received from the server into JavaScript objects.

* Serialization: basically, converts JSON data into instances of .NET Framework types and back into JSON data (<-> deserialization)

```js
//serialization
JSON.stringify({
  key: 'value',
  arr: [1, 2, 3],
  nullProp: null,
  undefinedProp: undefined // undefined is not included in the process of serialization
});

//deserialization
JSON.parse('{"key":"value","arr":[1,2,3],"nullProp":null}');
```


## Date

- Date objects are based on a **time value** that is the number of milliseconds since 1 January 1970 UTC.

- Basic syntax is as follows:

```js
new Date();
new Date(value);
new Date(dateString);
new Date(year, month [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);



// To calculate a time difference between two certain times

const start = new Date();
alert('Time goes by....');
const end = new Date();
alert(`${end - start} Duration of time`);
```

* Powerful library: [moment.js](https://momentjs.com/)


### Symbol

- The Symbol() function returns a value of type symbol

- A symbol value may be used as an identifier for object properties; this is the data type's only purpose.

```js

const sym = Symbol();
console.log(typeof sym); // symbol
console.log(sym); // Symbol()
```

### Map

- A Map object iterates its elements in insertion order — a for...of loop returns an array of [key, value] for each iteration

- Note here!  Key-value pair!! => a whole new different data structure comes out!

```js
const m = new Map();

m.set('hello', 'world');
console.log(m.get('hello')); // 'world'
console.log(m.has('hello')); // true
```

