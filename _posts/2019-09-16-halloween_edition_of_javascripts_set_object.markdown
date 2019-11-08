---
layout: post
title:      "Halloween edition of JavaScript's Set object"
date:       2019-09-16 17:52:18 -0400
permalink:  halloween_edition_of_javascripts_set_object
---


I may be far beyond my trick-or-treating days, but in the spirit of fall, I am throwing it back to the Halloween nights I spent tallying up my pillowcase of candy and negotiating swaps with my sister. Much to our dismay, my mom would make us combine our candy stashes to "save space" in the pantry. I'm going to demonstrate how the Set object works by using it to combine my sister and I's lists of candy into a single list with no duplicates.

First, I create an array of candy types for each pillowcase. Then, my sister and I begrudgingly combine the contents of our pillowcases into one container. To mimic this, I combine the two arrays using the `concat()` method.

![](https://i.imgur.com/HIMpRcI.png?1)

The new array has duplicate candy types that were present in both `haleysCandy` and `sistersCandy`. The duplicate candy types include:

* M&M's
* Reeses
* `{ "chocolate-bar": "Hershey's Special Dark" }`

An easy way to remove duplicates from a list of values involves using the Set object in JavaScript.

![](https://i.imgur.com/fqiMtjD.png)

A Set object in JavaScript is a collection of unique *values*. A new Set is created by passing an array as an argument. I pass in `combinedCandy` to create a new Set object, in hopes that the duplicate candy types will be removed...

![](https://i.imgur.com/GijRG78.png)

Only the duplicate strings ("M&M's" and "Reeses") are removed when `setCandy` is created. Why are there still two occurrences of the `{ "chocolate-bar": "Hershey's Special Dark" }` object?

Remember, a Set object is a collection of unique *values*. Only primitive data and object references are evaluated for uniqueness when a new Set is created.

Primitive data includes anything that is *not* an object and has no methods (i.e. strings and numbers).

According to [MDN's JavaScript Guide for Working with Objects](http://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects), 

>  In JavaScript, objects are a reference type. Two distinct objects are never equal, even if they have the same properties. Only comparing the same object reference with itself yields true.

I tested out this concept in the snapshot below. In the first two comparison statements, JavaScript does not recognize the objects as identical, even though they contain the same key and value. JavaScript is testing whether or not the objects reference the same *location in memory*, which is more efficient than evaluating the actual values within both objects.

The last example returns true because the same object reference is used on both sides of the operator.

![](https://i.imgur.com/1iWcphF.png)

In order for JavaScript to recognize both occurrences of `{ "chocolate-bar": "Hershey's Special Dark" }` as identical, I must:

**1. Store the object's location in memory as a variable**

![](https://i.imgur.com/3iiSJFZ.png)

**2. Reference that variable in the array that's used to create the new Set**

![](https://i.imgur.com/0WaOQKy.png)

In the snapshot above, `candySet` contains all unique values! By storing each chocolate object in a variable, I had easy access to each object's reference, or location in memory. I referenced these variables in the arrays to keep object references consistent. JavaScript removed the duplicate `hersheysDark` object reference when `candySet` was created.

Overall, using the Set object can be handy if you need to compile a list of unique values from an array of data. However, you need to be aware of *what* JavaScript actually evaluates for uniqueness in order to obtain the desired result.





