---
layout: page
description: "Dawn is a source code static analyzer for security issues. It scans web application written in ruby programming language using either Rails, Sinatra or Padrino frameworks."
tags: [dawn, static analysis, ruby, appsec, application security]
image:
  feature: winter-dawn.jpg
  credit: Alexander Roth
  creditlink: http://www.flickr.com/photos/relexi/
---

# Codesake::Dawn - The security code scanner for Ruby

Codesake::Dawn is a source code scanner designed to review your code for
security issues. 

Codesake::Dawn is able to scan your ruby standalone programs but its main usage
is to deal with web applications. It supports applications written using majors
MVC (Model View Controller) frameworks, like: 

* [Ruby on Rails](http://rubyonrails.org)
* [Sinatra](http://www.sinatrarb.com)
* [Padrino](http://www.padrinorb.com) 

Codesake::Dawn version 1.0 has 142 security checks loaded in its knowledge
base. Most of them are CVE bulletins, that applies to gems, framework or the
ruby interpreter itself.

When you run Codesake::Dawn on your code it parses your project Gemfile.lock
looking for the gems used and it tries to detect the ruby interpreter version
you are using or you declared in your ruby version management tool you like
most (RVM, rbenv, ...).

Then the tool tries to detect the MVC framework your web application uses and
it applies the security check accordingly. There checks designed to match rails
application or checks that are appliable to any ruby code.

Codesake::Dawn can also understands the code in your views and to backtrack
sinks to spot cross site scripting and sql injections introduced by the code
you actually wrote. In the project roadmap this is the code most of the future
development effort will be focused on.

Codesake::Dawn security scan result is a list of vulnerabilities with some
mitigation actions you want to follow in order to build a stronger web
application.
