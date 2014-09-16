---
title: Using awk and friends with Hadoop
tags:
- hadoop
- unix
- awk
- big data
external-url: http://grepalex.com/2013/01/17/awk-with-hadoop-streaming/
---
Use the friendly awk to analyze/manipulate large data files directly on hdfs.

A much better alternative to the very common flow of

1. `-get` the files to local disk
2. process ‘em using awk, grep and what not
3. `-put` the files back on hdfs if required
