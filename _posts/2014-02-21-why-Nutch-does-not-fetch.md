---
layout: post
title: "Why Nutch does not fetch"
description: "Nutch"
category: "Java"
tags: [Java, Nutch]
---
{% include JB/setup %}

If you find this:
```html
0/0 spinwaiting/active, 0 pages, 0 errors, 0.0 0 pages/s, 0 0 kb/s, 0 URLs
in 0 queues
-activeThreads=0
FetcherJob: done
```

I believe your nutch is not set properly.
You need to edit "{NUTCH_HOME}/runtime/local/conf/nutch-site.xml", add the following property between &lt;configuration&gt; and &lt;/configuration&gt;.
```xml
<property>
  <name>http.content.limit</name>
  <value>-1</value>
  <description>The length limit for downloaded content using the http
  protocol, in bytes. If this value is nonnegative (>=0), content longer
  than it will be truncated; otherwise, no truncation at all. Do not
  confuse this setting with the file.content.limit setting.
  </description>
</property>
```

Alternatively you can add this one, the description explains why.
```xml
<property>
  <name>parser.skip.truncated</name>
  <value>false</value>
  <description>Boolean value for whether we should skip parsing for truncated documents. By default this 
  property is activated due to extremely high levels of CPU which parsing can sometimes take.  
  </description>
</property>
```

That is: either you order Nutch not to truncate anything, or if the webpage gets truncated, do not skip it.