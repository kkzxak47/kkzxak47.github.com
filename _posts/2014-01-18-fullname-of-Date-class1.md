---
layout: post
title: "java.util.Date.class and Date.class"
description: ""
category: "Java"
tags: [BeanUtils]
---
{% include JB/setup %}
#### This is odd.
If you want to convert a String to a Date, and write the code like

```java
ConvertUtils.register(dateConverter, Date.class);
```

console would give you this warning

```log
一月 18, 2014 8:39:22 上午 org.apache.commons.beanutils.converters.DateConverter toDate
警告:     DateConverter does not support default String to 'Date' conversion.
一月 18, 2014 8:39:22 上午 org.apache.commons.beanutils.converters.DateConverter toDate
警告:     (N.B. Re-configure Converter or use alternative implementation)
```

if you change the code to

```java
ConvertUtils.register(dateConverter, java.util.Date.class);
```

everything will be fine again.

Don't understand why yet.

# sh_t happens. It turns out I imported another Date in java.sql
