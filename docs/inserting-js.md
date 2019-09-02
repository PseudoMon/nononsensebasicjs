# Inserting JavaScript into Your Page

In the same way that you can put your CSS into your HTML file by using the `<style></style>` tag, you can type your JavaScript directly inside your HTML file by using the `<script></script>` tag. 

Much like CSS, you can also put your JavaScript in a different file and then link that into the HTML. Your script file should have the `.js` extension. It can then linked by putting this code into your HTML.

```html
<script src="path/to/javascript/file.js"></script>
```

Unlike the `<link rel="stylesheet">` you use for CSS files, `<script>` always needs a closing tag `</script>`. Don't forget!

You can put your Javascript anywhere, although by convention, it's usually put either at the `head` or at the bottom of `body`. Javascript in an external file can be treated as if they're copy-pasted to wherever that `<script>` tag is put.

This positioning is important! Javascript will be run before every HTML tags underneath it. This means that if your script references a HTML tag (e.g. to read it, to manipulate it) that's further down in the file, it won't be able to find it; technically that tag hasn't existed yet!

```html
<script>
var box = document.getElementById('box') 
//the above code tries to get the box
</script>

<div id="box">
But it won't work because this hasn't been made yet!
</div> 
```

Javascript that's positioned at the end of `body` negates this problem, but there are times when you won't be sure *where* your script will be put.
	
To deal with this, Javascript on the web has a function that only runs after the site loads: `window.onload`.

```js
window.onload = () => {
	//codes here will only be run after the page is loaded.
}
```

You can just put all your code inside that function, and it won't matter where you insert the script.

You can also use `document.onload` instead of `window.onload`. They do more or less the exact same thing. Feel free to google their difference.

## Experimenting with JavaScript
There are many online services that let you try out JavaScript on your browser without having to mess around with files. My personal favourite is [CodePen](https://codepen.io/), but there's also [JSFiddle](https://jsfiddle.net/) and probably others.

While they're good for experimenting or for sharing your code with other people, you should also get used to attaching your own HTML, CSS, and JS files together.

You can also use your browser's Developer Tools to experiment. You can usually open it by pressing F12 or by right-clicking -> inspect element. 
