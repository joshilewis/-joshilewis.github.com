=The States, Interactions and Outcomes Model=

**TL;DR:**  In my experience, teams don't have a structured way to explore, discuss and document the factors that affect system behaviour. The States, Interactions and Outcomes model provides such a structure.  Using the model makes Specification by Example and BDD easier and more effective. The model focuses on making system boundaries, states, interactions and outcomes explicit.

--------

Specification by Example is the practice of specifying expected system behaviour using concrete values instead of natural-language descriptions. For more on Specification by Example,you can't do better than [Gojko Adzic's book](). One of the reasons I use Specification by Example is that it allows us to work with something tangible, instead of just 'invisible ideas'. Some of the benefits of Specification by Example are:  

* Getting feedback on the work from a wider audience earlier in the process.
* Making edge cases more obvious. 

Ordinarily, we would need to write some software to achieve these things. By using Specification by Example we can get these benefits **before** writing any software. However it is not always easy to get started with Specification by Example.

A common challenge teams face when they start using Specification by Example is understanding the difference between interactions and states, and how to differentiate between them. It is important to understand that the outcome of an interaction with a system is determined **not only** by the interaction, but also by the state of the system at the time of the interaction. Furthermore, it is often not obvious or well understood that systems generally have multiple types or dimensions of state. That is, the state of a system is described by specifying concrete values of more than one type. 

A note: I have come to use the terms 'Interaction' and 'Outcome' instead of 'input' and 'output' respectively, because they are closer to the way most people think about working with software products: "I interact with a system to achieve some outcome". Although the term 'output' generally includes system post-conditions or state, 'output' can be confusing if the result of an interaction is only a change in system state, and there is no explicit or obvious 'value' returned.

The model states that expected system behaviour can be completely and comprehensively specified by describing the expected outcome for every possible combination of state and interaction. If we can enumerate all the possible combinations of state and interaction, and express the expected outcome for each of these combinations, we have created a complete and comprehensive specification of the functionality of that system. 

Part of the model is a set of steps cross-functional teams can follow to collaboratively create such an enumeration of states, interactions and outcomes. These steps are:    

1. Explicitly define and bound the system under specification. What is included, what is excluded?
2. What are the different inputs to the system?
3. What are the types of state that the system can have? Another way to ask this: Besides the inputs, what can affect the outcome of an interaction?
4. What constitutes system outcome? Is any output returned to the user? Note that an outcome must, by definition, include all states as identified above. Outcome can also include error conditions.
5. For each type of state, what are the possible values?
6. For each type of input, what are the possible values?
7. For each combination of state and interaction, what is the expected outcome (including all dimensions)?

To demonstrate the model and the process, I will take you through applying it to a problem I use frequently in coaching and training. Imagine we are creating software to calculate the total cost of a bunch of items at a point of sales. (This problem is inspired by [Dave Thomas' Supermarket Pricing Kata]().) Imagine you walk up to a till at a supermarket, hand the check-out person your items one-by-one, and the checkout person starts calculating the total of the items you want to purchase. Note that the total is updated each time the checkout person records an item for purchase.

We would like to include a number of ways of calculating the total price, especially for promotions supermarkets may offer from time to time. Some of the pricing methods are:

* Simple Pricing: the total cost is calculated simply by adding up the cost of each individual item recorded at the point of sale.
* Three-for-Two Promotion: By two of any particular item, pay for only two. This promotion is specific to the type of item being sold. For example, buy three loaves of Brand-X bread,  pay for only two.
* Combo Deal: A discount is applied when a specific combination of items is purchased.
* Bulk Discount: A discount is applied when more than a specific number of a particular item is purchased.  

In this article I will deal with only 'Simple Pricing' and 'Three-for-Two Promotion'. I will deal first with 'Simple Pricing' completely, and then start with 'Three-for-Two Promotion'.

**Simple Pricing**  
**System boundaries**: We are concerned only with the way the total for the purchased items is calculated. We are not concerned with things like how the cost of an item is acquired (e.g. barcode scanning), accepting payment etc.  
**Types of inputs**: For Simple Pricing, the only input is the price of the item being recorded - *item price*.   
**Types of state**: Besides inputs, what affects calculating the total price? For Simple Pricing, the total after recording an item - the new total - is determined by both the price of the captured item, as well as the total before the item is captured. Therefore state consists of *current total*.  
**Outcome dimensions**: For Simple Pricing, the outcome consists only of the total calculated as a result of capturing an item - *new total*.  
**Possible values for state types**: *Current total* is an integer, which can be negative, 0, or positive.   
**Possible values for inputs**: *Item price* is an integer, which can be negative, 0, or positive.  
**Expected outcomes for combinations of state and inputs**:
|State|Interaction|Outcome|Scenario Name|
|:---|:---|:---|:---|
|Current total|Item price|New total||
|0|0|0|
|0|10|10|First item|
|10|10|10|Second item|
|0|-10|ERROR - item price can't be negative|First item with negative price|
|10|-10|ERROR - item price can't be negative|Second item with negative price|
|10|ABCDEF|ERROR - invalid input|Text input|


