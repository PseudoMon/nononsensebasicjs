# Events

This is probably the #1 thing JavaScript is used for. **Event** refers to whatever happens on the webpage, usually through user interaction. When a button is clicked, when you type into a text field, when the page is loaded: those are all events. You can write JavaScript to make your webpage react to any of these events.

## Reacting to Events

To make your JavaScript listen to an event, you can put an event attribute into your HTML tag. For instance, if you put the `onclick` attribute on a `<button>`, it will wait for when the button is clicked, then run the Javascript attached to it.

```js
<button onclick="alert('Hi')">Click Me</button>
```

That will result in 
<button onclick="alert('Hi')">Click Me</button>

Most of the time, instead of piling the entirety of your JavaScript inside that attribute, you're just going to make that attribute run a function. You can then put the function wherever you put the rest of the script.

```html
<button onclick="buttonClicked()">Click</button>
You've clicked the button 
<span id="counter">0</span> times.
```
```js
var timesClicked = 0
function buttonClicked() {
    timesClicked++
    document.getElementById('counter').innerHTML = timesClicked
}
```

<button onclick="buttonClicked()">Click</button>
You've clicked the button 
<span id="counter">0</span> times.

<script>
var timesClicked = 0
function buttonClicked() {
    timesClicked++
    document.getElementById('counter').innerHTML = timesClicked
}
</script>

## Common Events
These are probably the most common events, and the ones you should bother remembering:

- click
- change
- input
- load
- focus
- blur
- mouseover
- mouseout
- submit

Remember to add "on" when you're adding it as an attribute to your HTML element (onclick, onblur, onmouseover, etc).

You've seen what **click** is. **Change** is pretty self-explanatory: for example, when you choose a different answer from a dropdown, **onchange** is fired (but not if you just choose the same answer again!).

<select onchange="alert('You chose a different option!')">
<option>Option 1</option>
<option>Option 2</option>
</select>

```html
<select onchange="alert('You chose a different option!')">
	<option>Option 1</option>
	<option>Option 2</option>
</select>
```

The caveat to this is that it doesn't immediately work when you change the content of a text input/textarea. **onchange** will only fire when the **focus** is away from the textbox (e.g., when you click on somewhere else in the page)

<textarea onchange="textbox1Changed(this)">
</textarea>
<div>
  You typed in <span id="textarea-result"></span></div>

<script>
function textbox1Changed(box) {
  var span = document.getElementById('textarea-result')
  span.innerHTML = box.value
}
</script>

To make it work immediately, we use **oninput** instead. 

<textarea oninput="textbox2Changed(this)">
</textarea>
<div>
  You typed in <span id="textarea2-result"></span></div>

<script>
  function textbox2Changed(box) {
  var span = document.getElementById('textarea2-result')
  span.innerHTML = box.value
}
</script>

Here's the code if you want to try it yourself ([CodePen](https://codepen.io) is good for this!). The two textboxes above are identical; I just changed **onchange** to **oninput**.

```html
<textarea onchange="textboxChanged(this)">
</textarea>
<div>
  You typed in <span id="textarea-result"></span></div>

<script>
function textboxChanged(box) {
  var span = document.getElementById('textarea-result')
  span.innerHTML = box.value
}
</script>
```

Don't worry about that `this` and `box` thing yet. I'll go there in a bit.

**Load** is when the page is loaded. You've actually seen it in before when we use `window.onload` to insert JavaScript into the page.

**Focus** is when the element is currently selected. When you click on a textbox and you can type into it, or when you click Tab to then highlight a button or a link, that's when those elements are **focused**. When you stop focusing on it, **blur** happens.

**Mouseover** and **mouseout** are when the mouse's cursor hover over or leave the area. But remember that these days, most people browse the internet though their phone using a touchscreen. Mouse events don't usually do much here.

**Submit** is when you submit a form. We'll go over that when we talk about Forms later.

For a list of all events, see [this page on W3Schools](https://www.w3schools.com/jsref/dom_obj_event.asp).

## Accessing Elements in Events
When an event happens, it's often useful to have direct access to the element it's associated with. In my above example for **onchange** and **oninput**, I give the function the argument `this`.

You'll learn more about `this` the more you learn about Javascript. For now, think of `this` as a special variable that refers to "the thing itself". Every element has a `this`, and when you give it to a function that it's attached to, you're letting that function access the element.

See the example below:

<input type="text" oninput="smolboxChanged(this)">
</input>
<div>
  You typed in <span id="input-result"></span></div>

<script>
function smolboxChanged(box) {
  var span = document.getElementById('input-result')
  span.innerHTML = box.value
}
</script>

```html
<input type="text" onchange="textboxChanged(this)">
</input>
<div>
  You typed in <span id="input-result"></span></div>

<script>
function textboxChanged(box) {
  var span = document.getElementById('input-result')
  span.innerHTML = box.value
}
</script>
```

In the above example, `this` refers to the textbox element. I then hand that over to the function, renaming it to `box` in the process. Renaming it is just a precaution since `this`  can mean something else here. Feel free to name it whatever else you like.

You can then treat that variable as if we **Get** that element through, say, `getElementById()`. You can access and set everything (`style`, `innerHTML`, attributes) the same way as before.

(For more about `this`, you can just google "js this". [This W3Schools page](https://www.w3schools.com/js/js_this.asp) has a pretty good explanation.)

## Adding Event Handlers Within the Script
In addition to adding an event handler as attributes to the element, you can also add them using the function `addEventListener()`. 

This:

```html
<button onclick="clickme()">Click</button>
<script>
function clickme() {
	alert('hello')
}
</script>
```

works identically to this:

```html
<button id="clickable">Click</button>
<script>
function clickme() {
	alert("hello")
}
var button = document.getElementById("clickable")
button.addEventListener('click', clickme)
</script>
```

The basic syntax for creating an event handler is ***element*.addEventListener(*event*, *function*)**

There's one crucial difference, however: event handlers created through `addEventListener()` can receive an **event** object. This **event** object contains various data about the event itself. The important parts of this object are `preventDefault()` and `target`.

The event's `target` is the element that the event is attached to, similar to how you'd use `this`. Look at the two examples below. They work identically.

```html
<button onclick="clickme(this)">Click</button>
<script>
function clickme(el) {
    ...
}
</script>
```

```html
<button id="clickable">Click</button>
<script>
function clickme(event) {
    var el = event.target
    ...
}
var button = document.getElementById("clickable")
button.addEventListener('click', clickme)
</script>
```

`preventDefault()` prevents the default behaviour of the element. This is mostly used when dealing with forms. By default, submitting a form will reload the page. Using `preventDefault()` will stop that from happening.

```js
function dontReload(event) {
    event.preventDefault()
}
document.getElementById("someform").addEventListener('submit', dontReload)
```

## Recap
Did you get all that? Do you know how to **get** elements and **set** its attributes? Do you know what **events** are, how they work, and how to handle them? If you do, congrats, you know 90% of basic DOM manipulation with JavaScript.

If you don't, scroll back up, read some more, do some practices!

The next couple of pages aren't as *essential*, per se, but they're very good to know if you want to dive further into web development. 