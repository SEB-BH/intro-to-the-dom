<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead"><code>Nodelist</code></span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to convert a `NodeList` into an array using the `Array.from()` method and the `spread` syntax.

As briefly discussed in the [Working with Collections of Elements lecture](../working-with-collections-of-elements/README.md), methods designed to return a collection of DOM elements return an array-like object called a [`NodeList`](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) instead of an array.

A `NodeList` will have a `forEach()` method but doesn't contain any other useful methods that full-fledged arrays have.

If you need to hold your DOM elements in an array, the following two approaches will do the trick.

## `Array.from()` method

Here's how you can use the [`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) static method to convert an iterable, such as a NodeList, into an array:

```js
const itemEls = Array.from(commentElements);
```

Now, `itemEls` would be an array with all array methods available.

## Spread syntax

Another way to convert a NodeList or HTMLCollection into an array is by using the [Spread Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) within an array literal:

```js
const itemEls = [...commentElements];
```
