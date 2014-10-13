# Response

The response will always be in JSON.

## Response codes

### Success

Code | Description
---- | -----------
200 | OK - Standard response for successful HTTP requests. The actual response will depend on the request method used. In a GET request, the response will contain an entity corresponding to the requested resource. In a POST request the response will contain an entity describing or containing the result of the action.
201 | Resource created - The request has been fulfilled and resulted in a new resource being created.

### Errors

Code | Description
---- | -----------
400 | Bad request - The request cannot be fulfilled due to bad syntax or missing parameters.
401 | Unauthorized - Similar to 403 Forbidden, but specifically for use when authentication is required and has failed or has not yet been provided.
403 | Forbidden - The request was a valid request, but the server is refusing to respond to it. Unlike a 401 Unauthorized response, authenticating will make no difference.
404 | Not found - The requested resource could not be found but may be available again in the future.
405 | Method not allowed - A request was made of a resource using a request method not supported by that resource; for example, using GET on a form which requires data to be presented via POST, or using PUT on a read-only resource.

### Fatal

Code | Description
---- | -----------
500 | Internal server error - A generic error message, given when an unexpected condition was encountered and no more specific message is suitable.
