# Decoupling Specifications from Tests

The 'test code' specifying the behaviour we expect from our system can be decoupled from the code interacting with the system. This gives several benefits:  
 1. The spec describes what's expected of the system, and not how it should be achieved
 2. The spec doesn't change if the implentation changes
 3. The spec can be written in higher-levl language (e.g. the domain language)
 4. The spec can be 'applied' to smaller or larger parts of the system, depending on context, without having to change the spec (like `2` above)

------

For a long time, the automated tests I wrote described **how** the system under test (SUT) was working. It took me a long time before I learned to write my checks such that they described **what** the SUT should be doing. Once I learned how to do this, I realised there were several benefits of doing so, which can be described as *decoupling specs from tests*. This article is about these benefits, and how to go about decoupling specs from tests.

First of all, I want to define what I mean by `test` and `spec`, and how I see them as different. (For a more in-depth and rigorous discussion on some of these thoughts, [this article](http://www.satisfice.com/blog/archives/856) by Michael Bolton and James Marcus Bach is higly recommended.) In this article, a `spec` is an expression of the behaviour expected from the SUT, ideally expressed in user- or domain-level language. A `spec` includes only the **what**, and none of the **how**, or implementation details. a `test` is some code which interacts with SUT, and makes some judgement about the outcome of that interaction. In this way of thinking, we can 'apply' a `spec` to some system through a `test`. We can verify that the system works accordint to the `spec` by executing a `test`. (Note that these definitions differ slightly from those used by Bach and Bolton in the article linked above). 