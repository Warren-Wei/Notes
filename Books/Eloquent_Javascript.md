# Notes for the book <Eloquent JavaScript (3rd Edition)>

- Author: Marijn Haverbeke
- Vertion: 3rd Edition 2018

## Ch. 1 Values, Types, and Operators

### 1.1 Values

### 1.2 Numbers

- Infinity & -Infinity. Don't put too much trust in infinity-based computation.
- NaN stands for "Not a Number", event though it is a value of the number type. You;ll get this result when you, for example, try to calculate 0 / 0 (zero divided by zero), Infinity - Infinity, or any number of other numeric operations that don't yield a meaningful result

### 1.3 Strings

### 1.4 Unary operators

### 1.5 Boolean Values

### 1.6 Empty values

- There are two special values, written null and undefined, that are used to denote the absence of a meaningful value. They are themselves values, but they carry no information.

### 1.7 Automatic type conversion

- When an operator is applied to the "wrong" type of value, JavaScript will quietly convert that value to the type it need, using a set of rules that often aren't what you want or expect. This is called *type coercion*.

### 1.8 Summary

## Ch. 2 Program Structure

### 2.1 Expressions and statements

### 2.2 Bindings

### 2.3 Binding names

### 2.4 The environment

### 2.5 Functions

### 2.6 The console.log function

### 2.7 Return values

### 2.8 Control flow

### 2.9 Conditional execution

### 2.10 while and do loops

### 2.11 Indenting Code

### 2.12 for loops

### 2.13 Breaking Out of a Loop

### 2.14 Updating bindings succinctly

### 2.15 Dispatching on a value with swich

### 2.16 Capitalization

### 2.17 Comments

### 2.18 Summary

### 2.19 Exercises

## Ch. 3 Functions

### 3.1 Defining a function

### 3.2 Bindings and scopes

### 3.3 Functions as values

### 3.4 Declaration notation

### 3.5 Arrow functions

### 3.6 The call stack

### 3.7 Optional Arguments

- JavaScript is extremely broad-minded about the number of arguments you pass to a function. If you pass too many, the extra ones are ignored. If you pass too few, the missing parameters get assigned the value `undefined`

### 3.8 Closure

### 3.9 Recursion

### 3.10 Growing functions

### 3.11 Functions and side effects

### 3.12 Summary

### 3.13 Exercises

## Ch. 4 Data Structures: Objects and Arrarys

### 4.1 The weresquirrel

### 4.2 Data sets

### 4.3 Properties

### 4.4 Methods

### 4.5 Objects

### 4.6 Mutability

### 4.7 The lycanthrope's log

### 4.8 Computing correlation

### 4.9 Array loops

### 4.10 The final analysis

### 4.11 Further arrayology

### 4.12 Strings and their properties

### 4.13 Rest parameters

### 4.14 The Math object

- `Math.max()`
- `Math.min()`
- `Math.sqrt()`
- `Math.random()` returns a new pseudorandom number between zero (inclusive) and one (exclusive)

### 4.15 Destructuring

### 4.16 JSON

- All property names have to be surrounded by double quotes, and only simple data expressions are allowed — no function calls, bindings, or anything that involves actual computation. Comments are not allowed in JSON.

### 4.17 Summary

- Most values in JavaScript have properties, the exceptions being `null` and `undefined`. Properties are accessed using `value.prop` or `value["prop"]`.

### 4.18 Exercises

## Ch. 5 Higher-Order Functions

### 5.1 Abstraction

### 5.2 Abstrating repetition

### 5.3 Higher-order functions

- Functions that operate on other functions, either by taking them as arguments or by returning them, are called *higher-order functions.* In simple words, A Higher-Order funciton is a function that receives a function as an argument or returns the function as output **
- Higher-order functions allow us to abstract over actions, not just values
- A JavaScript Callback Function is a function that is passed as a parameter to another JavaScript function, and the callback function is run inside of the function it was passed into. JavaScript Callback Functions can be used synchronously or asynchronously.

### 5.4 Script data set

### 5.5 Filtering arrays

### 5.6 Transforming with map

### 5.7 Summarizing with reduce

### 5.8 Composability

### 5.9 Strings and character codes

### 5.10 Recognizing text

### 5.11 Summary

- Arrays provide a number of useful higher-order methods
    - use `forEach` to loop over the elements in an array
    - use `filter` method returns a new array containing only the elements that pass the predicate function
    - transforming an array by putting each element through a function is done with `map`
    - use `reduce`to combine all the elements in an array into a single value
    - use `some` method tests whether any element matches a given predicate function
    - use `findIndex` finds the position of the first element that matches a predicate

### 5.12 Exercises

## Ch. 6 The Secret Life of Objects

### 6.1 Encapsulation

