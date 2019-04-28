# JavaScript Questions

## Explain Event Delegation

Event delegation - when you attach one event listener to the whole container and then
be able to access each item when it's actually clicked. It's more efficient than
attaching separate event handlers.

General: mechanism of responding to UI events via a single common parent rather than each child, through the magic of event "bubbling" (aka event propagation)

The event is dispatched to its target EventTarget and any event listeners found there are triggered.
Bubbling events will then trigger any additional event listeners found by following the EventTarget's parent chain upward checking for any event listeners registered on each successive EventTarget. This upward propagation will continue up to and including the Document.

Event bubbling provides the foundation for event delegation in browsers. When you bind an event handler to a parent element, handler will be executed whenever any child of the parent has an event that occurs.

Example:

<!-- <ul onclick="alert(event.type + "!")">
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
</ul>

JS:
function toggleDone(event) {
    if (!event.target.matches(`input`)) return
    console.log(event.target)
    // manipulate node here
}
 -->

Less event bindings
Reduced memory

## Explain how this works in JavaScript

### Give an example of one of the ways that working with this has changed in ES6

If you call this in a global scope, it will refer to the window object. In functions and objects, this refers
to variables that are declared globally, but can be refered locally if they are initialised in the function or object.

In ES6, let and const have been introduces as an alternative for var. With let and const, they have block scope which means that this initialised to let or const variable will reference a thing that is inside that block or its parent function/object.

## Explain how prototypal inheritance works

Prototypal inheritance - JavaScript is based on prototype inheritance model. This means that every single JS object has a property called prototype which points ot a different object.

That different object is the object prototype. Our object uses that prototype to inherit properties and methods from another object. Main purpose is to allow multiple instances of an object share common properties.

## What is the difference between a variable that is null, undefined or undeclared?

### How would you go about checking for any of these states?

Undefined - a variable has been declared but has not been assigned a value yet.
Null - can be assigned to a variable to represent no value. It's an assignment value.
Undeclared - variable is not declared, if you try to call undeclared variable, then error is thrown.

To check whether a variable is undefined, null or undeclared, use typeof. E.g. typeof myVariable.

## What is a closure and how/why would you use one?

So, closure can happen in functions and objects. Basically, it's another function in a function. Let's call function 1 outer and function 2 inner. Closure happens when inner function is inside outer function. Inner function can access all the variables and data of outer function, but outer function cannot access all the variables and data of inner function. That's what closure is.

How to use it:

<!-- function outer() {
    var x = 2;
    function inner() {
        x = 4;
    }
    console.log(x) // prints out 4
} -->

Why use closure?

It helps to make private/public scope for functions or objects. Also, variables with the same names are not overriden if one is in the closure.

## What language constructions do you use for iterating over object properties and array items?

To iterate through object properties:

<!-- for (var property in object) {
    if (object.hasOwnProperty(property)) {
        // code goes here...
    }
} -->

To iterate throug array items:
One way is to do :

<!-- for (let i = 0; i < array.length; i++) {
    console.log(array[i]);
} -->

Or

<!-- myArray.forEach(function(s) {
    // do smth with s here...
}) -->

Other way is to (ES6):

<!-- var s, myArray = ["Hello", "World"];

for (s of myArray) {
    // do something with s here
} -->

## Can you describe the main difference between the Array.forEach() loop and Array.map() methods and why you would pick one versus the other?

forEach(): iterates over an array and applies some operations on them and it doesn't return anything.
map(): iterates over a an array, transforms each member of that array, returns another array of the same size with the transformed members.

I would pick forEach when I would like to iterate through an array because it has its own scope therefore it doesnt pollute parent scope.

Map, on the other hand is useful when I would like to transform elements of an array and get completely new array therefore keeping the original array as it is.

## What is a typical use case for anonymous functions?

One of the most typical use for them is to pass anonymous functions as an argument to other functions.
Another popular use case is to create closures with anonymous functions (especially for frameworks)
You can also use anonymous functions as callbacks.

What's the difference between host and native objects?

Host objects - supplied by a certain environment. Not always the same because each environment differsand contains host objects that accomodates execution of ECMAScript.

Native objects - standard built-in objects provided by JavaScript. They sometimes referred as "global objects".

## Explain the difference between: function Person() {}, var person = Person() and var person = new Person()

