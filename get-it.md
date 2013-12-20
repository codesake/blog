---
layout: page
permalink: /get-it/index.html
title: How to get codesake-dawn security source code scanner
tagline: How to fetch repository or how to download the gem
tags: [about, codesake-dawn, application security, get it]
modified: 12-19-2013
image:
  feature: 
  credit: 
  creditlink: 
---

codesake-dawn security source code scanner is a ruby application itself. The
source code is opensource (and it will be open **ever**) and licensed under the
MIT license.

## Grab the sources

The source code is hosted on [github.com](https://github.com/codesake/codesake-dawn).

If you want to stay cutting edge, you may want to use codesake-dawn from sources. 

First step is cloning the repository on your machine and then building the gem from source.
Procedure is straightforward easy:

    $ git clone https://github.com/codesake/codesake-dawn/codesake-dawn.git
    $ cd codesake-dawn
    $ rake install

The codesake-dawn gem will be built in a pkg directory and then installed
on your system. Please note that you have to manage dependencies on your own
this way. Personally I created a gemset using rvm and managing my local bundle
this way.

## Install the package from the Internet

You can install dawn, directly using [Rubygems](https://rubygems.org) by typing:

    gem install codesake-dawn

If you want to add dawn to your project Gemfile, you must add the following:
    
    group :development do
      gem 'codesake-dawn', :require=>false
    end

And then upgrade your bundle 

    $ bundle install
