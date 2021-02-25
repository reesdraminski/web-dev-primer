# web-dev-primer
A modern guide of the useful parts of HTML, CSS, and JS to get quickly started with web development. This guide assumes knowledge of at least one other programming language and some basic concepts of Computer Science.

# JavaScript
## Declaring Variables
In JavaScript, you can have a variable that changes value (mutable) or one that does not change value (immutable). For mutable variables, you use let and for immutable variables, you use const.
```js
const myName = "Rees";

let myAge = 19;
```
There is also the `var` keyword, but there is hardly occasion to use it when you can use `const` or `let`, so just don't use it.

**Further Reading:** [MDN Article on the let keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#examples)

JavaScript is dynamically typed, which means that a variable with the same name can change the type of data at any moment during the program's runtime. With some other languages, you have to specify the type when you create the variable, but JavaScript is much more flexible in this regard.
```js
let myVariable = 5; // Number
myVariable = "blah"; // String
myVariable = false; // Boolean
myVariable = [1, 2, 3]; // Array
```
### Objects
A more advanced type of JavaScript variables are something called objects. They are just like "dictionaries" or "maps" in other languages: an unordered collection of key-value pairs.
```js
let myObj = { key1: "Hello", key2: "World" };
```

You can get object attributes with the bracket or dot syntax.
```js
const myKey = "key1";

// Bracket syntax (especially helpful when you have a variable containing the key name
myObj["key1"]; // = "Hello"
myObj[myKey]; // = "Hello"

// ... or using the dot syntax, provided the key is a valid identifier.
myObj.key2; // = "World"
```
### Arrays
A special type of object in JavaScript is the array. Arrays are ordered lists of values, of any type.
```js
let myArray = ["Hello", 45, true];
```
Array elements can be accessed using the square-brackets syntax. Array indices start at zero in JavaScript.
```js
let myArray = ["Hello", 45, true];

myArray[1]; // = 45
```

In JavaScript, arrays are mutable and of variable length.
```js
myArray.push(5.0); // Add as last element
myArray.pop(); // Remove last element

myArray.length; // = 3
```
**Further Reading:** [MDN Article on the Array object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

### Strings
Strings kind of act like arrays in JavaScript, but they're not actually arrays.
```js
// Strings can be declared with single or double quotes 
// (this only matters when you have one of these characters in between the two quotes and need to escape it)
let myString = "Hello";
let otherString = 'Hello';

// Strings can be concatenated with + and += (you'll learn more about those operators below)

// Strings have a .length property like arrays
myString.length; // = 5

// You can access characters at a particular index with the brackets like in arrays
myString[1]; // = "e"

// However, strings are immutable so you can't change anything with the brackets like in arrays
myString[0]; = "J" // this does nothing
```

### Template Strings
Template strings are a cool way to interpolate variables into your strings in a readable format.
```js
let favoriteNum = 5;

// You use backticks and surround a JavaScript variable or expression in the ${} symbols
let statement = `My favorite number is ${favoriteNum}!`;
let otherStatement = `My favorite number is ${3 + 2}!`; // prints the same thing as above
```
**Further Reading:** [MDN Article on Template Strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

## Operators
There are many types of operators in JavaScript, but we will only focus on three main ones, arithmetic operators, assignment operators, and comparison operators.

### Arithmetic Operators
The arithmetic operators look just like the ones you would use in your math class.
```js
const four = 2 + 2; // Addition
const two = 5 - 3; // Subtraction
const eight = 4 * 2; // Multiplication
const three = 6 / 2; // Division
const one = 5 % 2; // Modulus (Remainder)
```

### Assignment Operators
You have already seen the most basic assignment operator which is just the equals sign, but you can also combine the equals sign with an arithmetic operator to utilize different assignment operators that help save the amount of typing you have to do.
```js
let count = 5;

count += 4;
count -= 3;
count *= 1;
count /= 2;
```
If you are just adding or subtracting one from a variable, there are additional shorthand operators to help you.
```js
let count = 0;

count++;
count--;
```

### Comparison Operators
Comparison operators are for comparing two values.
```js
const num = 4;

// Equality is ==
1 == 1; // = true
2 == 1; // = false
num == 3 // = false

// Inequality is !=
1 != 1; // = false
2 != 1; // = true
num != 3 // = true

// More comparisons
1 < 10; // = true
1 > 10; // = false
2 <= 2; // = true
2 >= 2; // = true
```
**Further Reading:** [MDN Article on Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

## Conditionals
If, else-if, and else statements are just as you'd find them in any other C-style language.
```js
let count = 1;
if (count == 2){
    // evaluated if count is 2
} 
else if (count == 3){
    // evaluated if count is 3
} 
else {
    // evaluated if it's neither 2 nor 3
}
```
**Advanced Reading**: [MDN Article on the Ternary Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

## Loops
While, do-while, and for loops are just as you'd find them in other C-style languages as well.
```js
while (true){
    // An infinite loop!
}

// Do-while loops are like while loops, except they always run at least once.
let input;
do {
    input = prompt("What is your name?");
} while (input != "");

// The for loop follows a familiar format:
// initialization; continue condition; iteration
for (let i = 0; i < 3; i++){
    // will run 3 times
}

// The for-in loop allows for the iteration of properties (keys) of an object
const myObj = { key1: "Hello", key2: "World" };
for (let key in myObj) {
    console.log(myObj[key]); // would print every value in the object
}

// The for-of loop allows for the iteration over an iterable object (like an Array or String)
const arr = [1, 2, 3, 4];
for (let num of arr) {
    console.log(num);
}
```
**Further Reading**: [For vs. For-in vs. For-of vs. forEach](https://thecodebarbarian.com/for-vs-for-each-vs-for-in-vs-for-of-in-javascript)  
**Advanced Reading:** If you want to make an object iterable, you can use [Object.entries/values/keys()](https://javascript.info/keys-values-entries)

## Functions
You define functions in JavaScript with the `function` keyword and you invoke functions with `()` just like in most other languages. If you need to return a value, the `return` keyword is used. Since this is a dynamically typed language, you don't need to declare parameter or return types.
```js
function myFunction() {
    console.log("Hello, World!");
}

myFunction();

// Function with parameters
function addTwoNumbers(numOne, numTwo) {
    return numOne + numTwo;
}
```

### Default Parameters
You can also set default parameters in JavaScript.
```js
function printString(str="Foo") {
    console.log(str);
}

printString("Hello") // prints "Hello"
printString(); // prints "Foo"
```
**Further Reading:** [MDN Article on Default Parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

### Immediately Invoked Function Expressions
Something cool that you can do in JavaScript is an Immediately Invoked Function Expression (IIFE). Essentially you define a function and call it at the same time.
```js
// This function is also an anonymous function, it has no name
// This function could not be called anyway because the parenthesis around the function create a closure
(function() {
    console.log("Hello, World!");
})();
```
**Further Reading:** [MDN Article on IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)  
**Further Reading:** [MDN Article section on Anonymous Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions#the_function_expression_function_expression)  
**Further Reading:** [MDN Article on Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)

### Passing Functions as Arguments
You can pass functions as arguments to other functions, which becomes useful in many cases.
```js
// prints "Hello" every five seconds"
setInterval(function() {
    console.log("Hello");
}, 5000);

// waits 3 seconds, then prints "World"
setTimeout(function() {
    console.log("World");
}, 3000);
```
**Further Reading:** [W3Schools Article on Timing Event](https://www.w3schools.com/js/js_timing.asp)

### Arrow Function Expressions
There is another way to create functions, which are called arrow functions. These are a special type of functions that don't bind to `this` which means they can't be used in all situations. They are always anonymous, but can be assigned to a variable and can be used like any other function.
```js
// Much more compact!
setTimeout(() => {
    console.log("World");
}, 3000);

// Parameters are in the same format you would expect in another function expression
const addTwoNumbers = (numOne, numTwo) => {
    return numOne + numTwo;
};

addTwoNumbers(3, 4); // returns 7

// One line arrow functions can omit the brackets
const printString = (str) => console.log(str);

printString("Hello"); // prints "Hello"

// If an arrow function is one line and returning something, the return keyword is not necessary
const addTwo = (num) => num + 2;

addTwo(2); // returns 4
```
**Further Reading:** [MDN Article on Arrow function expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

### Uses for Arrow Functions
Arrow functions are predominately used with functions associated with "functional programming" so `map`, `filter`, and `reduce`.
```js
const arr = [1, 2, 3, 4, 5];

// map applies a function to each value in the array and then returns a new array
const doubled = arr.map(num => num * 2); // returns [2, 4, 6, 8, 10]

// filter applies a function to each value in the array and keeps the values where
// the function returns true
const evens = arr.filter(num => num % 2 == 0); // returns [2, 4]

// reduce applies a function to each value and keeps an "accumulator" variable which it
// returns at the end
const sum = arr.reduce((acc, num) => acc + num); // returns 15
```
**Further Reading:** [Map, Filter, and Reduce](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d)

# JavaScript-HTML Interaction
HTML is represented as a tree and is accessible to JavaScript via the DOM (Document Object Model) API.

**Further Reading:** [MDN Article on DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_W3C_DOM_Level_1_Core)

All that you really need to know is that you can get a reference to an HTML element via JavaScript and then call functions on it like you would any other JavaScript object.
```html
<p id="numClicks">0</p>
<button id="myButton">Click me!</button>
```

```js
// get the element with the id "myButton" and store in the variable
const button = document.getElementById("myButton");

const numClicksEl = document.getElementById("numClicks");

// whenever the button is clicked by the user in the browser,
// the onclick function is called, and we just bound a function to it
button.onclick = () => {
    // + will work as concatentation with a string, so we need to convert to a number
    numClicksEl.innerText = parseInt(numClicksEl.innerText, 10) + 1;
}

// this would have the same effect as the code above, but usually .onclick is cleaner
// to write
button.addEventListener("click", () => {
    // + will work as concatentation with a string, so we need to convert to a number
    numClicksEl.innerText = parseInt(numClicksEl.innerText, 10) + 1;
});
```
**Further Reading:** [Article on DOM Manipulation](https://www.hongkiat.com/blog/dom-manipulation-javascript-methods/)

# Credits
Some code examples and explanations in the JavaScript section were taken and modified from [Learn JavaScript in Y minutes](https://learnxinyminutes.com/docs/javascript/), except they were updated to use a more modern form of JavaScript (ES6).
