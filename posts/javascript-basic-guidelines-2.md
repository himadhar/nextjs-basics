---
title: 'JavaScript Basic Guidelines'
date: '2022-03-21'
---
# JavaScript Basic Guidelines

## Introduction

![](/images/blogs/js-basics-2.jpeg)

As a JavaScript developer, I needed a standard as to start off any work that I do while handling client-side validations. I started off googling a bit to summarize on basic rules one should have while writing code in JavaScript or while using any of the plugins written using it.

---

## Basic Concepts

I have listed some of the basic rules a developer should follow as a ‘rule of thumb’ before coding in JavaScript. Feel free to comment on any part of the below list and if necessary I’ll edit the post to incorporate your comments as a point too.

- **var**: Declaring a variable must be done always with a var prefix to it. This makes its scope local to its context (this). Not declaring a variable (prefixing it with a var) might change the scope of the variable from local to global. Global also creates ambiguity as its browser dependent and it means, it can be either local to the document or the window itself.
  For Eq.; var x = ‘this is a string variable’;
- **Constants**: Variables who are intentionally supposed to be constant through out the project must be declared in ALL_CAPS _FORMAT.
  var time.MILLISECONDS = 60;  //time in milliseconds, is always constant
- **Multiline string variables**: While declaring a multiline string literal, each line should end with a ‘+’ symbol to retain the empty spaces , the string composure in its actual form.
  For Eq.; var x = ‘hello’ +
  ‘world’;
- **Naming conventions**: These are a list of possible elements with their standard naming conventions, such as functionNamesLikeThis, variableNamesLikeThis, EnumNamesLikeThis, parent.namesLikeThis.child, CONSTANT_NAMES_LIKE_THIS and fileNamesLikeThis.js.
  * **Semi colons** : Compiler by default adds a ‘;’ semicolon at the end of each line. But, not adding it wherever necessary creates issues like not adding it between prototypal modules. JavaScript never add by ‘default’ a semicolon if the next line is an infix or a bracket
    var  eatables = [apples, oysters, sprayOnCheese]  // No semicolon here.
    -1 == ‘a’ || ‘b’; // returns  ‘b’ since eatables -1 = NaN and hence would is false
  * **Nested functions**: A base for prototypal modal, it helps keep the code clean and secure and must be used as and when required.
  * **Functions in a clause block**: Writing a function in an if block, for example, is not recommended though most browsers support this route of coding. ECMAScript has proposals to completely remove it in future versions. Instead, declaring functions and consuming them based on their scope is recommended.
  For Eq.; `var x = function() { //code }`
  * **Exception handling**: Every code written, if with a non-trivial purpose, must be written with complete exception handling to avoid any lag in user experience.
  For Eq.; try `{ //code } catch(event) { //catch exception }`
  Custom exception handling is a way of handling exceptions gracefully. By anticipating exceptions, user can be displayed with various informations based on the type of exception.
  * **Using standards**: Use of standard features provided by ECMAScript is the best way to handle code re-usability and portability rather than using JS hacks to achieve tasks.Standard – `str.charAt(0),  Hack – str[0] // both return first character of ‘str’ variable`
  * **Wrapping primitive objects**: There is no purpose or need to wrap objects of primitive types.
  For Eq.; `var x = Boolean(false)`
  But instead, type casting can be used as and when required.
  For Eq.; `var x = Boolean(0)`
  * **Multi level prototype hierarchies**: Inheritance is achieved in JavaScript using multi level prototype hierarchies. Having more number of hierarchies might create an issue in handling the code. Instead, closures can be used as and when required to retain code consistency and achieve modularity.
  * **Methods and properties**: Objects can have methods as their properties, or their properties as methods based on their purpose and usage. Declaring them can be done in the below preferred way,
  `App.prototype.prop = function () { //code }`
  `function App() { this.prop = function() { //code } }`
  * **Delete**: Deleting a property of an object consumes more time and must be engaged only if necessary. Instead, their values can be set to null to handle computational speed
  * **Closures**: Using closures to bind events with parameters to a DOM object will create a cycle of references and hence must be avoided.
  * **this**:  The semantics of ‘this’ can refer to the global object (in most places), the scope of the caller (in eval), a node in the DOM tree (when attached using an event handler HTML attribute), a newly created object (in a constructor), or some other object (if function was call()ed or apply()ed). Usage must be highly controlled and only if necessary.
  * **Associative array**: Associative arrays are not allowed in JavaScript. To use a Hash or mapping technique to fetch elements by using non numerals for indexes, use objects instead
  * **Modifying built in prototypes**: Modifying built in prototypes are strictly forbidden since they lead to code maintenance complexities and debugging issues.
  * **IE specific conditional statements**: Writing code by identifying browser every time might hinder the loading time as it affects creation of JavaScript tree in the page. Additionally, it might also affect the automated tools and cause performance issues.
  * **Code formatting**: The basic standards for code formatting are as below:
  - Curly braces begin always in first line as the declaration of the function
  - Single-line array and object initializers are allowed when they fit on a line
  - Multiline array initializers and object initializers are indented 2 spaces, with the braces on their own line, just like blocks.
  - When possible, all function arguments should be listed on the same line. If doing so would exceed the 80-column limit, the arguments must be line-wrapped in a readable way.
  - Parent child sections must always be indent-separated
  - The unit of indentation is 4 spaces. Using tabs must be avoided. Even though using spaces will produce a larger file, it is trivial if minification is considered.
  - Comments must be added generously to retain code re-usability and legibility, and at the same time, not comment on unnecessary items. For Eq.; `var i=0; //set i to zero`
  - There shouldn’t be more than one return statement in a function. The return value expression should consist the beginning of the return value to begin in the same line after ‘return’ keyword to avoid semicolon injection.
  * **Loading JavaScript code**: JavaScript code must never be written within a HTML file since it lags the performance and must always be loaded via an external ‘.js’ file using script tag. Additionally, since the DOM will not be loaded until each line of HTML is executed, loading JS files as late as possible in a HTML file (for Eq.; just before the end tag of body) will help render DOM fast and also retain user’s attention.
  * **Linting**: Verify code patterns and structures before deploying using the linting method. Among the many online tools available for linting, JSHint is a popular tool used for linting code to check for structure consistency and code leakage if any.

---

## Conclusion

Javascript has its nightmares but if you can focus on mastering the basics, the difficulty drastically reduces. All the best!

---

<h6 style="text-align: right">
- Himadhar
</h6>