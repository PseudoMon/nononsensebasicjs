# Getting and Manipulating Elements

### Get
Basic Javascript on the web can "**get**" a HTML element by using some specific functions. One of them is `getElementById()`. 

```js
document.getElementById("example")
```

This function will search the entire web page for an element with the **id** `example`. You should already know this when learning HTML: Every id should be unique. Make sure that no two elements have the same id!

You can also use `getElementsByClassName()` and `getElementsByTagName()`. As there can be multiple elements with that class/tag name, these functions will return an array of those elements. 

[Read up](js-quickguide.md) if you don't know what an array is. Basically it's like a list of things. You can access the first item in that list with `arrayname[0]`, the second item with `arrayname[1]` and so on.   

### Reading and Changing Content
Once you've reached the element you want, you can then access and modify its content, CSS styles, or attributes.

To access the content of an element, we use `innerHTML`. For example, take a look at the codes below.

```html
<div id="textdiv">Hello this is a text!</div>

<script>
var x = document.getElementById("textdiv")
console.log(x.innerHTML)
x.innerHTML = "Hello this text has been modified!"
</script>
```

(friendly reminder that you can put these codes into [CodePen](https://codepen.io) to see it in action)

This script will first read the div with the id `textdiv` and outputs its content: "Hello this is a text!" to the console. It will then change the content of that div to "Hello this text has been modified". This happens very quickly, so you won't be able to see the div before it's modified.  

Note that we put the element we're reaching into the variable `x`. This helps us access that element again without having to type out the long `getElement` function again. 

If you want to modify its content, don't put `document.getElementById(...).innerHTML` inside a variable. This will not work:

```html
<div id="textdiv">Hello this is a text!</div>

<script>
var x = document.getElementById("textdiv").innerHTML
x = "Hello this text has been modified!"
// this won't work!
</script>
```

The reason for that isn't really important right now. But if you're curious, you can google about "passing by reference" and "passing by value".   

### Reading and Changing CSS
To access an element's CSS styling, you can use `style`. 

```js
console.log(x.style)
```

That'll output a very long list containing every single CSS properties possible, even those that are unmodified. We usually just directly point to the property we need.
 
```js
console.log(x.style.color)
```

Note that variable name in Javascript can't contain hyphen (-). CSS properties that use hyphen is automatically transformed to camelCase in JavaScript: `font-weight` will become `fontWeight`, `margin-right` will become `marginRight`, etc.

Now that you have access to the HTML element, you can freely modify it like you did with `innerHTML`.

```js
x.innerHTML = "Hello I am modified!"
x.style.color = "blue"
```

Note that innerHTML and CSS values are all always strings. Even when you modify a CSS property that's just a number, you'll still need to send it as a string.

```js
x.style.lineHeight = "0.5" // this is good
x.style.lineHeight = 0.5 // this is bad
```

Some browsers might be able to interpret it fine, but not all. When in doubt, just use the safer option.

### Content of Input Elements
To access the **value** of an input element (like textboxes), the code is just `element.value`.
```html
<input id="inputthing" type="text">Thing is typed here</input>

<script>
console.log(document.getElementById("inputthing").value)
</script>
```

This will also work for other types of input like checkboxes, and also for `<option>` of a `<select>`. [Here](https://www.w3schools.com/html/html_form_input_types.asp)is the reference page for input types, and [here](https://www.w3schools.com/tags/tag_select.asp) is for selectable. 

### Other Attributes
Attributes are those things you put inside the tag e.g. `src` or `href` or `id`. Some attributes, like `value` and `style`, can be accessed like I showed you above. Another attribute you can access directly is `class`, which you can access with `element.className`. 

For everything else, use the `getAttribute()` function.

```html
<a id="my-link" href="http://github.com">Click</a>
```

```js
var x = document.getElementById('my-link')
console.log(x.getAttribute('href'))
```

This will output `http://github.com`.

To change the value of that attribute, use the `setAttribute()` function.

```js
x.setAttribute('href', 'https://mozilla.org`)
```

This will change the value of the attribute `href` to `https://mozilla.org`, thus changing where the link direct to. You can also use this function to add an attribute that isnt't defined yet.
 
```js
x.setAttribute('target', '_blank')
``` 

As you know, `target="_blank"` will make the link open in a new tab. 