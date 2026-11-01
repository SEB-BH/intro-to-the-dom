<h1>
  <span class="headline">Intro to the DOM</span>
  <span class="subhead">Displaying Data on the Page</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to use functions to display JavaScript data in a collection of DOM elements.

## From data to display

Imagine an office has three meeting rooms. A screen near reception shows whether each room is available.

Our application has two parts:

- **Data:** JavaScript variables that store the room statuses.
- **Display:** HTML elements that show those statuses to visitors.

We need to connect them. When our data changes, we need to update the display.

## Prepare the status board

Add this Meeting Room code to your HTML `<body>` with:

```html
<br>

<h1>Meeting Room Status</h1>

<p id="message">Loading office information...</p>

<ul>
  <li>Room A: <span class="room-status">Loading...</span></li>
  <li>Room B: <span class="room-status">Loading...</span></li>
  <li>Room C: <span class="room-status">Loading...</span></li>
</ul>
```


Add this new code in `app.js`:

```js
const roomStatuses = ['Available', 'In use', 'Available'];

let isOfficeOpen = true;

const roomStatusElements = document.querySelectorAll('.room-status');
const messageElement = document.querySelector('#message');

console.log(roomStatusElements);
console.dir(messageElement);
```

Open the page and check the console.

You should have:

- A NodeList containing three `<span>` elements.
- A reference to the message paragraph.

> 🧠 Check your selected elements before trying to change them. The number of status elements should match the number of items in our data array.

## Access one element by its index

We already use an index to access an item in an array:

```js
console.log(roomStatuses[0]);
// 'Available'
```

We can also use an index to access an element in our NodeList:

```js
console.dir(roomStatusElements[0]);
// The span inside Room A's list item
```

Both collections start at index `0`.

| Index | Data | Display element |
|---|---|---|
| `0` | `'Available'` | Room A’s status |
| `1` | `'In use'` | Room B’s status |
| `2` | `'Available'` | Room C’s status |

Add this line to display the first status:

```js
roomStatusElements[0].textContent = roomStatuses[0];
```

Refresh the page. Room A should now show **Available**.

> 💡 `roomStatusElements[0]` is an element. `roomStatuses[0]` is a string. We assign the string to the element’s `textContent`.

### 🎓 You Do

Use index `1` to display Room B’s status.

Refresh the page to check your work.

## Display every status with a loop

We could write a separate statement for every room. A loop lets us repeat the same task.

Remove the individual `textContent` assignments you just wrote. Add this instead:

```js
roomStatuses.forEach((status, index) => {
  roomStatusElements[index].textContent = status;
});
```

The callback has two parameters:

- `status`: the current item in the array.
- `index`: the position of that item.

On the first repetition:

```js
// status is 'Available'
// index is 0

roomStatusElements[0].textContent = 'Available';
```

On the second repetition:

```js
// status is 'In use'
// index is 1

roomStatusElements[1].textContent = 'In use';
```

The loop continues until every status has been displayed.

> 🧠 The selected elements follow their order in the HTML. Our data array must use the same room order.

## Make the update reusable

We will need to update this board more than once. Put the loop inside a function so we can run it whenever needed.

Replace the loop with:

```js
function updateRoomStatuses() {
  roomStatuses.forEach((status, index) => {
    roomStatusElements[index].textContent = status;
  });
}

updateRoomStatuses();
```

Defining the function gives JavaScript instructions. Calling the function runs those instructions.

Refresh the page. All three statuses should still appear.

## Display a message using a condition

We can also choose what to display based on a variable.

Add this function:

```js
function updateMessage() {
  if (isOfficeOpen === true) {
    messageElement.textContent = 'Reception is open for room bookings.';
  } else {
    messageElement.textContent = 'Reception is closed.';
  }
}
```

Then call it:

```js
updateMessage();
```

Refresh the page. You should see the open message.

The condition checks our **data**. The assignment updates our **display**.

## Bring the updates together

Our page now has two update functions. We can create another function that calls both.

Remove the separate calls to `updateRoomStatuses()` and `updateMessage()` from outside the functions. After your function definitions, add:

```js
function render() {
  updateRoomStatuses();
  updateMessage();
}

render();
```

**Render** means to display the application’s current data on the page.

> 💡 `render()` is an ordinary function that we named. It is not a built-in JavaScript or DOM method.

## Changing data does not automatically change the page

At the bottom of your JavaScript file, after `render();`, add:

```js
roomStatuses[0] = 'In use';
isOfficeOpen = false;
```

Refresh the page.

The variables have changed, but the page still shows the earlier information. We last updated the page **before** changing the data.

Add another call:

```js
render();
```

Refresh again. Room A should now show **In use**, and the message should say reception is closed.

The pattern is:

1. Change the data.
2. Call the function that updates the display.

## Clear an element’s text

An **empty string** removes the text inside an element:

```js
messageElement.textContent = '';
```

Add this at the bottom of your file. Refresh the page to see the message disappear.

Then add:

```js
render();
```

The message returns because `render()` displays the current data again.

### 🎓 You Do

1. Change Room B’s status to `'Cleaning'`.
2. Set `isOfficeOpen` to `true`.
3. Call `render()` to display your changes.
4. Add Room D to the HTML using the same structure and class.
5. Add a fourth status to `roomStatuses`.
6. Refresh the page and check that all four room statuses appear.
