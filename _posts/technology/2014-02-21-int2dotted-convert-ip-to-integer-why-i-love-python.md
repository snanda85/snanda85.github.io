---
layout: post
title: int2dotted - Convert IP to Integer | Why I love python
subtitle: A small tool to convert ip addresses in different notations
date: '2014-02-21T00:31:08+05:30'
category: technology
comments: true
tags:
- python
- why i love python
- ip address
---
<a href="https://github.com/snanda85/int2dotted"><img style="position: absolute; top: 0; right: 0; border: 0;width:auto;padding:0;margin:0;box-shadow:none;" src="https://github-camo.global.ssl.fastly.net/365986a132ccd6a44c23a9169022c0b5c890c387/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f7265645f6161303030302e706e67" alt="Fork me on GitHub" data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_red_aa0000.png"></a>
##Problem
I work with routing data and I need to convert IP addresses between *Expanded* and *Integer* notations very frequently. There are a couple of existing options to deal with this:

1. A few websites like [this](http://www.aboutmyip.com/AboutMyXApp/IP2Integer.jsp) provide this facility, but frequently switching between a browser and a unix terminal is really a hassle.
2. A set on \*nix tools by the same name, but like other \*nix tools this is not available for all unix flavors.

##Solution
Neither of the above tools was great for me, so one fine day I fired up `vi` and started coding it myself.  
As it turned out, this wasn’t a difficult task after all.

<!--more-->

**Convert an IPv4 address to Integer.** Just one line of code:  

``` Python
struct.unpack("!i", socket.inet_pton(socket.AF_INET, addr))[0]
```

1. `socket.inet_pton(socket.AF_INET, addr)` converts an ip address string to a packed binary format.
2. `struct.unpack` decodes this binary data. The first argument `!i` tells that the byte order is network and the data needs to be interpreted to int

**Convert an Integer to IPv4 string**  

``` Python
socket.inet_ntoa(struct.pack("!i", integer))
```

This is the exact reverse of the above code. `struct.pack` encodes the integer to binary data and then `socket.inet_ntoa` converts the binary data to IPv4 string notation.

A couple of similar lines were added for IPv6 handing, and Voilà..We have a cross platform tool to convert ip address notations.

The source code of this tool is hosted on [github](https://github.com/snanda85/int2dotted). Take a look, Fork it and feel free to suggest any enhancements or gotchas.

