---
title: "Ruby Enumerable: Detect vs Select"
layout: post
date: 2019-10-25
image: /assets/images/markdown.jpg
headerImage: false
tag:
- ruby
category: blog
author: nkumar
description: Ruby Enumerables
permalink: blog/:title/
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

### Enumerable: Detect vs Select

The Enumerable mixin provides collection classes with several traversal and searching methods, and with the ability to sort. 
The class must provide a method each, which yields successive members of the collection.

## Detect
Returns the first for which block is not false. find is an alias for detect method.
{% highlight ruby %}
 array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
 array.detect{ |i| i > 5 }
 # => 6
{% endhighlight %}

## Select
Returns an array containing all elements of enum for which the given block returns a true value.
{% highlight ruby %}
 array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
 array.select{ |i| i > 5 }
 # => [6,7,8,9,10]
{% endhighlight %}


try this out..  ;)

