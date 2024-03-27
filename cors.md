# CORS



## Why does it exist?🤔 <a href="#e7cc" id="e7cc"></a>

To protect us! It’s our friend!❤️🐕

Most of the time a website will require resources hosted in the same place as the website is, for example, making API calls to the same backend that is serving the website.🏡

So this policy would be the first layer of protection to avoid other unknown people using our API.⚔️

### What is Cross-Origin Resource Sharing (CORS)?

Interestingly, this is not an error as we portray it, but rather the expected behavior. Our web browsers enforce the **same-origin policy**, which restricts resource sharing across different origins. [Cross-origin resource sharing](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS), or CORS, is the mechanism through which we can overcome this barrier. To understand CORS, let us first understand the same-origin policy and its need.



&#x20;_I introduce you to CORS or Cross-Origin-Resource-Sharing which is one of the most important and fundamental protocols used in web technology today. You will learn the basic concepts that you will use in the majority of cases you will ever encounter. In addition to that, we will see examples of how to correctly configure CORS in Node.js._

It is uncommon to find a complex web page that gets all the data it displays from only one website or origin. Some of the resources displayed, like images, tweets and texts, come from other domains. This process of sharing resources between different origins is controlled by the protocol called CORS or **Cross Origin Resource Sharing.**

```javascript
// config Express.js
app.use(express.json());
app.set('port', 3000)
app.use((req, res, next) => {
    // allow different IP address
    res.setHeader('Access-Control-Allow-Origin', '*');
    // allow different header field 
    res.header('Access-Control-Allow-Headers', '*');
    res.header('Access-Control-Allow-Methods', 'POST, PUT, GET, OPTIONS');

    next();
});
```

or&#x20;

```javascript
const express = require('express')
const cors = require('cors')

const app = express()

// globally
app.use(cors())

// alternatively, per-route
app.get('/foobar', cors(), (req, res) => res.send('foobar'))

app.listen(8080, () => console.log('Listening on port 8080'))
```

#### The same-origin policy

In simple terms, the same-origin policy is the web version of “don’t talk to strangers” incorporated by the browser.

All modern web browsers available today follow the same-origin policy that restricts how `XMLHttpRequest` and `fetch` requests from one origin interact with a resource from another origin. What’s an origin, exactly?

It’s the combination of a scheme, domain, and port. The scheme could be HTTP, HTTPS, FTP, or anything else. Similarly, the port can also be any valid port number. Same-origin requests are essentially those requests whose scheme, domain, and port match. Let’s look at the following example.

Assuming our origin is `http://localhost:3000`, the requests can be categorized into same-origin or cross-origin requests as follows:

| Origin                                  | Request Type | Reason                                                                  |
| --------------------------------------- | ------------ | ----------------------------------------------------------------------- |
| http://localhost:3000/about             | Same-origin  | The path “/about” is not considered as a part of the origin             |
| http://localhost:3000/shop/product.html | Same-origin  | The path “/shop/product.html” is not considered as a part of the origin |
| http://localhost:5000                   | Cross-origin | Different port (5000 instead of 3000)                                   |
| https://localhost:3000                  | Cross-origin | Different scheme (HTTPS instead of HTTP)                                |
| https://blog.logrocket.com              | Cross-origin | Different scheme, domain, and port                                      |

This is the reason why your frontend running on <mark style="color:red;">`http://localhost:3000`</mark> <mark style="color:green;">**cannot make API calls to your server**</mark> running <mark style="color:red;">`http://localhost:5000`</mark> or any other port when you develop single-page applications (SPAs).

Also, requests from origin <mark style="color:orange;">**`https://mywebsite.com`**</mark> to origin <mark style="color:orange;">**`https://api.mywebsite.com`**</mark> are still considered cross-site requests even though the second origin is a subdomain.

