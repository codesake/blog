--- 
tags: 
title: Hello world, again
image: 
  cover: 
layout: post
published: true
categories: article
---

# Introduction

It was almost one year ago, I last wrote on codesake.com blog. I was sketching
up a [padrino](http://www.padrinorb.com) web application with a gem, called
sake, that it wasn't ever released and It was intended to be both static than
dynamic source code analysis engine for my application security software as a
service platform.

In April 2013, after the successful experience at
[railsberry](https://www.railsberry.com) I started coding
[codesake-dawn](https://rubygems.org/gems/codesake-dawn), a source code static
analyzer for security issues, designed to work for web applications written in
Ruby programming language.

# The security checks

[codesake-dawn](https://rubygems.org/gems/codesake-dawn) supports either rails,
padrino and sinatra MVC ruby framework. Its security checks are implemented
with native ruby classes. 

There are **four** basic security checks:

* dependency check 
* ruby interpreter check
* pattern matching check
* combo check

At the time of writing this, in version 0.80, there are 75 security checks.

## Dependency check
Most of the security controls implemented in
[codesake-dawn](https://rubygems.org/gems/codesake-dawn) are about auxiliary
rubygems your web application it depends upon. Let's assume you're a skilled
developer and you care about your code. Your web application is solid but one
of the rubygems you used in your project introduces a security issues. The
application itself is than vulnerable and your effort is wasted.

That's why testing for security issues introduced by dependencies is so important.

## Ruby interpreter check
Sometimes the vulnerability is in the programming language interpreter itself.
Recently there were discovered some heap based buffer overflow in ruby that
eventually could lead in remote code execution. This is bad, and that's why
there is a basic check for ruby interpreter.

## Pattern matching check
This is an heuristic check it can lead to false positives. Let's assume that
some keywords introduces security issues when found in a code, is it possible
with a grep-like security check to spot them. 
False positives are still possible since the context is not analyzed at all. 

In [codesake-dawn](https://rubygems.org/gems/codesake-dawn) checks implementing
this basic class are the ones related to quality (unmanaged code, FIXME or TODO
marked routines, ...).

## Combo check
For more complex security issues it was necessary to combine together different
basic checks, that's why the combo check was designed.

No real magic here, just a bunch of basic checks in OR or in AND.

