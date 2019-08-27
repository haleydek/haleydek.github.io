---
layout: post
title:      "Incorporating error messages into Response objects from server"
date:       2019-08-27 15:25:14 +0000
permalink:  incorporating_error_messages_into_response_objects_from_server
---


“That’s so fetch!” Although Gretchen Wieners probably wouldn’t understand, this is what I found myself thinking as I learned how to use JavaScript and the fetch() method to communicate with a Rails API. (Sorry, I couldn’t help myself.)

What happens when your server returns a blank or “undefined” response? How can a developer communicate an error message to the end user? This is a task I conquered when I was building a Pokemon app, where each trainer’s team can have a maximum of six Pokemon. Each team has an “Add a Pokemon” button that sends a “POST” request to pokemons#create via the `fetch()` method.

#### Defining Error Message in Rails API
I wrote the logic for controlling the size of the trainer’s team in the Rails API, as opposed to the front end, because it involves calling upon the model relationships. If the trainer's team has less than six Pokemons, a new Pokemon is created and sent back via a json response. Otherwise, the json response would only have a message key containing “A team cannot have more than 6 Pokemons.”

However, every time I tried adding a seventh Pokemon to a team, JavaScript would still add a new element to the list of Pokemon with a nickname displayed as “undefined.” I needed to control what was rendered on the page when the Rails API refused to create more than six Pokemons for a team.

![](https://i.imgur.com/akveza2.png)

#### Rendering Error Message Using JavaScript
I resolved this by adding an if/else statement in the second then() method call, after the fetch response was parsed into a json object. If the Rails API refuses to create a new Pokemon, the nickname attribute is undefined in the json object. Instead, the json object would contain the error message defined in pokemons#create.

In order to show this message to the end user, I used the `alert()` method. When a user tries to add a seventh Pokemon to a team, an alert box pops up with the message, “A team cannot have more than 6 Pokemons.“

![](https://i.imgur.com/sfNNOwp.png)

