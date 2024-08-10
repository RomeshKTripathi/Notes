# Fundamentals
## _use strict_

`use strict` is used to strictly run modern JavaScript on browsers
```js
"use strict";

// this code works the modern way
...
```
> [!NOTE]
> _"use strict"_ should always be on top of file.
> there is not any way to cansel _"use strict"_.
> In browser console use multiline code for _"use strict"_

> [!TIP]
> If you aren't useing OOP in JS then you should use _"use strict"_ to run latest features, but if you are using OOP then you can omit it.

## Data Types in JavaScript.
```
There are 8 data types:

number for both floating-point and integer numbers,
bigint for integer numbers of arbitrary length,
string for strings,
boolean for logical values: true/false,
null – a type with a single value null, meaning “empty” or “does not exist”,
undefined – a type with a single value undefined, meaning “not assigned”,
object and symbol – for complex data structures and unique identifiers, we haven’t learnt them yet.
```
### Number
The number type represents both integer and floating point numbers.
```js
let n = 123;
n = 123.45;
Infinity //  is a number greater than any value in JS
```
### BigInt
In JS _Number_ type can't safely represent integer values larger than `2^53 - 1` or less `-2^53` there'll be a precision error.

```js
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```
### Strings
```js
const str = "this is string";
const str1 = 'this is string';
const str2 = `this is string `;
```

### Boolean
```js
const result = true;
const isLoaded = false;
```

### null
Just a special value which represents "noting", "empty" or "value unknkown".
```js
const value = null;
```

### undefined
The meaning of undefined is "value is not assigned"
```js
let age;
// age is undefined.
let name = undefined; // explicitly undefined.
```

### Objects & Symbols
- `Object` is special type.
- all other types are called _primitives_ because they contains only single thing.
  ---- read Objects below-----

### `typeof` Operator

the `typeof` operator returns the _type_ of operand
```js
let value = 123;
console.log(typeof value) // Number`
```

## Interaction via `alert`, `prompt` and `console`
### `alert()`
- To show some import message to visitor
```js
alert("Hello user");
```


### `prompt()`
- function prompt accepts two arguments
```js
result = prompt ( title, [default]);
// title: the text shown to visitor
// default: an optional second paramenter, the initial value for the input field.
```

### `confirm()`
The function confirm shows a model window with a question and two buttons: OK and Cancel. The result is _true_ if OK is pressed and _false_ otherwise.
```js
let isValid = confirm("Is your name valid");
```

## Type Conversion

```
String -> Number -> String
Boolean -> String -> Boolean
```

## Operators
### Unary & Binary Operators
```
Addition +,
Subtraction -,
Multiplication *,
Division /,
Remainder %,
Exponentiation **.
```

### Comma
The comma operator , is one of the rarest and most unusual operators. Sometimes, it’s used to write shorter code, so we need to know it in order to understand what’s going on.

The comma operator allows us to evaluate several expressions, dividing them with a comma ,. Each of them is evaluated but only the result of the last one is returned.
```js
let a = (1 + 2, 3 + 4);
alert( a ); // 7 (the result of 3 + 4)
```

### Comparision Operators
```
equal with value, ==
equal with value and TYPE,  === (Strict equal)
<, > =< , >=,

```
```js
alert(null === undefined); // false
alert(null == undefined); // true
```
### Conditional Operator `?`
```js
let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );
```
### Logical Operators
```
||, && , ^
```
> `??` Nullish Coalescing return first valid value
```js
let value = undefined ?? 23; // 23
let value1 = true ?? 9;  // true
let value2 = false ?? 67; // false
let value3 = null ?? 45; // 45

