+++
title = "Boolean logic"
date =  2018-04-03T12:03:53+02:00
weight = 2
+++

In the previous section, we have seen that we can use **gates** in a digital circuit to represent and answer more complex problems.

## Logic in software

When programming software, we will often have to deal with decisions on a logical level or even on a bit-level. To allow us to do that, all programming languages offer some kind of boolean logic operators.

{{%expand "Recap: Boolean values" %}}

We have established that in digital logic, we work with two values. They represent the concept of "true" and "false" and their meanings can be slightly different depending on how you look at them, for instance:

| true | false |
| ---- | ----- |
| yes | no |
| 1 | 0 |
| on | off |
| positive voltage | negative voltage |

These values are also referred to as **boolean value** or **boolean** for short, i.e. something that can have one of two values and nothing else.

{{% /expand%}}

For this chapter, we will use `true` and `false` to refer to our boolean values.

## The operators

Let's see what those operators are:

* Not (negation)
* And (conjunction)
* Or (disjunction)
* Exclusive Or (XOR)

Let's dive into each of them!

## NOT

This operator is most useful in combination with one of the other two operators, but can also be used alone.
It inverts, i.e. "turns around" a boolean value:

| x | NOT x |
| --- | --- |
| true | false |
| false | true |

In most programming languages this operator is either expressed as `!` (e.g. `!x` is the negation of a boolean `x`) or the word `not`.

![A logical circuit for the NOT operator](/img/content/foundations/boolean-not.gif)

{{%expand Example %}}
```js
var child = { wasNice: false };
var wasNice = child.wasNice;
var wasNaughty = !wasNice; // wasNaughty will be true
```
{{% /expand %}}

## AND

The logical _and_ operator can be used when two booleans need to be true for the result to be true.

| x | y | x AND y |
| --- | --- | --- |
| false | false | false |
| true | false | false |
| false | true | false |
| true | true | true |

![A logical circuit for the AND operator](/img/content/foundations/boolean-and.gif)

{{%expand Example %}}
```js
var user = { isLoggedIn: true, isAdmin: false };
if (user.isLoggedIn && user.isAdmin) {
  console.log('Welcome, boss!');
}
```
{{% /expand %}}

## OR

The logical _or_ operator can be used when **at least one** of two booleans need to be true for the result to be true.

| x | y | x OR y |
| --- | --- | --- |
| false | false | false |
| true | false | true |
| false | true | true |
| true | true | true |

![A logical circuit for the OR operator](/img/content/foundations/boolean-or.gif)

{{%expand Example %}}
```js
var wantsKetchup = true;
var wantsMayo = false;

if (wantsKetchup || wantsMayo) {
  console.log('Putting sauce(s) on your fries...');
}
```
{{% /expand %}}

## XOR

The previous logical `OR` operator returns `true` when _at least one_ of the inputs is `true` - but often we want to make sure that _exactly one_ of the inputs is true.

This is a common logical operator called _e**X**trutruclusive **OR**_ or `XOR` for short.
It is usually not consider a _basic_ boolean operator because it can be created using `NOT`, `AND` and `OR`.

{{%expand "Creating the XOR from other operators" %}}

The `XOR` operator can be built from `NOT`, `AND` and `OR` operations.
We have two booleans `x` and `y` and we only want to have a `true` as the result if _either_ `x` or `y` are `true`, but _not_ if _both_ are `true`.

There are multiple ways of implementing this with logical `NOT`, `AND` and `OR`:

1. `(x && (!y)) || ((!x) && y)`
2. `(x || y) && (!y || !x)`

Here's a logical circuit to demonstrate this by comparing the first way to an actual XOR:

![Using two AND gates, two inverters and one OR gate to create an XOR gate](/img/content/foundations/boolean-xor.gif)

[Here is an interactive version](https://simulator.io/board/3mrRGpOUrx/1)

{{% /expand%}}