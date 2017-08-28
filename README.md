# Promises-and-Fetch


## What is a Promise?

What is fetch and how do you use it?

The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP requests and responses. It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.
Fetch is a modern concept equivalent to XMLHttpRequest. It offers a lot of the same functionality as the XMLHttpRequest, but is designed to be more extensible and efficient.
Making fetch requests
A basic fetch request is really simple to set up. Have a look at the following code:

```
var myImage = document.querySelector('img');
fetch('flowers.jpg').then(function(response) {
return response.blob();
}).then(function(myBlob) {
var objectURL = URL.createObjectURL(myBlob);
myImage.src = objectURL;
});

```
Here we are fetching an image across the network and inserting it into an <img> element. The simplest use of fetch()takes one argument — the path to the resource you want to fetch — and returns a promise containing the response (a Response object).


## Waht are the downsides to using Fetch?

* When you use ```.fetch()``` there is a two-step process when handing JSON data.
The first is to make the actual request and then the second is to call the .json() method
on the response.