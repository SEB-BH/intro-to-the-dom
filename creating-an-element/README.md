<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead">Creating an Element</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to create new elements in the DOM using JavaScript.

## Adding elements to the page

We've already seen how we can select and modify pre-existing elements, but how do we create elements from scratch? One of the powerful features of JavaScript in web development is the ability to create new elements on a webpage. This is done using the `createElement()` method, a fundamental tool in dynamically manipulating a web page's structure.

We're going to add a new `<h2>` element immediately after the `<p>` element in the `body` of our webpage. This `<h2>` element will have the text content `'Comments section'`.

### 1. Select the `body` element

To add an element inside the `<body>` element, we first select the `<body>` element from the DOM. We can use `querySelector()` for this and specify the body element's tag name as the argument:

```javascript
const bodyElement = document.querySelector('body');

console.dir(bodyElement);
```

If we selected the element correctly, we'll have the entire body of our document logged in the browser console! Now that we have access to the `<body>` element, we can create a new element to place inside of it.

### 2. Create a new element

First, we'll need to create an element. We can do this with the [`createElement()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) method on the `document` object.

```javascript
const h2Element = document.createElement('h2');
```

In this example, we're creating a new `<h2>` element. The `createElement()` method takes one argument, a string, which specifies the type of element to create. Here, we pass `'h2'` to create an `<h2>` element. This element is now a JavaScript object that can be manipulated and inserted into the DOM.

Once you have created an element, you can treat it like any other element that you might have selected from the DOM. This means you can modify its properties, styles, and content.

For example, we can add text content to this new element:

```javascript
h2Element.textContent = 'Comments section';
```

Here, we’re setting the textContent of the h2Element to 'Comments section'. This adds the specified text to our new `<h2>` element.

Great! Except it doesn't appear on our page.

> It's important to note that this element only exists in our JavaScript application. It does not yet exist as an element you can see on the page in your browser. When an element has been created, but not yet placed on the page, we refer to it as being **_in memory_**.

To see it, we need to place it on the page!

### 3. Place the element in the DOM

There are several methods we could use to do this, but we're going to use the most common - the [`appendChild()`](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) method. This is why we needed access to the `<body>` element. Let's use its `appendChild()` method to add the `h2Element` to the end of it:

```javascript
bodyElement.appendChild(h2Element);
```

You should now see the `<h2>` we created in the browser! The `<h2>` element has been appended as a child of the `<body>` element in the DOM tree.

> ⚠ The `appendChild()` method works by adding the element we've passed to it as the **_last element_** inside of the element we're appending it to. Because the last element inside the body in our HTML is currently the `<p>` element, the `<h2>` element we've added will appear immediately after it.
>
> However, if we manually add more elements to the end of the current HTML file, the `<h2>` element will appear after those- because it is added by our JavaScript at runtime. You'll see this soon. If you're interested in techniques to place elements more exactly, check out the `Placing Elements Precisely` lesson.
