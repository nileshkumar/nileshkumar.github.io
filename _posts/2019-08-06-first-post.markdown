---
title: "Rails: Delegate"
layout: post
date: 2019-08-06
image: /assets/images/markdown.jpg
headerImage: false
tag:
- rails
- ruby
category: blog
author: nkumar
description: Markdown summary with different options
permalink: blog/:title/
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

### Understanding delegate:

Provides a delegate class method to easily expose contained objects’ public methods as your own. Delegation is particularly useful with Active Record associations:

### Syntax
{% highlight ruby %}
delegate(*methods, to: nil, prefix: nil, allow_nil: nil)
{% endhighlight %}

### Usage
The macro receives one or more method names (specified as symbols or strings) and the name of the target object via the :to option (also a symbol or string).

{% highlight ruby %}
class Book < ApplicationRecord
  def author
    "DHH"
  end
  
  def price
    "$10"
   end
end

class Page < ApplicationRecord
  belongs_to :book
  delegate :author, :price, to: :book
end
Page.new.author   # => "DHH"
Page.new.price    # => "$10"
{% endhighlight %}

If the target is nil and does not respond to the delegated method a +Module::DelegationError+ is raised. If you wish to instead return nil, use the :allow_nil option.

{% highlight ruby %}
  class User < ApplicationRecord
    has_one :profile
    delegate :age, to: :profile
  end

  User.new.age
  # => Module::DelegationError: User#age delegated to profile.age, but profile is nil
{% endhighlight %}

But if not having a profile yet is fine and should not be an error condition:

{% highlight ruby %}

  class User < ApplicationRecord
    has_one :profile
    delegate :age, to: :profile, allow_nil: true
  end

  User.new.age # nil

{% endhighlight %}

The :prefix can be set to true to prefix the delegate method with the name of the object being delegated to.
{% highlight ruby %}

  class Post
    belongs_to :user

   delegate :name, :to => :user, :prefix => true
    # post.user_name

   delegate :name, :to => :user, :prefix => "author"
     # post.author_name
   end
{% endhighlight %}

That's all folks!!!  :)
