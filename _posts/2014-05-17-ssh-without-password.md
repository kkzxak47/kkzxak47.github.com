---
layout: post
title: "You never know what the users have done"
description: "SSH without password"
category: ""
tags: []
---
{% include JB/setup %}
    ssh-keygen -t rsa
    cat id_rsa.pub >> authorized_keys
    chmod 700 .ssh
It seems all is right, but "ssh localhost" still asks for password.
Why? Why? Why?
It turns out this friend changed "root" directory privileges to 777.
And another example is "root" being chowned to another user.
FML.