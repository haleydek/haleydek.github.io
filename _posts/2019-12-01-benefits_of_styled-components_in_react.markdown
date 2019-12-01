---
layout: post
title:      "Benefits of styled-components in React"
date:       2019-12-01 22:12:32 +0000
permalink:  benefits_of_styled-components_in_react
---


Styling a React application, or any application for that matter, can get messy quickly if you don’t have a solid system for incorporating CSS. There are many options for styling React apps, and the preferred option varies amongst developers and companies. Recently, I decided to implement a popular option called [styled-components](https://www.styled-components.com/docs) in one of my side projects. I am going to walk through the benefits of using styled-components with React.

## Unique class names

Have you ever accidentally used the same class name more than once to define different styles in an application? As the scale and complexity of applications grow, it’s easy to forget which class names have already been used to define CSS styling.

This problem is eliminated with styled-components because it automatically creates unique class names. The snapshot below shows the HTML elements rendered in the React app I built using styled components. Each class name includes the name of the styled component and a unique identifier.

![](https://i.imgur.com/6je0HfP.png)

## Easy to locate styles

When class names are reused across multiple components, it can be difficult to know which class is responsible for a specific style on a component. Also, it can be cumbersome to sift through multiple stylesheets to find the class or style you’re looking for.

With styled-components, styles are easier to locate for two reasons:

1. Styles are only applied to a single component.
2. Styles are defined in the same file as the component.

In the snapshot below, the styled component, StyledFooterContent, is defined within the same file as the React component that returns it. This makes the styling for FooterContent easy to locate and maintain. If there is an issue with styles inherited from a parent component, you can simply check the styled component that’s defined within the parent component’s file.

![](https://i.imgur.com/w1Id4xt.png)

## Global themes

Styled-components enables you to define styles inside of a global theme object. Then, you can wrap your app, or a portion of your app, in the ThemeProvider helper component. This gives all of the ThemeProvider’s child components access to the theme object via props.

For example, I defined all of the colors I planned to use in a global theme object within App.js. I wrapped my entire app with the ThemeProvider to give all styled components access to the colors.

![](https://i.imgur.com/33UH5UX.png)

In the StyledHeader component, I accessed the “primary” color from the theme object via props. If I wanted to change the “primary” color, I would only need to update the value in one place--the global theme object in App.js.

![](https://i.imgur.com/LNAKpWf.png)

Overall, I enjoyed using styled-components in my React app because it simplified the ties between CSS styling and components. I found it easier to create simple, reusable components with consistent styling. Styled-components allowed me to focus more on the functionality of my components and less on the class names required to style them properly.