function Person() {} - it declares a function but doesnt get executed
var person = Person() - it's a function expression therefore contains value reference to a Person function. It returns a value.
var person = new Person() - it's an object that inherits properties and methods from Person class

## Explain the differences o the usage of foo between function foo() {} and var foo = function() {}

So function foo() {} can be declared anywhere in a global scope and you can call it even above it, whereas var foo = function() {} you cannot call it above it because of the hoisting. Hoisting puts functions and variable declarations on top of the global scope. Note that it puts variable declarations but not values. Values are initialised in the same line where they were before run time.

## Can you explainwhat Function.call and Function.apply do? What's the notable difference between the two?

Its used to invoke method with an owner object as an argument. FOr example, if we have a person object with a method fullName inside that returns concatenated first and last name and we also have person one object with first name Mark and last name James then when you call person.fullName.call(person one) it returns concatenated "Mark James".

Difference between .call and .apply is that .call takes arguments as it is explicitly whereas .apply takes arguments as an array

## Explain function.prototype.bind

Bind creates a new function that will have this set to the first parameter passed to bind(). So no mater how the function is called, it will be called with a particular this value. It makes sure that this would be the same as what it was intended.
It's also great for reusing methods.

## What's the difference between feature detection, feature inference and using the UA string?

Feature Detection - a way to determine if a feature exists in certain browsers. An example is a location feature in modern HTML5

<!-- if (navigator.geolocation) {
    // detect user location
} -->

Feature Inference - when you determined that a feature exists and assumed the next web technology feature you are implementing into your app exists as well. It's bad practice to assume so better explicitly specify features you want to detect and plan a fallback action.

UA String (User Agent String) - string text of data that each browser send and can be access via navigator.userAgent. This data contains info of the browser environment you are targeting.

## Explain "hoisting"

Hoisting - functions and variable declarations are moved to the top of the global scope during run time.

## Describe event bubbling

Event bubbling occurs when a user interacts with a nested element and the event propagates up ("bubbles") through all of the ancestor elements. So basically it moves up until it reaches document.

## Describe event capturing

Rarely used. Capturing is when the event goes down to the element instead of going up from the element.

## What's the difference between an attribute and a property?

Attributes are in HTML itself whereas properties are in the DOM. Attributes are very similar to properties, but not quite good. An attribute can only be a string whereas a property can be any kind of data type(number, string, boolean, etc). Properties can be updated wheras attributes if they have default value and are updates will show default value anyway.

# What are the pros and cons of extending built-in JavaScript objects?

Pros:
Looks better and is more intuitive (syntax sugar). It's a type/instance specific function , so it should be specifically bound to that type/instance.

Cons:
When the object is extendes, its behavior is changed. If you use it for your own its completely fine, but if you change the behavior of something that is also used by the other code then there's a risk that the other code could be broken.

Risk of breaking something is very high when adding methods to objects in JavaScript.

## What is the difference between == and === ?

=== checks strictly for the same type and value whereas == checks for the same value and if its not of the same type then converts it to the same type.

## Explain the same-origin policy with regards to JavaScript

Same-origin policy is a critical security mechanism that restricts how a document or script loaded
from one origin can interact wit ha resource from another origin. It helps isolate potentially malicious documents, reduces possible attack vectors. Attack like this is known as Cross Site Scripting attack.

In JavaScript, the "origin" is the same if three things are the same:

- Protocol (HTTP vs HTTPS)
- Domain (yoursite.com vs subdomain.yoursite.com)
- Port (:80 vs :4567)

If all of these match, then JavaScript views the site as the same. If any of them are different, code is marked as potentially malicious and doesn't run.

## Why is it called a Ternary operator, what does the worh "Ternary" indicate?

Ternary comes from the n-ary word setup. Other exampels are unary and binary. All of these are operands. The prefix section of their name lists how many inputs the operand accepts.

Unary accepts one parameter
Binary accepts two parameters
Ternary accepts three parameters.

<!-- var shineSun = is_sunny ? "yes" : "no"; -->

Ternary is an operator that takes 3 arguments and defines a conditional expression. One line shorthand for an if else statement.

In JavaScript, conditional operators can be evaluated to an expression and not just the statement.

## What is strict mode? What are some of the advantages/disadvantages of using it?

Advantages:

