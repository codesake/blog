---
layout: post
published: true
title: '[ANNOUNCE]: Codesake::Dawn v1.0.6 released'
categories: article
tags: announce 1.0.6 release
image:
  feature: 
  credit: 
  creditlink: 
---

A new CVE bullettin is out for [rack-ssl
rubygem](https://rubygems.org/gems/rack-ssl). Accordingly to [CVE-2014-2538
advisory](http://osvdb.org/show/osvdb/104734) rack-ssl Gem for Ruby contains a
flaw that allows a reflected cross-site scripting (XSS) attack. This flaw
exists because the program does not validate input passed via error messages
before returning it to users. This may allow a context-dependent attacker to
create a specially crafted request that would execute arbitrary script code in
a user's browser session within the trust relationship between their browser
and the server.

The advisory is included in Codesake::Dawn, either in the
upcoming 1.1 version than in a new stable version patch, the
[1.0.6](https://github.com/codesake/codesake-dawn/commit/096b8cd52af778927dae1e2151fa8f9402e59683)

## Installation

To upgrade ```codesake-dawn``` to version 1.0.6 you can simply run a ```bundle
update``` command inside the project you're using ```codesake-dawn```. If
you're using the gem as a standalone gem, simply run ```gem install
codesake-dawn```.

Enjoy it!