Due to the same-origin policy, the browser will automatically prevent responses from cross-origin requests from being shared with the client. This is great for security reasons! But not all websites are malicious and there are multiple scenarios in which you might need to fetch data from different origins, especially in the modern age of [microservice architecture](https://blog.logrocket.com/methods-for-microservice-communication/) where different applications are hosted on different origins.

### Allowing cross-site requests with CORS

We’ve established that the browser doesn’t allow resource sharing between different origins, yet there are countless examples where we are able to do so. How? This is where CORS comes into the picture.

CORS is an HTTP header-based protocol that enables resource sharing between different origins. Alongside the HTTP headers, CORS also relies on the browser’s preflight-flight request using the `OPTIONS` method for non-simple requests. More on simple and preflight requests later in this article.

Because HTTP headers are the crux of the CORS mechanism, let’s look at these headers and what each of them signifies.

#### `Access-Control-Allow-Origin`

The `Access-Control-Allow-Origin` response header is perhaps the most important HTTP header set by the CORS mechanism. The value of this header consists of origins that are allowed to access the resources. If this header is not present in the response headers, it means that CORS has not been set up on the server.

If this header is present, its value is checked against the `Origin` header of request headers. If the values match, the request will be completed successfully and resources will be shared. Upon mismatch, the browser will respond with a CORS error.

To allow all origins to access the resources in the case of a public API, the `Access-Control-Allow-Origin` header can be set to `*` on the server. In order to restrict only particular origins to access the resources, the header can be set to the complete domain of the client origin such as `https://mywebsite.com`.

#### `Access-Control-Allow-Methods`

The `Access-Control-Allow-Methods` response header is used to specify the allowed HTTP method or a list of HTTP methods such as `GET`, `POST`, and `PUT` that the server can respond to.

This header is present in the response to pre-flighted requests. If the HTTP method of your request is not present in this list of allowed methods, it will result in a CORS error. This is highly useful when you want to restrict users from modifying the data through `POST`, `PUT`, `PATCH`, or `DELETE` requests.

#### `Access-Control-Allow-Headers`

The `Access-Control-Allow-Headers` response header indicates the list of allowed HTTP headers that your request can have. To support custom headers such as `x-auth-token`, you can set up CORS on your server accordingly.

Requests that consist of other headers apart from the allowed headers will result in a CORS error. Similar to the `Access-Control-Allow-Methods` header, this header is used in response to pre-flighted requests.

#### `Access-Control-Max-Age`

Pre-flighted requests require the browser to first make a request to the server using the `OPTIONS` HTTP method. Only after this can the main request be made if it is deemed safe. However, making the `OPTIONS` call for each pre-flighted request can be expensive.

To prevent this, the server can respond with the `Access-Control-Max-Age` header, allowing the browser to cache the result of pre-flighted requests for a certain amount of time. The value of this header is the amount of time in terms of delta seconds.

Overall, here’s the syntax of how CORS response headers look like:

```javascript
Access-Control-Allow-Origin: <allowed_origin> | *
Access-Control-Allow-Methods: <method> | [<method>]
Access-Control-Allow-Headers: <header> | [<header>]
Access-Control-Max-Age: <delta-seconds>
```

### Simple requests vs. pre-flighted requests

Requests that do not trigger a CORS preflight fall under the category of simple requests. However, the request has to satisfy some conditions only after it is deemed as a simple request. These conditions are:

1. The HTTP method of the request should be one of these: `GET`, `POST`, or `HEAD`
2. The request headers should only consist of CORS safe-listed headers such as `Accept`, `Accept-Language`, `Content-Language`, and `Content-Type` apart from the headers automatically set by the user agent
3. The `Content-Type` header should have only either of these three values: `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`
4. No event listeners are registered on the object returned by the `XMLHttpRequest.upload` property if using `XMLHttpRequest`
5. No `ReadableStream` object should be used in the request

On failing to satisfy either of these conditions, the request is considered to be a pre-flighted request. For such requests, the browser has to first send a request using the `OPTIONS` method to the different origin.

This is used to check if the actual request is safe to send to the server. The approval or rejection of the actual request depends on the response headers to the pre-flighted request. If there is a mismatch between these response headers and the main request’s headers, the request is not made.

### Enabling CORS

Let’s consider our initial situation where we faced the CORS error. There are multiple ways we could resolve this issue depending on whether we have access to the server on which the resources are hosted. We can narrow it down to two situations:

1. You have access to the backend or know the backend developer
2. You can manage only the frontend and cannot access the backend server

#### If you have access to the backend:

Because CORS is just an HTTP header-based mechanism, you can configure the server to respond with appropriate headers in order to enable resource sharing across different origins. Have a look at the CORS headers we discussed above and set the headers accordingly.

For [Node.js](https://nodejs.org/en/) + [Express.js](https://expressjs.com/) developers, you can install the `cors` middleware from npm. Here is a snippet that uses the Express web framework, along with the CORS middleware:

```
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());

app.get('/', (req, res) => {
  res.send('API running with CORS enabled');
});

app.listen(5000, console.log('Server running on port 5000'));
```

If you don’t pass an object consisting of CORS configuration, the default configuration will be used, which is equivalent to:

```javascript
{
  "origin": "*",
  "methods": "GET,HEAD,PUT,PATCH,POST,DELETE",
  "preflightContinue": false,
  "optionsSuccessStatus": 204
}
```

Here is how you could configure CORS on your server which will only allow `GET` requests from `https://yourwebsite.com` with headers `Content-Type` and `Authorization` with a 10 minutes preflight cache time:

```
app.use(cors({
  origin: 'https://yourwebsite.com',
  methods: ['GET'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  maxAge: 600
}));
```

While this code is specific to Express.js and Node.js, the concept remains the same. Using the programming language and framework of your choice, you can manually set the CORS headers with your responses or create a custom middleware for the same.

#### If you only have access to the frontend:

Quite often, we may not have access to the backend server. For example, a public API. Due to this, we cannot add headers to the response we receive. However, we could use a proxy server that will add the CORS headers to the proxied request.

The [cors-anywhere](https://github.com/Rob--W/cors-anywhere) project is a Node.js reverse proxy that can allow us to do the same. The proxy server is available on `https://cors-anywhere.herokuapp.com/`, but you can build your own proxy server by cloning the repository and deploying it on a free platform like [Heroku](https://www.heroku.com/) or any other desired platform.

In this method, instead of directly making the request to the server like this:

```
fetch('https://jsonplaceholder.typicode.com/posts');
```
