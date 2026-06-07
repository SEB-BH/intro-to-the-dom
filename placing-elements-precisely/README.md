<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead">Placing Elements Precisely</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to use various DOM manipulation methods like `after()`, `before()`, and `replaceChild()` to place new elements in specific locations within the DOM.

In [Creating an Element](../creating-an-element/README.md), we covered placing an element onto the page with the `appendChild()` method. This is the most commonly used method for placing elements on a page, but sometimes, you need to place elements more precisely than that. Let's check out how.

What would have helped most in this situation is adding the new element relative to its sibling element. For example, say we always wanted the `<h2>` element to always be immediately after the `<p>` element in the document:

```html
<body>
  <h1 id="main-title" class="title">Intro to the DOM</h1>
  <p class="cool">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto fuga suscipit sint autem. Iure nam, libero perferendis ad doloremque quo eius nesciunt eveniet saepe. Voluptas qui dignissimos aliquam illo alias!
  </p>

  <!-- We *always* want the <h2> to be here!! -->
  
  <ul id="comments">
    <li>first comment</li>
    <li>second comment</li>
    <li>third comment</li>
  </ul>
  <button disabled>Click me!</button>
</body>
```

In this case, we could use the `<p>` element's [`after()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/after) method. The element we pass to the `after()` method will be placed immediately after the `<p>` element in the DOM. Luckily, there's already a cached element reference for this element - `paragraphElement`. To avoid there being a duplicate `<h2>` element on our page, get rid of this line:

```javascript
bodyElement.appendChild(h2Element);
```

And replace it with this:

```javascript
paragraphElement.after(h2Element);
```

Now, the `<h2>` element always follows the `<p>` element!

Many other methods exist to place elements more precisely. You might have already guessed that there is a [`before()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/before) method. There's a [`replaceChild()`](https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild) method that can also be handy for swapping one element for another. Explore the possibilities on your own if you require them!
