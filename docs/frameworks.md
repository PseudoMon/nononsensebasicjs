# Frameworks and Libraries: Why we need them
Basic JavaScript is great if you just want to, say, add some nice menu transition or a changeable colour theme or a small pop-up. But once you start building more complicated websites, you'll soon notice that your code is cluttered with too many `getElement` and `addEventListener` and too many IDs and variable names than you can remember.

So basic JavaScript is actually pretty hard to use when building large websites. To make this process easier, people built **libraries** that helps simplify certain tasks and **frameworks** which transform the entire process. 

## Libraries
A **library** in programming-speak is a collection of codes that do specific things and can be reused in multiple different environments. So basically someone wrote some code that do Thing, and then they released it for other people to use. You can then just **include** (also called **import**s) their code into your code and you can also do Thing without having to make the entire thing from scratch. Capiche?

[jQuery](https://jquery.com/) is probably the most used JavaScript library in the world. It contains A Lot, but its main appeal is that instead of having to write this:

```js
document.getElementById('button').addEventListener('click', ...)
``` 

You just have to write this:

```js
$('#button').click(...)
```

This simplicity caused jQuery to be so widespread, but it's also packed with so many features that it might be too bloated for your website. Modern JavaScript has also incorporated many of the functions that make jQuery so popular, so there's less reason to use it nowadays. If you just want a bit of extra functionalities, basic JavaScript is preferred over including jQuery's entire library. 

There are also other libraries that only add specific functionalities. For example, [Popper.JS](https://popper.js.org/) lets you easily make small pop-ups. There's also [Moment.js](https://momentjs.com/), which helps you in showing and calculating the time.

## Frameworks
While you can think of a **library** as a set of new tools that you can use, a **framework** transforms how you code and how you think about your code. It's all normal, standard-compliant, JavaScript underneath, but it gives you an interface to code in a simpler, less cluttered syntax.

The Big Three of frontend framework at the moment is [React](https://reactjs.org/), [Vue](https://vuejs.org/), and [Angular](https://angularjs.org/). You can check their websites to see just how different coding with them is.

My personal favourite for projects that aren't too large, is [Riot](https://riot.js.org/). It's, in my opinion, easier to use and much closer to basic HTML/CSS/JS while still being useful.

## Isn't framework also a library?
Yes, a framework is also considered library. There's no really clear-cut definition of what's a "framework" and what's not. The definition I use is one version. Other people might also consider jQuery a framework. \*shrugs\*.

## Including libraries in your website
It's best to defer to each library's homepage to know how to best include it in the owebsite you're building. The simplest ones have a `<script src=...>` that you can just copy-paste. Others let you download a .js file. Other might involve something called **NPM**. 

**NPM** is short for Node Package Manager, and explaining *that* is going to be too much for this simple guide. Find out on your own! Good luck! 

