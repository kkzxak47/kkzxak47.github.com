---
layout: post
title: "difference between [set()]*10 and [set() for _ in xrange(10)]"
description: ""
category: "Python"
tags: [Python]
---
{% include JB/setup %}

In a Python REPL,
> \>>> a = [set()]*10
>  
> \>>> b = [set() for _ in xrange(10)]
> 
> \>>> a==b

> True

This is deceiving, cause a and b are not the same at all.
If you add an element to a[0], you will know why:

> \>>> a[0].add('ss')
>
> \>>> a
> 
>[set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss']), set(['ss'])]
>
> \>>> b[0].add('ss')
> 
> \>>> b
> 
> [set(['ss']), set([]), set([]), set([]), set([]), set([]), set([]), set([]), set([]), set([])]
> 
> \>>> a==b
> 
> False

Explanation: http://www.python-course.eu/deep_copy.php
