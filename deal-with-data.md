# Deal with data

In a backend application, you often need to retrieve data from various sources such as <mark style="color:red;">**URLs, JSON files, and request bodies.**</mark> Here's how you might handle each of these sources

**URLs**: When you need to fetch data from a URL, you typically make an HTTP request to the specified URL. This could be a GET request to retrieve data or a POST request to send data to the server.



```javascript
const axios = require('axios');

async function fetchDataFromUrl(url) {
    try {
        const response = await axios.get(url);
        return response.data; // Extracting data from the response
    } catch (error) {
        console.error('Error fetching data from URL:', error);
        throw error;
    }
}

// Usage
const url = 'https://example.com/api/data';
fetchDataFromUrl(url)
    .then(data => {
        console.log('Data fetched from URL:', data);
    })
    .catch(error => {
        console.error('Error:', error);
    });

```

**JSON files**: If you have data stored in a JSON file, you can read the file using file system APIs provided by Node.js.

```javascript
 codeconst fs = require('fs');

function readJsonFile(filePath) {
    try {
        const jsonData = fs.readFileSync(filePath, 'utf8');
        return JSON.parse(jsonData);
    } catch (error) {
        console.error('Error reading JSON file:', error);
        throw error;
    }
}

// Usage
const filePath = 'data.json';
const jsonData = readJsonFile(filePath);
console.log('Data from JSON file:', jsonData);
```

**Request body**: When handling incoming HTTP requests in your backend server, you can access the request body to retrieve data sent by the client. This is commonly done using middleware like `body-parser` or built-in functionality in frameworks like Express.js.

```javascript
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
app.use(bodyParser.json());

app.post('/api/data', (req, res) => {
    const requestData = req.body;
    console.log('Data received in request body:', requestData);
    // Process the data as needed
    res.send('Data received successfully');
});

app.listen(3000, () => {
    console.log('Server is running on port 3000');
});

```

To achieve storing <mark style="color:red;">**PDF**</mark> files in your local database using Express.js

**Set Up Express Middleware**:

* The `express.urlencoded()` middleware in Express.js is used to parse incoming requests with URL-encoded payloads. It is commonly used to handle form data submitted via POST requests.

The `express.urlencoded()` middleware in Express.js is used to parse incoming requests with URL-encoded payloads. It is commonly used to handle form data submitted via POST requests.

When a form is submitted with `enctype="application/x-www-form-urlencoded"` (which is the default for HTML forms), the data is sent in the request body in the form of key-value pairs separated by "&" characters. For example, a form with fields `name` and `email` might submit data like this:

```css
cssCopy codename=John&email=john@example.com
```

The `express.urlencoded()` middleware parses this data and makes it available in `req.body` object.

Here's how you can use `express.urlencoded()` in an Express.js application:

```javascript
javascriptCopy codeconst express = require('express');
const app = express();

// Middleware to parse URL-encoded data
app.use(express.urlencoded({ extended: true }));

// Route handler to handle form submission
app.post('/submit-form', (req, res) => {
    console.log(req.body); // Access form data from req.body
    res.send('Form submitted successfully');
});

app.listen(3000, () => {
    console.log('Server is running on port 3000');
});
```

In this example, when a POST request is made to the `/submit-form` endpoint with URL-encoded form data, the `express.urlencoded()` middleware parses the data and makes it available in the `req.body` object inside the route handler.

The `extended: true` option allows for nested objects and arrays to be encoded in the URL-encoded format. If you don't need this feature, you can set it to `false`. However, it's generally recommended to set it to `true` for compatibility with browsers and other clients.

