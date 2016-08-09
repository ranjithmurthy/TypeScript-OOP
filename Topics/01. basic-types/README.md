<!-- section start -->
<!-- attr: { id:'', class:'slide-title', showInPresentation:true, hasScriptWrapper:true } -->
# Basic Types
<article class="signature">
	<p class="signature-course">TypeScript OOP</p>
	<p class="signature-initiative">Telerik Software Academy</p>
	<a href="http://academy.telerik.com" class="signature-link">http://academy.telerik.com</a>
</div>


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Table of Contents
- [Introduction](#introduction)
- [Boolean](#boolean)
- [Number](#number)
- [String](#string)
- [Array](#array)
- [Tuple](#tuple)
- [Enum](#enum)
- [Any](#any)
- [Void](#void)


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Table of Contents
- [Type assertions](#type-assertions)
- [A note about let](#a-note-about-let)






<!-- section start -->
<!-- attr: { id:'introduction', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Introduction


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Introduction
- For programs to be useful, we need to be able to work with some of the simplest units of data: numbers, strings, structures, boolean values, and the like. In TypeScript, we support much the same types as you would expect in JavaScript, with a convenient enumeration type thrown in to help things along.




<!-- section start -->
<!-- attr: { id:'boolean', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Boolean


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Boolean
- The most basic datatype is the simple true/false value, which JavaScript and TypeScript call a boolean value.

```javascript
let isDone: boolean = false;

```





<!-- section start -->
<!-- attr: { id:'number', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Number


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Number
- As in JavaScript, all numbers in TypeScript are floating point values. These floating point numbers get the type number. In addition to hexadecimal and decimal literals, TypeScript also supports binary and octal literals introduced in ECMAScript 2015.

```javascript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;

```





<!-- section start -->
<!-- attr: { id:'string', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# String


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# String
- Another fundamental part of creating programs in JavaScript for webpages and servers alike is working with textual data. As in other languages, we use the type string to refer to these textual datatypes. Just like JavaScript, TypeScript also uses double quotes (") or single quotes (') to surround string data.

```javascript
let color: string = "blue";
color = 'red';

```



<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# String
- You can also use template strings, which can span multiple lines and have embedded expressions. These strings are surrounded by the backtick/backquote (`) character, and embedded expressions are of the form ${ expr }.

```javascript
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ fullName }.

I'll be ${ age + 1 } years old next month.`

```



<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# String
- This is equivalent to declaring sentence like so:

```javascript
let sentence: string = "Hello, my name is " + fullName + ".\n\n" +
    "I'll be " + (age + 1) + " years old next month."

```





<!-- section start -->
<!-- attr: { id:'array', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Array


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Array
- TypeScript, like JavaScript, allows you to work with arrays of values. Array types can be written in one of two ways. In the first, you use the type of the elements followed by [] to denote an array of that element type:

```javascript
let list: number[] = [1, 2, 3];

```

- The second way uses a generic array type, Array&lt;elemType&gt;:

```javascript
let list: Array&lt;number&gt; = [1, 2, 3];

```





<!-- section start -->
<!-- attr: { id:'tuple', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Tuple


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Tuple
- Tuple types allow you to express an array where the type of a fixed number of elements is known, but need not be the same. For example, you may want to represent a value as a pair of a string and a number:

```javascript
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error

```



<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Tuple
- When accessing an element with a known index, the correct type is retrieved:

```javascript
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'

```

- When accessing an element outside the set of known indices, a union type is used instead:

```javascript
x[3] = "world"; // OK, 'string' can be assigned to 'string | number'

console.log(x[5].toString()); // OK, 'string' and 'number' both have 'toString'

x[6] = true; // Error, 'boolean' isn't 'string | number'

```



<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Tuple
- Union types are an advanced topic that we’ll cover in a later chapter.




<!-- section start -->
<!-- attr: { id:'enum', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Enum


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Enum
- A helpful addition to the standard set of datatypes from JavaScript is the enum. As in languages like C#, an enum is a way of giving more friendly names to sets of numeric values.

```javascript
enum Color {Red, Green, Blue};
let c: Color = Color.Green;

```

- By default, enums begin numbering their members starting at 0. You can change this by manually setting the value of one of its members. For example, we can start the previous example at 1 instead of 0:


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Enum

```javascript
enum Color {Red = 1, Green, Blue};
let c: Color = Color.Green;

```

- Or, even manually set all the values in the enum:

```javascript
enum Color {Red = 1, Green = 2, Blue = 4};
let c: Color = Color.Green;

```

- A handy feature of enums is that you can also go from a numeric value to the name of that value in the enum. For example, if we had the value 2 but weren’t sure what that mapped to in the Color enum above, we could look up the corresponding name:


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Enum

```javascript
enum Color {Red = 1, Green, Blue};
let colorName: string = Color[2];

alert(colorName);

```





<!-- section start -->
<!-- attr: { id:'any', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Any


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Any
- We may need to describe the type of variables that we do not know when we are writing an application. These values may come from dynamic content, e.g. from the user or a 3rd party library. In these cases, we want to opt-out of type-checking and let the values pass through compile-time checks. To do so, we label these with the any type:

```javascript
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean

```



<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Any
- The any type is a powerful way to work with existing JavaScript, allowing you to gradually opt-in and opt-out of type-checking during compilation. You might expect Object to play a similar role, as it does in other languages. But variables of type Object only allow you to assign any value to them – you can’t call arbitrary methods on them, even ones that actually exist:


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Any

```javascript
let notSure: any = 4;
notSure.ifItExists(); // okay, ifItExists might exist at runtime
notSure.toFixed(); // okay, toFixed exists (but the compiler doesn't check)

let prettySure: Object = 4;
prettySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.

```

- The any type is also handy if you know some part of the type, but perhaps not all of it. For example, you may have an array but the array has a mix of different types:


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Any

```javascript
let list: any[] = [1, true, "free"];

list[1] = 100;

```





<!-- section start -->
<!-- attr: { id:'void', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Void


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Void
- void is a little like the opposite of any: the absence of having any type at all. You may commonly see this as the return type of functions that do not return a value:

```javascript
function warnUser(): void {
    alert("This is my warning message");
}

```

- Declaring variables of type void is not useful because you can only assign undefined or null to them:

```javascript
let unusable: void = undefined;

```





<!-- section start -->
<!-- attr: { id:'type-assertions', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# Type assertions


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Type assertions
- Sometimes you’ll end up in a situation where you’ll know more about a value than TypeScript does. Usually this will happen when you know the type of some entity could be more specific than its current type.
- Type assertions are a way to tell the compiler “trust me, I know what I’m doing.” A type assertion is like a type cast in other languages, but performs no special checking or restructuring of data. It has no runtime impact, and is used purely by the compiler. TypeScript assumes that you, the programmer, have performed any special checks that you need.


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# Type assertions
- Type assertions have two forms. One is the “angle-bracket” syntax:

```javascript
let someValue: any = "this is a string";

let strLength: number = (&lt;string&gt;someValue).length;

```

- And the other is the as-syntax:

```javascript
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;

```

- The two samples are equivalent. Using one over the other is mostly a choice of preference; however, when using TypeScript with JSX, only as-style assertions are allowed.




<!-- section start -->
<!-- attr: { id:'a-note-about-let', class:'slide-section', showInPresentation:true, hasScriptWrapper:true } -->
# A note about let


<!-- attr: { showInPresentation:true, hasScriptWrapper:true } -->
# A note about let
- You may’ve noticed that so far, we’ve been using the let keyword instead of JavaScript’s var keyword which you might be more familiar with. The let keyword is actually a newer JavaScript construct that TypeScript makes available. We’ll discuss the details later, but many common problems in JavaScript are alleviated by using let, so you should use it instead of var whenever possible.




<!-- section start -->
<!-- attr: { id:'', class:'slide-questions', showInPresentation:true, hasScriptWrapper:true } -->
# Basic Types
## Questions



