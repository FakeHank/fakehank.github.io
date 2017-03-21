---
layout: post
title: Parallel & Multithreaded Programming(3)
date: 2017-02-28
categories: [PROGRAMMER_JAVA]
tags: [PROGRAMMER]

---

__To design a thread-safe class:__

* State variables (fields)
* Specification (invariants)
* Synchronization policy

One commonly used synchronization policy, (performance is bad)

* Make all fields private
* Make all methods synchronized

__Instance Confinement__

__The Producer-Consumer Pattern__

__Delegation ensures thread-safety if__

1. Instance fields are thread-safe
2. No invariant constrains multiple instance fields
3. No precondition requres checking of value of instance fields
4. Instance fields are not published

__wait()/notify()/notifyAll()__

* To suspend, a thread performs a ```wait()```
* Other threads perform ```notify()/notifyAll()``` to enable resumption of suspended threads

__how do you map tasks to threads?__

* One thread used to execute all the tasks sequentially
* One thread / task

__An executor can be in one of three states__

* Running:  executor is executing tasks, accepting new tasks
