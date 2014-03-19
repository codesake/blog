---
layout: post
published: true
title: '[ANNOUNCE]: Codesake::Dawn v1.0.5 released'
categories: article
tags: announce 1.0.5 release
image:
  feature:
  credit:
  creditlink:
---

Last week there were announced two new CVE bulletins about ruby gems.
[CVE-2014-0036](http://seclists.org/oss-sec/2014/q1/509) was about the rbovirt
ruby gem that it wasn't properly controlling SSL certificate when using
rest-client gem. Because of this, all software built upon rbovirt vulnerable
gem is affected by a man in the middle vulnerability.

The other advisory,
[CVE-2014-2322](http://packetstormsecurity.com/files/125679/Ruby-Gem-Arabic-Prawn-0.0.1-Command-Injection.html)
was about a command injection vulnerability for the Arabic-Prawn ruby gem
passing unsanitized string to shell.

Both the two vulnerabilities are included in Codesake::Dawn, either in the
upcoming 1.1 version than in a new stable version patch, the
[1.0.5](https://github.com/codesake/codesake-dawn/commit/53607818361573597e56bf93f55a0e9de015a4d0).

## Installation

To upgrade ```codesake-dawn``` to version 1.0.5 you can simply run a ```bundle
update``` command inside the project you're using ```codesake-dawn```. If
you're using the gem as a standalone gem, simply run ```gem install
codesake-dawn```.

Enjoy it!
