---
layout: page
permalink: /using/index.html
description: "Using Codesake::Dawn"
tags: [dawn, static analysis, ruby, appsec, application security]
image:
  feature: winter-dawn.jpg
  credit: Alexander Roth
  creditlink: http://www.flickr.com/photos/relexi/
---

# Using Codesake::Dawn

You can start your code review with Codesake::Dawn very easily. Simply tell the tool
where the project root directory. 

Underlying MVC framework is autodetected by Codesake::Dawn using target Gemfile.lock
file. If autodetect fails for some reason, the tool will complain about it and
you have to specify if it's a rails, sinatra or padrino web application by
hand.

Basic usage is to specify some optional command line option to fit best your
needs, and to specify the target directory where your code is stored.

```
$ dawn [options] target
```

In case of need, there is a quick command line option reference running ```dawn -h``` at your OS prompt.

    $ dawn -h

    Usage: dawn [options] target_directory

    Examples:
        $ dawn a_sinatra_webapp_directory
        $ dawn -C the_rails_blog_engine
        $ dawn -C --json a_sinatra_webapp_directory        
        $ dawn --ascii-tabular-report my_rails_blog_ecommerce        
        $ dawn --html -F my_report.html my_rails_blog_ecommerce

    -r, --rails                                  force dawn to consider the target a rails application   
    -s, --sinatra                                force dawn to consider the target a sinatra application   
    -p, --padrino                                force dawn to consider the target a padrino application
    -G, --gem-lock                               force dawn to scan only for vulnerabilities affecting dependencies in Gemfile.lock
    -D, --debug                                  enters dawn debug mode
    -f, --list-known-framework                   list ruby MVC frameworks supported by dawn
    -k, --list-knowledgebase [check_name]        list dawn known security checks. If check_name is specified dawn says if check is present or not
    -a, --ascii-tabular-report                   cause dawn to format findings using table in ascii art   
    -j, --json                                   cause dawn to format findings using json   
    -V, --verbose                                the output will be more verbose   
    -C, --count-only                             dawn will only count vulnerabilities (useful for scripts)   
    -z, --exit-on-warn                           dawn will return number of found vulnerabilities as exit code
    -F, --file                                   tells dawn to write output to filename   
    -v, --version                                show version information
    -h, --help                                   show this help

## Codesake::Dawn security scan in action

As output, Codesake::Dawn will put all security checks that are failed during the scan.

