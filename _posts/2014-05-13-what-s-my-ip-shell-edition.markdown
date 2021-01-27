---
layout: post
title: "What's my IP, shell edition"
permalink: /2014/05/13/what-s-my-ip-shell-edition
date: 2014-05-13 17:08:02 +0100
---

Setup:

{% highlight bash %}
alias extip="dig +short myip.opendns.com @resolver1.opendns.com"
alias intip="ifconfig | grep 'inet ' | grep -v 127.0.0.1 | cut -d ' ' -f 2"
{% endhighlight %}

Usage:

{% highlight bash %}
$ extip
87.184.251.94

$ intip
192.168.2.101
{% endhighlight %}
