---
title: "ActiveRecord::Batches#find_each"
layout: post
date: 2020-01-09
image: /assets/images/markdown.jpg
headerImage: false
tag:
- ruby
category: blog
author: nkumar
description: ActiveRecord
permalink: blog/:title/
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

### #each
Looping through a collection of records from the database (using the all method, for example) is very inefficient 
since it will try to instantiate all the objects at once and it causes more and more memory to be consumed over time.
{% highlight ruby %}
 Project.all.each(&:recalculate_statistics!)
{% endhighlight %}

### ActiveRecord::Batches#find_each
Batch processing methods allow you to work with the records in batches, thereby greatly reducing memory consumption.
The #find_each method uses #find_in_batches with a batch size of 1000 (or as specified by the :batch_size option).

{% highlight ruby %}
Person.find_each do |person|
  person.do_awesome_stuff
end

Person.where("age > 21").find_each do |person|
  person.party_all_night!
end
{% endhighlight %}

It's not possible to set the order. That is automatically set to ascending on the primary key (“id ASC”) to make the batch ordering work. 
This also means that this method only works with integer-based primary keys.

So when the query returns a number of records that would be too much memory for the server's available resources, 
then using #find_each would be a great choice.

HAPPY NEW YEAR, GUYS....
