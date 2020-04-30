# A Really Quick Guide to Programming with JavaScript
I'm not going to teach you how to program. This is just a quick cheatsheet to get you up to speed if you're already familiar with programming with another language. If you haven't programmed before, this might familiarize yourself with the language.

You don't have to *memorize* all this, obviously. You also don't really have to know everything to understand the rest of the guide.

To try out the codes yourself, open the Developer Tools on your browser (usually by pressing F12) and open the **console**. In modern browsers, you can just copy and paste a whole block of codes instead of having to put the line in one by one. I highly suggest doing this and experimenting yourself if you're confused.

## Most Basic
JavaScript has five data types: string, number, boolean, array, object. [This page](https://www.w3schools.com/js/js_datatypes.asp) has neat explanations of all of them)

`console.log()` will print text to the console.

`var x = 10` create a variable `x` with the value `10`, a number.

`var x = "Ten"` create a variable `x` with the value `"Ten"`, a string. You can also use single quote (`'`) instead of double quote (`"`).

Alternatively, you can use `const` instead of `var`, if it's a constant (i.e., it doesn't change). You can also use `let` instead of `var`, which will be scoped to the current block (don't worry if you don't get that yet). To avoid errors, it's usually recommended to use `let` over `var`.  

`x = 1 + 1` change the value of the variable `x` to `1 + 1`, which is `2`. **`x` should already be defined!**

Strings can be combined using `+`. So `"Hello " + " World"` will result in `Hello World`.

```js
var name = "World"
var greeting = "Hello " + name
console.log(greeting)
```
The above code will print out "Hello World".

In the old days we have to end every line with a semicolon (`;`). Modern JavaScript don't require that anymore, but some people might still insist on using them. Do whatever you like, as long as it's consistent.

## Logic
The notation for **AND** is `&&`. The notation for **OR** is `||`.

The two booleans are `true` and `false`.

You can reverse a boolean with `!`. So: `!false` is `true`.

* `true && true` is true. 
* `true && false` is false.
* `false && false` is false.
* `true || true` is true.
* `true || false` is true.
* `false || false` is false.

**If** works like this:

```js
if (thing) {
	// if thing then do what?
} else if (otherThing) {
	// if other thing then do what?
} else {
	// if neither of those are true, what to do?
}
```

For example:

```js
const likesIceCream = true
const likesStrawberry = false
const likesChocolate = false

if (likesIceCream && likesStrawberry) {
	giveStrawberryIceCream()
}
else if (likesIceCream || likesChocolate) {
	giveChocolateIceCream()
}
else {
	giveNothing()
}
// they'll get chocolate ice cream
```

If you don't need them, you don't have to add `else` and `else if`.

You can also use `switch` when dealing with just one variable.

```js
var favFood = "fruits"

switch(favFood) {
	case 'ice cream':
		giveIceCream()
		break
	case 'beef':
		giveSteak()
		break
	case 'fish':
		giveTuna()
		break
	default:
		dontHaveWhatYouWant()
}
//result: sorry, friend. We don't have what you want
```

To check if two data are equal, use `===`.

```js
var favFood = 'beef' 
if (favFood === 'fish') {
	giveFish()
}
// result: fish won't be given
```

To check if two data are not equal, use `!==`. To check if a number is bigger, use `>`, or if you also want to return true if it's equal, use `>=`. Likewise but for checking if it's smaller, use `<` or `<=`.

