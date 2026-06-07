<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead">Element Attributes</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to change the attributes of an element on a webpage using JavaScript.

## Accessing and modifying the attributes of an element

Attributes in HTML provide additional information about elements. Common examples include `id` and `class`.

As a reminder, in this code snippet, `id` and `class` are both attributes:

```html
<h1 id="main-title" class="title">Intro to the DOM</h1>
```

There are several methods in JavaScript that let you work with these attributes:

- [`getAttribute()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute): Retrieves the value of a specified attribute.
- [`setAttribute()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute): Sets or updates the value of a specified attribute.
- [`hasAttribute()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/hasAttribute): Checks if an element has a certain attribute.
- [`removeAttribute()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/removeAttribute): Removes a specified attribute from an element.

These methods are essential for dynamically changing an element's characteristics in your application.

## Practical example: enabling a button

To see this in action, let’s apply these methods in a practical scenario:

Add a button to your HTML like this:

```html
<button disabled>Click me!</button>
```

> 💡 `disabled` is a boolean attribute that doesn't have a value. If it's present on an element, then that element cannot be modified or interacted with by a user. This means the button is initially unclickable.

1. Use `querySelector()` to select the button element:

   ```javascript
   const buttonElement = document.querySelector('button');
   ```

2. To make the button clickable, we first check if it has the `disabled` attribute, and then remove it if it does.

   - To see if an element has an attribute, we'll use the `hasAttribute()` method. It accepts a single string argument. If the element has the attribute we specify, it will return `true`. Otherwise, it will return `false`.

     ```javascript
     if (buttonElement.hasAttribute('disabled') === true) {
       // the button has the disabled attribute
     }
     ```

   - We can then remove the `disabled` attribute with the `removeAttribute()` method. It accepts a single string argument. If the element has the attribute we specify, it will be removed.

     ```javascript
     if (buttonElement.hasAttribute('disabled') === true) {
       buttonElement.removeAttribute('disabled');
     }
     ```

After removing the `disabled` attribute, the button becomes interactive, meaning you can now click it.
It still doesn't do anything, but at least we can interact with it!

### 🎓 You Do

Test out the `setAttribute()` method. It accepts two arguments - the first is the name of the attribute we would like to change, and the second is the value we would like to change it to. Check out the [documentation for `setAttribute()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) for more support.

Give the `buttonElement` we created above an `id` of `'submit'`.

Inspect the element in the DevTools to confirm that this was successful.

## The `class` attribute

When working with the class attribute of HTML elements, JavaScript provides a powerful and convenient property called [`classList`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList). This property is more efficient and versatile for handling classes compared to using general attribute methods.

The `classList` property is an object that offers specific methods to manipulate the classes of an element. These methods are designed to handle common tasks related to CSS classes.

Here are some of its methods:

- `add(className, ...)` -  Adds one or more class names to an element. If the class already exists, it won't be added again.
- `remove(className, ...)` -  Removes one or more class names from an element. If the class does not exist, nothing happens.
- `toggle(className)` -  Adds the class if it does not exist, and removes it if it does.
- `contains(className)` -  Checks if the element has the specified class.
- `replace(oldClass, newClass)` -  Replaces an existing class with a new class.

To add a class named 'btn' to our button element, we use the `add()` method:

```javascript
buttonElement.classList.add('btn');
```

Inspect the element in the DevTools to confirm that this was successful.

### 🎓 You Do

Following the examples in the [`classList` documentation](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList), write some code to remove the `'btn'` `class` from the `buttonElement`, then give it a new `class` called `action-button`

Inspect the element in the DevTools to confirm that this was successful.
