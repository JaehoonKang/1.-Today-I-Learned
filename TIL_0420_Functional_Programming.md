# TIL 0420 Functional Programming

## Chanllenges of today of all

> 1. What on earth is `Functional Programming`?? => I don't even know right now...not a bit only know that it is a more recent concept than `Object Oriented Programming`
> 
> 2. More about `object and its properties`
>

- Let's get it started...!


## Functional Programming 

- Easy definition: `the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects`

- In class, it didn't dive deep into this concept

- I learned 3 key parts: `Higher-order function`, `Closure`, and `Recursion function`


### Higher-order function

- it `takes` one or more functions as arguments `OR` `returns` a function as its result.

```js
// this takes functions as arguments
function func2(f) {
  f();
}

// this returns a function as its results
function func1() {
  return function() {};
}
```

<br>

> actually, a lot of methods in array(`map` or `filter`), they take function as an argument so they are high-order functions 
>
> these functions taken by another function are called "`call-back` function"
>

<br>

### Closure

- It simply means 1) `function inside of a function` and 2) `you can have access to a variable defined inside of a function from the outside` (it sounds awkward now...Don't worry)

<br>

```js
for (let i = 0; i < 10; i++) {
  console.log(i);
}
// Mostly, there is no way to access `i` variable after for-loop is executed outside
```


```js

function func1(x) {

  return function () {
    return x++;
  }
}

const func2 = func1(1);

console.log(func2()); //2
console.log(func2()); //3
console.log(func2()); //4
console.log(func2()); //5

//Here you can access x anytime you want 
```


- So, `closure` : Both `variables` and `functions` that are stored somewhere outside, to enable both of them called even when located outside

```js
function personFactory(initialAge) {
  let age = initialAge;
  return {
    getOlder() {
      age++;
    }
    getAge() {
      return age;
    }
  };
}
```
> Here, where both `let age` and `method getAge` are stored in a memory is called `closer`

### Recursion

- *notice* : This concept is hard. Even I want to go deep inside, I cannot....I don't get this fully. 

- **Recursion**: calling a function on itself. 

- Below is a quick overview of what `Recursion` is 

<br>

```js
function factorialRec(n) {
  return n <= 1 ? 1 : n * factorialRec(n - 1);
}
```

> If you take a closer look at this code, function `factorialRec` has itself inside. 
>
> Whenever `recursion function` is invoked, it creates a variable (or computational space) in what's called `"stack"` in a `memory`.
>
>And after the final or last variable is figured out, then all the spaces created in the stack are gone.


<br>
<br>

## More about Object Property

- Using property accessor accesses `its own property` or `inherited property`

```js
// obj inherits one property called 'interitedProp'
const obj = Object.create({inheritedProp: 'inheritedProp'});

// this time obj directly has a property called 'ownProp'
obj.ownProp = 'ownProp';


// you can see whether an object has a property by 'in' or '.'

console.log(obj.inheritedProp); // inheritedProp
console.log(obj.ownProp); // ownProp
console.log(obj.constructor); // [Function: Object]

console.log('inheritedProp' in obj); // true
console.log('ownProp' in obj); // true
console.log('constructor' in obj); // true
```

<br>

- But with `Object.prototype.hasOwnProperty`, you can see if a property is an object's own property or inherited one.

<br>

```js
const obj = Object.create({inheritedProp: 'inheritedProp'});
obj.ownProp = 'ownProp';

console.log(obj.hasOwnProperty('inheritedProp')); // false
console.log(obj.hasOwnProperty('ownProp')); // true
console.log(obj.hasOwnProperty('constructor')); // false
```



### Data Property and Property Attribute

```js
const obj = {prop: 1};

delete obj.prop; // true
obj.prop; // undefined;
```

> You can always not delete a property with `delete` method
>

<br>

```js
delete Math.PI; // false

Math.PI; // 3.141592653589793
```

> some properties do not work as you expect like this `Math.PI` because whether properties can be deleted or changed heavily depends on `Property Attribute`

<br>

- you can check this `Property Attribute` with `Property Descriptor` method. Let's find what it is.

```js
const obj = {prop: 1};

Object.getOwnPropertyDescriptor(obj, 'prop');
// { value: 1, writable: true, enumerable: true, configurable: true }

Object.getOwnPropertyDescriptor(Math, 'PI');
// { value: 3.141592653589793, writable: false, enumerable: false, configurable: false }
```

> Here, there are 4 parts(or characteristics): `value`, `writable` ,`enumerable` , and `configurable`
>


<br>

### Accessor Property

```js

const obj = {
  get prop() {
    console.log('getter가 호출되었습니다.');
    return this._hidden;
  },
  set prop(arg) {
    console.log('setter가 호출되었습니다.');
    this._hidden = arg;
  }
}

// `set prop` calls 1
obj.prop = 1;

// `get prop` is invoked, and the variable is called on
obj.prop; // 1

Object.getOwnPropertyDescriptors(obj);
// {
//   prop: {
//     get: [Function: get],
//     set: [Function: set],
//     enumerable: true,
//     configurable: true
//   },
//   ...
// }

```

> Those get, set are `Accessor Property`.