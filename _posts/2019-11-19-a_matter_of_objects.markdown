---
layout: post
title:      "A matter of objects"
date:       2019-11-19 20:04:51 +0000
permalink:  a_matter_of_objects
---


Programming is a matter of objects when using many popular languages, such as Java, Python, and Ruby. If you are thinking, “Hold up! Programming is *way* more complex than 'just a bunch of objects!'” I agree with you. However, understanding object-oriented design patterns is a key to producing code that is more adaptive to change, DRY, reusable, and, in many ways, *less* complex.

Object-oriented programming provides a way for developers to organize and interact with data in a way that’s familiar. For example, you set a meal inside of a microwave and push buttons on the touchpad to heat up your food. A microwave’s touchpad provides a simple way to initialize complex processes that result in a warmed-up meal.

<iframe src="https://giphy.com/embed/NXfv0airL9nsk" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/best-gifs-amazon-dash-NXfv0airL9nsk">via GIPHY</a></p>

A microwave has attributes like wattage, model, and size. It also has functions like defrost, cook popcorn, set cook time, etc. Similar to microwaves, objects in programming come with attributes and functions, making data easier to organize and interact with.

Let’s dive into the four paradigms that make object-oriented programming so powerful.

## Encapsulation

Imagine you were programming representations of your kitchen appliances. You would need attributes and functions for your microwave, oven, and refrigerator, among many others. Your code would get confusing very quickly if you didn’t have a way to group the data for each appliance.

The ability to group related attributes and functions together via object-oriented programming reduces complexity.

## Abstraction

The pillar of abstraction relates back to the touchpad on the microwave. For example, simply pressing the “popcorn” button triggers a complex process that results in perfectly popped kernels. The “popcorn” button hides the nitty-gritty details of complex, electrical processes.

Similar to the buttons on a microwave, an object’s variables and functions provide a simple interface for interacting with it.

## Inheritance

Let’s say you are shopping for a new refrigerator. You notice that some models can dispense water, and an entertainment model has a screen for streaming TV. However, all of the models have the ability to cool and freeze food.

![](https://imgur.com/673YTS3)

When modeling the refrigerators in code, it would be silly to write the chill() and freeze() functions for every single refrigerator. Instead, you could write a single Refrigerator class that includes the generic methods shared by all refrigerators. Then, the Entertainment and Dispenser classes could inherit from the Refrigerator class.

Inheritance eliminates redundant code by allowing shared variables and functions to be defined one time.

## Polymorphism

While we continue shopping for refrigerators, we notice that all models have the ability to make ice. The Refrigerator class will have a makeIce() method. However, makeIce() will behave slightly differently depending on the model. For example, some models may produce square cubes, while others may produce long, curved cubes. Some models may produce 10 cubes per hour, while others only produce five.

Polymorphism adds flexibility by allowing customization of common methods or attributes based on the object’s data type or class. This pillar can be used to avoid long conditional statements.

Overall, understanding the pillars of object-oriented programming will help you to write clean, DRY, reusable, and adaptable code. That is why object-oriented languages continue to be widely used by programmers.