```

## Basic Terminologies

### loops `while`, `for`
### The `switch` statement

### Functions
```js
function sayHi(){
  alert("hi");
}
```
### Function Expression
Storing function in variable.
```js
let sayHi = function(){
  alert("HI");
}
```

### Arrow Functions.
Single line Arrow function
```js
let func = (arg1, arg2, ..., argN) => expression;
```

Multiline arrow function
```js
let func = (arg1, arg2, ..., argN) =>{
 // Your multiline code here.
return value;
}
```

## Code Structure
That’s called “automatic semicolon insertion”. Sometimes it doesn’t work, for instance:
```js
alert("There will be an error after this message")
[1, 2].forEach(alert)
```
> [!TIP] Most codestyle guedes agree that we should put a semicolon after eact statement.

> [!NOTE] to fully enable all features of modern JavaScript, we should start scripts with `"use strict"`

```js
"use strict"
// code
```

### Variables `let`, `const`, `var`
```
let
const (constant, can't be changed
var (old style)
```

## Polyfills and transpilers
As a Programmer, how to make our modern code work on older engines that don’t understand recent features yet?

There are two tools for that:
1. Transpilers.
2. Polyfills.

### Transpilers
A Transpiler is a special piece of software that translates source code to another source code.It can parse _("Read and Understand")_ modern code and rewrite it using older syntax constructs, so that it'll also work in outdated engines.

```
E.g. Javascript before year 2020 didn't have the "nullish coalescing operator" ??. So if a visitor uses an outdated browser, it may fail to understand the code like height = height ?? 100.

A transpiler would analyze our code and rewrite height ? 100 into:
(height !== undefined && height !== null ) ? height : 100
```

```js
// before running the transpiler
height = height ?? 100;

// after running the transpiler
height = (height !== undefined && height !== null) ? height : 100;
```

### Polyfills
New language features may include not only syntax constructs and operators, but also built-in functions.
For example  `Math.trunc(n)` is a function that _cutts off_ the decimal part of a number, e.b Math.trunc(1.23) returns 1.
In some (very outdated) JavaScript Engines, there's no `Math.trunc()` so such code will fail . 
As we're talkin about new function, not syntax changes, there's no need to transpile anything here. We just need to declare the missing function.
A script  that updates/adds new functions is called "polyfill". It "fills in" the gap and adds missing implementations.
For this particular case, the polyfill for `Math.trunc()` is a script that implements it, like this:

```js
if (!Math.trunc) { // if no such function
  // implement it
  Math.trunc = function(number) {
    // Math.ceil and Math.floor exist even in ancient JavaScript engines
    return number < 0 ? Math.ceil(number) : Math.floor(number);
  };
}
```


# Objects: The basics
objects are used to store keyed collections of various data and more complex entities. In JavaScript, objects penetrate almost every aspect of the language. So we must understand them first before going in-depth anywhere else.

We can imagine an object as a cabinet with signed files. Every piece of data is stored in its file by the key. It’s easy to find a file by its name or add/remove a file.

An empty object (“empty cabinet”) can be created using one of two syntaxes:
```js
let user = new Object(); // "Object constructor" syntax
let user = {}; // "Object literal" Syntax.
```

We can immediately put some properties into `{...}` as _"key:value"_ pairs:
```js
let user = {
  name: "John",
  age:30,
}
```

Property values of object are accessible by `dot: . ` notattion
```js
alert(user.name); // John
alert(user.age); //30
```

The value can be of any type. Let's add a boolean value
```js
user.isAdmin = true;
```

> [!TIP]
> to remove a property you can use `delete` operator

```js
delete user.age;
```

> We can also multiword property names, but then they must be quoted:
```js
let user = {
name:"Sachin",
age:24,
"likes Coding":true,
// comma on the last propery can be avoided, it is called trailing or hanging comma
}
```
> [!NOTE]
> To access _multiword properties_ we can't use dot `.` operator
> we have to use _Square Brackets_
```js
user['likes Coding'] = true;

alert(user['likes Coding']);

delete user['likes Coding'];

let key = 'likes Coding';
alert(user[key]);
```
### Computed properties
We can use _Square brackets_ in an object literal, when creating an object. That's called _computed properties_

```js
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
  [fruit]: 5, // the name of the property is taken from the variable fruit
};

alert( bag.apple ); // 5 if fruit="apple"
```

### Property value shorthand
we often use existing variables a values for property names.
```js
function makeUser(name, age) {
  return {
    name: name,
    age: age,
    // ...other properties
  };
}

let user = makeUser("John", 30);
alert(user.name); // John
```
In the example above, properties have the same names as variables. The use-case of making a property from a variable is so common, that there’s a special property value shorthand to make it shorter.
Instead of name:name we can just write name, like this:

```js
function makeUser(name, age) {
  return {
    name, // same as name: name
    age,  // same as age: age
    // ...
  };
}
```
We can use both normal properties and shorthands in the same object:

```js
let user = {
  name,  // same as name:name
  age: 30
};
```

### Property name limitations:
As we already know, a variable cannot have a name equal to one of the language-reserved words like “for”, “let”, “return” etc.

> [!NOTE]
> But for an object property, there’s no such restriction:

```js
// these properties are all right
let obj = {
  for: 1,
  let: 2,
  return: 3
};

alert( obj.for + obj.let + obj.return );  // 6
```
Other types are automatically converted to strings.

For instance, a number 0 becomes a string "0" when used as a property key:
```js
let obj = {
  0: "test" // same as "0": "test"
};

// both alerts access the same property (the number 0 is converted to string "0")
alert( obj["0"] ); // test
alert( obj[0] ); // test (same property)
```
> [!WARNING]
> There’s a minor gotcha with a special property named __proto__. We can’t set it to a non-object value:

```JS
let obj = {};
obj.__proto__ = 5; // assign a number
alert(obj.__proto__); // [object Object] - the value is an object, didn't work as intended
```

### Property Existence test, _`in`_ operator:
> A notable feature of objects in JavaScript, compared to many other languages, is that it’s possible to access any property. There will be no error if the property doesn’t exist!

Reading a non-existing property just returns undefined. So we can easily test whether the property exists:

```js
let user = {};

alert( user.noSuchProperty === undefined ); // true means "no such property"
```
There’s also a special operator "in" for that.

The syntax is:
> "key" in object

Example:

```js
let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age exists
alert( "blabla" in user ); // false, user.blabla doesn't exist
```
Please note that on the left side of in there must be a property name. That’s usually a quoted string.

If we omit quotes, that means a variable should contain the actual name to be tested. For instance:

```js
let user = { age: 30 };

let key = "age";
alert( key in user ); // true, property "age" exists
```

### The _`for..in`_ loop
To walk over all keys of an object, there exists a special form of the loop: _for..in_. This is a completely different thing from the for(;;).

```js

for (key in object) {
  // executes the body for each key among object properties
}
```
Example:

```js
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```

### Order of keys in objecs
Are objects ordered? In other words, if we loop over an object, do we get all properties in the same order they were added? Can we rely on this?

The short answer is: “ordered in a special fashion”: integer properties are sorted, others appear in creation order. The details follow.

As an example, let’s consider an object with the phone codes:

```js
let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",
  // ..,
  "1": "USA"
};

for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
```
> [!NOTE]
> Non integer keys are listed in _creation_ order.

```js
let user = {
  name: "John",
  surname: "Smith"
};
user.age = 25; // add one more

// non-integer properties are listed in the creation order
for (let prop in user) {
  alert( prop ); // name, surname, age
}
```

## Object References and Copying
> One of the fundamental differences of objects versus primitives is that objects are stored and copied “by reference”, whereas primitive values: strings, numbers, booleans, etc – are always copied “as a whole value”.







