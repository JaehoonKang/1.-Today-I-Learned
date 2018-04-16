# 0416_JS_Object_Prototype

## What I thought

- This concept of JS Prototype is quite confusing and nerve-wracking but I am sure to say it is interesting itself. 

- **Object Prototype** : Every **object** inherits **Object Prototype** so any object I create or you do can be an object itself or have many methods such as hasownProperty or toString.

- *Why is it needed?*  Simply put, developers hate repeating so if the very first container(you know, every object, array, or function) is used as many times as you want

- This concept happens only between **TWO** objects. 


```js
{a:1} === {a:1} // output is false
[1,2,3] === [1,2,3] // output is false
```

- in the example above, those two are not the same object or array.

- data in an object or array is stored as a reference(as a location in a memory), it is not saved as a value!


### Prototype Chain

> any object I create -> `Object Prototype` -> `Null`
>
> If one object inherits an object prototype and I try to search a property in the object that I created, 
>
>JS searchs all the way up until it meets Null(if a property does not exist in Object Prototype Chain)

