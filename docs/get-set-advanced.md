# Getting and Manipulating Elements - Advanced

While the [previous page](get-set.md) about getting and manipulating elements contain the most basic way to manipulate the DOM, modern JavaScript also contains more ways to more easily access and change the elements you want. This page will cover the more useful ones! 

## Query Selector
Other than the standard `getElementById` and `getElementByClassNames`, you can also access an element through ts *CSS selector* using `document.querySelector()`.

You should already know what CSS selector is from learning CSS! All selector that you can use in CSS can work with this method, including long chained ones.

Here's an example:

```html
<ol>
  <li>Lorem</li>
  <li>Ipsum</li>
  <li>I should be blue!</li>
</ol>

<script>
let x = document.querySelector('li:nth-child(3)')
x.style.color = "blue"
</script>
```

Unlike selecting within CSS, `querySelector` will only select the first element that fits the criteria. In the above example, if you have multiple lists, then only the third element of the *first* list will be affected.

To select *all* elements that fit the criteria, use `querySelectorAll`. It will return an array-like containing all the elements, similar to using `getElementsByClassName`. 

Note: Technically, `querySelectorAll` returns a *NodeList* object and `getElementsByNameClassName` returns a *HTMLCollection* object. But they work mostly like arrays, so don't worry about it for now. When I say array-like, just think of it as an array. 

## Changing Text
`innerHTML` contains everything inside the element, including HTML codes. Likewise, when you modify it, any HTML code you put into it will also be parsed.

If you just want to change the *text* of an element, the more recommended way of doing it is through `textContent`. This way, it'll only give you the text you can *see* in the element (and not hidden text, span codes, etc).

Here's a demonstration. The content of this textbox will modify the paragraphs after it. 

<textarea id="innertextexample">Type <strong>something</strong> here. </textarea>

With innerText: <span id="innertextdisplay"></span>

With innerHTML: <span id="innerhtmldisplay"></span>

<script>
const innerTextDisplay = document.getElementById('innertextdisplay')
const innerHTMLDisplay = document.getElementById('innerhtmldisplay')
const exampleTextarea = document.getElementById('innertextexample')

innerTextDisplay.innerText = exampleTextarea.value
innerHTMLDisplay.innerHTML = exampleTextarea.value

exampleTextarea.addEventListener('input', (e) => {
	innerTextDisplay.innerText = e.target.value
	innerHTMLDisplay.innerHTML = e.target.value
})
</script>

## Taking Care of Children
To get elements that are children of an element, we can use `element.children`. It'll return an array-like containing the elements inside that element.

To add an element into another element, you can use `parentElement.appendChild(newElement)`. If you got the new element from elsewhere in the page, it'll move it to the new parent (so it won't be in its original place anymore.

To remove an element from its parent, you can use `parentElement.removeChild(theElementYouWantRemoved)`. If you've already assigned the element you want removed to a variable, you can still manipulate it freely there, and then append it somewhere else, if you want to.

Here's a full example showing how `children`, `appendChild` and `removeChild`, can be used: 

```html
<ol id="firstlist">
<li>One</li>
<li>Two</li>
<li>Three</li>
</ol>

<ol id="secondlist">
<li>Four</li>
<li>Five</li>
</ol>

<script>
let listOne = document.querySelector('#firstlist')
let listTwo = document.querySelector('#secondlist')

listOne.appendChild(listTwo.children[0])
listOne.removeChild(listOne.children[1])
</script>
``` 

The result:
<ol id="firstlist">
<li>One</li>
<li>Two</li>
<li>Three</li>
</ol>

<ol id="secondlist">
<li>Four</li>
<li>Five</li>
</ol>

<script>
let listOne = document.querySelector('#firstlist')
let listTwo = document.querySelector('#secondlist')

listOne.appendChild(listTwo.children[0])
listOne.removeChild(listOne.children[1])
</script>


## Class Manipulation
You can access the class(es) of an element using `element.className`. This will return to you the classes as it is typed in the HTML i.e. multiple class will be separated by spaces. 

Another way to access the classes of an element is using `element.classList`. This will return an array-like containing all the classes. 

You can add more classes to the resulting array-like using `add(newClass)`, remove from it with `remove(oldClass)`, or even toggle (add it if it's not there, remove it if it's there) using `toggle(class)`.

Here's an example:

```html
<div id="classbox" class="box">
Click the button to change my class!
</div>

<button onclick="makeBlue()">Make Blue</button>
<button onclick="giveBorder()">Give border</button>
<button onclick="removeBorder()">Remove border</button>
<button onclick="toggleVis()">Hide / Show</button>

<style>
#classbox.blue {
  color: blue;
}

#classbox.bordered {
  padding: 0.2em;
  border: solid black;
}

#classbox.hidden {
  visibility: hidden;
}
</style>

<script>
var classBox = document.querySelector('#classbox')

function makeBlue() {
	classBox.classList.add('blue')
}

function giveBorder() {
	classBox.classList.add('bordered')
}

function removeBorder() {
	classBox.classList.remove('bordered')
}

function toggleVis() {
	classBox.classList.toggle('hidden')
}
</script>
```

The result:

<div id="classbox" class="box">
Click the button to change my class!
</div>

<button onclick="makeBlue()">Make Blue</button>
<button onclick="giveBorder()">Give border</button>
<button onclick="removeBorder()">Remove border</button>
<button onclick="toggleVis()">Hide / Show</button>

<style>
#classbox.blue {
  color: blue;
}

#classbox.bordered {
  padding: 0.2em;
  border: solid black;
}

#classbox.hidden {
  visibility: hidden;
}
</style>

<script>
var classBox = document.querySelector('#classbox')

function makeBlue() {
	classBox.classList.add('blue')
}

function giveBorder() {
	classBox.classList.add('bordered')
}

function removeBorder() {
	classBox.classList.remove('bordered')
}

function toggleVis() {
	classBox.classList.toggle('hidden')
}
</script>


