---
cover: >-
  https://images.unsplash.com/photo-1610337673044-720471f83677?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxlcnJvcnxlbnwwfHx8fDE3MDg2MDc2MDF8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Errors handling

ApiError

class ApiError extends Error { constructor(statusCode, message = "Something went wrong", errors = \[], stack = "") { super(message);

```javascript
    // Ensure the Error object has a stack trace
    if (stack) {
        this.stack = stack;
    } else {
        Error.captureStackTrace(this, this.constructor);
    }

    // Custom properties
    this.statusCode = statusCode;
    this.message = message;
    this.errors = errors;
    this.success = false;
}
}
export { ApiError };
```

**Constructor Arguments**: The constructor now accepts four arguments: `statusCode`, `message`, `errors`, and `stack`. The `statusCode` and `message` are provided with default values in case they are not provided. `errors` will hold any validation errors or additional error details, and `stack` is the stack trace of the error.

1. **`super()` Call**: The `super()` call in the constructor is used to call the parent `Error` class constructor. This ensures that the `message` property of the error is set correctly.
2. **Stack Trace**: If the `stack` argument is provided, it is set directly on the error instance. Otherwise, `Error.captureStackTrace()` is used to generate a stack trace for the error.
3. **Custom Properties**: The `statusCode`, `message`, `errors`, and `success` properties are set on the error instance to provide additional information about the error.
4. **Export Statement**: The `ApiError` class is exported from the module to make it accessible to other parts of the application.

Your `ApiResponse` class appears to represent a standardized structure for API responses.

```javascript
class ApiResponse {
    constructor(statusCode, data, message = "Success") {
        this.statusCode = statusCode;
        this.data = data;
        this.message = message;
        this.success = statusCode < 400; // Check if status code indicates success (less than 400)
    }
}

```

1. **Constructor Arguments**: The constructor accepts three arguments: `statusCode`, `data`, and `message`. `statusCode` represents the HTTP status code of the response, `data` contains the response data, and `message` provides a descriptive message for the response. The `message` parameter has a default value of `"Success"`.
2. **Success Property**: The `success` property is set based on whether the `statusCode` indicates success. In HTTP, status codes less than 400 typically indicate success, so the `success` property is set to `true` if `statusCode` is less than 400, and `false` otherwise.
