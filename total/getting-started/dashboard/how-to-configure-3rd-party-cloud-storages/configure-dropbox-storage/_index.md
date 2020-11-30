---
title: "Configure DropBox Storage"
type: docs
url: /getting-started/dashboard/how-to-configure-3rd-party-cloud-storages/configure-dropbox-storage/
weight: 30
---

You have to complete following steps to configure Dropbox Storage:

* Log into [Dashboard](https://dashboard.groupdocs.cloud).
* Access the [Storages](https://dashboard.groupdocs.cloud/storages) Page.
* Select [DropBox Storage](https://dashboard.groupdocs.cloud/storages/dropbox/create) from the 'Create New Storage' menu.
* Enter **Storage Name** and click on **Generate Token** button.
* Log into Dropbox and Authorize our app.
* Dropbox will generate your Access Token and you will be redirected to our Dashboard.
* Press **Save** button to create storage.

Now you can use this storage with Aspose REST APIs. For instance:

https://api.aspose.cloud/v4.0/words/storage/file/testfile.txt?storage=MyDropboxStorage