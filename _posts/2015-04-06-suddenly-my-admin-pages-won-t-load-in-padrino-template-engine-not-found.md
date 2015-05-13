---
layout: post
title: "Suddenly my admin pages won't load in Padrino (Template Engine not found)"
description: ""
category:
tags: []
---

Suddenly my admin pages won't load in Padrino (Template Engine not found)


I've never had an issues with the admin pages in my app before, but after a reboot of my machine I'm getting this error:

    RuntimeError at /admin/sessions/new
    Template engine not found: /sessions/new

With this abbreviated backtrace:

    /Users/jeremysmith/code/robusto_server/admin/controllers/sessions.rb in block (2 levels) in <top (required)>
  render "/sessions/new", nil, :layout => false
    /Users/jeremysmith/.rvm/rubies/ruby-1.9.2-p180/lib/ruby/1.9.1/webrick/httpserver.rb in service
    si.service(req, res)

Everything in app.rb is the same as it was when this used to work:

    set :login_page, "/admin/sessions/new"
    
    
enable :sessions
disable :store_location
    
    
access_control.roles_for :any do |role|
  role.protect "/"
  role.allow "/sessions"
end
    
    
access_control.roles_for :admin do |role|
  role.project_module :stat_definitions, "/stat_definitions"
  role.project_module :accounts, "/accounts"
end


--------------------------------------- 
I ran into this same issue using modular Sinatra pattern application and slim for my templating engine. I couldn't render templates or partials. Here is how I fixed it:

    # Gemfile
    gem 'padrino-core'
    gem 'padrino-helpers'
    
    
    # app.rb
    require 'padrino-core/application/rendering'
    require 'padrino-helpers'
    
    
    class App < Sinatra::Base
register Padrino::Rendering
register Padrino::Helpers
    end

more information at [http://www.padrinorb.com/guides/standalone-usage-in-sinatra](http://www.padrinorb.com/guides/standalone-usage-in-sinatra)


