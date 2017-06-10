= Technical Debt =

**TL;DR**: Technical Debt occurs when we don't change our software based on what we've learned. There is no such thing as a perfect or even a good software design, there is only good enough. All designs are based on assumptions. These assumptions can be invalidated at any time. At some point interest on Technical Debt must be paid otherwise it becomes too difficult and expensive to change the software. Code is never wrong or broken and it doesn't need to be *fixed*, it may need to be remodeled. The developers who wrote the code were not stupid or incompetent, they used the best design they could based on their understanding and context at the time.

---

[Ward Cunningham's original definition](http://wiki.c2.com/?WardExplainsDebtMetaphor) talks about not incorporating what we've learned over time back into the software system. This article is about what I've come to learn about Technical Debt.

When we create a new software system, we usually design it based on a *domain model*. A domain model is a 'map' of:  

* The types of  *things*, or elements, in the problem space  
* The relationships between these elements, and  
* Rules and policies for how the elements interact with each other  

Generally, the domain model is created not just by programmers, but collaboratively by a cross-functional team. By nature, the domain model is based on certain assumptions: assumptions about the kind of elements, their relationships and interaction policies. The domain model may be tacit and hidden, or may be explicit and formally documented.

As happens, the software needs to be changed to cater for new or different requirements. At some point, one of these changes will invalidate one of the assumptions made when the domain model was created. The domain model has changed. Because the software design is based on the pre-change domain model, it cannot elegantly, non-intrusively cater for the required change. The programmers now have a choice: they can either change the software design to match the updated domain model, or they can 'compromise' the design. 

Usually it doesn't make sense to remodel the software design since this can require a large investment. We can't predict the future and don't know whether the software will continue to change in the same way, and in the same place. Therefore we don't know how much of a return we will get from this investment. Taking the ['Refactor the third time' heuristic](https://books.google.co.za/books?id=HmrDHwgkbPsC&pg=PA58&dq=refactoring+fowler+don+roberts+guideline&hl=en&sa=X&ved=0ahUKEwi3_JTGgZfSAhUpJ8AKHQ7aCE0Q6AEIIjAB#v=onepage&q=refactoring%20fowler%20don%20roberts%20guideline&f=false) into account makes remodeling even less attractive. 

The common course therefore is to compromise the software design. A compromise is something like adding a new type of element, or creating a relationship between two previously unrelated elements etc. Note that a compromise is _**not**_ smelly or bad code. Programmers don't usually like doing this (it usually goes against everything that was drummed into them during their education).

The outcome is that the software design *drifts away* from the domain model. What tends to happen is that over time the design is compromised over and over again, with compromises on top of compromises. This has two effects:   

 1. The software design drifts further and further from the domain model.  
 2. The software design becomes more and more difficult to reason about and change, because there are no longer consistent patterns in the way elements relate to each other - the design has been compromised.  

 Because the programmers can no longer rely on a sensible, consistent design across the software system, they need to spend a lot more time figuring out *where* and *how* to make the change. Even worse, because its difficult to reason about how things are related to each other, we can't predict the effects of change very well. A change in one part of the software breaks something in an entirely different, supposedly unrelated part of the system. Longer lead times and higher defect counts, especially in 'unchanged' parts of the system, are very strong indicators of technical debt.

