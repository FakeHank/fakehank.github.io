---
layout: post
title: Parallel & Multithreaded Programming(2)
date: 2017-02-16
categories: [PROGRAMMER_JAVA]
tags: [PROGRAMMER]

---

__Atomic__: Atomic operations are uninterruptible__Guaranteed to be atomic in Java__ * Reads, writes of non-64-bit primitive types (ints, chars, floats, etc.)* Reads, writes of references (32-bit and 64-bit)__Two aspects of an opration__
* Atomic* Visibility

__Volatile__: is used to mark a Java variable as "being stored in main memory"

__Sharing Objects__

* Publishing
* Escape (unintended pulishing)

__Thread Local__

__Anonymous Inner Class__

__An object is immutable if__

* All its fields are final
* Its state never changes after construction
* Properly constructed (```this``` does not escape)

__To avoid publication problems for mutable objects__:

* Make sure objects are properly constructed
	* store reference in volatile variable
	* store reference in final field of a properly constructed object
	* store reference in a variable that is properly locked
* Initialize objects in a static initializer




