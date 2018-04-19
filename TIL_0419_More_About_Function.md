# 0419 More About Function

<br>

### The first challenge of today hit me: What could `method`, `function`, `Constructor` be differentiated?

### The second challenge: Both `Arrow` function and `function` syntax(starting with function) are the same? Or are they different?

### What on earth is `this` keyword? or What does it do?

<br>

> Let's dive deep into these two questions!


<br>

- What it's called, `function`, is born from `Function Constructor`(Yes, it is what Array construtor does, creaing array(`[]`))

```js
function func(){}

func instanceof Function;
Object.getPrototypeOf(func) === Function.prototype;

//true, meaning that function is created by Function Construtor
```

- It has the unique characteristic: function is callable! Which means that they can be called on an object as a method.

- It also has two special properties: 1) `length` 2) `name`

```js
function add(x, y) {
  return x + y;
}
console.log(add.length); // 2
console.log(add.name); // add
```

> Here, this function has a name property of `add`
>
> It also has the length property of 2 because it takes 2 parameters

<br>

### Regarding `this` Keyword 

- `this` keyword refers to an object in `Constructor ` or `method`

- However, when `this` is used outside of Constructor or method, it does not direct or show an error. In this case, `this` can refer to a `global object`

<br>

```js
function printThis() {
  console.log(this);
}

printThis(); // Window { ... }
```

> Before ES5, this property of `this` referring to a global object can give numerous errors
>

```js
function Person(name) {
  this.name = name;
}

Person('john');
```

<br>


>Here, if you forget to call or use `new` keyword at the front, `this` refers to a global object of window
>

<br>

- `this` keyword can be volatile! So what makes it stick to or point to the specific one??

- Of course, there are. Use `bind` / `call` and `apply`

- I briefly explain `bind` here

<br>

```js
function printGrade(grade) {
  console.log(`${this.name} scores ${grade}`);
}

const student = {name: 'Mary'};
const printGradeForMary = printGrade.bind(student);

printGradeForMary(100); // `Mary scores 100`
```
<br>

> you can guess what `bind` means as it means in English
>
> in the above example, when `bind` method is called on with the arugment of ('student'), it can set `this.name` equal to a property in a student object

<br>

- Another interesting property in a function: `Argument`

- let's get straight to the example below

```js
function add(x, y) {

  console.log(arguments[0], arguments[1]);
  return x + y;
}

add(1, 2); // 1 2
```

<br>

> Here, even though we don't put arguments of x and y inside of console.log(), `argument[i]` can automatically point to a value of x and y.
>
> `Argument` is an `array-like` and `iterable` object


- But after ES5, when `rest parameters` syntax was introduced, it can do much more than `arguement`

- `rest parameters` is an array, not array-like object

```js
function sum(...ns) {
  let result = 0;
  for (let item of ns) {
    result += item;
  }
  return result;
}

sum(1, 2, 3, 4); // 10
```
<br>

## Constructor, method, function

- I intentionally capitalized the word, "Constructor"

- Here is a simple difference you should know upfront

- All of them is `function`!! but the difference comes in when or where to use.

```js
function Person(name) {
    this.name = name;
} 
//Here comes just a comman function you can see anywhere.


const whatIsConstrutor = new func('Jay'); // this new keyword is what makes a Construtor!


Person.name; // this period ('.') is what makes a method!
```

## Arrow vs function syntax with this keyword

- Both are very simlar, but there is a huge difference behind

- In the following example, I will show the basic syntax for both of them for quick

<br>

```js
function introduce() {
  return `Hello, ${this.fullName}.`;
}

//----------------------------------------------

const introduce = () => {
  return `Hello, ${this.fullName}.`;
}

// Above, I created two, looking very similar but totally different, object

const person1 = {
  fullName: 'JJ',
  introduce
}

const person2 = {
  fullName: 'Will',
  introduce
}

const boundIntroduce = introduce.bind({fullName: 'Jay'});


console.log(person1.introduce());
console.log(person2.introduce());
console.log(boundIntroduce());
```

> When you execute these code twice (at first, with `function introduce` is turned on and the other with `const introduce` is turned on)
>
> it shows two totally different outputs
>

<br>

- The difference between those two is as follows

- `Arrow` function cares about how it is created and once it creates, `this` cannot be changed. It always directs to the outer object

- `function` syntax is more volatile than Arrow. The output of `this` keyword varies where it is called on

- If this concept confuses you, keep in mind how those two are invoked: `as a method`(Object + '.' + function) OR `as just a function`

- One last example would be in the below:

```js

function Person(name) {
  this.name = name;
  
  this.getName = () => {
    return this.name;
  } // when using an arrow function
  
  //compare the above one with the following! Execute the above one turned on and the bottom one
  
  this.getName = function () {
    return this.name;
  }// in case of just a function
}

const mary = new Person('mary');

const getName2 = mary.getName;

console.log(getName2());

```

> The first `arrow` function, as I told you, points to the outer object of(this.getName -> this.name -> Person(name)) in this example
>
> However, `console.log(getName2());` with just a function turned on gives me nothing because with a method this directs to a global object of `window`

