# Timing

## Timeout
Timeout can be used to make your codes "wait" a set amount of time before running. The code for that is **setTimeout(*function*, *time in milliseconds*)**. 

So for example if you have this code:

```js
function doAnimation() {
...// animation code here
}
setTimeout(doAnimation, 3000)
```

The function `doAnimation()` will be run after 3 seconds (3000 milliseconds). By the fault, that's 3 seconds after the code is parsed, but you can also combine that with events.

```js
function doThing() {
...
}

function onBlueButtonClick(e) {
	setTimeout(doThing, 2500)
	...
}

var button = document.getElementById('bluebutton').
button.addEventListener('click', onBlueButtonClick)
```

With that code, `doThing()` will run 2.5 seconds after the 'bluebutton' button is clicked.

## Interval

Another thing you can do is `setInterval()`. It works the same way, except the function will be run over and over again, after the set interval. 

```js
function doAnimation() {
...// animation code here
}
seInterval(doAnimation, 3000)
```

With that, `doAnimation()` will run after 3 seconds, and then it will run again 3 seconds after that, and on and on.

To stop a `setInterval()` you have to first put it inside a variable i.e. `var interval = setInterval(...)`. You can then use `clearInterval([interval function])` to stop it. Say you have a button that can stop the infinite loop of above's `doAnimation()`. The code will look like this: 

```js
function doAnimation() {
...// animation code here
}
function stopAnimation() {
	clearInterval(intervalSetter)
}

var intervalSetter = setInterval(doAnimation, 3000)

var stopButton = document.getElementById('stopbutton')
stopButton.addEventListener('click', stopAnimation)
```

`setTimeout()` can also be cancelled by using `clearTimeout()` in much the same way. 

Here's an example of what you can do with setting and clearing interval. See if you can make something similar!

<div class="bar-container">
<div class="bar" id="progress-bar">
</div>
</div>

<div>
<button class="progress-button" id="progress-start">Start</button>
<button class="progress-button" id="progress-stop">Stop</button>
</div>

<style>
.bar-container {
	border: solid 1px dimgray;
	width: 60%;
	margin: 0 auto;
	height: 20px;
}
.bar {
	background-color: dimgray;
	height: 100%;
	width: 0;
}
.progress-button {
	font-size: 17px;
	display: block;
	margin: 10px auto;
}
</style>

<script>
var progress = 0
var progressInterval 

function startProgress() {
	// reset the bar
	// without this there will be multiple intervals running!
	clearInterval(progressInterval) 
	progress = 0
	
	progressInterval = setInterval(moveProgress, 50)
}

function moveProgress() {
	let progressBar = document.getElementById('progress-bar')
	progress += 1
	progressBar.style.width = String(progress) + "%"
	
	if (progress >= 100) {
		clearInterval(progressInterval)
	}
}

document.getElementById('progress-start').addEventListener('click', startProgress)

document.getElementById('progress-stop').addEventListener('click', () => { clearInterval(progressInterval) })
</script>

[Click here](https://codepen.io/PseudoMon/pen/jONVoWO) for the codes.
