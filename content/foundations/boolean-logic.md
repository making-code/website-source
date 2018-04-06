+++
title = "Boolean logic"
date =  2018-04-03T12:03:53+02:00
weight = 2
+++

In the previous section, we have seen that we can use **gates** in a digital circuit to represent and answer more complex problems.

## Logic in software

When programming software, we will often have to deal with decisions on a logical level or even on a bit-level. To allow us to do that, all programming languages offer some kind of boolean logic operators.

## Recap: Boolean values

We have established that in digital logic, we work with two values. They represent the concept of "true" and "false" and their meanings can be slightly different depending on how you look at them, for instance:

| true | false |
| ---- | ----- |
| yes | no |
| 1 | 0 |
| on | off |
| something | nothing |

These values are also referred to as **boolean value** or **boolean** for short, i.e. something that can have one of two values and nothing else.

For this chapter, we will use `true` and `false`, but we could as well use any other example from the table above.

## The operators

Let's see what those operators are:

* Not (negation)
* And (conjunction)
* Or (disjunction)

Let's dive into each of them!

## Negation

This operator is most useful in combination with one of the other two operators, but can also be used alone.
It inverts, i.e. "turns around" a boolean value:

| `x` | `NOT x` |
| --- | --- |
| true | false |
| false | true |

In most programming languages this operator is either expressed as `!` (e.g. `!x` is the negation of a boolean `x`) or the word `not`.

{{%expand Example %}}
```js
var child = { wasNice: false }
var wasNice = child.wasNice;
var wasNaughty = !wasNice; // wasNaughty will be true
```
{{% /expand %}}

## Conjunction



## Disjunction