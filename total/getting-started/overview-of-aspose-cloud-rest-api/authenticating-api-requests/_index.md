---
title: "Authenticating API Requests"
type: docs
url: /authenticating-api-requests/
weight: 10
---

**Table of Contents**

- [OAuth 2.0](#OAuth2.0) 
  - [Applications](#Applications)
  - [Get Access/Refresh Token](#GetAccess/RefreshToken) 
    - [cURL Example](#cURLExample)
  - [Obtain new Access/Refresh Token using the Refresh Token](#ObtainnewAccess/RefreshTokenusingtheRefreshToken) 
    - [cURL Example](#cURLExample.1)
  - [Call REST API](#CallRESTAPI) 
    - [cURL Example](#cURLExample.2)
  - [Tokens Lifetime](#TokensLifetime)
- [URL Signing](#URLSigning) 
  - [How to authenticate (URL Signing)](#Howtoauthenticate\(URLSigning\))

There are two ways to authenticate Aspose for Cloud REST APIs.

1. OAuth 2.0
1. URL Signing

Though we are still supporting URL Signing, we recommend our users to switch to OAuth 2.0 as it is an industry standard and more convenient to use.
### **OAuth 2.0**
The Aspose for Cloud REST API supports the OAuth 2.0 protocol using the **client\_credentials** workflow to authorize calls.

[OAuth 2.0](https://en.wikipedia.org/wiki/OAuth#OAuth_2.0) is an authorization framework that enables applications to obtain access to user accounts data through our REST API. OAuth provides authorization flows for web and desktop applications, and mobile devices.

The basic concept and how it works is described in the next image:
#### **Applications**
To access the REST API using OAuth2.0 protocol, you need to [create an application](/create-new-app-and-get-app-key-and-sid/). To register new applications, login into the [Dashboard Developer](https://dashboard.aspose.cloud/#/) site using your Aspose Account, and go to the [My Apps](https://dashboard.aspose.cloud/#/apps) view. Once you create a new application, we will issue a **client\_id** (App SID**)** and **client\_secret** (App Key) that you can use to authenticate your REST API calls using the OAuth2.0 protocol. (You can generate new secrets for your Apps, but make sure you update it when issuing new access tokens using those credentials.)
#### **Get Access/Refresh Token**
After you have created a new application you can obtain an access token by sending a **POST** request to **/oauth2/token** endpoint. Still, you must authenticate your access token request using Client Credentials authorization grant type flow:

  POST request to: https://api.aspose.cloud/oauth2/token
  Headers:
    Accept: application/json
    Content-Type: application/x-www-form-urlencoded
    Body:
      grant\_type: client\_credentials
      client\_id: APP\_SID
      client\_secret: APP\_KEY

The endpoint acts as an authorization server and it verifies your credentials, if they are correct it returns a JSON ticket containing several items, through each, you can find the access\_token, refresh\_token, expire time of both tokens etc. The provided access\_token is a Bearer Token that you can further use in the Authorization header of your request.

For each Application you create in the dashboard, you can only have one refresh\_token in use for it. Any new request for refresh\_token will override and revoke the previous one.
##### **cURL Example**
{{< tabs tabTotal="2" tabID="2" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -v "https://api.aspose.cloud/oauth2/token" \
-X POST \
-d 'grant\_type=client\_credentials&client\_id=91a2fd07-bba1-4b32-9112-abfb1fe8aebd&client\_secret=0fbf678c5ecabdb5caca48452a736dd0' \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{

  "access\_token": "VvrtTA8PodA3XbdHsmLvXX0T5k0ge-Nk67NjQx7-3W2YGU\_JbPYD7E9bqlNdnYcw7zdoEfrKZKKfYRn\_4ADWFngoOQPNp1S5udD1ZCqlIQeJ\_WUoUOiSmBfnlgaAkwjMQhKKdL5vzTVu1BLsdiTGrKZw54JdfylTABl4OcQWUtmferlhmZjSzyuFT8ppiuOTxYbiYhVq-KAvNrT1xbYP4JED98nH7CQykbHmznavYedR2PjJ79N2k4riFV9e-F4MmanBOdufqSfs6fFMLlqsmCLQCGbVpHOvQLQcdaaAqmAEWEnp9jiorQIc-phoLnBQgtTQT1vumvP3ecdpxnbBdLP2rru7kv\_mGm28uoPv18YKeEiM62Pda04cvjozOyb8G9a6j9R8pqglluuGypaZG\_-jdFygR28yIXBpQK18SGRmxE-N",

  "token\_type": "bearer",

  "expires\_in": 86399,

  "refresh\_token": "ae1d4e78f9af45539d6daa44ddbba579",

  "client\_id": "91a2fd07-bba1-4b32-9112-abfb1fe8aebd",

  "clientRefreshTokenLifeTimeInMinutes": "525600",

  ".issued": "Sun, 15 Oct 2017 14:58:12 GMT",

  ".expires": "Mon, 16 Oct 2017 14:58:12 GMT"

}

```

{{< /tab >}}

{{< /tabs >}}
#### **Obtain new Access/Refresh Token using the Refresh Token**
The access token is only valid for a small period of time, to continue to work with the REST API you can issue new access token by only using the refresh token provided at the above POST request. To obtain a new access token using the refresh token you can make a POST request to the same /oauth2/token endpoint but using different grant type this time:

  POST request to: https://api.aspose.cloud/oauth2/token
  Headers:
    Accept: application/json
    Content-Type: application/x-www-form-urlencoded
    Body:
      grant\_type: refresh\_token
      refresh\_token: the-refresh-token-perviously-generated

The returned ticket will be the same as the above, but a new refresh\_token is issued now and the old one is revoked, so make sure you replace it in your application with the new one from the ticket you just received.
##### **cURL Example**
{{< tabs tabTotal="2" tabID="5" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -v "https://api.aspose.cloud/oauth2/token" \
-X POST \
-d 'grant\_type=refresh\_token&refresh\_token=ae1d4e78f9af45539d6daa44ddbba579' \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{

  "access\_token": "nkNK16oOZl3aUsa0UdHvkmgMiO-tuTw9HWRGMFlKAVZA6p4QVXCevKwjKThO5B6XERMAGPhAZAx-qrPj1JCArmYcXKnE-HtaKPGzciwovAzfatguLfOosvmi9ZXMXro9SL9wy5usnclEs1ronLncys1rHIqtEHNzYVUvitWvW71TZ0xtez7yE3fWDwAFUHa3SLfvkP45DwVcPkPDquS6X\_tKi252W-gn3JZ\_11nvos5Du0wt9EZ1\_c0SgnhaNBJOI04mE1E0EscQf-lwSdhQCWKXpsEiUccmOJhLrxh6t0qyENrhFRfgMmzv8\_w4LWx5qWnM44PlwkBj0kvJejrLe1GeYSaLouu3gQsfPo2M\_z8FCwjNWWm6v20uKh9Jqizf0IQFNBdrPFaykjsj66oea2YKEjGY8n4T46FC9UP73rvLIseW48c99EUKTLphjKR\_Ab\_Tcw",

  "token\_type": "bearer",

  "expires\_in": 86399,

  "refresh\_token": "48b76a316aa34431bb6b973c91cbd1fa",

  "client\_id": "91a2fd07-bba1-4b32-9112-abfb1fe8aebd",

  "clientRefreshTokenLifeTimeInMinutes": "525600",

  ".issued": "Sun, 15 Oct 2017 15:21:33 GMT",

  ".expires": "Mon, 16 Oct 2017 15:21:33 GMT"

}

```

{{< /tab >}}

{{< /tabs >}}
#### **Call REST API**
Now that you have the Bearer Token (access\_token) generated using the application credentials, you can make API calls and authorize by adding the access token in the ‘Authorization’ header, as it’s defined in the OAuth 2.0 protocol.

  Headers:
    Authorization: Bearer ACCESS\_TOKEN

*You authorize with one application, but you can access files from all storages in your account, or all Application’s default storage by specifying query parameters (storage or AppSid).*
##### **cURL Example**
{{< tabs tabTotal="2" tabID="8" tabName1="Request" tabName2="Response" >}}

{{< tab tabNum="1" >}}

```java

curl -v "https://api.aspose.cloud/v1.1/cells/myWorkbook.xlsx/documentproperties" \
-X GET \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer VvrtTA8PodA3XbdHsmLvXX0T5k0ge-Nk67NjQx7-3W2YGU\_JbPYD7E9bqlNdnYcw7zdoEfrKZKKfYRn\_4ADWFngoOQPNp1S5udD1ZCqlIQeJ\_WUoUOiSmBfnlgaAkwjMQhKKdL5vzTVu1BLsdiTGrKZw54JdfylTABl4OcQWUtmferlhmZjSzyuFT8ppiuOTxYbiYhVq-KAvNrT1xbYP4JED98nH7CQykbHmznavYedR2PjJ79N2k4riFV9e-F4MmanBOdufqSfs6fFMLlqsmCLQCGbVpHOvQLQcdaaAqmAEWEnp9jiorQIc-phoLnBQgtTQT1vumvP3ecdpxnbBdLP2rru7kv\_mGm28uoPv18YKeEiM62Pda04cvjozOyb8G9a6j9R8pqglluuGypaZG\_-jdFygR28yIXBpQK18SGRmxE-N"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

{

  "DocumentProperties": {

    "DocumentPropertyList": [

      {

        "Name": "Title",

        "Value": "worksheet functions.xlsx",

        "BuiltIn": "True",

        "link": {

          "Href": "/Title",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Subject",

        "Value": "Excel 2007 Bible",

        "BuiltIn": "True",

        "link": {

          "Href": "/Subject",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Author",

        "Value": "John Walkenbach",

        "BuiltIn": "True",

        "link": {

          "Href": "/Author",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Keywords",

        "Value": "©2007, JWalk & Associates, Inc.",

        "BuiltIn": "True",

        "link": {

          "Href": "/Keywords",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Comments",

        "Value": "Example file distributed with 'Excel 2007 Bile'",

        "BuiltIn": "True",

        "link": {

          "Href": "/Comments",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "LastSavedBy",

        "Value": "John Walkenbach",

        "BuiltIn": "True",

        "link": {

          "Href": "/LastSavedBy",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "CreateTime",

        "Value": "8/4/2006 4:30:22 PM",

        "BuiltIn": "True",

        "link": {

          "Href": "/CreateTime",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "LastSavedTime",

        "Value": "11/13/2006 3:55:46 PM",

        "BuiltIn": "True",

        "link": {

          "Href": "/LastSavedTime",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Category",

        "Value": "http://www.j-walk.com/ss",

        "BuiltIn": "True",

        "link": {

          "Href": "/Category",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "NameOfApplication",

        "Value": "Microsoft Excel",

        "BuiltIn": "True",

        "link": {

          "Href": "/NameOfApplication",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Security",

        "Value": "0",

        "BuiltIn": "True",

        "link": {

          "Href": "/Security",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "ScaleCrop",

        "Value": "False",

        "BuiltIn": "True",

        "link": {

          "Href": "/ScaleCrop",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Company",

        "Value": "JWalk & Associates",

        "BuiltIn": "True",

        "link": {

          "Href": "/Company",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "LinksUpToDate",

        "Value": "False",

        "BuiltIn": "True",

        "link": {

          "Href": "/LinksUpToDate",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      },

      {

        "Name": "Version",

        "Value": "12.0000",

        "BuiltIn": "True",

        "link": {

          "Href": "/Version",

          "Rel": "self",

          "Title": null,

          "Type": null

        }

      }

    ],

    "link": {

      "Href": "http://api.aspose.com/v1.1/cells/myWorkbook.xlsx/documentproperties",

      "Rel": "self",

      "Title": null,

      "Type": null

    }

  },

  "Code": 200,

  "Status": "OK"

}

```

{{< /tab >}}

{{< /tabs >}}

#### **Tokens Lifetime**
The time of the tokens is finite. By default, the **access\_token** lifetime is **1 day**, and the **refresh\_token** lifetime is **1 year**. Before you create a new access\_token, use it and renew it only before it expires. To detect when an access token expires, you must write specific code that will check for any of these:

- **expires\_in** value in the ticket generated by OAuth2 endpoint.
- will handle the **401 Unauthorized** error responses from the API endpoint and issue a request for a new token.
### **URL Signing**
Each Aspose for Cloud API request must include the following query string parameters:

|**appSID**|The public key provided to a client that allows the Aspose API to know which client is making the API request|
| :- | :- |
|**signature**|A HMAC-SHA1 signature of the request that is generated by the client using their private key|
#### **How to authenticate (URL Signing)**
Aspose for Cloud uses URL signing for authorization of requests. All requests sent to the Aspose for Cloud Web Service must be signed using user's private key which they retrieve via the Web UI when they sign up. Using the Private key ensures that only authorized application can create valid REST requests to our Web API.

Please take following steps to generate a valid signature (as an example we are using appSID=c821f123-1a8b-4b97-925a-9d69a6b2fcd8 and key=23e9d89a967a5f18142221fa8f7cbcd0):

1. Build the URL which requires to be signed including all parameters. 
   ` `<https://api.aspose.com/1.1/storage/folder/test_folder>
1. Remove trailing '/' character if any.
1. Append App SID to the given URL as query parameter 
   <https://api.aspose.com/1.1/storage/folder/test_folder?appSID=c821f123-1a8b-4b97-925a-9d69a6b2fcd8>
1. Use HMAC-SHA1 algorithm to compute the hash of the URL. App Key will be used as a secret cryptographic key.
1. Use Base64 encoding to convert message authentication code (MAC) from a binary format in an ASCII string format. JgLReiOyORY8BYpCJ32CbCc0UHg=
1. Remove any trailing '=' characters: JgLReiOyORY8BYpCJ32CbCc0UHg
1. URL-encode generated string: JgLReiOyORY8BYpCJ32CbCc0UHg. This step encodes the string to be used in a query part of a URL.
1. Finally, append the encoded value to the URL as a signature parameter.<https://api.aspose.com/1.1/storage/folder/test_folder?appSID=c821f123-1a8b-4b97-925a-9d69a6b2fcd8&signature=JgLReiOyORY8BYpCJ32CbCc0UHg>

{{% alert color="primary" %}} 

We didn't use registered application ID and application key here, so the resulting URL does not pass authorization but all calculationwerecompleted using the real algorithm, so you can use the results for internal testing.

{{% /alert %}} 

See below implementation of the URL signing algorithm in different languages.

**URL Signing**

{{< tabs tabTotal="9" tabID="11" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Ruby" tabName5="Python" tabName6="Node.js" tabName7="Android" tabName8="Objective C" tabName9="Perl" >}}

{{< tab tabNum="1" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.cs" >}}

{{< /tab >}}

{{< tab tabNum="2" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.java" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.php" >}}

{{< /tab >}}

{{< tab tabNum="4" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "utils.rb" >}}

{{< /tab >}}

{{< tab tabNum="5" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.py" >}}

{{< /tab >}}

{{< tab tabNum="6" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "utils.js" >}}

{{< /tab >}}

{{< tab tabNum="7" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.java" >}}

{{< /tab >}}

{{< tab tabNum="8" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "ASPOSEUtils.m" >}}

{{< /tab >}}

{{< tab tabNum="9" >}}



{{< gist "" "4ae4287d8c09cc6f038c72df8c7f59ea" "Utils.pm" >}}

{{< /tab >}}

{{< /tabs >}}
