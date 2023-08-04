# Adaptation

## Overview

The first example of a context, `Some Int: context Int.`, described itself as an adaptation. Adaptation is a type of inheritance[^1] for Contextual Programming. A context is primarily data being organized and presented in a manner most appropriate for the use of that context, so adaptation focuses only on enabling a context/record, called the descendant, to inherit the desired parts of another context/record, called the ancestor, and to present those parts appropriately for its use.

Adaptations have three primary aspects.



## Aliasing

All adaptations are essentially a form of aliasing, which means an adaptation provides an alternative way to refer to something that already exists. In the first example, `Some Int: context Int.`, the descendant's name, `Some Int`, is an alias of the ancestor, `Int`. An instance of one type [can always be used](#user-content-fn-2)[^2] as an instance of an aliased type.

The purposes of aliasing are to enable a context to be more specific to its use, to enable re-usability of code for related constructs, and to simplify conversions of data for different uses. All of these purposes can be seen with the `Some Int` example.

* `Some Int` may be intended for specific use. The name, which is purposefully very meaningless in this example, could convey that use better than `Int`, which is widely used in most situations when a basic integer number is needed.
* `Some Int` may be used in different scenarios than `Int` yet `Some Int` will maintain the same integer value as `Int` and can be used with all the same decorators in the same way (at least in how it is currently defined). However, the code for `Some Int` is very short, precisely because `Int` has already defined all of those decorators. This reduces how much code must be re-implemented for the same use.
* `Some Int` is a context, whereas `Int` is not. This means they will have significantly different uses, but converting between them can be done easily because `Some Int` is essentially an `Int` by another name.

Not only can the types themselves be aliased, but the properties within them can be aliased as well. This can be seen with an alias for `Position`:

```
Other Position: context Position
    {
        New Y: replaces Y;
    }.
```

In the above example, `Other Position` is an alias for `Position` and it has declared that a property `New Y` will replace `Position(Y)`. `New Y` is the same as `Y` whenever the types are aliased between each other or whenever a decorator of `Position` refers to `Y` in some way and whenever a decorator of `Other Position` refers to `New Y` in some way. This kind of aliasing furthers the purpose first described above; for the descendent to be more suitable to its specific use.



## Extending

Adaptations can go beyond aliasing to differentiating the capabilities of the descendant from the ancestor. One way this is accomplished is by extending the ancestor with new properties or decorators. Looking again at building upon the `Position` example:

```
3D Position: context Position
    {
        Z: Int;
    },
    this matches Int, Int, and Int: (x, y, z) => 
        this(X) = x && this(Y) = y && this(Z) = z;
    -this: () => { X[-this(X)], Y[-this(Y)], Z[-this(Z)] };
    this + 3D Position: (other) => 
        { X[this(X) + other(X)], Y[this(Y) + other(Y)], Z[this(Z) + other(Z)] }.
```

`3D Position` can be used as a `Position` with its `X` and `Y` and all of its decorators, but it also defines a new `Z` property and new decorators that are appropriate for working specifically with a `3D Position`. It has extended `Position`'s original properties and decorators with new ones that are better suited for its specific uses.



## Excluding

Adaptations can also go in the opposite direction. Instead of extending an ancestor, they can exclude properties or decorators to limit the use of the descendant. This can be seen with a descendant of `3D Position`:

```
Limited 3D Position: context 3D Position
    {
        !: replaces X;
    }.
```

{% hint style="warning" %}
In Rede, the `!:` notation specifies that there is no declaration name being defined. The declaration will proceed to fulfill its intended purpose, but the result will not be identifiable or referenceable in the current scope[^3].
{% endhint %}

`Limited 3D Position` can be used the same as a `3D Position` but whenever it is known as a `Limited 3D Position` the `X` property will be unavailable. Were any decorators excluded, as is [shown later](../chapter-3-evaluating-with-operations/expanding-on-when.md#identifiers-and-execution-order), then they would be unavailable as well. The actual `X` property and its (default) value exist but are excluded from any use of the `Limited 3D Position`. This is another way that adaptation enables descendants to take on a form that is most appropriate for their specific use.

[^1]: Inheritance is a concept of Object-Oriented Programming. Usually, inheritance defines a parent type (sometimes called a superclass) for a child type (sometimes called a subclass). The child type inherits any defined properties and functionality of the parent type. An instance of the child type can usually be used as an instance of the parent type, but the reverse can usually not be assumed.

[^2]: This isn't true in most paradigms or languages, but in Contextual Programming (at least with Rede) it is expected for all values to have defaults, so any properties that may be in (or excluded from) the alias of a type can be substituted with the default values.

[^3]: Scope is a term in programming that refers to a part of the code where the identifiers of the constructs at hand are recognizable. In this case, the scope is within the `Limited 3D Position` context and any place where an instance of that context is explicitly used as a `Limited 3D Position`.
