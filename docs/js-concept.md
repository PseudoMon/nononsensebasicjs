# JavaScript?
JavaScript is the programming language of the web. Basically, with JavaScript you can make your website to Do Stuff instead of just showing them. You can make fancy menus and animation, you can have some spiffy interaction, you can even make a video game with it, if you're dedicated enough.

You see [this site](http://xacla.diverse.jp/) and [this](https://hypnosismic.com/)? You need some heavy JavaScript knowledge to do those. 

Learning JavaScript is an absolute must if you want to get anywhere at all in web development. Most websites these days are built with the help of a JavaScript "framework" or "library" like React or jQuery. While they can be very helpful in building complicated websites, it's best if you learn learn the basic first. That's what this guide is for!

Let's get some basic concepts down first!

## 1. JavaScript is a Programming Language
JavaScript is a programming language. That means that if you've learned any programming language before, then learning JavaScript should be pretty easy.

JavaScript has most of the basic programming shenanigans. It has variables, it has functions, it has logical operations. It has booleans, strings, numbers, arrays, and objects. Most things you can do in other programming languages, you can do here.

If you've learned programming before, JavaScript might have some weird behaviours that will throw you off. You'll get used to it.

I'm not going to teach you how to program, but the concepts in this guide aren't very complicated. If you're savvy, you can maybe learn as so you go along. 

[Here's a really quick guide](js-quickguide.md), if you need it.

## 2. JavaScript is Run by the Browser
JavaScript, like HTML and CSS, is run by your browser. When you open a website, it sends you a package of HTML/CSS/JavaScript codes that your computer will then read and process into the website you see.

This means that whatever you do to that website, whatever part of the website change when you interact with it, it will only affect what you're seeing right now. Some websites are equipped with ways to transmit your input to the server. The server *can* then use this data to change how other people see the website. JavaScript alone, however, won't be able to do jack squat to other people seeing the same website.

This *also* means that when you build a website with JavaScript, it's the website visitors who ultimately decide how that script is run. They might block it, they might have a browser add-on that can modify it. If your script is particularly heavy their device might not have the power to run it. Different browsers might also have different specifications, and old browsers will probably fail to run modern JavaScript. Keep this in mind when building your websites!

This collection of HTML, CSS, and JavaScript codes (and images and other files) that are transmitted to your browser is called the **front-end**. This is different from codes that run in the server: we call that the **back-end**. 

You can always see every part of the front-end that you receive. If you view the **source** of this website (right-click -> View Source), you can see all the HTML/CSS/JS that built it. 

However, most JavaScript on most websites are bundled and minified (i.e., having all the spaces and readability squished to save space), so viewing the **source** won't be very useful if you want to learn how the website work.

Most modern desktop browser lets you run JavaScript code on the fly. If you're reading this with Firefox or Chrome on desktop, open the Developer Tools by pressing F12, then click on Console. You can type in any JavaScript code in there and it'll run it. Use this to play around with the language.

You're going to use that Developer Tools *a lot* in web development, so you should get used to it too.

## 3. JavaScript on the Web are Used to Manipulate the DOM

**DOM** is short for Document Object Model, but it's easier to think of it as The Things You See On-Screen. When we say we "manipulate the DOM", it means we're changing what's being shown on-screen.

<div class="example-box" id="divtochange">Try clicking the button</div>

<button style="margin-top: 1em;" class="example-button" onclick="changeDiv()">Click me</button>

<script>
function changeDiv() {
	console.log('uwu')
	var div = document.getElementById("divtochange")
	console.log(div.innerHTML)
	if (div.innerHTML === "Changed!") {
		div.innerHTML = "Changed again!"
	} else if (div.innerHTML !== "Changed!") {
		div.innerHTML = "Changed!"
	}
}
</script>

The **Click me** button is connected to a JS function that changes the content of the box. Try inspecting the box element with your browser's DevTools (press F12, or right-click and choose Inspect Element) and see how it changes whenever you click the button. 

That's the thing that Javscript on the web do. It modifies the base HTML and CSS that's shown on your screen. Learning JavaScript for web development is just figuring out how to do that effectively. 

Remember, JavaScript is ran by your browser. It only changes how the website looks on *your* browser, not the **source**. The base HTML and CSS files in the server is unaffected.

## The Three Concepts Redux

1. JavaScript is a programming language
2. JavaScript is ran by the browser
3. JavaScript on the web is used to manipulate the DOM

You got that? Make sure you remember and understand these before moving on.