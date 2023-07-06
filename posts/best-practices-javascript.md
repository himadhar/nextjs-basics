---
title: 'Best Practices – JavaScript'
date: '2017-08-19'
------------------

# Best Practices – JavaScript

## Introduction

![](/images/blogs/js-best.jpeg)

JavaScript is a powerful and versatile programming language used for web development. To write clean, maintainable, and efficient code, it's essential to follow best practices. This article presents some of the best practices for JavaScript development.

Many solutions exist to solve a problem from a front-end’s perspective. But it needs a lot of efforts to get it right, to tune the performance to the best possible way, to keep things in sync in the most controlled and efficient manner, every time you build a webapp. As a front end developer, I believe that most of the cases, we tend to ignore that, whatever be the size of the app, performance should be the elementary concern for choosing the right – frameworks, libraries, storage mechanisms and so on.

Through this blog, I will attempt to collate a series of possibilities, when implemented, could lead to a great performance quality in your application. I’ll focus on 3 areas separately – HTML, CSS and the JS part of the app.

---

## 1. HTML

- The DOM (Document Object Model) is the first thing browser focuses on rendering. The (not so but) best approach to load files within a file is to first allow the stylesheets to exist, then the view components load (body tag part) and lastly, the scripts can be included to keep the view ready, and probably have a preloader (loading screen) until the last file gets loaded. It is a “NOT SO” good approach, simply because, for larger applications, the javascript files tend to be huge and this means there will be a delay in the compiling time, which will impact the page an end user gets to see.
- Remove all unnecessary tags simply put to give a structural feel. For example, if the view has two areas, a left and right, having two divs would do justice here but not anything more (keep in mind the CSS box model) and anything more would simply mean the page takes that much time to load.

---

## 2. CSS

- CSS allow us to achieve wonderful animations which in-turn provide us with great visual experience. But sometimes, this could lead to disasters too, since CSS relies completely on the GPU layer to handle the rendering aspect, and it cannot be burdened a lot. This means, if you have too many animations for every action within your application, chances are, your browser might be knocked out cold simply because it couldn’t take it anymore! As a workaround, keep your css animations at check, render animations only when it matters.
- Try to group as many components as possible with a common class name to have single object reference while rendering happens.
- It is also a good point to notice that, if you have css added to elements ID based, you could end up helping the JS layer to have best results too, since its way slow when it comes to class names as compared to the IDs.

---

## 3. JavaScript

