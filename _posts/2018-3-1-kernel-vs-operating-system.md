---
layout: post
title: "Interview preparations: Operating System vs Kernel"
categories: interview-preparations
---

Let’s talk about a kernel, an operating system, and all the differences between
the two. I’ll explain what happens when you turn on your computer, and when you
run programs. Computers, smartphones, even cars — operating systems are everywhere. It’s worth
knowing why we need this type of software, and what it does (other than taking
up that precious disk space).

{% figure [caption:"Almost all electronic devices run some kind of an operating system
([source](https://www.pexels.com/photo/iphone-technology-iphone-6-plus-apple-17663/))"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/1100/1*1qBb2G3QXlZUzPtN__Reog.jpeg)
{% endfigure %}

#### Why do we need an operating system?

Computers changed quite a bit since the twentieth century when they were
invented. First computers could only run a **single program** until it finished…
or crashed 😱

Each program used all of the available hardware and was responsible for all
standard tasks a computer had to perform. For example, **every program had to
contain all necessary drivers**.

Computers were not beginner friendly, to say the least.

Keeping track of what program was supposed to be run next was done by humans.
Sometimes quite a bit of creativity was required:

> At Cambridge University the job queue [a queue of programs waiting to be
> executed] was at one time a washing line from which tapes were hung with
different colored clothes-pegs to indicate job-priority.
([source](https://en.wikipedia.org/wiki/Operating_system#History))

And you’re complaining that your internet is too slow to stream Full HD videos,
huh? 🤣

As the complexity of software, demand, and the number of users grew, it became
too cumbersome and time-consuming to do all those things manually.

A program that could manage hardware, schedule program execution, and monitor
resources was needed. That software should:

1.  **Allow multiple applications to run at the same time**. Hardware resources (for
example, CPU time, network connections, opened files, and so on) should be
shared “fairly” between those programs.
1.  **Make sure that a buggy or malicious program cannot disrupt other
applications**.

### Kernel

**Kernel is an always-running program that has complete control over everything
in the system.**

When you power on your device (for example, a computer or a smartphone) a small
program called a **boot loader** is executed. Boot loader is a very small
program — it starts the process of loading the operating system (including the
kernel) and finishes immediately afterwards.

From then on, kernel is the king.

It decides what program will run next, and for how long.

It decides which memory can be used by each program.

If a program wishes to use any input/output device (like a mouse, a keyboard,
and so on), it has to request access to that device from the kernel. If multiple
programs want to access the same resource at the same time, kernel decides which
program will get access first.

Kernel makes sure that a buggy or malicious program cannot disrupt other
programs. It stops programs from monopolizing access to hardware, or modifying
memory belonging to other processes. If a program misbehaves kernel will kill it
😨

Kernel is very powerful, but it only provides a basic level of control over the
hardware it’s running on.

{% figure [caption:"Kernel is the king"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/880/1*Vg893Xwy99b_N5V6S9L0nw.jpeg)
{% endfigure %}

### Operating system

In essence, a computer is just a tool we use to get things done. It has to be
easy to use and user friendly. Hence, we need features such as a graphical user
interface, a multimedia player, antivirus software, and so on.

**An operating system (OS) consists of a kernel and additional software
providing those features**

What software is included in the operating system is entirely up to the creator
of that OS. This makes defining an OS very difficult so it’s often described as
“whatever you get when you order an operating system”.

For example, Windows 10 offers:

- a sophisticated kernel
- graphical user interface
- firewall and
antivirus software
- web browser
- multimedia player
- small utility programs like a calculator, text editor, and so on

…and many other features.

### Summary

A kernel is an essential part of an operating system. It’s an always-running
program that is in control of everything in the system. It manages hardware
resources and program execution.

An operating system consists of a  kernel and some additional software making
user’s interaction with his or hers device more pleasant. This might include
graphical user interface, shell, web browsers, and so on.