- Prevents bad coding
- Eliminates some JS silent erros by changing them to throw errors
- Fixes mistakes that make it difficult for JS engines to perform optimization
- Can be run faster than normal code even if its the same
- Prohibits some syntax likely to be defined in the future versionf of ECMAScript

Disadvantages:

- When mixed strict and normal modes, developer can call some actions that wouldn't work if he is used to normal mode instead of strict

## What arre some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

Advantages:

- Classes. Many transpiled languages gives you classes, inheritance and sometimes interfaces. Under the hood you still have JS prototypical inheritance, but classes are always syntax sugar.
- Types. Most transpiled languages fix this to one degree or another that eliminates bugs. That's why TypeScript exists.
- Features. JS evolves quite slowly in terms of browser implementation. To use ES6, need to transpile to ES5.

Disadvantages:

- Will need external transpilers and bundlers such as webpack, parcel or gulp.
- Smaller amount of developers that are familiar with it.

## What tools and techniques do you use debugging JavaScript code?

- To verify a value I use console.log that lets me to check var, const, let or this values at the time I need.
- Chrome Dev Tools Debugger. Just add debugger statement in the code at the line where I need to inspect values.
- React Dev Tools

When I need to check if a request was sent:

- Chrome Dev Tools Network Tab - look in the call list for the request. Can check status code.

When debugging server side code:

- Node Inspect - like chrome dev tools but for server side. It runs on node 6.6+ and chrome 55+.
  node --inspect path/to/server/file.js

When I need to check a server response

- Postman - lets to pick request method, add creentials and s
  end the request.

When I have a syntax error

- Webpack - throws errors if it can't build. Shows a lot of helpful details.

## Explain the differene between mutable and immutable objects

Mutable objects have fields that can be changed
Immutable objects have no fields that can be changed after the object is created.

### What is an example of an immutable object in JavaScript?

To make an object immutable, Object.freeze() can be used on it. It freezes the object and doesn not let it to be updated after.

### What are the pros and cons of immutability?

Pros:

- Functions are easier to understand
- Code is easeier to parallelize
- Less complicated to think about (No evolution over time)
- No need to make defensive copies of immutable objects when returning or passing to other functins because there are no possibility that this object will be modifies behind the back
- Objects can be cached or the same object can be re-used multiple times

Cons:

- Takes more memory.
- Data structures such as graphs are difficult to build.
- When allocating lots of small objects rather than modifying one big one it can have performance impact.

How can you achieve immutability in your own code?

- To achieve immutability, I would make sure that functions have their own private variables instead of using global ones where possible. On some of the objects I could also use Object.freeze() and if I need to change something in an object I would probably use Object.assign() to create a new copy instead of mutating the original one.

## Explain the difference between synchronous and asynchronous functions

Synchronous functions are those that run in step-by-step process. You can think of it like a set of instructions. Everything is in order and runs smoothly. However, this has some drawbacks. Mainly, for a large instruction it could freeze all the program because it doesn't let other operations to run at the same time.

That's why asynchronous functions come to rescue. Using callbacks and promises (or async/await in ES6) you can make sure that some of the code in your program can run at the same time instead of waiting for the above instruction to finish. It makes programs run better and provides better UX. There's no more waiting for a process to finish.

## What is event loop?

Event Loop is a constantly running process that checks if the call stack is empty. If it's empty, it looks into the Event Queue. If there's something in the Event Queue that is waiting then it's moved to the call stack. If not, nothing happens.

### What is the difference between call stack and task queue?

JavaScript keeps track of what function is currently executing and what function to execute after in a Call Stack. It's an array-like data structure with some limitations. Items can be added to the back and removed only the last element. Functions are added to the stack once they are about to be executed.

Task Queue is a data structure similar to stack. It stores the correct order in which the function should be executed. Receives functioncalls from Event Table and sends it to the Call Stack. It uses Event Loop to send it.

The main difference is that in Call Stack functions gets executed and fetched from Task Queue whereas in Task Queue functions are placed in order ready to be executed in the Call Stack.

## What are the differences between variables created using using let, var or const?

var is the built-in JavaScript keyword for creating variables and you can assign any type of value to it. It also has a global scope.

let and const has block scope which means that outer functions does not have access to them if they are declared in their own block.

Let can be re-assigned, but const is read-only which means once initialised you cannot change its value.

## What are the differences between ES6 class and ES5 function contructors?