- DOM traversal is the key to baby steps in optimization from a JS perspective. Whenever there requires for a DOM manipulation, use IDs for elements as much as possible. This way, JavaScript returns with the first-hit and proceeds with the next actions like – document.getElementById(“ElementID”). With libraries like JQuery, the code becomes even more efficient if you handle them using the indexes though they are w.r.t class names like – `$(‘.elementClassName”)[0]`. Traversing through the tag type like – $(“div > section > span”) for manipulating any values (get / set) becomes too heavy an operation.
- If you are a beginner, you might want to know that, DOM parsing happens sequentially – line by line from your HTML file. If you load your JS files – the libraries, plugins, and your custom code – in the first part of your HTML file, chances are, your page could load very slow, based on the lengthy files you include. Because, each such files are first compiled, processed and then the next one is picked up. This means, every single file, as long as it could be, once included in a script tag in your HTML, will be compiled and then the next line will be taken up. As an amateur fix, you can load all your JS files in the end, but first minify them (every character matters, junk characters like – spaces or comments eat up processing time, and will slow the compiling activity). Once done, add their reference just before the closing of the body tag. This way, basic DOM will be rendered and ready. You can have an init method to handle the delay time during the startup actions you need to settle up before user begins using your app (adding a preloader image could be a good start).
- Read about “Asynchronous Module Definition (AMD) API“, a page from RequireJS website. The approach is something, that is way way better method to solve the problem Point (B) tried to – to reduce the burden on the DOM loading / rendering time. AMD allows a developer to isolate the HTML rendering from the JS loading / compiling part. This allows the developer to focus more on the performance with better handling of the loading of the JS files asynchronously.
- Any DOM manipulations you do – can be done using single action methods instead of splitting them into individual actions. Every single DOM manipulation forces to refresh the view part of the DOM to reflect the update. By carefully consolidating them, you could reduce the screen updating (not the page refresh, but the visual rendering update a browser like Chrome or IE does when data changes) considerably like – a code as this > `$(“#selector”)`.css(“background”, “red”).css(“color”, “white”); can be consolidated to a single line $(“#selector”).css({“background”: “red”, “color”: “white”});
- On the same lines of point (D), as a developer you should build the DOM from dynamic data from JS code (any AJAX response that you possibly use to build your HTML contents) before making them visually available – any table you need to render to display data, you can first build the entire table and simply append it to the tag you want it to be at, like – $(“div.table-parent”).append(tableComponent) // where table component is a huge string built with AJAX response. This could be handy when the app is built on frameworks like AngularJS (<1.5) where watchers end up to be the sole reason where the app becomes clumsy and tardy because of the huge data it plays with.
- JS Libraries exist with the sole purpose to ease a developer’s life. Sometimes, they end up becoming a nightmare too. Since, plugins / libraries are built to be powerful. Sometimes really powerful!! This also means, they end being too long and can slow down the performance of the application, like – JQuery is a very powerful plugin. But if the only purpose for it to be a part of your application is for ease in accessing the HTML selectors, then it would be really useful for you to look out for alternatives, something like SizzleJS or pure old JavaScript.
- Objects are a clean solution for many of the developers’ problems. For example, if you have a value from a HTML that is used often, it would be good to create a parent object and add a reference to that tag as a value within this object like – for a tag with id=”selector”, you can write var selectors = {}; selectors.selector = document.getElementById(“selector”).value; // for a input type tag.

### Below is a list of things you need to keep in mind while you code in Javascript:

#### - Use Meaningful Variable and Function Names

Choose descriptive names for variables and functions to improve code readability. Avoid single-letter variable names or ambiguous names that may confuse other developers.

#### - Follow Proper Indentation and Formatting

Consistent indentation and formatting enhance code readability and maintainability. Use consistent spacing, line breaks, and indentation to make your code more organized.

#### - Declare Variables Properly

Always use `var`, `let`, or `const` to declare variables. Avoid global variables as they can lead to naming conflicts and make your code harder to maintain.

#### - Avoid Global Namespace Pollution

Minimize the use of global variables and functions to avoid conflicts with other scripts. Encapsulate code within functions or modules to keep the global namespace clean.

#### - Use Strict Mode

Enable strict mode by adding the directive `'use strict';` at the beginning of your JavaScript files. Strict mode enforces stricter rules and prevents common coding mistakes.

#### - Use Comments Wisely

Include comments to explain complex logic, important decisions, or non-obvious code sections. Use descriptive comments that provide meaningful insights into the code's purpose and functionality.

#### - Handle Errors Properly

Implement proper error handling to prevent unexpected crashes or failures. Use try-catch blocks to handle exceptions and provide informative error messages for debugging.

#### - Optimize Loops and Iterations

Avoid unnecessary looping and optimize loops by minimizing operations within the loop body. Consider using methods like `forEach`, `map`, or `reduce` for better readability and performance.

#### - Perform Regular Code Reviews

Regular code reviews help identify and fix issues early on. Collaborate with your team to review each other's code, provide feedback, and ensure adherence to best practices.

#### - Stay Updated with JavaScript Best Practices

JavaScript evolves over time, and new best practices emerge. Stay updated with the latest developments, read coding guidelines, and follow industry-accepted practices.

---

## Conclusion

By adhering to these best practices, you can write clean, maintainable, and efficient JavaScript code. Consistency, readability, and good coding practices are crucial for improving code quality and making your codebase more manageable.

I have added those that came to my mind now. If you feel anything else can be added, please feel free to comment below, and I’ll study it and add it if it is useful for others. Meanwhile, I’ll try to better my points by adding more clearer ones as often as possible.

---

<h6 style="text-align: right">
- Himadhar
</h6>