- The core idea in object-oriented programming is to divide programs into smaller pieces and make each piece responsible for managing its own state. Different pieces of such a program interact with each other through *interfaces*, limited sets of fcuntions or bindings that provide useful functionality at a more abstract level, hiding their precise implementation. Such program pieces are modeled using objects. Their interface consistes of a specific set of methods and properties. Properties that are part of the interface are called *public*. The others, which outside code should not be touching, are called *private*.
- It is common to put an underscore (_) character at the start of property names to indicate that those properties are private
- Separating interface from implementation is a great idea. It is usually called *encapsulation*

### 6.2 Methods

- Methods are nothing more than properties that hold function values
- Usually a method needs to do something with the object it was called on. When a function is called as a method — looked up as a property and immediately called, as in `object.method()` — the binding called `this` in its body automatically points at the object that it was called on
- You can think of this as an extra parameter that is passed in a different way. If you want to pass it explicitly, you can use a function's `call` method, which takes the `this` value as its first argument and treats further arguments as normal parameters
- Since each function has its own `this` binding, whose value depends on the way it is called, you cannot refer to the `this` of the wrapping scope in a regular function defined with the `function` keyword
- Arrow functions are different — they do not bind their own `this` but can see the `this` binding of the scope around them

### 6.3 Prototypes

- In addition to their set of properties, most objects also have a *prototype*. A prototype is another object that is used as a fallback source of properties. When an object gets a request for a property that it does not have, its prototype will be searched for the property, then the prototype's prototype, and so on

### 6.4 Classes

- Constructors (all functions, in fact) automatically get a property named `prototype`, which by default holds a plain, empty object that derives from `Object.prototype`
- By convention, the names of constructors are capitalized so that they can easily be distinguished from other functions
- It is important to understand the distinction between the way a prototype is associated with a constructor (through its `prototype` property) and the way objects have a prototype (which can be found with `Object.getPrototypeOf`). The actual prototype of a constructor is `Function.prototype` since constructors are functions. Its prototype *property* holds the prototype used for instances created through it.

### 6.5 Class notation

- The `class` keyword starts a class declaration, which allows us to define a constructor and a set of methods all in a single place. Any number of methods may be written inside the declaration's braces. The one named `constructor` is treated specially. It provides the actual constructor function, which will be bound to the name Rabbit. The others are packaged into that constructor's prototype.

### 6.6 Overriding derived properties

### 6.7 Maps

- A *map* (noun) is a data structure that associates values (the keys) with other values
- `Object.keys` returns only an object's *own* keys, not those in the prototype. As an alternative to the `in` operator, you can use the `hasOwnProperty` method, which ignores the object's prototype.

### 6.8 Polymorphism

- When a piece of code is written to work with objects that have a certain interface — in this case, a `toString` method — any kind of object that happens to support this interface can be pugged into the code, and it will just work. This technique is called *polymorphism*

### 6.9 Symbols

- Symbols are values created with the `Symbol` function. Unlike strings, newly created symbols are unique — you cannot create the same symbol twice
- Being both unique and usable as property names makes symbols suitable for defining interfaces that can peacefully live alongside other properties, no matter what their names are

    ```jsx
    const toStringSymbol = Symbol("toString");
    Array.prototype[toStringSymbol] = function() {
    	return `${this.length} cm of blue yarn`;
    };
    console.log([1, 2].toString());
    console.log([1, 2][toStringSymbol]());
    ```

### 6.10 The iterator interface

### 6.11 Getters, setters, and statics

### 6.12 Inheritance

### 6.13 The instanceof operator

### 6.14 Summary

### 6.15 Exercises

## Ch. 7 Project: A Robot

### 7.1 Meadowfield

### 7.2 The task

### 7.3 Persistent data

### 7.4 Simulation

### 7.5 The mail truck's route

### 7.6 Pathfinding

### 7.7 Exercises

## Ch. 8 Bugs and Errors

### 8.1 Language

### 8.2 Strict mode

### 8.3 Types

### 8.4 Testing

### 8.5 Debugging

### 8.6 Error propagation

### 8.7 Cleaning up after exceptions

### 8.8 Selective catching

### 8.9 Assertions

### 8.10 Summary

### 8.11 Exercises

## Ch. 9 Regular Expressions

### 9.1 Creating a regular expression

### 9.2 Testing for matches

### 9.3 Sets of characters

### 9.4 Repeating parts of a pattern

### 9.5 Grouping subexpressions

### 9.6 Matches and groups

### 9.7 The Date class

### 9.8 Word and string boundaries

### 9.9 Choice patterns

### 9.10 The mechanics of matching

### 9.11 Backtracking

### 9.12 The replace method

### 9.13 Greed

### 9.14 Dynamically creating RegExp objects

### 9.15 The search method

