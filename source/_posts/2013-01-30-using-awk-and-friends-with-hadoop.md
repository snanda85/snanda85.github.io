---
layout: post
title: Using awk and friends with Hadoop
date: '2013-01-30T21:49:35+05:30'
tags:
- hadoop
- unix
- awk
- big data
tumblr_url: http://sandeep-n.tumblr.com/post/41870127098/using-awk-and-friends-with-hadoop
external-url: http://grepalex.com/2013/01/17/awk-with-hadoop-streaming/
---
Use the friendly awk to analyze/manipulate large data files directly on hdfs.

A much better alternative to the very common flow of

1. `-get` the files to local disk
2. process ‘em using awk, grep and what not
3. `-put` the files back on hdfs if required