[This page](https://www.w3schools.com/js/js_comparisons.asp) has a table containing these comparison operators.

## Arrays and Objects
An array is a like a list of data. Order in an array is important.

`[]` is an empty array.

For example, `['cat', 'dog', 'lizard']` is an array containing three string data. You can freely mix different data types in an array, e.g. `['cat', 42, false]`

You can access an element in an array like this: ** *arrayname*[*order*]**. Order starts from **0**. With
`var animals = ['cat', 'dog', 'lizard']` then `animals[1]` will yield `'dog'`. 

Use ** *arrayname*.length** to see how many elements is in that array. Use ** *arrayname*.push(*newelement*)** to add a new element to an array.

The easy way to think about is **object** is that it's like an array, but each element have a **key**.

```js
var person = {
	name: "Ann",
	age: 20,
	favFood : "fish",
	allergy: null
}
``` 

You can access an element in an object like this: ** *object*['*key*']**. With the above's `person` object, `person['age']` will yield `20`. Note that the key is always a string. Another way to access it is through ** *object*.*key* **. So with the above object, `person.name` will yield `"Ann"`.

## Loops

The basic structure of a loop is **while (*condition*) { *thing to loop* }**. Here's an example:

```js
const goodScore = 80
var score = 60

while (score < goodScore) {
	console.log("Studying...")
	score = score + 10
}

console.log("Done!")
```

The result of that is:

```text
Studying...
Studying...
Done!
```

Another loop you can use is **for**. 

To loop through an array, the structure is **for (*x* of *array*) { *things to loop* }**. *x* will be the element. For example:

```js
const peopleNames = ["Seth", "Franz", "Forde", "Kyle"]

for (name of peopleNames) {
	console.log(name)
}
```

The result will be

```text
Seth
Franz
Forde
Kyle
```

You can also loop through an object with **for (*x* in *object*) { *things to loop* }**. *x* will be the key. For example:

```js
var person = {
	name: "Ann",
	age: 20,
	favFood : "fish",
	allergy: null
}

for (attribute in person) {
	console.log("My " + attribute + " is " + person[attribute])
}
```

The result will be 

```text
My name is Ann
My age is 20
My favFood is fish
My allergy is null
```

There is also another **for** loop that's more common, but in my opinion not very useful for beginners. You can read up on that [here](https://www.w3schools.com/js/js_loop_for.asp). 

## Functions
The simplest way to think of a **function** is that it's a set of programming codes that can be repeated over and over again without having to type the entire thing again.

We sometimes say we **run** a function, and sometimes we say we **call** a function. They're basically the same thing, don't worry about it.

A **function** can have a **argument**, which is like a variable that's handed to it when we call it. A function can have as many arguments as it likes, including none.

One way to make a function is **function *name*(*argument*) { *add code here* }**. For example:

```js
function sayHello(recipient) {
	console.log("Hello " + recipient)
}
sayHello("World")
```

This will result in `Hello World` printed to your console.

If you create a function with an argument, you must always give those arguments when you call it. You can also create a function without any argument. Just leave the brackets (`()`) empty.

A function can also be without a name. We call these **anonymous** functions. There are two ways to make an anonymous function. This is the long version: **function(*arguments*) { *code* }**. This is the newer, shorter version: **(*arguments*) => { *code* }**. The second version is often called the **arrow** syntax.

Not a lot of programming language use anonymous function. You can consider this a JavaScript thing.

Here's an example of how an anonymous function can be used:

```js
function doThingToFood(food, thingToDo) {
	thingToDo(food)
}

doThingToFood("meat", (food) => { 
	console.log(food + " is being cooked...")
})
```

This should result `meat is being cooked...` printed to your console.

It's a bit of a roundabout way to do it, but this kind of thing is pretty common in JavaScript.

You can treat an anonymous function like you treat any other data types. You can give it a name the same way you create a variable. 

```js
var doThing = () => { 
	// insert function here
}
```

A function can **return** something when it is called. Here's an example:

```js
function combineName(firstName, lastName) {
	return firstName + " " + lastName
}

var name = "Ferdinand"
var family = "von Aegir"

console.log("I am " + combineName(name, family) + ".")
```

A function can also **return** nothing. This is used when you want to end it earlier.

## Shenanigans
**If** also has a more compact version: ** *condition* ? *a* : *b* **. If the condition is met, the data is *a*, otherwise it's *b*. 

```js
var likesChocolate = true
var milkshakeFlavour = likesChocolate ? 'chocolate' : 'vanilla'

//milkshakeFlavour will be `chocolate`
```  

Another useful shorthand is how the OR notation (**||**) can be used.

```js
var start = 19
var count = start || 0

//count will be 19
```

With ** *a* || *b* **, if *a* is falsy (i.e. if it's false, 0, or undefined), the data will be *b*. Otherwise it's *a*.

# That's all here
There's plenty more to JavaScript than all of the above, but this should be good enough for anyone starting with the language. 

If you're still confused even after reading this guide and experimenting by yourself, Google is your friend! Alternatively, you can [contact me](guestbook.md)!