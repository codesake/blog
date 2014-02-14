---
layout: page
permalink: /install/index.html
description: "Installing Codesake::Dawn"
tags: [dawn, static analysis, ruby, appsec, application security]
image:
  feature: winter-dawn.jpg
  credit: Alexander Roth
  creditlink: http://www.flickr.com/photos/relexi/
---

# Install Codesake::Dawn

## Installing gem version 1.0.x

You can install latest Codesake::Dawn version, fetching it from
[Rubygems](https://rubygems.org) by typing:

```
$ gem install codesake-dawn 
```

In order to install a release candidate version, the gem install command line
is the following:

```
$ gem install codesake-dawn --pre
```

## Installing upcoming version 1.1.x

Codesake::Dawn gem is cryptographically signed since version 1.1.0. To be sure the gem you
install hasn’t been tampered, you must first add ```paolo@codesake.com```
public signing certificate as trusted to your gem specific keyring.

```
$ gem cert --add <(curl -Ls https://raw.github.com/codesake/codesake-dawn/certs/paolo_at_codesake_dot_com.pem)
```

You can install latest Codesake::Dawn version, fetching it from
[Rubygems](https://rubygems.org) by typing:

```
$ gem install codesake-dawn -P MediumSecurity
```

The MediumSecurity trust profile will verify signed gems, but allow the
installation of unsigned dependencies. This is necessary because not all of
Codesake::Dawn’s dependencies are signed, so we cannot use HighSecurity.

In order to install a release candidate version, the gem install command line
is the following:

```
$ gem install codesake-dawn --pre -P MediumSecurity
```

## Add Codesake::Dawn to project Gemfile

If you want to add dawn to your project Gemfile, you must add the following:
    
    group :development do
      gem 'codesake-dawn', :require=>false
    end

And then upgrade your bundle 

    $ bundle install

You may want to build it from source, so you have to check it out from github first:

    $ git clone https://github.com/codesake/codesake-dawn/codesake-dawn.git
    $ cd codesake-dawn
    $ rake install

And the codesake-dawn gem will be built in a pkg directory and then installed
on your system. Please note that you have to manage dependencies on your own
this way. It makes sense only if you want to hack the code or something like
that.
