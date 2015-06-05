---
layout: post
title: "Rails console returns nil for column that contains a value"
description: ""
category:
tags: ['ruby']
permalink: "rails-console-returns-nil-for-column-that-contains-a-value/"
---

Rails console returns nil for column that contains a value


I am developing an app that uses the CanCanCan gem, which is an update of Ryan Bates' CanCan, for authorization. CanCan uses a `:role` attribute to assign Abilities. My User model also uses STI, containing Admins and another role called "Agents." To avoid redundancy, and keep things DRY, I utilize the `:role` attribute as the `inheritance_column` as well.

{% highlight ruby %}
class User < ActiveRecord::Base
  has_secure_password
  attr_reader :role
  scope :profile, -> { includes(:address, :city, :state, :zip, :phone, :email)}
  scope :office_use, -> { includes(:username, :role, :type, :last_name, :first_name, :password_digest)}
  self.inheritance_column = :role

  def self.roles
     %w[Admin Agent]
  end
end
{% endhighlight %}

In the Rails console, I create a new user. I removed the choice to assign roles from the input form, figuring I'd create Admins manually since there won't be many, so it enters the default, "Agent":

    (63.4ms) COMMIT
     => #<User id: 2, username: "ff001", role: "Agent", password_digest: "$2a$10$osm9oEB51GKilUkX64sV7eMlt6pEfuzEfKIf3gRo/az...", last_name: "Flintstone", first_name: "Fred", address: nil, city: nil, state: nil, zip: nil, phone: nil, email: nil, created_at: "2015-01-01 19:01:11", updated_at: "2015-01-01 19:01:11"> 2.1.4 :019 >

Retrieving the row:

    > User.last
User Load (0.6ms) SELECT `users`.* FROM `users` ORDER BY `users`.`id` DESC LIMIT 1
    => #<Agent id: 2, username: "ff001", role: "Agent", password_digest: "$2a$10$osm9oEB51GKilUkX64sV7eMlt6pEfuzEfKIf3gRo/az...", last_name: "Flintstone", first_name: "Fred", address: nil, city: nil, state: nil, zip: nil, phone: nil, email: nil, created_at: "2015-01-01 19:01:11", updated_at: "2015-01-01 19:01:11"> 2.1.4 :020 >

Now a query for the `:role` attribute:

    > User.last.role
    User Load (0.4ms) SELECT `users`.* FROM `users` ORDER BY `users`.`id` DESC LIMIT 1
    => nil

This happens ONLY in the case of the role attribute--all, other columns when queried return their correct value. The role is used not only for authorization in the app, but also for routing to different resources for Admins. Since ActiveRecord is returning nil in the controller, my routing is not working properly either. I haven't even reached the point where authorization comes into play. Until the routes work correctly, authorization is kinda moot.

Why would this be happening? The `:role` attribute is the only one behaving this way.


---------------------------------------
Remove `attr_reader :role` - this should already be outlined in your schema.

Then try `User.last.role` in your console, and you'll get back what you've assigned.


