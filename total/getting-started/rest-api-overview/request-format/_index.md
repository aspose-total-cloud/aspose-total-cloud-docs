---
title: "Request Format"
type: docs
url: /getting-started/rest-api-overview/request-format/
weight: 30
---

## Authenticating API Requests
Please read [this article](/total/getting-started/rest-api-overview/authenticating-api-requests/). It explained in detail how to authenticate Aspose for Cloud API requests.

## Content types
The API handles request and response content types separated. To specify the response content type you have to set the *Accept-Header* header to:

- *application/json*
- *application/xml*
- *application/octet-stream*

To specify the mime type of the request body, you have to set the *Content-Type* header to:

- *application/json*
- *application/xml*
- *multipart/form-data*

## Request Parameters and Request Body
Applications can send data to the REST API either as Request Parameters (the part after the '**?**' in a URL) or within the Request Body (i.e. equivalent of 'posting' an HTML form).  
Generally, the Request Body is used when there are larger amounts of data or attachments require to be sent to the REST API as part of an operation and usually such operations will be using the POST or PUT methods.

## Retrieving Resources using HTTP GET Method
Resources are retrieved by using the HTTP GET method. The default response unless otherwise specified is XML for all not binary resources (which are not files, images etc). For Files the default response will match the File Format.

{{% alert color="primary" %}} 

You can also use Accept header (Accept: application/json) to get the response in JSON format. 

{{% /alert %}} 

## Safe & Idempotent
All Aspose Cloud HTTP GET requests will be Safe (they are guaranteed not to change the state of a resource), and idempotent (calling once has the same effect as multiple calls).

This is vital because the infrastructure of the Web and all HTTP Clients & Tools assumes GET request are safe in order to support Caching, Indexing etc.

## Creating & Updating Resources using HTTP POST and PUT Methods
Resources will be created or updated by performing an HTTP PUT or HTTP POST to a resource URL. In a PUT or POST request, the properties of the object you wish to update will be represented as form urlencoded key/value pairs.

Generally, developers should set the HTTP Content-Type header to "application/x-www-form-urlencoded" when making requests like this, however, we should be flexible in what we receive so should not require this if the requests intention is obvious.

## When to use POST and when to use PUT
- **POST** is not idempotent and therefore will be used for CREATE operations where requesting the same URI multiple times should create multiple operations.
- **PUT** is idempotent so is used for UPDATE operations where requesting the same URI multiple times simply has the same effect as calling it once.

As with GET the semantics of the above operation are important as the infrastructure of the Web such as proxies, clients, caches etc. will behave appropriately so long as the correct method is used.

{{% alert color="primary" %}} 

POST is the most flexible method and in addition to creating resources it has the following uses in our API;

- To create a new resource, using the resource as a factory.
- To modify one or more resources via a controller resource.
- To run queries with large inputs as described.
- To perform any unsafe or non-idempotent operation when no other HTTP method
- seems appropriate.

{{% /alert %}} 

## Deleting Resources using HTTP DELETE Method
To delete a resource the user will make a HTTP DELETE request to the resource's URL.

If a resource has already been deleted then a subsequent calling of this method will resort in a HTTP 404 error.
