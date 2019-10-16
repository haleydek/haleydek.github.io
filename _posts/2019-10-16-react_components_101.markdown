---
layout: post
title:      "React components 101"
date:       2019-10-16 08:18:14 -0400
permalink:  react_components_101
---


React is a JavaScript library that simplifies the process of creating an app's user interface. React is centered around the use of components, which accept data as props and return JSX elements. JSX is basically a JavaScript syntax that looks like real HTML.  Elements written in JSX must be compiled by [Babel](https://babeljs.io/) before they can be rendered on the DOM. Don't let that intimidate you. The beauty of React is that it allows us to break up our code into many reusable pieces (a.k.a. components), which can help tremendously with debugging.

In order to help maintain organization and uphold the single responsibility principle throughout a React app, it is important to understand the convention of building **presentational** and **container** components.

### Presentational components:
* Responsible for how things ***look***
* Display content
* Cannot alter data they render
* Usually stateless
* Data they display is passed to them as props

### Container components:
* Responsible for how things ***work***
* Manage state and class methods
* Contain complex logic
* Import presentational components (children components are often presentational)
* Have very little HTML markup of their own, aside from wrapping children in <div>
* Often have state
* Often connected to Redux store
* Provide data and behavior (i.e. callbacks) to their children components

Below are two component examples from my React-Redux project to help you visualize the difference between presentational and container components.

### BadgesContainer

![](https://i.imgur.com/rV4KAqe.png)

BadgesContainer is a *container* component (suprise!) because it:
* Connects to Redux store
* Imports Badge component
* Provides data to Badge children components
* Has very little HTML markup

### Badge

![](https://i.imgur.com/lCXuUB6.png)

Badge is a *presentational* component because it:
* Receives props from BadgesContainer
* Displays content
* Does not alter data it receives via props

Overall, it is helpful to start with building stateless presentational components, especially when you are new to React. Then, it becomes easier to visualize what container components you need in your React app.


