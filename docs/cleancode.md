# A Reminder to Keep your Code Clean and Well-Structured

A computer doesn't care how you write your code; as long as the syntax is right, even if it's an unreadable pile of spaghetti, it'll run without problem. But you, as the person who writes and will eventually have to read it, should care. If something goes wrong, you're going to have to look through your code to fix it. If you want to add more features, or to remove some, or to modify things, or to upgrade, or for a myriad of other reasons, and there will be reasons, you're gonna have to read what you wrote. And if other people want to look at your code, you shouldn't put them through hell. 

That's why good, clean code, matters. While at the beginning I'd encourage you to go hog wild---try everything, do anything, get a feel of what's possible---at some point your code shouldn't "just work". It should also be easy to read and easy to add to. 

There's no one way to describe what a good piece of code is like, but I like to think of it as fulfilling all of the below:

1. It works
2. You can tell why it works
3. It's pleasant to read
4. It's not a dumb resource hog

There will be plenty of time when your code works, but you can't figure out why that is so. This can be either because you misunderstood something in the basic underlying of the program, or your code is bad enough you can't tell what it's actually doing. 

The solution: Learn more about what you're trying to do. Clean up.

Unfortunately, I can't tell you exactly how to keep your code clean. It's a bit like an art: I can give you tips, you can learn about how other people do it, but at the end it's the sort of thing that you can only get through experience.

But I *can* give you tips:

## 1.  Give your variables meaningful names
I occasionally name my variables `x` or `y` in the [quick guide](js-quickguide.md). If you're actually building things, you shouldn't do this. Give your variables names that can quickly tell you what it is. It's a <form> element? Name it `contactForm` or something. 

Do note that JavaScript on the web has plenty of names that they're already using, like `document` or `window`. If you're going to name your variable a common word, check first if it's already used.    

This also applies to your functions. Give them good names that tells you what they do. If they return something, try to make it clear what its type is just from the name. For example, you'll expect something named `isMobileBrowser()` will return either a `true` or `false`.  

## 2. When names aren't enough, insert comments
You shouldn't have to scroll through mountain of codes to know what a piece of your program means. Giving good names is a good first step, but in case it's not enough, or if the program is complicated enough you can't guess from first glance,   