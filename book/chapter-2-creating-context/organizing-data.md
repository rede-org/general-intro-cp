# Organizing Data

## Contexts vs. Records

Contextual Programming defines two ways to structure data, **contexts** and **records**. These types are nearly equivalent, except for the following:

* Contexts cannot be part of other contexts or records.
* Only contexts and their properties can be evaluated by operations/behaviors.
* Only contexts can have their data manipulated across operations.

These differences create clear and explicit expectations for working with data. Consider if contexts could be composed of other contexts. When an inner context changes, do reactive evaluations occur for the outer context as well? When evaluating an outer context, does an inner context get evaluated by its own operations too? If an inner context is entirely replaced, what kind of change should that be considered and does the inner context persist for its own behaviors?

While these questions can have defined answers, any set of answers would complicate practicing Contextual Programming without adding any particular value that cannot already be achieved by other means. To keep the paradigm simple and focused, a distinction is created between contexts and records; contexts being the containers for persistent and changeable data and records being organized data for use within contexts or local manipulations within an operation.

## Defining a Context

In its most simple form, contexts are defined by declaring a name, stating that the construct is a context, and then describing the form of its data. The data may either be another [singular data type](#user-content-fn-1)[^1] or a set of properties[^2].

In general, a context declaration looks like the following, where text within quotations is replaced by text meaningful to an actual declaration:

<pre><code>"Context Name": <a data-footnote-ref href="#user-content-fn-3">context</a> "Data Type or Set of Properties".
</code></pre>

Here are a couple of concrete examples of declaring contexts:

{% hint style="info" %}
By the way, comments[^4] in Rede are any text contained within backticks ( \` ).
{% endhint %}

<pre><code>`An adaptation of the built-in Int type.`

Some <a data-footnote-ref href="#user-content-fn-5">Int</a>: context Int.
</code></pre>

```
`A context for two integers, intended to be used as a position.`

Position: context
{
    X: Int;
    Y: Int;
}.
```

{% hint style="info" %}
Collections of anything throughout Rede are wrapped in curly braces.
{% endhint %}

### Default Values

All data types in Rede are expected to have default values. There is no "null[^6]" concept that is found in some other languages. Built-in types already have defaults, such as "Int" defaulting to 0. These defaults will propagate to the use of those types in new data types, but explicit defaults can also be specified. For the previous examples, adding defaults of -1 would look like:

```
Some Int: context Int [-1].
```

```
Position: context
{
    X: Int [-1];
    Y: Int [-1];
}.
```

{% hint style="info" %}
Specifying any value or other type that can take the place of another in specific circumstances, also called a "stand-in", is denoted in Rede by square brackets. In this case, the explicit integer value of -1 is being defined as the stand-in for a default integer when instances of these types are created.
{% endhint %}

[^1]: This relationship between an ancestor data type and a descendent data type is called [Adaptation](adaptation.md).

[^2]: Named data values, like a number called "X".

[^3]: If this keyword were omitted, then this code would be declaring a record.

[^4]: Non-compiling text intended to convey information about the code to a programmer.

[^5]: "Int" stands for "Integer" a type of number.

[^6]: Also known as "None" or "Nil", this value is often a stand-in for the lack of any value, either for any data type or for data types that are permitted to be "nullable".
