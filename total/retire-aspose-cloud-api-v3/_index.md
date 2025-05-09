---
title: "Aspose Cloud Legacy API Retirement: Migration Guide & Deadlines"
type: docs
description: Legacy Aspose Cloud APIs are retiring by 15 Nov. Learn which versions are affected and how to migrate to the latest API versions for uninterrupted service.
url: /retire-aspose-cloud-api-v3/
weight: 1
---
### **Important Notice: Migration Required as Legacy Aspose Cloud Versions Are Retiring**

As part of our continued efforts to improve the performance, security, and long-term maintainability of the Aspose Cloud platform, we are announcing the retirement of several older API versions.

This change is designed to streamline our services and focus development resources on the most modern and widely adopted API versions.

**Retirement Schedule**

Support for the following legacy API versions will be discontinued:

* #### **Support for API Versions 1.0, 1.1, and 2.0** of all Aspose Cloud products will be fully retired.

* **The following v3.0 modules**, which were used in legacy integrations, will also be discontinued:  
  * **Aspose.Words Cloud (v3.0)**  
  * **Aspose.PDF Cloud (v3.0)**  
  * **Aspose.HTML Cloud (v3.0)**  
  * **Aspose.Storage Cloud (v3.0)**  
* Additionally, the token generation endpoint **/oauth2/token** (used in **cURL requests and direct API calls**) will be retired. All integrations must switch to the newer **/connect/token** endpoint.

These versions will remain accessible for the next **6 months(until 15 November)**, after which all related services will be permanently shut down.

#### **🔄 Migration Required**

If you are still using one of the soon-to-be-retired versions, please migrate to the latest supported versions as soon as possible.

🆕 Explore the latest releases here: [https://releases.aspose.cloud](https://releases.aspose.cloud)

#### **‼️Recommended Actions**

#### To ensure uninterrupted access to Aspose Cloud services, we recommend the following:

* #### Identify and update all requests to retired API versions and paths.

* #### Migrate to the latest supported versions (e.g., v4.0 or higher where applicable).

* #### Replace all uses of /oauth2/token with /connect/token. (Done automatically when using the latest SDK versions).

#### **🤝 We’re Here to Help**

We are committed to supporting you through this transition. Our team can assist with migration planning and provide usage summaries on request. If you have questions, please reach out via our support forum: [https://forum.aspose.cloud](https://forum.aspose.cloud)
