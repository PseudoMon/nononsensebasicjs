# Animating with Transition
You can do a lot of neat animation with just a bit of Javascript and CSS. Just add a `transition` property to the CSS and modify the style with JS.

<div id="colourbox" class="colourbox">
</div>
<style>
.colourbox {
  height: 100px;
  width: 100px;
  background-color: skyblue;
  position: relative;
  left: 0;
  transition: 1s;
}
</style>

<script>
function animateBox(e) {  
	let box = e.target
  box.style.backgroundColor = "lightcoral"
  box.style.left = "100px";
}

document.getElementById("colourbox").addEventListener('click', animateBox)
</script>

Here's the script for that:

```html
<div id="colourbox" class="colourbox">
</div>
```

```css
.colourbox {
  height: 100px;
  width: 100px;
  background-color: skyblue;
  position: relative;
  left: 0;
  transition: 1s;
}
```

```js
function animateBox(e) {  
	let box = e.target
  box.style.backgroundColor = "lightcoral"
  box.style.left = "100px";
}

document.getElementById("colourbox").addEventListener('click', animateBox)
```

Note that I put `left: 0` in the CSS. Your element should have default values for every properties that the script will modify. Otherwise, the transition might not work.

Here's a version where you can toggle between the two colour/positions.

<div id="colourbox2" class="colourbox blue">
</div>
<style>
.colourbox {
  height: 100px;
  width: 100px;
  position: relative;
  left: 0;
  background-color: skyblue;
  transition: 1s;
}

.colourbox.blue {
  background-color: skyblue;
  left: 0;
}

.colourbox.red {
  background-color: lightcoral;
  left: 100px;
}
</style>
<script>
function animateBox2(e) {  
    let box = e.target
    if (box.className === "colourbox blue") {
      box.className = "colourbox red"
    } else {
      box.className = "colourbox blue"
    }
}

document.getElementById("colourbox2").addEventListener('click', animateBox2)
</script>

[Open this CodePen](https://codepen.io/PseudoMon/pen/wvwgpNE) if you want to see the code I used for that. Or you can try making it yourself, and then compare the codes.

I should probably write a proper guide for CSS transition some day, since there's a lot about it that might not be obvious. For now, [here's the W3Schools reference page for transition](https://www.w3schools.com/cssref/css3_pr_transition.asp). Read up.
  
For prettier transitions, you might not want to keep using the embarassingly basic `transition: 1s`. Use [these easing functions](https://easings.net/en).