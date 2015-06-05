---
layout: post
title: "rails import sql, column mismatch on id"
permalink: "rails-import-sql-column-mismatch-on-id/"
description: ""
category:
tags: []
---

rails import sql, column mismatch on id


I have a series of sql statements that I am reading into my db - specificially, I am seeding a table with cities and coordinates, but am a little confused as how to handle missing ID columns in sql dumps.

My migration to create the table:

{% highlight ruby%}
class CreateCitiesExtended < ActiveRecord::Migration
  def change
    create_table :cities_extended do |t|
      t.string :city
      t.string :state_code
      t.integer :zip
      t.float :latitude
      t.float :longitude
      t.string :county
    end
  end


  def down
    drop_table :cities_extended
  end
end
{% endhighlight %}

After running the migration:

    sqlite> PRAGMA table_info(cities_extended)
    0|id|INTEGER|1||1
    1|city|varchar(255)|0||0
    2|state_code|varchar(255)|0||0
    3|zip|integer|0||0
    4|latitude|float|0||0
    5|longitude|float|0||0
    6|county|varchar(255)|0||0

The sql file looks something like this:

    INSERT INTO `cities_extended` VALUES ('Holtsville', 'NY', '00501', '40.8152', '-73.0455', 'Suffolk');
    INSERT INTO `cities_extended` VALUES ('Holtsville', 'NY', '00544', '40.8152', '-73.0455', 'Suffolk');
    INSERT INTO `cities_extended` VALUES ('Adjuntas', 'PR', '00601', '18.1788', '-66.7516', 'Adjuntas');

But when I attempt to read the .sql file into my sqlite table, I get a column mismatch error:

    rails db
    sqlite> .read ./db/data/cities_extended.sql

    Error: near line 41780: table cities_extended has 7 columns but 6 values were supplied
    Error: near line 41781: table cities_extended has 7 columns but 6 values were supplied

As you can see from the migrated table, an extra column called id was created by rails. This prevents the table from being seeded. What is the best way to satisfy the column requirements?


---------------------------------------

So i found a work around, but I'm not convinced its the best way:

{% highlight ruby %}
class CreateCitiesExtended < ActiveRecord::Migration
  def change
    create_table :cities_extended, :id => false ...
  end
end
{% endhighlight %}

Setting `:id => false` allows me to bypass the requirements.

It works for my cause, but I'm not sure its the best way because there will not be any unique ID's on any of the records.

source: [Create an ActiveRecord database table with no :id column?](http://stackoverflow.com/questions/874634/create-an-activerecord-database-table-with-no-id-column)
