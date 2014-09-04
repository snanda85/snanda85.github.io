---
layout: post
title: Singletons in Python
subtitle: My experience with implementing singleton pattern in python
date: '2014-07-17T00:27:59+05:30'
category: technology
comments: true
tags:
- python
- singleton
- my experience
tumblr_url: http://sandeep-n.tumblr.com/post/91970350712/singletons-in-python
---
There are quite a few ways to implement Singletons in python. Here are a couple of them and my experiences with them:

1. Base class ([Example](http://stackoverflow.com/a/1810391/956362)): A base class is created with a `__new__` method which takes care of keeping track of the single instance of the class. Your custom singleton classes will inherit from this class.  
   *Problem*: We need to take care when using multiple inheritance. What happens if multiple base classes (or the derived class) needs to override the `__new__` method?

2. Metaclass ([Example](http://stackoverflow.com/a/33201/956362)): Neatest method of all. Create a Metaclass to keep track of the instances of each class it creates.  
   *Problem*: `__metaclass__` is not beautiful. And I don’t want my new-to-python users to put their heads in how `__metaclass__` works. Why complicate their lives?

<!--more-->

**My solution**: A variation of the metaclass approach. Create a metaclass to implement Singleton, but abstract its use through a base class.

```Python
class MetaSingleton(type):
    _instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(MetaSingleton, cls).__call__(*args, **kwargs)
        return cls._instances[cls]

class SingletonMixin(object):
    """A singleton mixin which can be subclassed to create singleton classes"""
    __metaclass__ = MetaSingleton
```


Now, a new singleton class can be created as:

```Python
class MyClass(SingletonMixin):
    pass

>>> obj1 = MyClass()
>>> obj2 = MyClass()
>>> obj1
<__main__.MyClass object at 0x10d7fb850>
>>> obj2
<__main__.MyClass object at 0x10d7fb850>
# Note that both the names (obj1 and obj2) refer to the same instance.
```

Note: All of this is for python 2
