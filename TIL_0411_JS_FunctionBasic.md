# TIL_0410_JS_Function_Basics

## JS Function Basic

```JS
function add(x, y){ - 1
    return ~ -3
}

const result = add(2,3); -2
```

- In the example above, how the computer understands the code is `1` -> `3` -> `2`.

- `1` create `add` function first

- `3` when called the `add` function, `2` return is executed.
<br><br>

#### Return vs Console.log() 

> Feel like those two operations accomplish the same result
>
> However, you save the value in the return value so you can call or use the value anytime
>
> In constrast, "Console.log()" is only writing the argument value on the console.
<br><br>

## Function and Function Scope 
<br>

> In JavaScript, functions are first-class objects, i.e. they are objects and can be manipulated and passed around just like any other object. Specifically, they are Function objects.

>
>
>Scope determines the accessibility (visibility) of variables.
> Let's find out the example below

<br>

```js
for (i = 0; i < 10; i++)  {
    console.log(i); - 1
}
console.log(i); - 2
```
<br>

> 1 and 2 have different values
>
> i value in 1 will be 9
> Whereas, i in 2 will be 10


- More: Scope Chain, Variable Shadowing, Lexical Scoping

* Make sure to remember when you use a function, Variable should be accessed within a function


## What I learned

- still hard to get how it flows of double-forLoop.

- The most important thing is I am having fun now. Every problem that I face feels like challenging me and I am like a captain in the Army. 