---
layout: post
published: false
title: '[ANNOUNCE]: Codesake::Dawn v1.0.4 released'
categories: article
tags: announce 1.0.4 release
image:
  feature: 
  credit: 
  creditlink: 
---

Last 2 months was quite active in Ruby security world. There were 5 new
vulnerabilities out there, already included in Codesake::Dawn development tree.
Unfortunately, I didn't apply all the changes in master, so people using
official codesake-dawn gem was not able to test their code for latest
vulnerabilities.

Since release 1.1 is delayed due to a lot of work to be done, I backported 4
out of 5 of those vulnerabilities:

* CVE-2014-1233: The paratrooper-pingdom gem 1.0.0 for Ruby allows local users
  to obtain the App-Key, username, and password values by listing the curl
  process.
* CVE-2014-1234: The paratrooper-newrelic gem 1.0.1 for Ruby allows local users
  to obtain the X-Api-Key value by listing the curl process.
* CVE-2014-0081: Multiple cross-site scripting (XSS) vulnerabilities in rails
* CVE-2014-0082: Denial of service in Rails before 3.2.17

CVE-2014-0080 can't be backported. In order to support this check, I introduced
in development a new `Codesake::Dawn::Kb::VersionCheck` supporting beta,
release candidate and pre auxiliary version numbers. Due to deep integration
with `Codesake::Dawn::Kb::DependencyCheck`, this can't be backported to master
right now, so you can't check for
[CVE-2014-0080](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0080)
with Codesake::Dawn version 1.0.x

## Installation

To upgrade ```codesake-dawn``` to version 1.0.4 you can simply run a ```bundle
update``` command inside the project you're using ```codesake-dawn```. If
you're using the gem as a standalone gem, simply run ```gem install
codesake-dawn```.

Enjoy it!