1. Main difference is how they are instantiating new objects and what this refers to when creating them
2. Class is a syntax sugar for Constructor functions (defines a new name and append functions to its prototype)
3. When creating using ES6 class this refers to that object whereas in ES5 constructor that's not the case.

## Can you offer a use case for the new arrow => function syntax? How does this new syntax differ from other functions?

1. One of the best use cases in when you need to apply it to items in a list over and over again.

Example, if you have an array of values that you want to transform, array function is perfect.

<!-- const array = ["word", "nextWord"];
const lowerCaseWords = array.map(item => item.toLowerCase()); -->

It's simpler to write, takes less space writing the code therefore takes less memory than regular function declarations.

## What advantages is there for using the arrow syntax for a method in a constructor?

1. Scope safety. It makes sure that you will be using this which is the same as in the constructor
2. Easier to read and write
3. It gives more clarity.

## What is the definition of a higher-order function?

Higher-order functions are functions that operate on other functions by taking them as arguments or returning them.

## Can you give an example of destructuring an object or an array?

Destructuring allows to extract properties from an object or item from an array

If you have an object person

<!-- const person = {
    first: "John",
    last: "Biern"
} -->

and if you need to extract data

<!-- const first = person.first;
const last = person.last; -->

It's an issue because it's repetative.

Using destruction you can do the same thing in less amount of lines

<!-- const { first, last } = person; -->

For arrays, if you have an array of countries

<!--
const countries = ["UK", "Australia", "USA", "China"] -->

Using destructuring to extract some of the data, you would do:

<!-- const [firstCountry, secondCountry, , fourthCountry] = countries;
// returns UK, Australia and China. -->

## Can you give an example of generating a string with ES6 Template Literals?

Template literals are an additional way to create and handle dynamic strings/string templates

To generate a string, you would use:

<!--
let myVar = "I am a variable in the code";
let myString = `Hi, I am a string. I can use other variables from my code and show them to you ${myVar}` -->

You can write code in the \${} inside the `` instead of concatenating strings, etc...

## Can you giv an eample of a curry function and why this syntax offers an advantage?

Currying is operatoin taking a function, which accepts multiple arguments at once, turns that function into another function which takes first argument, turns that into another which takes second argument and so forth until no more arguments are left and returns the last function.

SO an example of currying is:

const sum = x => y => z => x + y + z;

To use it

sum (3)(2)(1) // produces 6

Advantages:

1. Little pieces of code can be configured and reused easily
2. Encourage creation of functions instead of methods.

## What are the benefits of using spread syntax and how is it different from rest syntax?

Spread syntax allows an iterable such as an array or string ot be expanded in places where zero or more arguments or elements are expected.

Let's say we have two arrays:

<!-- const array1 = [1,2,3]
const array2 = [4,5,6,7] -->

Using spread syntax we can combine both of them

<!-- const array3 = [...array1, ...array2]; -->

Benefit of using it is that is significantly faster than for example concat operation. Especially for large operations.

It's different from rest syntax because spread syntax copies all the values of already defined array(s) whereas rest syntax is used when we need to retrieve all REMAINING elements after a destructuring operation.

<!-- const [first, second, ...rest] = array1
// first = 1, second = 2 and third = 3
// ...rest = third = 3 -->

## How can you share code between files?

1. Avoiding globals, you can use module system such as CommonJS or Harmony. Basically you export functions as modules and then import them in other file such as

exporting:

<!-- // mathExpresions.js
module.exports = function() {
    return {
        add: function(num1, num2) {
            return add(num1, num2);
        },
        substract: function(num1, num2) {
            return substract(num1, num2);
        }
    }
} -->

importing using Harmony:

<!-- // newFile.js
var { add, substract } = require("./mathExpressions"); -->

Using modules makes the code more modular and easily reusable while keeping global scope clean.

## Why you might want to create static class members?

Static methods are called on the class itself rather than on its instances.
You might want to use them for such things as utility methods for example functions to create or clone objects.

<!-- class StaticMethodCall {
    static staticMethod() {
        return "Static method has been called";
    }
}

StaticMethodCall.staticMethod(); // "Static method has been called"; -->

To call it from class constructor

<!-- class StaticMethodCall {
    constructor() {
        console.log(StaticMethodCall.staticMethod()) // "static method has been called"

        console.log(this.constructor.staticMethod()) // "static method has been called"
    }

    static staticmethod() {
        return "static method has been called";
    }
} -->
