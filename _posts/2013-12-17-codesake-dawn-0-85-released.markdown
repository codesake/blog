---
layout: post
published: true
title: Codesake Dawn 0.85 released
categories: article
tags: release codesake-dawn
image:
  cover: 
---

Today, [Codesake Dawn version 0.85 has been released](https://rubygems.org/gems/codesake-dawn/versions/0.85). This release
adds support for 6 new security checks against vulnerabilities announced in the
last week.

From the [changelog](https://raw.github.com/codesake/codesake-dawn/master/Changelog.md) changes in the new version are:

* refactoring bin/dawn script: some stuff were moved into Codesake::Core class
* Added a check against Denial of Service vulnerability for Nokogiri 1.5.x 
  and 1.6.0 when used with JRuby. The announcement on [ruby-security-list](https://groups.google.com/forum/#!topic/ruby-security-ann/DeJpjTAg1FA)
* Added a check against Denial of Service vulnerability due to entity expansion
  for Nokogiri 1.5.x and 1.6.0 when used with JRuby. The announcement on [ruby-security-list](https://groups.google.com/forum/#!topic/ruby-security-ann/DeJpjTAg1FA)
* Added a check for [CVE-2013-4478](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-4478&cid=3) (sup remote code execution)
* Added a check for [CVE-2013-4479](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-4479&cid=3) (sup remote code execution)
* Added a check for [CVE-2013-1812](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-1812&cid=3) (ruby-openid denial of service)
* Added a check for [CVE-2013-6421](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-6421&cid=3) (sprout remote code execution)


To upgrade to the newest version you can issue the command: ```gem install codesake-dawn```

## Issues 

For any problem, bugs, feature requests, comments or whatever, please report it opening an [issue](https://github.com/codesake/codesake-dawn/issues) on project repository.

Also consider following [@codesake](https://twitter.com/codesake) on Twitter and use #dawnscanner hashtag.

