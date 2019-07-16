---
layout: post
title:      "Breaking down rack"
date:       2019-07-15 16:23:42 -0400
permalink:  breaking_down_rack
---


Upon completion of my first MVC Sinatra app, I decided to step out of the weeds and made my way to the top of the hill overlooking the swampy, weedy valley. In other words, I spent so much time worrying about the details of my app that I wanted to review the high-level concepts I used to build it before moving on with the curriculum.

First, I started reviewing the gems that were required to simply allow my app to run in the browser. This list included Sinatra and Shotgun, but when I dug deeper into both of these, there was another gem that kept popping up. Enter 'rack.'

### What is rack?

Rack is a Ruby gem that acts as the middleman between web servers and web frameworks (i.e. Sinatra). It simplifies the process of receiving HTTP requests and sending responses.

Rack is like a mailbox. When you put a letter into a mailbox, you give that letter access to a network of mailmen who know how to interpret the address and quickly deliver it to the correct destination. Without a mailbox, you would have a long and clunky journey to deliver the letter. You might have to waste time sitting in traffic on your way to the post office to pick up your mail.

Rack handles HTTP requests and responses through a single method, `#call`. This method accepts an environment ("env") hash as an argument. 

Where does the env hash come from, you ask? When an HTTP request is sent, it includes an env hash containing a lot of useful information. Some key components include the:
* HTTP verb
* Requested URL path
* Server address/port
* Input data from a form
* Session hash

This is not the full list of info included in the env hash, but it gives you an idea of how important it is for our apps to access the env. For example, RESTful routes wouldn't exist without the ability to identify the HTTP verb and URL path.

When the `#call` method accepts env as an argument, a new Rack::Request object is created. Upon initialization of the Rack::Request object, we gain access to a new set of methods that make it easy to grab and interpret the env data. Among these methods is the handy `#params` method.

```def call(env)
req = Rack::Request.new(env)
end```

Your app can then match up the HTTP verb and URL path from the env hash to controller actions.

HTTP responses must be sent in an array containing a status, header, and body. Rack also takes care of this for us through the initialization of a Rack::Response object.

```def initialize(body = [], status = 200, header = {})
. . .
end```

The `#finish` method is called on the Rack::Response object to simply put the status, header, and body into an array.
	
	```def call(env)
	req = Rack::Request.new(env)
	resp = Rack::Response.new
	resp.finish
	end```

Rack prevents developers from having to manually write boilerplate code for receiving and sending HTTP responses in every app they create. This is why there were multiple gems in my app that were built using Rack!




