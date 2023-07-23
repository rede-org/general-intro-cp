# What is Contextual Programming?

## It's About 'When'

In the last section, paradigms were described as a "way of thinking". Contextual Programming is intended to help a programmer think more on 'when' data will be changed instead of 'how' it will be changed (Imperative Programming) or 'what' will be done to change it (Declarative Programming). A programmer will still need to define the 'what' and 'how', but when practicing Contextual Programming those concerns are not at the forefront of the programmer's mind.

More specifically, when practicing Contextual Programming, data take the form of **contexts**. Contexts can be evaluated by **operations**, when the contexts qualify per some conditions, which manipulate the contexts per some logic. **Behaviors** can encapsulate operations, grouping them together and permitting reactive evaluation; that is, evaluation that occurs automatically in response to specific change to the behavior's contexts. As with operations, contexts are only associated with a behavior if they qualify per some conditions.

Contexts that are related across behaviors can be organized together as **compositions**. Given that which contexts qualify for which behaviors varies based on whether contexts qualify for the conditions of a behavior, a composition's contexts are temporal and very dynamic. Compositions with other specified contexts can be evaluated by operations, for which they must collectively qualify.

All of these constructs and their relationships lead to very flexible scenarios for when logic may occur, and it's this 'when' that a programmer will likely be focused on when practicing Contextual Programming.



## To What End?

In a practical sense, by structuring a program based on 'when':

* The logic that guides the program can be more decoupled. Instead of explicitly stating what logic should occur next, thus coupling that logic to the current flow of logic, a programmer declares that some context(s) should be evaluated by whatever logic is qualified to evaluate it.
* Relationships between data constructs become temporal, based on when the data meet certain conditions. This makes some data-oriented concepts (e.g., data management and injection) that are traditionally difficult in other paradigms inherently supported.
* The state of data and its potential relationships/manipulations are already known with conditions for conflict being explicitly declared, so parallel programming can be inherently supported.
* Data that should be considered for behaviors (and thus, must persist outside of the current stack of operations) must be explicitly registered and explicitly deregistered. This is similar to manually allocating/deallocating memory but is a practical concept towards solving the programmer's problem instead of a new concern. In essence, this means that garbage collection or other means of memory management are not necessary as the programmer is already doing those tasks without realizing it.
* All data are manipulated through limited side effects that can be managed through reactive operations. This results in code that is conceptually consistent throughout its various uses across an application but with a security that is usually limited to more restrictive coding practices.
* Logical constructs can be named to the advantage of the programmer, since they aren't explicitly called elsewhere in code. This lessens the burden of making succinct but meaningful names, while enabling more self-documenting code.

In general, Contextual Programming is conceptually more applicable than other paradigms when developing highly dynamic and interactive applications; applications that maintain a lot of constantly changing (in parallel) data that demands specific responsive logic based on the current application state.
