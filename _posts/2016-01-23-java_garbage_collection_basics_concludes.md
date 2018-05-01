---
layout: post
title: Java GC Basics Conclusion
date: 2016-01-23
categories: [不会写代码的数据分析师不是好的产品经理_PROGRAMMER]
tags: [不会写代码的数据分析师不是好的产品经理]

---

###JVM Generations

![Hotspot Heap Structure](http://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/images/gcslides/Slide5.png)

* __Young Generation__: where all new objects are allocated and aged. When the young generation fills up, this causes a minor garbage collection.

_Minor collections can be optimized assuming a high object mortality rate. A young generation full of dead objects is collected very quickly. Some surviving objects are aged and eventually move to the old generation._

* __Old Generation__: is used to store long surviving objects.

_Typically, a threshold is set for young generation object and when that age is met, the object gets moved to the old generation. Eventually the old generation needs to be collected. This event is called a major garbage collection. __Often a major collection is much slower because it involves all live objects.___

* __Permanent Generation__: contains metadata required by the JVM to describe the classes and methods used in the application.

###The Generational GC Process

* First, any new objects are allocated to the eden space.

![ObjectAllocation](http://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/images/gcslides/Slide13.png)

* When the eden space fills up, a minor garbage collection is triggered.

![FillingTheEdenSpace](http://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/images/gcslides/Slide14.png)

* Referenced objects are moved to the first survivor space. Unreferenced objects are deleted when the eden space is cleared.

* At the next minor GC, the same thing happens for the eden space. Unreferenced objects are deleted and referenced objects are moved to a survivor space. However, in this case, they are moved to the second survivor space (S1). In addition, objects from the last minor GC on the first survivor space (S0) have their age incremented and get moved to S1. Once all surviving objects have been moved to S1, both S0 and eden are cleared. Notice we now have differently aged object in the survivor space.
* At the next minor GC, the same process repeats. However this time the survivor spaces switch. Referenced objects are moved to S0. Surviving objects are aged. Eden and S1 are cleared.
* This slide demonstrates promotion. After a minor GC, when aged objects reach a certain age threshold (8 in this example) they are promoted from young generation to old generation.
* As minor GCs continue to occure objects will continue to be promoted to the old generation space





