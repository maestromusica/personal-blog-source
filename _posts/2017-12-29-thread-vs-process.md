---
layout: post
title: "Interview Preparations: Thread vs Process"
categories: interview-preparations
---

Modern programming languages abstract a lot of low-level details of how our code
works. Nonetheless, a good understanding of underlying computer science concepts
can help you write better code… and pass technical interviews 😉 Let’s talk about a popular interview question: *“What are the differences between a process and a thread?”*

I will assume that you have a basic understanding of how a processor works, and
how data is stored in memory. In particular, you should be familiar with **CPU
registers**, [stack, and
heap](https://www.gribblelab.org/CBootCamp/7_Memory_Stack_vs_Heap.html).

Before we try to make any comparisons, we need to get a solid grasp of relevant
terminology.

First, we need to understand what a **computer program** is.

> **A computer program is a set of instructions that can be executed by the CPU**.

A program is a static entity: it might be an executable file located somewhere
in the file system. When you double-click the icon or run a command in the
terminal, the program is loaded into RAM, and then it becomes a **process**.

> A **process** is a program in execution.

So, if you run a program multiple times there will be a few processes running
simultaneously, all corresponding to the same program.

**Why do we need processes?**

Each process contains everything required to run (or restart) the program:

* **Address space** — an abstraction for all memory available to that process.
Address space contains program’s code and data required to run the program
(static data, heap, and stack).
* One or more **threads of execution** (I’ll explain that term in detail later)
* Set of **OS resources**, for example opened files or network connections

{% figure [caption:"*A photo of a thread. I’m very funny.*"] [class:"class1 class2"] %}
![](https://cdn-images-1.medium.com/max/1000/0*30_qL_hReOgXKmMU.jpg)
{% endfigure %}

Each process contains a single or multiple **threads of execution**. If a
process has a single thread, only one action can be performed at a time. If a
process has multiple threads, it can perform multiple actions at the same time.

A thread is a sequence of instructions that can be executed independently from
other code.

> A Thread (or a thread of execution) is a sequence of instructions that can be
> processed by a single CPU core.

Imagine that you are planning a programming conference: you should create a plan
of the event: who will be giving talks, what will they be about, and so on
(that’s our **program**). The big day comes, guests arrive and our event is
taking place (our **process**). During the conference, many talks (**threads**)
might happen at the same time.

#### **Threads**

Each thread contains all information necessary to execute it’s code. We need to
keep track of 1) which part of the program is currently being executed and 2)
what is currently stored in memory.

That’s why each thread has its own **program counter** (a pointer that indicates
which instruction will be executed next), **CPU registers**, and a **stack**.

Threads within the same process share all other memory segments:

* **heap** — containing dynamically allocated variables
* **text segment** — containing program’s code
* **data segment** — containing global or static variables

Other system resources such as currently opened files are shared as well. If a
file is opened, all threads can use it.

**Okay, but we didn’t really answer the question — what are the differences
between a thread and a process?**

The most significant, practical difference is in how processes and threads
communicate.

In a multithreaded process, **threads share memory**. Thus, many threads can
access and modify the same memory, which may lead to bugs that are very
difficult to find.

Processes don’t share memory in this way, they have to use [inter-process
communication](https://en.wikipedia.org/wiki/Inter-process_communication)
instead.

Creating a process is fairly resource-intensive. It is generally more efficient
to use a single multi-threaded process than to spawn multiple single-threaded
processes.

To summarise:

* A **process** is a program in execution. A **thread** is a sequence of program’s
instructions that can be executed by a single CPU.
* A process might contain many threads. Those threads will share most of memory
segments. **Threads may access and modify shared memory.** Processes use
*inter-process communication* instead.

*****
