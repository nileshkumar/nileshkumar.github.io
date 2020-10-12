---
title: "Truncate file: Linux"
layout: post
date: 2020-10-12
image: /assets/images/markdown.jpg
headerImage: false
tag:
- linux
category: blog
author: nkumar
description: Truncate a file
permalink: blog/:title/
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

###
Over time, size of the log files becomes gigantic. And we do not want the disk space covered with this size.
So we can truncate these growing log files using Truncate command in Linux:

```console
truncate -s 0 filename
```
For example, to empty the development log you would use:
```console
sudo truncate -s 0 /var/log/development.log
```

This way our disk size will be always in check.  
