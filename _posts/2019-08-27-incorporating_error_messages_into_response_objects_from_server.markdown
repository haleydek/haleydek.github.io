---
layout: post
title:      "Incorporating error messages into Response objects from server"
date:       2019-08-27 11:25:15 -0400
permalink:  incorporating_error_messages_into_response_objects_from_server
---


“That’s so fetch!” Although Gretchen Wieners probably wouldn’t understand, this is what I found myself thinking as I learned how to use JavaScript and the fetch() method to communicate with a Rails API. (Sorry, I couldn’t help myself.)

What happens when your server returns a blank or “undefined” response? How can a developer communicate an error message to the end user? This is a task I conquered when I was building a Pokemon team app, where a trainer may have a maximum of six Pokemon on his/her team. Each team has an “Add a Pokemon” button that sends a “POST” request to pokemons#create via the `fetch()` method.

### Defining Error Messages in Rails API
I wrote the logic for controlling the size of a trainer’s team in the Rails API, as opposed to the front end, because it involves calling upon the model relationships. If a trainer's team has less than six Pokemon, a new Pokemon is created in the database and sent back as a Response object containing its nickname, species, etc. Otherwise, the Rails API sends a Response object containing only a "message" key with a value of: “A team cannot have more than 6 Pokemon.”

I tested this in the browser by clicking "Add a Pokemon" to a team that already had six members. JavaScript still added a new list element for a seventh Pokemon, but its nickname was displayed as “undefined.” I needed to control what was rendered on the page when the Rails API refused to create more than six Pokemon for a team.

![](https://i.imgur.com/akveza2.png)

### Rendering Error Messages Using JavaScript
I resolved this by adding an if/else statement in the second `then()` method call, after a fetch response is parsed into a JSON object. If the Rails API does *not* create a new Pokemon, the nickname attribute is undefined, and the JSON object contains the error message defined in pokemons#create.

In order to show this message to the end user, I used the `alert()` method. When a user tries to add a seventh Pokemon to a team, an alert box pops up with the message, “A team cannot have more than 6 Pokemons.“

![](https://i.imgur.com/sfNNOwp.png)

![](https://i.imgur.com/W7D0IZ5.png)

