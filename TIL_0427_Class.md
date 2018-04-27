# TIL_0427_All_About_Class

### Before it begins, I let you know that this concept of **Class** Ain't easy so hold tight and see it coming on your way!


## Today's challenges

    - relationship between class and prototype

    - What is Static method ?

    - Difference between Arrow function syntax and function syntax

    - So what on earth is Class Inheritance?

<br>

### Instance method

```js
class Calculator {
    add(x,y){
        return x + y;
    }
}
```

> instance method of "add" is actully inside of `Calculator.prototype`.
>
> The above one can be shown in a different way
>

```js
function Calculator {
    Calculator.prototype.add = function (x,y){

    }
}
// Both of codes in the above work same
```

### What is Constructor?

- My interpretation of constructor is a function(widely an object) that creates another instance.

- However Class is `neither Function or Object`!!!



### How `getter` or `setter` works?

- The get syntax **binds** an **object** property to a **function** that will be called when that property is **looked up**.

- a setter can be used to execute a function whenever a specified property is attempted to be changed.


```js
class Account {
  constructor() {
    this._balance = 0;
  }
  get balance() {
    return this._balance; //getter
  }
  set balance(newBalance) {
    this._balance = newBalance; //setter
  }
}

const account = new Account();
account.balance = 10000; //setter is called on 
account.balance; // 10000 // getter is called on
```

<br>

## Static method

- If you apply `static keyword` with any method, it is known as static method. A static method belongs to `the class` rather than object of a class. A static method invoked without the need for creating an instance of a class

- What it means is that when several instances share one or more properties, that's where `static` method or instance comes in!

<br>

```js
class Person {
  constructor({name, age}) {
    this.name = name;
    this.age = age;
  }

  // static here defines what static method is
  static sumAge(...people) {
    return people.reduce((acc, person) => acc + person.age, 0);
  }
}

const person1 = new Person({name: '윤아준', age: 19});
const person2 = new Person({name: '신하경', age: 20});

Person.sumAge(person1, person2); // 39
```

<br>

> In this code, `Person` class is a class so it is neither object or function 
>
>but when you put `static` method or instance, you can add or use this `sumAge` with a dot notation.
>

<br>

### Class Field

- Class Field Syntax: in a class scope, using `=`(equal operator), you can bind an object property to a class

```js
class Counter {
  static initial = 0; // static class field
  count = Counter.initial; // class field
  inc() {
    return this.count++;
  }
```

## method inside of a Constructor and outside of it?

```js
class A {
    constructor{
        getA= () => {}
    }
  _getA (){

  } 
}
```

> What is difference of those two?
>
> the first getA is actually inside of each instance that is creating
>
> Whereas, the second _getA exists in `A.prototype`
>
> Constructor's prototype = Instance's prototype!
>

<br>

```js

const obj1 = new A ();
const obj2 = new A ();

obj1._getA() === obj2._getA() //true. those exist inside prototype
obj1.getA() === obj2.getA() // false. those exist sperately in each instance of obj1 and obj2

```


### `This` key word in Arrow VS function syntax

- **Conclusion**: when using a function(or method) in another method(map, reduce, or filter), make sure to use `Arrow` function!!

- because when arrow function is created, what `this` keyword indicates is set and never changes later

- But `this` keyword in *function* syntax varies when the function is called on. 

<br>


## Class Inheritance


```js
class Parent {
  static staticProp = 'staticProp';
  static staticMethod() {
    return 'I\'m a static method.';
  }
  instanceProp = 'instanceProp';
  instanceMethod() {
    return 'I\'m a instance method.';
  }
}

class Child extends Parent {} //there is nothing inside Child class!!

console.log(Child.staticProp); // staticProp
console.log(Child.staticMethod()); // I'm a static method.

const c = new Child();
console.log(c.instanceProp); // instanceProp
console.log(c.instanceMethod()); // I'm a instance method.
```


![Class Inheritance](class-inheritance-prototype-chain.svg)

