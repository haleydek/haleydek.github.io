---
layout: post
title:      "Babbling about Babel"
date:       2019-12-09 00:59:21 -0500
permalink:  babbling_about_babel
---


React encourages the use of the latest JavaScript syntax to allow developers to take advantage of the newest syntactic sugar. However, not all browsers are compatible with ECMAScript 2015+. This compatibility issue is solved via Babel.

## What is Babel?

[Babel](https://babeljs.io/) is a JavaScript compiler that transforms the latest JavaScript syntax into older syntax that is interpreted by all browsers. It allows developers to write ES6+ code, without waiting for all browsers to support the newest syntax.

## Babel in React

`@babel/preset-react` is a Babel package that’s preset for React apps. If you use create-react-app, this Babel package will automatically be setup in your app. Otherwise, you can install it with the command below.

`npm install --save-dev @babel/preset-react`

The Babel preset for React includes the following plugins:
* @babel/plugin-syntax-jsx
* @babel/plugin-transform-react-jsx
* @babel/plugin-transform-react-display-name
* @babel/plugin-transform-react-jsx-self (with the development option)
* @babel/plugin-transform-react-jsx-source (with the development option)

As you may have noticed, many of the plugins above are related to JSX.

### What is JSX?

JSX is a syntax that resembles HTML. React elements are closely tied to the UI, so JSX makes it easy for developers to write HTML-like elements in the same file as JavaScript code.

### What does Babel have to do with JSX in React?

Babel translates JSX into valid JavaScript code, which is able to be interpreted by browsers. Without Babel, browsers would not be able to understand JSX and render the corresponding HTML elements.

Babel is like a translator between browsers and JavaScript. Babel knows all of JavaScript's new lingo and translates it into an older version that is understood by all browers.
