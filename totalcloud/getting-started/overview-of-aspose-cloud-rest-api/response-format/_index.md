---
title: "Response Format"
type: docs
url: /response-format/
weight: 40
---

**Table of Contents**

- [Response Body](#ResponseBody)
- [Reponses & Errors](#Reponses&Errors) 
  - [GET Request - Possible Return Codes](#GETRequest-PossibleReturnCodes)
  - [POST & PUT Request - Possible Return Codes](#POST&PUTRequest-PossibleReturnCodes)
  - [DELETE Request - Possible Return Codes](#DELETERequest-PossibleReturnCodes)
- [Links to Other Resources](#LinkstoOtherResources) 
  - [List Resources & Resources (with Sub-Resources)](#ListResources&Resources\(withSub-Resources\)) 
    - [Version 1.0 Support - Lists just include links to the List sub-resource.](#Version1.0Support-ListsjustincludelinkstotheListsub-resource.)
## **Response Body**
In general every response from the API contains the following information, the default return type is XML, however JSON can be set by setting request Accept-Type header to "application/json", see [Request Format](/request-format-html/) for samples.  The structure of the response body remains identical regardless of the response type.

Where the response is xml/json, the specific method is always wrapped with the following generic response which also provide status codes and error messages;

|**XML Response Type**                      |**JSON Response Type**               |
| :- | :- |
|<p>```xml</p><p>`   `<Status>OK</Status></p><p>`      `...result xml...</p><p></p><p>```</p>|<p>```javascript</p><p>{</p><p>`   `"Status": "OK",</p><p>`      `...result json...</p><p>}</p><p>```</p>|
Note that both response types contain a consistent top-level element;

- status - This contains information about the success or failure of the API call itself see Status Codes below

The content of each response type will always be identical and they are designed to be interchangeable, however there are two important differences between response types;

XML root node - as a well-formed XML document the response has a root node of *<AsposeResponse>*, there is no equivalent to this in the JSON response.

Where there is an array of results, for example if multiple Job Statuses are queried in a single API call, then the XML response type will return multiple nodes with a singular name (i.e. *<jobstatus>*) whereas the JSON return type will return a plural array of results (i.e. *"jobstatuses":*).
## **Reponses & Errors**
All response codes are included in the HTTP Status response header, and in the *<status>* element of a response. HTTP status codes <status> values vary based on the type of operation, here is a summary;
#### **GET Request - Possible Return Codes**

|**HTTP Status Code**|**<status> Value**|**Description**|
| :- | :- | :- |
|200|OK|Success|
|302|FOUND|A common redirect response; you can GET the representation at the URI in the Location response header. (We will use this to allow us to make changes to the URIs and provide for redirection for old APIs).|
|304|NOT\_MODIFIED|Your client's cached version of the representation is still up to date. (**We may use this to support caching - needs technical investigation**.)|
|400|INVALID\_CALL|Resource Invalid (improperly-formatted request)|
|401|NOT\_AUTHORIZED|Unauthorized (incorrect or missing authentication credentials)|
|404|NOT\_FOUND |Resource Not Found (requesting a non-existent document, user, or other resource)|
|405|NOT\_ALLOWED|HTTP Method Not Allowed (e.g., trying to POST to a URL that responds only to GET)|
|406|NOT\_ACCEPTABLE|Not Acceptable (server can't satisfy the Accept header specified by the client)|
|500|APPLICATION\_ERROR|Application Error|
|503|SERVICE\_UNAVAILABLE|Any temporary error which prevents a response.  Essentially this code tells HTTP-Aware clients they should wait and try again later.|
#### **POST & PUT Request - Possible Return Codes**

|**HTTP Status Code**|**<status> Value**|**Description**|
| :- | :- | :- |
|200|OK|Success|
|201|CREATED|The request was successful, we created a new resource and the response body contains the representation.|
|400|BAD\_REQUEST |Resource Invalid (improperly-formatted request)|
|401|NOT\_AUTHORIZED|Unauthorized (incorrect or missing authentication credentials)|
|404|NOT\_FOUND |Resource Not Found (requesting a non-existent document, user, or other resource)|
|405|NOT\_ALLOWED|HTTP Method Not Allowed (e.g., trying to POST to a URL that responds only to GET)|
|406|NOT\_ACCEPTABLE|Not Acceptable (server can't satisfy the Accept header specified by the client)|
|500|APPLICATION\_ERROR|Application Error|
|503|SERVICE\_UNAVAILABLE|Any temporary error which prevents a response.  Essentially this code tells HTTP-Aware clients they should wait and try again later.|
#### **DELETE Request - Possible Return Codes**

|**HTTP Status Code**|**<status> Value**|**Description**|
| :- | :- | :- |
|200|OK|Success|
|401|NOT\_AUTHORIZED|Unauthorized (incorrect or missing authentication credentials)|
|404|NOT\_FOUND |Resource Not Found (requesting a non-existent document, user, or other resource)|
|405|NOT\_ALLOWED|HTTP Method Not Allowed (e.g., trying to DELETE to a URL that responds only to GET)|
|406|NOT\_ACCEPTABLE|Not Acceptable (server can't satisfy the Accept header specified by the client)|
|500|APPLICATION\_ERROR|Application Error|
|503|SERVICE\_UNAVAILABLE|Any temporary error which prevents a response.  Essentially this code tells HTTP-Aware clients they should wait and try again later.|
{{% alert color="primary" %}} 

More info on HTTP status codes can be found here: <http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html>. Generally we should stick to the semantics of the above, though for ease-of-use we will make just a few compromises (in particularly stick to simply 200 for success messages as opposed to some of the variants).

{{% /alert %}} 
## **Links to Other Resources**
In our API every resource representation obtained from a REST API request must include URIs that identify that resource and the resources related to it. This allows for clients to traverse resources very easily without complete knowledge of the API structure - this is important for Aspose for Cloud since parts of our REST structure will be dynamic.
#### **List Resources & Resources (with Sub-Resources)**
Where we have sub-resources we will use ATOM links to specify the URI for the sub-resource.  For version 1.0 of the REST API where a sub-resource is a collection (i.e. a list resource) we will not list the children in the parent resource, but simply have a link to the List sub-resource.  In a future version we may provide parameters which support "expansion" of sub-resources so that more information can be retrieved in a single request.  Here is a simplified example of each;
##### **Version 1.0 Support - Lists just include links to the List sub-resource.**
In this version clients will need to make a subsequent request to the specific sub-resource to actually get the list of pages, we do not pull in any summary information about the pages into the document resource.
