---
layout: post
title: Hadoop installation on Ubuntu - cheatsheet
date: '2013-01-25T23:36:00+05:30'
category: technology
comments: true
tags:
- hadoop
- ubuntu
- cdh
tumblr_url: http://sandeep-n.tumblr.com/post/41451162984/hadoop-installation-on-ubuntu-cheatsheet
crosspost_to_medium: true
---
I had tried installing various versions of hadoop manually on my ubuntu box, but every try ended up in a mess.

So the Best way I found to do it is to install using the [cloudera distribution](http://www.cloudera.com/).  
Here is a quick cheatsheet with the steps to install hadoop on your ubuntu machine.

<!--more-->
##Installation

1. Add Cloudera Repo:

        cat /etc/apt/sources.list.d/cloudera.list <
        deb [arch=amd64] http://archive.cloudera.com/cdh4/ubuntu/precise/amd64/cdh precise-cdh4 contrib
        deb-src http://archive.cloudera.com/cdh4/ubuntu/precise/amd64/cdh precise-cdh4 contrib
        [press ctrl+d]

2. On ResourceManager host, install Hadoop with YARN

        sudo apt-get install hadoop-yarn-resourcemanager

    Packages that will be installed:  
    >    bigtop-utils  
    >    hadoop  
    >    hadoop-yarn  
    >    hadoop-yarn-resourcemanager  
    >    zookeeper  

3. On NameNode host

        sudo apt-get install hadoop-hdfs-namenode

    Packages that will be installed:  
    >    bigtop-jsvc  
    >    hadoop-hdfs  
    >    hadoop-hdfs-namenode  


4. On SecondaryNameNode host

        sudo apt-get install hadoop-hdfs-secondarynamenode

    Packages that will be installed:  
    >    hadoop-hdfs-secondarynamenode

5. On cluster hosts (except ResourceManager):

        sudo apt-get install hadoop-yarn-nodemanager hadoop-hdfs-datanode hadoop-mapreduce

    Packages that will be installed:
    >   hadoop-hdfs-datanode  
    >   hadoop-mapreduce  
    >   hadoop-yarn-nodemanager  

6. Add JAVA_HOME to the conf file

        echo $JAVA_HOME <copy the output of this command>
        open `/etc/default/hadoop` in any text editor and add the below line at the end
        export JAVA_HOME=<JAVA_HOME path>

## HDFS Commands

Start hdfs services

    for service in /etc/init.d/hadoop-hdfs-*
    do
        sudo $service start
    done

Format hdfs for initial use

    sudo -u hdfs hdfs namenode -format

## YARN
Start YARN services

    sudo /etc/init.d/hadoop-yarn-resourcemanager start
    sudo /etc/init.d/hadoop-yarn-nodemanager start
    sudo /etc/init.d/hadoop-mapreduce-historyserver start
