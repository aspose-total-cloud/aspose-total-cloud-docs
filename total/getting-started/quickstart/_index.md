---
title: "Quickstart"
second_title: "Aspose Total Cloud Docs"
type: docs
url: /getting-started/quickstart/
aliases: [/quickstart/]
description: "Learn how to get started quickly with Aspose Cloud API and SDKs."
weight: 2
---
Before you call any Aspose REST API, you need to create **Aspose Cloud Account** and obtain **Client Id and Client Secret**.  
Instructions to perform these steps are given below:

## Create Aspose Cloud account ##

- Please visit <http://dashboard.aspose.cloud> website. You will be redirected to Aspose Single Sign On authentication service.
- If you have GitHub or Google account, simply **Sign Up.** Otherwise, click on the [Create a new Account](https://id.containerize.com/signup) button and provide the required information.

**Congratulations!** your account has been successfully created and you can access [Aspose Cloud Dashboard](http://dashboard.aspose.cloud).

## Obtain Client Id and Client Secret ##
- Once Logged In, go to [Applications View](https://dashboard.aspose.cloud/applications).
- Create a new applications and make sure you specify a default storage for it (if you have no storage, first create one of your choice).
- After creating, your new app will have an auto-generated set of keys called `Client Id` and `Client Secret`.
- Edit the Application to see them, you may need to click on the Lock icon to unhide your `Client Secret`.

Finally, you are ready to call Aspose REST APIs.

## Aspose Cloud SDKs ##
It is recommended that you use [Aspose Cloud SDKs](https://asposecloud.github.io/) to call Aspose REST APIs as SDKs take care of low-level details of authenticating, making requests and handling responses and let you focus on writing code specific to your project. SDKs are provided for different programming languages and mobile platforms. Moreover, [the SDKs](https://asposecloud.github.io/) are free and open source.

## API Reference ##
Call Aspose Cloud APIs directly from your browser by accessing the desired product UIs at <https://apireference.aspose.cloud/>.

## Make an API request ##
As an example, let's call Aspose.Words REST API to convert a PDF document to Word.

First, download [Cloud SDK](https://github.com/aspose-words-cloud/) of your required platform as explained below:

{{< tabs tabTotal="6" tabID="1" tabName1=".NET" tabName2="Java" tabName3="PHP" tabName4="Ruby" tabName5="Python" tabName6="Node.js" >}}

{{< tab tabNum="1" >}}

**Install via [NuGet](https://www.nuget.org/packages/Aspose.Words-Cloud/)**

PM> Install-Package Aspose.Words-Cloud

The source code is available on [GitHub.](https://github.com/aspose-words-cloud/aspose-words-cloud-dotnet)

{{< /tab >}}

{{< tab tabNum="2" >}}

**For [Maven](https://repository.aspose.cloud/webapp/#/artifacts/browse/tree/General/repo/com/aspose/aspose-cloud-words), add the following dependency to your POM:**

```xml
<repositories>
    <repository>
        <id>aspose-cloud</id>
        <name>artifact.aspose-cloud-releases</name>
        <url>http://artifact.aspose.cloud/repo</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words-cloud</artifactId>
        <version>YY.MM.XX</version>
    </dependency>
</dependencies>
```

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-java).

{{< /tab >}}

{{< tab tabNum="3" >}}

**The PHP library can be installed via [Composer](https://packagist.org/packages/aspose/words-sdk-php):**

composer require aspose/words-sdk-php

Thesource code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-php).

{{< /tab >}}

{{< tab tabNum="4" >}}

**Available as a [gem](https://rubygems.org/gems/aspose_words_cloud)**:

gem install aspose_words_cloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-ruby).

{{< /tab >}}

{{< tab tabNum="5" >}}

**Available through [PyPi](https://pypi.org/project/asposewordscloud/)**:

pip install asposewordscloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-python).

{{< /tab >}}

{{< tab tabNum="6" >}}

**Install via [npm](https://www.npmjs.com/package/asposewordscloud)**:

npm install asposewordscloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-node). 

{{< /tab >}}

{{< /tabs >}}  


Now use following code to convert a PDF document to Word. Please set `Client Id` and `Client Secret` variables to the values you obtained in Step 2.

**Input Document:** [awesome_table_in_pdf.pdf](attachments/557079/851970.pdf)

**Output Document**: [awesome_table_in_pdf.docx](attachments/557079/851969.docx)

{{< tabs tabTotal="3" tabID="2" tabName1="cURL" tabName2=".NET" tabName3="Python" >}}

{{< tab tabNum="1" >}}

```java

// First get the Access Token
// Get Client Id and Client Secret from https://dashboard.aspose.cloud/

curl -v "https://api.aspose.cloud/oauth2/token" \
-X POST \
-d 'grant_type=client_credentials&client_id=CLIENT_ID&client_secret=CLIENT_SECRET' \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

// cURL example to convert PDF Document to Word

curl -v "https://api.aspose.cloud/v4.0/words/awesome_table_in_pdf.pdf/saveAs" \
-X POST \
-d '{"SaveFormat":"docx", "FileName": "awesome_table_in_pdf.docx"}' \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer ACCESS_TOKEN"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "19215e2ac3d61ca0fd78d1ca2f1c1023" "ConvertPDFDocumentToWord.cs" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "303ca1faad43f8d1b672fbeac98ad2e0" "convert_pdf_to_word.py" >}}

{{< /tab >}}

{{< /tabs >}}

## **Questions?** ##
Aspose provides free technical support for all its products. The main avenue for support is the [Aspose Cloud Forum](https://forum.aspose.cloud/). Post your question in the forum and it will be answered within a few hours.
