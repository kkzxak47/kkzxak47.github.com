---
layout: post
title: "arrow keys in vim of cygwin output ABCD"
description: "arrow key vim solution"
category: "software"
tags: [cygwin, vim]
---
{% include JB/setup %}
#### Just installed cygwin in windows 7, and the arrow keys in vim are acting like crazy: they are spitting out ABCD!
This is because I don't have vim configured, the config file does not exist in user directory.
Simple solution:
> cp /usr/share/vim/vim73/vimrc_example.vim ~/.vimrc

Note that depending on your vim version, the "vim73" part may vary.
