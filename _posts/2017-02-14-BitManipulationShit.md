---
layout: post
title: Bit Manipulation Trick
date: 2017-02-14
categories: [不会写代码的数据分析师不是好的产品经理_PROGRAMMER]
tags: [不会写代码的数据分析师不是好的产品经理]

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