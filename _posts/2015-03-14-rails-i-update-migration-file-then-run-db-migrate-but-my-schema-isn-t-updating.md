---
layout: post
title: "Rails: I update migration file then run db:migrate, but my schema isn't updating"
description: ""
category:
tags: []
---

Rails: I update migration file then run db:migrate, but my schema isn't updating


Im trying to add an extra field to one of my tables.

Ive added the field in the migration file (under db\migrate) then ran 'rake db:migrate' which ran without troubles and my text editor even told me my schema.db file has been updated and needs to refresh.

The schema file does not contain my new field and any attempts to reference the field from my views fail miserably.

How do I do this? It is possible to update a table with an extra field via rails without having to totally drop and recreate the database again?

Thanks

Evolve


--------------------------------------- 
I was able to regenerate my schema with latter migrations by running `rake db:schema:dump`


