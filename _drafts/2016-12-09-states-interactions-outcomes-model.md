=The States, Interactions and Outcomes Model=

**TL;DR:**   A structure for discussing and documenting expected system behaviour to make Specification by Example and BDD easier and more effective. This is achieved by making system boundaries, states, interactions and outcomes explicit.

--------

Specification by Example is the practice of specifying expected system behaviour using concrete values instead of natural-language descriptions. For more on Specification by Example,you can't do better than [Gojko Adzic's book]. One of the promises of using Specification by Example

The outcome of an interaction with a system is determined **not only** by the interaction, but also by the state of the system at the time of the interaction.

What not obvious is what the dimensions or types of state a system has. This is important because the outcome of interacting with a system is 

Steps:  
1. Explicitly define and bound the system under specification. What is included, what is excluded?
2. What are the types of state that the system can have? Another way to ask this: Besides the inputs, what can affect the system outcome to an interaction?
3. What are the different types of inputs to the system?
4. For each type of state, what are the possible values?
5. For each type of input, what are the possible values?
6. For each combination of state and interaction, what is the expected outcome?