---
layout: post
title:  "Arrow Functions"
---

So far I've been showing you function examples using Python. I'm going to switch it up because in JavaScript, there's an elusive function concept: the **arrow** function, and I'm here to demistify it for you!

# The anatomy of a "fat arrow" function

```javascript
const functionName = () => // Your code goes here
```

As you can see, an arrow function is an anonymous function. It has a reference saved in the `functionName` variable, but the function itself is not named. In addition, you don't necessarily need the curly braces after the fat arrow.

In essence, what defines this as a function are the parentheses. The parentheses indicate that we're taking in some information and we want to do something specific to it at a certain point in our program.

```javascript
// ES5 anonymous function
const multiplyES5 = function(x, y) {
  return x * y;
};

// ES6 fat arrow anonymous function
const multiplyES6 = (x, y) =>  x * y;
```

These functions do the same thing!

**Curly braces are only required if there's more than one expression to be executed within the arrow function.**

You don't necessarily need the parenthases either. If you have one parameter, you may simply write it as so:

```javascript
const hello = name => `Hello, ${name}`
hello("Emily")
```

We're using an ES6 Template Literal to write the string `Hello` with the argument `Emily`. While this is a newer JavaScript feature, this syntax can be used in conjunction with any type of function.

Let's check out an example that takes multiple parameters:

```javascript
const identity = (id, name) => ({ id: id, name: name });
identity(1, "Emily")
```

This handy-dandy function takes two arguments, `1` and `Emily` and creates an object for us!

# The physiology of an arrow function

There are **special** use cases for arrow functions. In my opinion, arrow functions should be reserved for these special cases and the regular old `function(){}` syntax should be used 99.9% of the time.

**Array Manipulation**

Let's take an array of objects:

```javascript
const races = [
  { name:'CAP 10K', price: 65 },
  { name:'Boston Marathon', price: 180 },
  { name:'Tough Mudder', price: 100 }
];
```

A neat way of looping over this array of object and extracting just what we want is to use the `.map()` array method with an arrow function.

```javascript
const prices = races.map(races => races.price);
console.log(prices); //[65, 180, 100]
```

The same clean, concise syntax with the fat arrow can be used when utilizing `.reduce()` or `.filter()` array methods!

**Promises and Callbacks**

We could chain together promises by using anonymous function after anonymous function like so:

```javascript
anAsyncFunc().then(function() {
  returnbAsync();
}).then(function() {
  returncAsync();
}).done(function() {
  finish();
});
```

Or we could chain them together using the fat arrow:

```javascript
anAsyncFunc()
.then(() => bAsync())
.then(() => cAsync())
.done(() => finish);
```

Basically, it gives us a more streamlined view of what is happening in our code. 

**This**

When you have code with multiple nested functions it can be complicated to keep track of `this` in context. ES5 has methods to get around this, either by using the `.bind()` method *or* creating a closure within the very function by declaring `var self = this;` and continuing use of the variable `self` within the function.

Arrow functions allow us to retain the scope of the caller inside of the function!  

So, you can use function expressions if you need `this` to be dynamic, and arrow functions for a lexical `this` (`this` outside of the immediate function, or in a parent function).

```javascript
const obj = {
	name: "Emily",
	age: 36,
	incrementAge: function(age){
        age = age + 1;
        console.log(age, this)
    },
	greeting: (name) => {
        let greet = `Hello, ${name}`
        console.log(greet, this)
    }
}
```

When accessing methods inside of an object, arrow functions have a different `this` than funciton expressions and logging them out is the best way to see it.

In the function expression, `this` is the parent `obj`.  In the arrow function, it does not adopt the parent object as `this`, it retains the broader `this` context, ouside of the `obj` object (in Chrome Dev Console this would be the `window` object, and in Node this would be the node object)

So you can see that arrow functions are not here to replace function expressions but in a few cases for select reasons!

Always remember to be consistent in writing code and write it with **purpose**, not just because you heard about a cool new way to do things from some lady on the Internet 🤷🏽‍♀️

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Fat arrow =▶ functions⁉️ why and when to use them in <a href="https://twitter.com/hashtag/javascript?src=hash&amp;ref_src=twsrc%5Etfw">#javascript</a> <br><br>=▶=▶=▶<a href="https://t.co/GmVaYfO8K7">https://t.co/GmVaYfO8K7</a><br><br>=▶=▶=▶<a href="https://twitter.com/hashtag/WomenInTech?src=hash&amp;ref_src=twsrc%5Etfw">#WomenInTech</a> <a href="https://twitter.com/hashtag/Knowledgeispower?src=hash&amp;ref_src=twsrc%5Etfw">#Knowledgeispower</a> <br> <a href="https://twitter.com/hashtag/DEVcommunity?src=hash&amp;ref_src=twsrc%5Etfw">#DEVcommunity</a>  <a href="https://twitter.com/hashtag/e4everything?src=hash&amp;ref_src=twsrc%5Etfw">#e4everything</a> <a href="https://twitter.com/hashtag/webdevelopment?src=hash&amp;ref_src=twsrc%5Etfw">#webdevelopment</a></p>&mdash; Emily Anne Moses (@emilyannemoses) <a href="https://twitter.com/emilyannemoses/status/1147127994672013313?ref_src=twsrc%5Etfw">July 5, 2019</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<span><a href="https://eamoses.github.io/blog/2019/07/04/functions-cont.html" style="float:left;">Previous: Functions</a><a href="https://eamoses.github.io/blog/2019/07/12/errors.html" style="float:right;">Next: Error Handling</a></span>