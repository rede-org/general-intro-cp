# What is a Paradigm?

## Programming Paradigms

In the field of programming, a paradigm defines a way of thinking. There are many programming paradigms and sub-paradigms (often referred to still as their own paradigms). The relationships between the different paradigms are often described in a (mostly) tree-like structure, where more specific paradigms descend further down the tree.

Two of the most widely known programming paradigms recently include Object-Oriented Programming (OOP) and Functional Programming (FP). These paradigms are actually sub-paradigms of Imperative Programming and Declarative Programming, which may be used to more broadly describe some of their concepts.

As mentioned, there are many other paradigms at both a high and low level, but they will not be covered here in detail.

### As a Programmer

When a programmer is following a paradigm, their thought patterns to solve a problem are structured in a manner described by that paradigm. In the broadest sense, using the aforementioned paradigms, a programmer may be thinking through their solution either imperatively or declaratively:

* **Imperative** - The programmer is thinking about 'how' the solution will solve the problem. This may include the steps to implement an algorithm.
  * **Object-Oriented** - In the case of OOP, the programmer will likely think of the solution through a composition or inheritance of "objects". This allows them to consider how the data should be structured and how systems should interact, sometimes in a manner less abstract than how code normally may be thought of.
  * **Example A** - Ask some manager object for its objects, then loop through them to change the ones that should be changed.
* **Declarative** - The programmer is thinking about 'what' steps will solve the problem; they are considering in what way it can be described but they aren't concerned with the actual steps of a specific algorithm or what form the data is in.
  * **Functional** - In the case of FP, the programming will likely think of the solution through a composition of "functions". The functions contain the actual steps of how a part of the solution may be solved, but the composition is what the programmer focuses on.
  * **Example B** - Given some data, filter the data not relevant, create new data updated with expected changes, provide that data back to the requester.

In Example A, we see that a request to do something is handled by a dependency on some manager (an object) and that other objects are changed in a specific way (an algorithm) to satisfy that request.

In Example B, we see a request to do something involves being provided input (the data), some filtering (done by another function) and creation of new data (likely also done with another function) that fulfills the request, and then providing that back for the requester to continue working with.

Both examples essentially do the same thing: change some specified data in some expected way, but they do it by following a different way of thinking.

### As a Language

\[Describe how paradigms define languages.]
