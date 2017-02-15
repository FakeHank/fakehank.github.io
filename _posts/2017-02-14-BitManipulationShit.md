---
layout: post
title: Bit Manipulation Trick
date: 2017-02-14
categories: [PROGRAMMER_GENERAL]
tags: [PROGRAMMER]

---


* Check if a number is even or odd. ```n&1 //0 means even, 1 means odd```
* Remove the last 1 digit. ```n&(n-1)```
* Swap two integers. 

```
a ^= b;	//a = A^B;
b ^= a; //b = B^A^B = A
a ^= b;	//a = A^B^B^A^B = B
```

Recording bit manipulation shit. 