---
layout: post
title:      ".find vs .find_by: don't be deceived"
date:       2019-07-08 00:32:29 +0000
permalink:  find_vs_find_by_dont_be_deceived
---


Return values are extremely important, and I was reminded of this after banging my head against the wall trying to pass the last test of a Sinatra app lab. I mistakenly took the `.find` and `.find_by` methods at face value and assumed that the difference between them was insignificant. However, I learned that these two methods can produce very different results.

Both methods are “finder” methods available through the ActiveRecord gem. As the name suggests, they are used to find specific records in your database and return them as objects.
	
`.find` and `.find_by` have some differences in the arguments they can accept. `.find` accepts a record id or multiple record ids in the form of a list or an array (i.e. `(1, 2, 3)` or `( [1, 2, 3] )`). `.find_by` accepts one or more conditions as arguments in the form of `(attribute_name: value)`. The attribute name should correspond with a column name in your database. Both methods can find a record by its id, and I wrongfully assumed that you should always use `.find` to accomplish this.

The key difference between these methods is their return values when they *cannot* find a record that matches the given argument. If no record is found, `.find` returns `RecordNotFound`, whereas `.find_by` returns `nil`. The difference in return values becomes crucial when using these finder methods in RESTful controller actions.

In my case, I was using the `.find` method in a controller action designed to update a record. More specifically, I was using it in an if statement, which relies on boolean return values. I didn’t want a user to be able to edit a post that he/she did not author. If the requested post did not have a `:user_id` that matched the current user’s id, the program would redirect to a different page instead of rendering the edit form for that post. My program was breaking instead of redirecting to the specified route when it could not find a post with the given `:id` and `:user_id`. `RecordNotFound` is not truthy or falsey. On the contrary, `.find_by` returns `nil`, which is a falsey value, so my program is now able to redirect a user to the specified route in the conditional statement.

Using the `.find_by` method in RESTful controller actions can give you more power over which view is rendered and prevent your program from breaking when a record is not found.
