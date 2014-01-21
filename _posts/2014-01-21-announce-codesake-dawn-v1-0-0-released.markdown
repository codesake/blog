---
layout: post
published: true
title: '[ANNOUNCE]: Codesake::Dawn v1.0.0 released'
categories: article
tags: announcement codesake-dawn v1 release
image:
  feature: winter-dawn.jpg
  credit: Alexander Roth
  creditlink: http://www.flickr.com/photos/relexi/
---

## Prologue

It was 2006 and I was first introduced to [OWASP](http://www.owasp.org) world.
Since writing safe code was my primary concern since that, I started the Owasp
Orizon project to provide a securiy code review engine for Java web
applications. That project was a failure. I produced something working but
decompiling and interpreting a source code out of the box was a nightmare.

During the years I learnt that the quest for safe code can't be fight only with
an automatic scanning tool. There must be some human interaction to avoid
reports full of false positives or nonsense issues.

They were the years I felt in love with Ruby programming language and the
related MVC framework used to build web application smoothly (or at least, to
start having a working prototype very quickly). I started writing my
application security script in Ruby and I started to give talks about the usage
of Ruby in a penetration test.

In March 2013, all of those experiencies made me to create the
[Codesake::Dawn](http://github.com/codesake/codesake-dawn) project as an
opensource source code scanner for security issues for ruby written code.

## It's all true: we hit version 1.0

After 9 months, I covered all security bulletins since today (21st January
2014) excluding some CVEs there are no enough information on the wild for me to
write a security check. They are already included in the roadmap for version
1.1.0.

As far as today there are 142 security checks in the Codesake::Dawn knowledge
base. By now the scanner finds vulnerabilities provided by third party gems
included in your Gemfile.lock file. However this is just the **very first**
step. 

For Sinatra web applications there is a rough support for HAML views scanning
to find sinks for cross site scripting vulnerabilities. The capability of scan
custom code for cross site scripting, injection flaws and business logic issues
is the main concern for upcoming Codesake::Dawn releases.

After all Rome wasn't build in a day, was it!?!

## Install it and have fun

Installing the Codesake::Dawn rubygem is straightforward. Just issue the
command ```gem install codesake-dawn``` at the time your reading this and
version 1.0.0 will be installed in your system.

Including codesake-dawn in your project bundle, it gives you also a rake task
you may want to use in your continous integration process. Just type ```rake
dawn``` to invoke Codesake::Dawn on the current directory.

## The press release announcement

After 9 months of development, it's now time for Codesake::Dawn security source
code scanner first major release.

Codesake::Dawn is a static analysis security scanner for ruby written web applications.
It supports [Sinatra](http://www.sinatrarb.com),
[Padrino](http://www.padrinorb.com) and [Ruby on Rails](http://rubyonrails.org)
frameworks. 

Version 1.0 introduces 142 security checks against public bulletins since 2006,
you can use to check the vulnerabilities introduced by third party libraries
your web application include in its Gemfile.

Writing safe code it's important, but sometimes security issues are introduced
by third party code your application relies on. As example, consider a SQL
Injection vulnerability introduced by Ruby on Rails framework. Despite the
effort you spend in sanitize inputs, your web application inherits the
vulnerability suffering as well. An attacker can easily exploit it and break
into your database unless you upgrade the offended gem.

There is a comprehensive set of command line flags you can read more by issuing
```dawn -h``` flag or by reading [project README](https://github.com/codesake/codesake-dawn/raw/master/README.md) file.

The list of security checks included in version 1.0.0 can be found online at:
[http://dawn.codesake.com/knowledge-base](http://dawn.codesake.com/knowledge-base).

You can use [facilities provided by
github](https://github.com/codesake/codesake-dawn/issues) to submit bug
reports, product enhancements, new security checks you want to me to add in
future releases and even success stories.

Now it's time for you to install Codesake::Dawn version 1.0.0 with the
following command and start reviewing your code for security issues:

``` 
$ gem install codesake-dawn
```

Enjoy it!
Paolo - paolo@codesake.com
