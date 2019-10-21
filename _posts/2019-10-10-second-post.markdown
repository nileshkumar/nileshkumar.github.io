---
title: "Time Difference in Rails"
layout: post
date: 2019-10-10 22:48
image: /assets/images/markdown.jpg
headerImage: false
tag:
- ruby
- rails
category: blog
author: nkumar
description: Time difference in rails
permalink: blog/:title/
---
### Time Difference
Many times while coding we need to have the difference of timestamps. But in Rails we can’t simply subtract the timestamps to get the difference.
We can achieve this by following code:
{% highlight ruby %}
(Time.parse(DateTime.now.to_s) - Time.parse(current_user.created_at.to_s))/3600
{% endhighlight %}

It will give in the difference in hours.  <br/>

Now try it out in your code..  :)
