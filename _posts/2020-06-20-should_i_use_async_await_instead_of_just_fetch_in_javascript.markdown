---
layout: post
title:      "Should I use Async/Await instead of just fetch in JavaScript?"
date:       2020-06-21 00:15:01 +0000
permalink:  should_i_use_async_await_instead_of_just_fetch_in_javascript
---


If you have been programming in JavaScript for a while, then you have probably used the fetch() method to send and request information from an API. Here is what a typical fetch request looks like:

```
function getData() {
  fetch(myApi)
  .then(response => response.json())
  .then(results => {
    console.log(results)
    // return API data
  }
}
```
In ES8, JavaScript introduced the async and await keywords. If you see the keyword 'async' in front of a function, you can immediately tell yourself, “This function returns a promise.” Even if the function does not implicitly return a promise, the JavaScript engine will automatically wrap the returned value in a resolved promise.

Functions preceded by async run asynchronously via JavaScript’s event loop. The await keyword tells JavaScript to wait until a promise is resolved and then return its result. However, await can only be used inside an async function, or else you will get a syntax error. Here is the above example rewritten with async and await:
```

async function getData() {
  let response = await fetch(myApi);
  let results = await response.json();
  return results;
}
```
After you call the getData() function, you can attach a then() to manipulate the returned results and a catch() for any errors. The async and await keywords are ‘syntactic sugar’ that allow you to express things more clearly and concisely. In my opinion, it is much easier to read code blocks without multiple then() chains.

So should you use async/await instead of only fetch? In the end, they are both able to return the same data. But if your goal as a JavaScript programmer is to create clean, easy to read code, then you should embrace async and await and write that syntactic sugary goodness.
