# TIL_0417_More_About_Value

## Array

- arrary is an instance resulting from creating `Array` constructor.

- `array-like objects` works as an array even though it actually is not an array: `string`,`number`

> The following example describes how it works
>

```js
'abcde'[1] or 'adsdfas'[2]
//even though both are strings, string is an array-like object so index can be applied here
```
<br><br>
## let & const VS var

- `let and const` have block-level scope, whereas `var` has function-level scope

```js
function func(){
    for(){
        if (){
            var // var is created here

            const // const and let is created here 
            let
        }
    }
}
```

<br>

> The important note here is that as I described above, var (function-level scope) influences over `for` loop or `if` statement until it meets `function` scope. 
>
>Here, the way `var` works is called `Hosting`
>
>However, `let` or `const` is block-level(it simply means `{}`) scope so it cannot impact over its `if` scope

### Global Object

```js
let foo = 1;

window.foo;
```

> If a global object is defined, 
>
>the global object can provide or share all global variables and functions such as `alert`,`prompt`, and `fetch`.

## Reference

- This topic covers or gives you or me a better understading of `object` and `value`

- Simply put, variable is assigned either with **Reference** or **Primitive** value

- In other words, a variable can **hold** one of two value types: `primitive values` or `reference values`

- **Reference values** are objects stored in memory. And then it says nothing about how Primitive value is stored

<br>

>Primitive values are data that are stored on the stack.
>
>Primitive value is stored directly in the location that the variable accesses.
>
>Reference values are objects that are stored in the 
heap.
>
>Reference value stored in the variable location is a pointer to a location in memory where the object is stored.
>
>Primitive types include Undefined, Null, Boolean, Number, or String.
>

> The following two codes work totally different

<br>

```js
const obj = {};


function addProp(o) {
  o.prop = 1;
}

addProp(obj);

console.log(obj.prop);
```

> This example describes how reference value works by an object
>
> Briefly, a property in `obj` is {prop:1}.
>
> because Javascript calls by value, not a variable itself.

```js
let a  = 1;
function reassign(x){
  x = 2;
}
reassign(a);
console.log(a);
```

>This one shows what primitive value is stored in a memory
>
> However, a value of `a` is still 1, not 2
>
> The reason is that `x`,not a, becomes 1 -> 2.
>

<br>

- So when comparing `two (or more) objects`, keep in mind that you are now comparing them by reference or by value

- Also, there are two memories in a computer: **Stack** and **heap**

<br>

## Immutability

- There is never a single way you can change the value of **Primitive** type(you can think it as not an object)

```js
let x = 1;
x = 2;
```

>
> you can assume that `x` value is changed but it is not correct.
>
> Javascript just creates another new value of 2
>
> However, an object can be changed because it is stored in a `heap`

## Wrapper Object

- Here is a question: `something.~` can be executed when `something` is an object.

- But how can string, number, even blooen can be executed like `'sagsdf'`.toUpperCase();

- That's because string, number or blooean can be changed for a short time as an object by this **Wrapper Object**

- For example, in 'hello'.toUpperCase();, this `toUpperCase` exists in `String.prototype` as its property

- `String` is an object constuctor so it takes any string and turns it into an object for a short period of time.









