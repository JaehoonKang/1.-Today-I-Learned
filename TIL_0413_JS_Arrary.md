# 0413_JS_Array

### Reminder 

- Object: Data Stucture & Pair of 'key - value'

- Braket Notation: when a variable is possibly changing later, that's where Bracket Notation comes in

- Key value in a property should be `string`(not number or function)

<br>

## Object Oriented Programming

- Think in a way that relevant data(or attributes) should be combined together => `this` keyword comes in


## Array

- JavaScript **arrays** are used to store multiple values in a single variable.

- access each value in an array with `index` 


### Array Method

* Slice : if applied, not changing the original value

* reverse : it changed the original value

* splice : same as reverse method

* slice : when copying an array


**Remember**


```JS
arr = [{a:1}, {b:2}]

newArr = arr.slice()

newArr => [{a:1}, {b:2}]
```

> Here, in the example above, when changing either of objects in `arr`, it can affect the same object in `newArr`!

<br>

### Map vs forEach

> `map` creates an Array, but `forEach` just traverses!

<br>

## What I thought

- Mostly, I learned a whole new concept of `Array`

- Each and every method, it works in a different way so make sure when I make heavy uses of a method!


## Problem of Today

```js
문제 15
String.prototype.split과 똑같이 동작하는 함수를 작성하세요.

예:

split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```



