---
title: "Sending High Priority Email"
layout: post
date: 2019-10-15
image: /assets/images/markdown.jpg
headerImage: false
tag:
- rails
category: blog
author: nkumar
description: Email in Rails
permalink: blog/:title/
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

### High Priority Emails

We all have seen sending High priority mails in our MS-Outlook/Thunderbird mail clients. 
If we want to achieve same in Rails, we have to use the syntax as mentioned below in our mailer model file:

{% highlight ruby %}
 def send_high_priority_mail
 email_params.merge!({
        'Importance' => 'high', # for all mail clients supporting MIME RFC 4021
        'X-Priority' => '1', # for newer Outlooks
        'X-MSMail-Priority' => 'High' # for older Outlooks
      })
     
    mail(email_params)
 end
{% endhighlight %}

### Email With Attachment

Now, suppose we need to send an email containing attachment. We can do this by these steps mentioned below:
{% highlight ruby %}
 def send_mail_with_attachment(file)
   if file
      attachments[file.original_filename] =  {
        :content=> file.read,
        :mime_type=> file.content_type
        }
    end
 end
{% endhighlight %}

Now prioritize your email... :)
