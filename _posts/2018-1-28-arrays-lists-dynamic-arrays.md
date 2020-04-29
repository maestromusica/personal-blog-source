---
layout: post
title: "Interview preparations: Introduction to arrays, lists and dynamic arrays"
categories: interview-preparations
---

Modern programming languages abstract a lot of low-level details of how our code
works. Nonetheless, a good understanding of underlying computer science concepts
can help you write better code… and pass technical interviews 😉 Let’s talk about two fundamental data structures everyone needs to know:
**arrays** and **linked lists**.

{% figure [caption:"Photo by [Tim Gouw](https://www.pexels.com/photo/businesswomen-businesswoman-interview-meeting-70292/)"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/800/1*reYwnxuSVfy--DXjFgnjhQ.jpeg)
{% endfigure %}

### So what are arrays and linked lists? Let’s think low-level.

An array is a collection of variables (or objects) that is stored in a memory as
a consecutive block of data.

{% figure [caption:"myArray in memory"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/800/1*htdnGT1LBPpiRMuw4sRkPg.png)
{% endfigure %}

When an array is declared, an appropriately sized block of memory is reserved.

**An array has a constant size.** The memory “following” the array might be
already in use, so we can’t just make the array “longer” to store more elements.

Each element in the array has some index `i` that tells us where the element is
in the array.

Element’s address (where it is located in the memory) can be easily computed. We
need the address of the beginning of the array (called **base address**), and an
index `i` of that element:

`element_address = base_address + i * element_size`

This is important, because it allows us to **quickly access any element with a
known index.**

> An **array is just a block of memory containing a number of variables or objects**.

All elements are stored in order, one after another.

On the contrary, in a **linked list** there is no particular order in which
list’s elements are located in memory: they might be non-consecutive and
out-of-order. This is because memory is allocated as we create elements, on
as-needed basis.

{% figure [caption:"Linked list in memory"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/800/1*8ww-gpHZ-u7pJb1DTThWzw.png)
{% endfigure %}

In a (singly) linked list each element is represented by:

* the element itself
* a pointer `next_element` (represented by arrows on the illustration) to the next
element in the list

We have to keep a pointer (usually called `head`) to the first element in the
list. Often, we want to keep a pointer (usually called `tail`) to the last
element in the list for fast access. To summarize:

    Element contains:
       value - value/object we're storing
       next_element - pointer to the next element in the list

    LinkedList contains:
       head - pointer to the first element in the list
       tail - pointer to the last element in the list

### **Dynamic array**

#### **Arrays always have a constant size. What can we do if you want to add another element to an already full array?**

We can: 1) create a new, bigger array, 2) copy all elements from the old array
to it, 3) add the new element at the end.

[Dynamic arrays](https://en.wikipedia.org/wiki/Dynamic_array) use this approach.
To add a new element:

A) If there is space in the underlying array — just add the element<br> B) If
there is no more space for a new element — create a new, bigger array (typically
**twice the size**), copy all elements from the old array, and add the new
element at the end (see illustration below).

{% figure [caption:"Inserting elements into a dynamic array
([source](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Dynamic_array.svg/289px-Dynamic_array.svg.png))"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/800/1*gIsT4ryqzI3_gaMgFjte3A.png)
{% endfigure %}

**Size** (or **logical size**) is the number of elements that are stored in our
data structure. **Capacity** is the maximum number of elements that could fit in
the underlying array. For example, on the illustration below, initial capacity
of the array is 2 and its size is 1.

**Are those… turtles?**😱

Yes.

Notice that sometimes inserting a new element happens very fast (case A), but
sometimes we need to **copy an entire array** (case B). Thus, occasionally an
insertion will take longer (as indicated by those adorable turtles).

How much longer? That depends on the number of elements in the array — copying
an array takes linear time.

**That's quite sluggish, isn’t?**

Well, yeah, dynamic arrays are not *always* fast. But those slow insertions are
not happening that often…

> It can be [proved](http://www.cs.cornell.edu/courses/cs3110/2011sp/Lectures/lec20-amortized/amortized.htm) that **inserting an element into a dynamic array takes, on average, constant time**.

#### Wait, how can this be true?

A “proper” proof is beyond the scope of this article, but I’ll try to give you an intuitive explanation.

When doubling the size of the array, we have to copy some number of elements (let’s call that number `x`).

Newly allocated, bigger array will have `x` “free spots”, so next `x` insertions will be fast.

The “cost” of copying the array is proportional to `x`, but it is “amortized” over `x` insertions. Thus, average cost “per insertion” is constant.

If you’re still confused (or curious), you might want to watch this excellent video on Coursera:

#### Hey, but what about this extra memory we reserved? What happens when we remove elements?

Good question. Imagine a full dynamic array with a capacity of 10 000 elements. Now, let’s suppose we remove 9 000 elements.

If we don’t resize the underlying array, our data structure will only use 10% of the allocated space. That’s not good.

Just as we increased the capacity of the array when adding elements, we should reduce the capacity when removing elements.

Typically, when the size of a dynamic array drops below a certain percentage of it’s capacity, we move all elements to a new, smaller array.

Like when adding elements, just the other way around!

#### But I always just added and removed elements without think about any of those things!

Many high-level programing languages provide functionality of dynamic arrays “out of the box”. JavaScript engines do
[magic](https://blogs.msdn.microsoft.com/jscript/2008/03/26/performance-optimization-of-arrays-part-i/) that allows programmer to add and remove elements from the array as he pleases. In Python, lists are implemented using [dynamic arrays with some extra cleverness
added](https://docs.python.org/2/faq/design.html#how-are-lists-implemented).

Abstracting such details allows you to focus on solving the problem at hand and makes developing software easier.

*****

We talked about 3 fundamental data structures: arrays, lists and dynamic arrays.
But we barely scratched the surface.

In the next part we will compare those data structures. We will investigate
operations supported by them, and their time complexity.

Thanks for reading!
