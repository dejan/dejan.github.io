---
layout: post
title: "Don't escape in Strings"
permalink: /2008/10/26/dont-escape-in-strings
date: 2008-10-26 17:08:02 +0100
---

Please don't do:

{% highlight ruby %}
"#{name} said: \"Clap your hands!\""
{% endhighlight %}

It's ugly and you don't need it. Ruby has excellent support for arbitrary delimiters for string literals.

Above can be rewritten as:

{% highlight ruby %}
%-#{@name} says: "Clap your hands!"-
{% endhighlight %}

… or if String contains dash:

{% highlight ruby %}
%/#{@name} says: "Play tic-tac-toe!"/
{% endhighlight %}

... or if String contains dash and slash:

{% highlight ruby %}
%Q|#{@name} says: "Try ftp://ruby-lang.org/pub/ruby/1.9/"|
{% endhighlight %}

... and so on. No need to escape.

Excerpt from the great book [The Ruby programming Language](https://www.amazon.com/Ruby-Programming-Language-Everything-Need/dp/0596516177):

> "The sequence %q begins a string literal that follows single-quoted string rules, and the sequence %Q (or just %) introduces a literal that follows double-qouted string rules. The first character following q or Q is the delimiter, and the string literal continues until a matching delimiter is found. If the opening delimiter is (, [, {, or <, then the matching delimiter is ), ], }, or >. Otherwise, the closing delimiter is the same as the opening delimiter."
