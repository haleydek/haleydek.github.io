---
layout: post
title:      "Digging into a 'new' ActiveRecord association class method"
date:       2019-08-12 21:25:31 -0400
permalink:  digging_into_a_new_activerecord_association_class_method
---


As I built my first Rails project with multiple models and "many-to-many" relationships, I found myself returning to the [ActiveRecord Associations Class Methods](https://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html#method-i-has_many) documentation over and over again. There were a few situations where I knew I set up the associations correctly, but I was still getting errors like, "Did you mean `#users_trips`, not `#users_trip`?" I needed a better understanding of the methods my objects and classes had access to through their ActiveRecord associations. It became clear that `#build` just doesn't work for everything, so I dug into the docs to figure out why and what other method I could use instead.

In this case, I was concerned about three classes (Trips, DestinationsTrip, and Destinations), that were related via a many-to-many relationship, with DestinationsTrip as the join model. The problem arose when I was building the form for a new trip with `:destination_ids` nested in the form.

I wanted to add a `collection_select` field that allowed users to select multiple destinations for the new trip. I pre-populated the Destinations table with data from Atlas Obscura's website, so I didn't need to create new destinations from scratch.

I tried the code below in my trips controller.

```
def create
    @trip = @user.trips.build(trip_params)
    @trip.destinations.build(trip_params)
		
		if @trip.save!
    . . .
end

private

def trip_params
    params.require(:trip).permit(:title, :start_date, :end_date, user_ids:[], destination_ids: [])
end
```

However, my app was returning errors, such as "undefined attribute `:title` for Destination," or "No Method Errors" related to `:destination_ids`.

In response, I started digging through the "has_many" association class methods, which the Trips class inherits from ActiveRecord. I stumbled upon the following method:

`#collection_singular_ids=ids`, which is represented as `@trip.destination_ids=(trip_params[:destination_ids])` in my app.

I plugged it into the #create action, and. . . .

```
def create
    @trip = @user.trips.build(trip_params)
		
		if @trip.save!
		    @trip.destination_ids=(trip_params[:destination_ids])
    . . .
end

private

def trip_params
    params.require(:trip).permit(:title, :start_date, :end_date, user_ids:[], destination_ids: [])
end
```

**. . . it worked! But, why?**

`#collection_singular_ids=ids` replaces the destinations *collection* with destination *objects*. How do we get destination *objects*? They are identitied by the primary keys in the `:destination_ids` array.

Then, behind the scenes, ActiveRecord calls upon another has_many association class method, `#collection=objects`. This method creates the association between the trip and the destination *objects*. In other words, records are created in the join table using the trip's id and each destination object's id. `#collection=objects` adds or removes destinations from the `trip.destinations` collection, by comparing the objects passed in vs. any existing objects in the `trip.destinations` collection.

Understanding all of the methods your classes have access to is just one way you can demystify ActiveRecord/Rails "magic!"
