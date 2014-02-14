---
layout: post
published: true
title: '[ANNOUNCE]: Codesake::Dawn v1.0.3 released'
categories: article
tags: announce 1.0.3 release
image:
  feature: 
  credit: 
  creditlink: 
---
In the very beginning of January, [it was introduced a rake task](http://dawn.codesake.com/blog/dawn-now-fits-rake/) 
to be used to automate security review during deployment. Unfortunately that
code doesn't work.

Thank to [Paolo](http://paolomontrasio.com/) [reporting the issue](https://github.com/codesake/codesake-dawn/issues/37) it was possible to fix this annoying bug.
Yesterday I released Codesake::Dawn version 1.0.3 that introduces a
```dawn:run``` task.

## Installation

To upgrade ```codesake-dawn``` to version 1.0.3 you can simply run a ```bundle
update``` command inside the project you're using ```codesake-dawn```. If
you're using the gem as a standalone gem, simply run ```gem install
codesake-dawn```.

## Integrate Codesake::Dawn in your Rakefile

To integrate Codesake::Dawn in rake, you have to add this line in your
Rakefile.

```
require 'codesake/dawn/tasks'
```

Now running ```rake dawn:run``` your code will be audited for security issues.
A lot of improvements will be out to make the rake task even more useful,
starting from version 1.0.3 it works now.

Enjoy it!