### 9.16 Thel lastIndex property

### 9.17 Parsing an INI file

### 9.18 International characters

### 9.19 Summary

### 9.20 Exercises

## Ch. 10 Modules

### 10.1 Modules

### 10.2 Packages

### 10.3 Improvised modules

### 10.4 Evaluating data as code

### 10.5 CommonJS

### 10.6 ECMAScript modules

### 10.7 Building and bundling

### 10.8 Module design

### 10.9 Summary

### 10.10 Exercises

## Ch. 11 Asynchronous Programming

### 11.1 Asynchronicity

### 11.2 Crow tech

### 11.3 Callbacks

### 11.4 Promises

### 11.5 Failure

### 11.6 Networks are hard

### 11.7 Collections of promises

### 11.8 Network flooding

### 11.9 Message routing

### 11.10 Async functions

### 11.11 Generators

### 11.12 The event loop

### 11.13 Asynchronous bugs

### 11.14 Summary

### 11.15 Exercises

## Ch. 12 Project: A Programming Language

### 12.1 Parsing

### 12.2 The evaluator

### 12.3 Special forms

### 12.4 The environment

### 12.5 Functions

### 12.6 Compilation

### 12.7 Cheating

### 12.8 Exercises

## Ch. 13 JavaScript and the Browser

### 13.1 Networks and the Internet

### 13.2 The Web

### 13.3 HTML

### 13.4 HTML and JavaScript

### 13.5 In the sandbox

### 13.6 Compatibility and the browser wars

## Ch. 14 The Document Object Model

### 14.1 Document structure

### 14.2 Trees

### 14.3 The standard

### 14.4 Moving through the tree

### 14.5 Finding elements

### 14.6 Changing the document

### 14.7 Creating nodes

### 14.8 Attributes

### 14.9 Layout

### 14.10 Styling

### 14.11 Cascading styles

### 14.12 Query selectors

### 14.13 Positioning and animating

### 14.14 Summary

### 14.15 Exercises

## Ch. 15 Handling Events

### 15.1 Event handlers

### 15.2 Events and DOM nodes

### 15.3 Event objects

### 15.4 Propagation

### 15.5 Default actions

### 15.6 Key events

### 15.7 Pointer events

### 15.8 Scroll events

### 15.9 Focus events

### 15.10 Load event

### 15.11 Events and the event loop

### 15.12 Timers

### 15.13 Debouncing

### 15.14 Summary

### 15.15 Exercises

## Ch. 16 Project: A Platform Game

### 16.1 the game

### 16.2 The technology

### 16.3 Levels

### 16.4 Reading a level

### 16.5 Actors

### 16.6 Encapsulation as a burden

### 16.7 Drawing

### 16.8 Motion and collision

### 16.9 Actor updates

### 16.10 Tracking keys

### 16.11 Running the game

### 16.12 Exercises

## Ch. 17 Drawing on Canvas

### 17.1 SVG

### 17.2 The canvas element

### 17.3 Lines and surfaces

### 17.4 Paths

### 17.5 Curves

### 17.6 Drawing a pie chart

### 17.7 Text

### 17.8 Images

### 17.9 Transformation

### 17.10 Storing and clearing transformations

### 17.11 Back to the game

### 17.12 Choosing a graphics interface

### 17.13 Summary

### 17.14 Exercises

## Ch. 18 HTTP and Forms

### 18.1 The protocol

### 18.2 Browsers and HTTP

### 18.3 Fetch

### 18.4 HTTP sandboxing

### 18.5 Appreciating HTTP

### 18.6 Security and HTTPS

### 18.7 Form fields

### 18.8 Focus

### 18.9 Disabled fields

### 18.10 The form as a whole

### 18.11 Text fields

### 18.12 Checkboxes and radio buttons

### 18.13 Select fields

### 18.14 File fields

### 18.15 Storing data client-side

### 18.16 Summary

### 18.17 Exercises

## Ch. 19 Project: A Pixel Art Editor

### 19.1 Components

### 19.2 The state

### 19.3 DOM building

### 19.4 The canvas

### 19.5 The application

### 19.6 Drawing tools

### 19.7 Saving and loading

### 19.8 Undo history

### 19.9 Let's draw

### 19.10 Why is this so hard?

### 19.11 Exercises

## Ch. 20 Node.js

### 20.1 Background

### 20.2 The node command

### 20.3 Modules

### 20.4 Installing with NPM

### 20.5 The file system module

### 20.6 The HTTP module

### 20.7 Streams

### 20.8 A file server

### 20.9 Summary

### 20.10 Exercises

## Ch. 21 Project: Skill-Sharing Website

### 21.1 Design

### 21.2 Long polling

### 21.3 HTTP interface

### 21.4 The server

### 21.5 The client

### 21.6 Exercises