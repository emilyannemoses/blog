---
layout: post
title:  "Making HTTP Requests"
---

Here's how to use JavaScript's `XMLHttp`, `fetch()`, `ajax` (on the DOM) and `axios` or `isomorphic-fetch` (in Node) to make HTTP requests!

It's easy, I promise.

The Why.

Once we start building sites beyond static pages, we'll notice that we run into some issues with *how* to get data loaded onto our page!

JavaScript's built-in `XMLHttpRequest` objects interact with web servers. This means we can retrieve data from a URL without refreshing the page. This facilitates asynchronous work. A synchronously loaded web page would block your website from being viewed or interacted with until the data was loaded completely, which lends itself to poor user experience on the web.

`AJAX` stands for Asynchronous JavaScript And XML. This is because AJAX was built using JS's built-in XMLHttp object. AJAX and XMLHttp could colloquially be referred to as the same thing, but implementation of each could look different. Generally, when speaking of AJAX, many developers are talking about jQuery's `ajax()` method.

Aside on XML and JSON: When fetching data from an API, our requests could come thru as several different types of formats. Two popular ones: XML format and JSON format. I'm going to be using JSON format mainly because it's more popular in the web-world, mostly for its speed of processing and ease of use.

With the advent of ES6, JavaScript's Fetch API provides more powerful and flexible features, which is why it is becoming the choice above utilizing the entire jQuery library just to do a call to an API.

Examples:

If you follow [this link](https://eamoses.github.io/api-requests/) to this live site in another tab, you'll see a user can interact with the browser to make a call to an API.  The first button is triggering an XMLHttpRequest.

`XMLHttpRequest()`:

```javascript
// Vanilla JavaScript for the DOM
const xmlh = document.getElementById('xml-button');
xmlh.addEventListener('click', function(){
    var xhr = new XMLHttpRequest();
    xhr.open('GET', 'https://reqres.in/api/products/3', true);
    xhr.onload = function(){
        const xmlText = document.getElementById('xmlhttp');
        xmlText.innerHTML = `
        XHR Response:
            ${xhr.responseText}
        `
    };
    xhr.send();
```

jQuery `ajax()` request:

Note: First you'll have to import the jQuery libarary into your HTML file: `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>`

```javascript
// jQuery using ajax - also for DOM
$('#ajax-button').click(function(){
    $.ajax({
        url: "https://reqres.in/api/products/3",
        success: function(response){
            const jsonResponse = JSON.stringify(response)
            const ajaxText = document.getElementById('ajax');
            ajaxText.innerHTML = `
            Ajax Response:
                ${jsonResponse}
            `
        }
    });
})
// Output must be json.stringified to be readable on UI
```

`fetch()`:

```javascript
// ES6 fetch - used with DOM
const fetchMe = document.getElementById('fetch-button');
fetchMe.addEventListener('click', function(){
    fetch('https://reqres.in/api/products/3')
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        const jsonResponse = JSON.stringify(data)
        const fetchIt = document.getElementById('fetchIt');
        fetchIt.innerHTML = `
        Fetch Response:
            ${jsonResponse}
        `
    });
})
// Output must be json.stringified to be readable on UI
```

Notice that each of these examples targets an element on the DOM - a button with a specific ID name which will be triggerd on-click. These examples can *only* be used DOM-side.

The following are some examples of how to do API requests server-side with NodeJS:

`axios` is an [NPM package](https://www.npmjs.com/package/axios) that you can install into your project by typing `npm i axios`. 

Then you may require the package at the top of your `.js` file, and you may run it on the command line.

Here's an axios example:

```javascript
//NPM module axios - used only with Nodejs
const axios = require('axios');

axios.get('https://reqres.in/api/products/3')
  .then(function (response) {
    console.log("Axios response: ",response.data);
  })
```

Another NPM module you can use is [isomorphic-fetch](https://www.npmjs.com/package/@applitools/isomorphic-fetch)

Installing this into your projects ensures that JavaScript's Fetch API is global so that it is consistent between both client and server.

Here's an implementation:

```javascript
fetch('https://reqres.in/api/products/3')
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log("Fetch response: ", data);
    });
```

Word of warning, each of these are examples and shouldn't be use as-is in real projects. I've left out crucial information, such as error handling. You'll want to handle errors regardless of what method of requests you choose to use in your project. See documentation for each usage for best error handling practices.

[XMLHttpRequest Docs](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)

[jQuery Ajax Docs](https://api.jquery.com/category/ajax/)

[Fetch API Docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

[isomorphic-fetch Docs](https://www.npmjs.com/package/@applitools/isomorphic-fetch)

[Axios Docs](https://www.npmjs.com/package/axios)

[Reference my GitHub Repo for Examples](https://github.com/eamoses/api-requests)

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<span><a href="https://eamoses.github.io/blog/2019/07/23/naming.html" style="float:left;">Previous: Naming Things</a><a href="#" style="float:right;">Next: TBD</a></span>