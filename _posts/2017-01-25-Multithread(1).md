---
layout: post
title: Parallel & Multithreaded Programming(1)
date: 2017-01-25
categories: [PROGRAMMER_JAVA]
tags: [PROGRAMMER]

---

a JVM process terminates when _"there is nothing left that hs to be done."_

when all user threads terminate

* User Threads
* Daemon Threads [```setDaemon(boolean on)```]

__DataRace__

__Correctness:__ A class is correct if it satisfies its specification.

__Lock states:__

* locked, unlocked
* acquire, release

__Intrinsic/Monitor Locks__

* Every object in Java has a lock associated with it, called I/M locks.
* No explicit aquire/release operations

__Synchronized(obj) {Statements}__

1. Acquire intrinsic lock of obj
2. Execute statements
3. Release intrinsic lock

__Conditions Necessary for Deadlock__

1. Mutual exclusion
2. Hold-and-Wait
3. Non preemptability
4. Circular waiting

__Preventing:__ Inpose an order on the locks.