This the result of Codedake::Dawn running against a 
[Sinatra 1.4.2 web application](https://github.com/thesp0nge/railsberry2013) wrote for a talk I
delivered in 2013 at [Railsberry conference](http://www.railsberry.com).

As you may see, Codesake::Dawn first detects MVC running the application by
looking at Gemfile.lock, than it discards all security checks not appliable to
Sinatra (49 security checks, in version 1.0, especially designed for Ruby on
Rails) and it applies them.

    $ bundle exec dawn ~/src/hacking/railsberry2013
    08:09:47 [*] dawn v1.0.0 is starting up
    08:09:47 [$] dawn: scanning /Users/thesp0nge/src/hacking/railsberry2013
    08:09:47 [$] dawn: sinatra v1.4.2 detected
    08:09:47 [$] dawn: applying all security checks
    08:09:47 [$] dawn: 82 security checks applied - 0 security checks skipped
    08:09:47 [$] dawn: 1 vulnerabilities found
    08:09:47 [$] dawn: CVE-2013-1800 failed
    08:09:47 [$] dawn: Description: The crack gem 0.3.1 and earlier for Ruby does not properly restrict casts of string values, which might allow remote attackers to conduct object-injection attacks and execute arbitrary code, or cause a denial of service (memory and CPU consumption) by leveraging Action Pack support for (1) YAML type conversion or (2) Symbol type conversion, a similar vulnerability to CVE-2013-0156.
    08:09:47 [$] dawn: Solution: Please use crack gem version 0.3.2 or above. Correct your gemfile
    08:09:47 [!] dawn: Evidence:
    08:09:47 [!] dawn: Vulnerable crack gem version found: 0.3.1
    08:09:47 [*] dawn is leaving

---

When you run Codesake::Dawn on a web application with up to date dependencies,
it's likely to return a friendly _no vulnerabilities found_ message. Keep it up
working that way!

This is Codesake::Dawn running against a Padrino web application I wrote for [a
scorecard quiz game about application security](http://scorecard.armoredcode.com). 
Italian language only. Sorry.

```
08:17:09 [*] dawn v1.0.0 is starting up
08:17:09 [$] dawn: scanning /Users/thesp0nge/src/CORE_PROJECTS/scorecard
08:17:09 [$] dawn: padrino v0.11.2 detected
08:17:09 [$] dawn: applying all security checks
08:17:09 [$] dawn: 82 security checks applied - 0 security checks skipped
08:17:09 [*] dawn: no vulnerabilities found.
08:17:09 [*] dawn is leaving
```

---

Last example shows Codesake::Dawn against a very simple Sinatra application
designed to be buggy:

```
$ dawn target
08:28:18 [*] dawn v1.0.0 is starting up
08:28:18 [$] dawn: scanning /Users/thesp0nge/tmp/sinatra-vulnerable
08:28:18 [$] dawn: sinatra v1.2.6 detected
08:28:18 [$] dawn: applying all security checks
08:28:18 [$] dawn: 82 security checks applied - 0 security checks skipped
08:28:18 [$] dawn: 5 vulnerabilities found
08:28:18 [$] dawn: Not revised code failed
08:28:18 [$] dawn: Description: Analyzing comments, it seems your code is waiting from some review from you. Please consider take action before putting it in production.
This check will analyze the source code looking for the following patterns: XXX, TO_CHECK, CHECKME, CHECK and FIXME
08:28:18 [$] dawn: Solution: Please review the file fixing the issue.
08:28:18 [!] dawn: Evidence:
08:28:18 [!] dawn: {:filename=>"/Users/thesp0nge/tmp/sinatra-vulnerable/application.rb", :matches=>[{:match=>"# FIXME: I must raise an error here\n", :line=>30}]}
08:28:18 [$] dawn: CVE-2013-0269 failed
08:28:18 [$] dawn: Description: The JSON gem before 1.5.5, 1.6.x before 1.6.8, and 1.7.x before 1.7.7 for Ruby allows remote attackers to cause a denial of service (resource consumption) or bypass the mass assignment protection mechanism via a crafted JSON document that triggers the creation of arbitrary Ruby symbols or certain internal objects, as demonstrated by conducting a SQL injection attack against Ruby on Rails, aka "Unsafe Object Creation Vulnerability."
08:28:18 [$] dawn: Solution: Please upgrade JSON gem to version 1.5.5, 1.6.8 or 1.7.7 or latest version available
08:28:18 [!] dawn: Evidence:
08:28:18 [!] dawn: Vulnerable json gem version found: 1.4.6
08:28:18 [$] dawn: CVE-2013-1800 failed
08:28:18 [$] dawn: Description: The crack gem 0.3.1 and earlier for Ruby does not properly restrict casts of string values, which might allow remote attackers to conduct object-injection attacks and execute arbitrary code, or cause a denial of service (memory and CPU consumption) by leveraging Action Pack support for (1) YAML type conversion or (2) Symbol type conversion, a similar vulnerability to CVE-2013-0156.
08:28:18 [$] dawn: Solution: Please use crack gem version 0.3.2 or above. Correct your gemfile
08:28:18 [!] dawn: Evidence:
08:28:18 [!] dawn: Vulnerable crack gem version found: 0.3.1
08:28:18 [$] dawn: CVE-2013-4164 failed
08:28:18 [$] dawn: Description: Any time a string is converted to a floating point value, a specially crafted string can cause a heap overflow. This can lead to a denial of service attack via segmentation faults and possibly arbitrary code execution. Any program that converts input of unknown origin to floating point values (especially common when accepting JSON) are vulnerable.
08:28:18 [$] dawn: Solution: All users are recommended to upgrade to Ruby 1.9.3 patchlevel 484, ruby 2.0.0 patchlevel 353 or ruby 2.1.0 preview2.
08:28:18 [!] dawn: Evidence:
08:28:18 [!] dawn: ruby v2.0.0-p247 detected
08:28:18 [$] dawn: 1 reflected XSS found
08:28:18 [$] dawn: request parameter "name"
08:28:18 [*] dawn is leaving
```

If you need a fancy HTML report about your scan, just ask to Codesake::Dawn

```
$ dawn /Users/thesp0nge/src/hacking/rt_first_app --html --file report.html          (ruby-2.0.0-p353@codesake)

09:00:54 [*] dawn v1.1.0 is starting up
09:00:54 [!] dawn: this is a development Codesake::Dawn version
09:00:54 [*] dawn: report.html created (2952 bytes)
09:00:54 [*] dawn is leaving
```
