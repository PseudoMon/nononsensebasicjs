# Form Shenanigans
I hate forms. Every front-end web developer hates forms. Those who doesn't are just victims of Stockholm Syndrome.

As you should know if you know your HTML, a `<form>` is basically just a collection of `<input>`. The form can then be submitted by either clicking Enter, pressing a `<button>` or pressing a `<input type="submit">`. Some forms transmit the inputted data directly to the server, while some forms process it using JavaScript. Because this guide doesn't deal with things in the back-end, I'm just here to tell you about the latter.

First, if you want to process a form's content with Javascript, remember to use `preventDefault()` as I mentioned before.

Each element in the form should have a `name` attribute. You can then access those elements through the parent form with their `name` as key. Look here:

```html
<form id="example-form">
	<input type="text" name="textinput"/>
	<select name="selectable">
		<option value="first">First</option>
		<option value="second">Last</option>
	</select>
	<input type="submit" value="Submit" />
</form>
```

```js
function afterSubmit(e) {
	e.preventDefault()
	var textinput = e.target.textinput //look here
	var selectable = e.target.selectable //and here
	alert("You entered " + textinput.value + " and you selected the " + selectable.value + " option.") 
}

var form = document.getElementById('example-form')

form.addEventListener('submit', afterSubmit)
```

<form style="margin: 2em 0;" id="example-form">
	<input type="text" name="textinput"/>
	<select name="selectable">
		<option value="first">First</option>
		<option value="second">Last</option>
	</select>
	<input type="submit" value="Submit" />
</form>

<script>
function afterSubmit(e) {
	e.preventDefault()
	var textinput = e.target.textinput
	var selectable = e.target.selectable
	alert("You entered " + textinput.value + " and you selected the " + selectable.value + " option.") 
}
var form = document.getElementById('example-form')
form.addEventListener('submit', afterSubmit)
</script>

It only use `getElementById()` once, to **get** the form. Everything else is easily accessible through that form with the inputs' `name`s.

In fact, when trying to **get** forms, you don't even have to use its ID. If you give the form a `name`, say, like this: `<form name="someform">`, you can then access it through `document.form.someform`.

Remember that JavaScript can't have hyphen (-) in its variables! To mitigate for that, you can try accessing the name with `[]` instead of `.`. For example, if your form's name is `some-form`, you can access it with `document.form['some-form']`.

Using `[]` is generally more recommended, but, really, you can use whichever you want.

If you want to then send the data in the form on its way to the server as usual, use `submit()` on the form element. Don't forget to add the `action` attribute to the form itself.

```html
<form name="exampleform" action="/action.php" method="post">
Name: <input type="text" name="fname">
<input type="submit" value="Submit">
</form>
```

```js
function doThingsToForm(e) {
	e.preventDefault()
	... //do things here
	e.target.submit()
}
document.form['exampleform'].addEventListener('submit', doThingsToForm)
```

What the server does and what the heck `action.php` is are back-end things; they're outside the scope of this guide. Look them up elsewhere if you want to know!

There are also other ways to communicate with the server than just `submit()`. Since they're a bit beyond "basic JavaScript", I don't include them here. Look them up elsewhere if you're curious!