---
layout: post
title:      "A perspective on yield"
date:       2018-03-21 18:53:56 -0400
permalink:  yield_is_the_aquaman_of_programming
---

(From the point of view of someone who had a poor teacher. Let this be a lesson to you all)
(I later discovered I was wrong about these.)


![](https://1.bp.blogspot.com/-Q_RkNdVzFZc/WPzHoIzLeZI/AAAAAAAAELc/71VQQMth7gssdWx2lQ-ZTTBWtVEdnjAeACLcB/s400/Super_Antics_12.jpg)

It is near useless. 
Yield is a placeholder in order to insert more code after a method is called.

it is usually in the form of do or {} after a method is called

ex:    my_method([1,2,3,4]){}

but very few things can be placed inside the methods aside from putting strings  or integers. You can't access any variables.

I even tried asking a question about  yield to people far smarter than me. The response was "just put in yield. you're overthinking it."

Yield is much like aquaman, who can't fly or shoot laser beams, or move quickly outside of water.

But for the sake of my last lab, which was to make an each method without .each, using yield and  while.

I ended up gettting this.

def my_each(collection)
  i = 0
  while i < collection.length #works with arrays too!
   yield collection[i]
    i += 1
  end
  collection
end

Which is no different from this.


def my_each(collection)
  i = 0
  while i < collection.length #works with arrays too!
   collection[i]
    i += 1
  end
  collection
end



