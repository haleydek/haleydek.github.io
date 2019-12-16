---
layout: post
title:      "Do you even hoist?"
date:       2019-12-16 03:58:20 +0000
permalink:  do_you_even_hoist
---


In JavaScript, you have the ability to call a function, or use a variable, before it’s declared. This concept is called **hoisting**, and it sounds like magic, right? Well, maybe at first, but understanding how JavaScript code is executed will help to demystify this concept.

When JavaScript code is run, there are two phases that occur in relation to hoisting. In the first phase, variable and function declarations are saved in memory. At this point, declared variables are considered either uninitialized or undefined. In the second phase, variables are assigned values, and code is executed. Hoisting is possible because variables and functions are given references in memory *before* code is executed in the second phase.

Functions and variables each have their own nuances in regards to hoisting. It's important to understand these nuances and be mindful of them in order to utilize hoisting properly and avoid bugs.

## Functions

1. **Declarations** are hoisted to the top of their scope.
2. **Expressions** are NOT hoisted.

![](https://i.imgur.com/EcS8zPD.png)

In the code above, I tried hoisting a function declaration, `findApples()`, and a function expression, `findOranges()`. Even though `findApples()` was called *before* it was declared, the function call in line one still logged, "I found the apples!" to the console. However, the function expression, `findOranges()`, returned an error and was *not* hoisted.

## Variables

![](https://i.imgur.com/lLow4my.png)

1. **Declarations** are hoisted to the top of their scope.
2. **Assignments** are NOT hoisted.

![](https://i.imgur.com/2OJ7E3G.png)

JavaScript only hoists variable declarations, not assignment. The initialization of variables is handled differently, depending on whether *var*, *let*, or *const* is used to declare them.

In the example above, *let* was used to declare the honeycrisp variable, and it threw a reference error when it was hoisted on line one. The same reference error would occur if honeycrisp was declared using *const*. However, in the case of *var*, variables are initially set to `undefined` upon declaration. If honeycrisp was defined using *var*, the return value of line one would have been `undefined`.

Regardless of whether you use *var*, *let*, or *const*, the variable assignment on line five will never be hoisted.

3. If a variable is **assigned a value, but not declared**, the variable will become global once the assignment code is executed.

![](https://i.imgur.com/pQGXoPF.png)

In the `eatingApple()` function above, the grannySmith variable is assigned a value, but it is not declared using *var*, *let*, or *const*. Usually, when variables are declared and assigned values inside of a function, they are only accessible with that function's scope. In the case above, the undeclared grannySmith variable becomes *global* when the `eatApple()` function is executed.

## Hoisting order of prioritization

JavaScript follows the following order of prioritization when hoisting eligible code to the top of the stack:

1. Variable assignment
2. Function declarations
3. Variable declarations


## Takeaways

Although hoisting is a useful feature of JavaScript, it can cause confusion and unexpected bugs. The following guidelines will help you to write clear code and avoid negative side effects of hoisting.

1. Always declare variables at the top of their scope.
2. In addition to declaration, assign values to variables at the top of their scope whenever possible.
3. Declare and define all functions before using them.
4. Try to declare functions in order of their use.
