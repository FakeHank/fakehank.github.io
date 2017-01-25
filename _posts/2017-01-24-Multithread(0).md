---
layout: post
title: Parallel & Multithreaded Programming(0)
date: 2017-01-24
categories: [PROGRAMMER_JAVA]
tags: [PROGRAMMER]

---

* Concurrent - unrelated to physical processor
* Parallel - each flow has its own processor
* Distributed

__Java Memory Model__

* Stack

	* Local Variable
	* Method Parameters
	
* Heap

	* Objects
	* Every call to new allocates space on heap. 
	
__Running threads on Processors:__

1. Scheduler
2. Scheduling policy
3. Context switch (p26)

Processes: 1. on single machine; 2. not necessarily on a single processor.

Threads: 1. usually on a single processor; 2. some support thread migration.

__Two Approaches:__

1. Extends Thread;
2. Implements Runnable;

Pros:
	
1. Easy access to Thread; No intermediate object.
2. Can Inheritate from another class; Protect other Thread methods (start()).

__Thread States__

Thread.State/getState()

* NEW --start()--> RUNNABLE
* BLOCKED
* WAITING
* TIMED WAITING
* TERMINATED

isAlive()
void join()