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


