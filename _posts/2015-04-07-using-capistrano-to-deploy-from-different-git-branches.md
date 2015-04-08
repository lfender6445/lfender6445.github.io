---
layout: post
title: "Using capistrano to deploy from different git branches"
description: "Using capistrano to deploy from different git branches"
category:
tags: ['ruby', 'capistrano']
permalink: '/using-capistrano-to-deploy-from-different-git-branches/'
---

I am using capistrano to deploy a RoR application. The codebase is in a git repository, and branching is widely used in development. Capistrano uses deploy.rb file for it's settings, one of them being the branch to deploy from.

My problem is this: let's say I create a new branch A from master. The deploy file will reference master branch. I edit that, so A can be deployed to test environment. I finish working on the feature, and merge branch A into master. Since the deploy.rb file from A is fresher, it gets merged in and now the deploy.rb in master branch references A. Time to edit again.

That's a lot of seemingly unnecessary manual editing - the parameter should always match current branch name. On top of that, it is easy to forget to edit the settings each and every time.

What would be the best way to automate this process?

[more info](http://www.harukizaemon.com/2008/05/deploying-branches-with-capistrano.html).


---------------------------------------

For capistrano 3 users:

{% highlight ruby %}
desc "prompt for branch or tag"
task :git_branch_or_tag do
  on roles(:all) do |host|
    run_locally do
      execute :git, 'tag'
      tag_prompt = "Enter a branch or tag name to deploy"
      ask(:branch_or_tag, tag_prompt)
      tag_branch_target = fetch(:branch_or_tag, 'master')
      set(:branch, tag_branch_target)
    end
  end
end
before 'deploy:updated', :git_branch_or_tag
{% endhighlight %}


