---
title: "Getting Started"
type: docs
url: /getting-started/
weight: 10
---

## **Development Quickstart**
Before you call any Aspose REST API, you need to create **Aspose Cloud account** and obtain **App Key and App SID**. Instructions to perform these steps are given below:
#### **Step 1: Create Aspose Cloud account**
- Please visit <http://dashboard.aspose.cloud/> website. You will be redirected to Aspose Passport
- If you have GitHub or Google account, simply **Sign Up.** Otherwise, click on the [Create a new Account](https://id.containerize.com/signup) button and provide the required information

**Congratulations!** your account has been successfully created and you can access [Aspose Cloud Dashboard](http://dashboard.aspose.cloud/).



-----
#### **Step 2: Obtain App Key and App SID**
- Once Logged In, go to [My Apps](https://dashboard.aspose.cloud/#/apps) tab. A Default App has already been created for you, you can simply grab your App Key and App SID
- You may need to click on the Lock icon to unhide your App Key

Finally, you are ready to call Aspose REST APIs.



-----
#### **Aspose Cloud SDKs**
It is recommended that you use [Aspose Cloud SDKs](https://asposecloud.github.io/) to call Aspose REST APIs as SDKs take care of low-level details of making requests and handling responses and let you focus on writing code specific to your project. SDKs are provided for different programming languages and mobile platforms. Moreover, [the SDKs](https://asposecloud.github.io/) are free and open source.



-----
#### **API Reference**
<https://apireference.aspose.cloud/> contains API Reference of all Aspose Cloud products. In addition, the Swagger UI lets you call these APIs directly from the browser.



-----
#### **Make an API request**
As an example, let's call Aspose.Words REST API to convert a PDF document to Word. First, download [Cloud SDK](https://github.com/aspose-words-cloud/) of your required platform as explained below:

{{< tabs tabTotal="6" tabID="1" tabName1=".NET" tabName2="Java" tabName3="PHP" tabName4="Ruby" tabName5="Python" tabName6="Node.js" >}}

{{< tab tabNum="1" >}}

**Install via [**NuGet](https://www.nuget.org/packages/Aspose.Words-Cloud/)**

PM> Install-Package Aspose.Words-Cloud

The source code is available on [GitHub.](https://github.com/aspose-words-cloud/aspose-words-cloud-dotnet)

{{< /tab >}}

{{< tab tabNum="2" >}}

**For [**Maven](https://repository.aspose.cloud/webapp/#/artifacts/browse/tree/General/repo/com/aspose/aspose-cloud-words), add the following dependency to your POM:**

<repositories>
    <repository>
        <id>aspose-cloud</id>
        <name>artifact.aspose-cloud-releases</name>
        <url><http://artifact.aspose.cloud/repo></url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words-cloud</artifactId>
        <version>18.9.0</version>
    </dependency>
</dependencies>

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-java).

{{< /tab >}}

{{< tab tabNum="3" >}}

**The PHP library can be installed via [**Composer](https://packagist.org/packages/aspose/words-sdk-php):**

composer require aspose/words-sdk-php

Thesource code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-php).

{{< /tab >}}

{{< tab tabNum="4" >}}

**Available as a [**gem](https://rubygems.org/gems/aspose_words_cloud)**:

gem install aspose\_words\_cloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-ruby).

{{< /tab >}}

{{< tab tabNum="5" >}}

**Available through [**PyPi](https://pypi.org/project/asposewordscloud/)**:

pip install asposewordscloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-python).

{{< /tab >}}

{{< tab tabNum="6" >}}

**Install via [**npm](https://www.npmjs.com/package/asposewordscloud)**:

npm install asposewordscloud

The source code is available on [GitHub](https://github.com/aspose-words-cloud/aspose-words-cloud-node). 

{{< /tab >}}

{{< /tabs >}}

Now use following code to convert a PDF document to Word. Please set App Key and App SID variables to the values you obtained in Step 2.

**Input Document:** [awesome_table_in_pdf.pdf](attachments/557079/851970.pdf)

**Output Document**: [awesome_table_in_pdf.docx](attachments/557079/851969.docx)

{{< tabs tabTotal="3" tabID="2" tabName1="cURL" tabName2=".NET" tabName3="Python" >}}

{{< tab tabNum="1" >}}

```java

// First get Access Token
// Get App Key and App SID from https://dashboard.aspose.cloud/

curl -v "https://api.aspose.cloud/oauth2/token" \
-X POST \
-d 'grant\_type=client\_credentials&client\_id=0B17F60A-6D69-426B-9ABD-79F35A6E9F7B&client\_secret=53b8b19adffa41a3e87dbbd8858977ae' \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"



// cURL example to convert PDF Document to Word

curl -v "https://api.aspose.cloud/v1.1/words/awesome\_table\_in\_pdf.pdf/saveAs" \
-X POST \
-d '{"SaveFormat":"docx", "FileName": "awesome\_table\_in\_pdf.docx"}' \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer GyT9x5vXv6x-KtAcEvVNx2Wthay1eYe8IX9Limpa59i-WR212MoRPrM6SAK\_qDxKypsZQGb1absQvAv70WzPmcvyc7bWZleEz9xeO\_MT97r9e6DLkR3eOox\_cAmf3wlq3gg4zMN830vilo7DaQBBRGIh3pO6PvwGOrxNgA1N6zcgmrnPal9RhHdAdBuzoM\_CHuWT8FVPOBl1PUVUfVf3ULWiKUtGtGCodYpFYtary5ruFCRDwCvBtirIK7sbAC-LVVupenFLwD4-vlWDXPzb7ztI\_m3Pmy\_WE23ChkK\_-\_GLA5BREKamK3yDbiShXxxsYgqE2aHKSuHmwOk\_aGrGjWDG0eyC5dBp-X-fVI2Ud8tuwuI0wyKpA0wx6pYFsJ64viYYD\_j4jKFYbqqGlf3tk-JVrWl57e41CUdimoIzXDbOL0Po"

```

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< gist "aspose-cloud" "19215e2ac3d61ca0fd78d1ca2f1c1023" "ConvertPDFDocumentToWord.cs" >}}

{{< /tab >}}

{{< tab tabNum="3" >}}

{{< gist "aspose-cloud" "303ca1faad43f8d1b672fbeac98ad2e0" "convert\_pdf\_to\_word.py" >}}

{{< /tab >}}

{{< /tabs >}}



-----
#### **Questions?**
Aspose provides free technical support for all its products. The main avenue for support is the [Aspose Cloud Forum](https://forum.aspose.cloud/). Post your question in the forum and it will be answered within a few hours.



-----

