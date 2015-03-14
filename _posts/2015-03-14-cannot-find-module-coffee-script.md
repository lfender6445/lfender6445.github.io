---
layout: post
title: "Cannot find module 'coffee-script'"
description: ""
category:
tags: []
---

Cannot find module 'coffee-script'


Trying to get a basic site set up with TowerJS as a test, but ran into this error when running the scaffold generator.

    Macbook:app john$ tower generate scaffold Post title:string body:text belongsTo:user
    { [Error: Cannot find module 'coffee-script'] code: 'MODULE_NOT_FOUND' }
    
    
    module.js:340
  throw err;
        ^
    Error: Cannot find module '/Users/john/Sites/tower/app/app/config/shared/application'
  at Function.Module._resolveFilename (module.js:338:15)
  at Function.Module._load (module.js:280:25)
  at Module.require (module.js:362:17)
  at require (module.js:378:17)
  at Function.Tower.Application.Application.reopenClass.instance (/usr/local/lib/node_modules/tower/lib/tower-application/server/application.js:42:15)
  at _.extend.namespace (/usr/local/lib/node_modules/tower/lib/tower-support/shared/shared.js:218:30)
  at GeneratorScaffoldGenerator.Tower.GeneratorResources.buildApp (/usr/local/lib/node_modules/tower/lib/tower-generator/server/resources.js:273:66)
  at GeneratorScaffoldGenerator.Generator (/usr/local/lib/node_modules/tower/lib/tower-generator/server/generator.js:57:23)
  at new GeneratorScaffoldGenerator (/usr/local/lib/node_modules/tower/lib/tower-generator/server/generators/tower/scaffold/scaffoldGenerator.js:21:61)
  at Function.run (/usr/local/lib/node_modules/tower/lib/tower-generator/server/generator.js:22:12)


--------------------------------------- 
This did the trick for me

    npm install --save-dev coffee-script
    
    
    node -v # v0.10.31


