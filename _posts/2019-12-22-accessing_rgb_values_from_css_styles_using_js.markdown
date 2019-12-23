---
layout: post
title:      "Accessing RGB values from CSS styles using JS"
date:       2019-12-23 02:37:15 +0000
permalink:  accessing_rgb_values_from_css_styles_using_js
---


I recently wanted to set the background color of an HTML element based on the element's text color. I wanted to use the text color to dictate the background color to ensure there was enough contrast between the two. In order to dynamically decide the background color based on the text color, I needed to access the RGB color code of the element.

In this example, I have five different names, and each name is styled with a different color.

![](https://i.imgur.com/Vy7Cb7j.png)

When I log each name element's color to the console, the result is the color name, not the RGB code. Without the RGB code, I cannot calculate which background color will provide the best contrast.

![](https://i.imgur.com/9GtE3ZG.png)

In order to return the RGB code, you must use a JavaScript function, `getComputedStyle()`. You may pass in the HTML element whose CSS styles you want access to as an argument.

![](https://i.imgur.com/12FqWSi.png)

The `getComputedStyle()` function returns a large object containing all of the element's CSS styles. I saved the CSS styles object to a variable, `nameStyles`. Then, I used the `nameStyles` object to access the color.

![](https://i.imgur.com/Ig3FIHu.png)

When I log the color obtained from the `getComputedStyle()` function for each name element, the return value is the RGB color code! The only problem is that the RGB value is a string, so I need to parse it to obtain the numerical values inside of the parentheses. I used the following expression to parse the RGB string into an array containing the R, G, and B color values.

![](https://i.imgur.com/83Qb1gy.png)

![](https://i.imgur.com/nFjvLf4.png)

Now, I can use the array of R, G, and B color values of the text to calculate the background color with the best contrast!

