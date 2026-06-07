<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead">Working with Collections of Elements</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to select multiple elements from the DOM and iterate through those elements to carry out actions on them.

## Selecting multiple elements

When developing websites, it's common to need to select and work with multiple elements on a page at once. JavaScript provides a method for this: [`querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll).

Before diving into how it works, let's add the following HTML below the existing `<p>` element so that we have multiple elements to select!

```html
<ul id="comments">
  <li>first comment</li>
  <li>second comment</li>
  <li>third comment</li>
</ul>
```

This creates an unordered list (`<ul>`) with an id of "comments" and contains three list items (`<li>`), each representing a comment.

### Using `querySelectorAll()`

Now, to select these elements, we'll use `querySelectorAll()`. This method is similar to `querySelector()`, but with a key difference in how it selects elements:

1. `querySelector()` selects the **_first element_** that matches the specified CSS selector.
2. `querySelectorAll()`, on the other hand, selects **_all elements_** that match the CSS selector.

### 🎓 You Do

Try to select multiple elements in the DOM

1. Use `document.querySelectorAll()` to select all `<li>` elements that are nested within the element having the `id` of `comments`. Assign them to a variable named `commentElements`.
2. `console.log(commentElements)` to verify your work.

## Iterating over a collection of elements

When you use `querySelectorAll` in JavaScript, it returns a collection of elements that resembles an array. This collection, known as a _NodeList_, can be looped through or iterated over, just like an array.

Because `querySelectorAll()` always returns this data structure, it's a good practice to use a variable name that reflects that it contains multiple elements. This is why we named the variable `commentElements` instead of `commentElement`.

Now that we have `commentElements` stored in a variable, we can use a `for` loop, a `for...of` loop, or a `forEach()` loop to iterate over them.

Let's add the following `forEach()` loop to print the text content of each element:

```js
commentElements.forEach((commentElement) => {
  console.log(commentElement.textContent);
});
```

> 🧠 `querySelectorAll()` doesn't return a true array, but instead something called a `NodeList`. This technical distinction won't impact our normal interaction with them, but if you'd like to learn more or are trying to do something atypical, it may be worth checking out the `NodeList` lesson.

### 🎓 You Do

Use the `forEach()` method to modify the style of each comment element.

Inside the loop, change the font size of every `<li>` element to `30px`.

> Hint: You must use a string like `'30px'` - just the number `30` or the string of `'30'` will not work.
