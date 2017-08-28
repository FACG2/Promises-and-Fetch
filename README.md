# Promises-and-Fetch


## What is a Promise?

While synchronous code is easier to follow and debug, async is generally better for performance and flexibility. Why "hold up the show" when you can trigger numerous requests at once and then handle them when each is ready? Promises are becoming a big part of the JavaScript world, with many new APIs being implemented with the promise philosophy. Let's take a look at promises, the API, how it's used!

## Basic Promise Usage

```

var p = new Promise(function(resolve, reject) {

    // Do an async task async task and then...

    if(/* good condition */) {
        resolve('Success!');
    }
    else {
        reject('Failure!');
    }
});

p.then(function() {
    /* do something with the result */
}).catch(function() {
    /* error :( */
})

```


## What is fetch and how do you use it?

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


* Here is a simple example. We set the url has a variable and then pass it to fetch and set the .then() callback to console the data that gets returned from the request.

```
const url = 'https://api.spotify.com/v1/artists/0OdUWJ0sBjDrqHygGUXeCF'
fetch(url).then(data=>console.log(data));

```
https://cdn-images-1.medium.com/max/1600/1*MBFkZoDs-MQb6ztpjmM_ig.png

The second issue is how .fetch() handles error responses. Logically you would think that if .fetch() gets an error it would enter the .catch() block and return anything there, right? Not necessarily. Here is an example.
I have declare url variable which is incorrect url. I would expect a 400 error at this point and for my .fetch() to go into the .catch() block but this is what happens instead.

https://cdn-images-1.medium.com/max/1600/1*9ubEzV7mNNDPs2ZLh1k3pQ.png

const url = 'https://api.spotify.com/v1/artists/0OdUWJ0sBjDrqHygGUXeCFcdsds';
fetch(url).catch(error => console.log('BAD', error)).then(response => console.log('GOOD', response));
I’ve added the ‘BAD’ and ‘GOOD’ strings in the responses to clarify what is happening here.
https://cdn-images-1.medium.com/max/1600/1*5ZmMcEBqOE1v_evfWYmc7w.png
.
