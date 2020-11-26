---
title: "Configure FTP Storage"
type: docs
url: /getting-started/dashboard/how-to-configure-3rd-party-cloud-storages/configure-ftp-storage/
weight: 40
---

You have to complete the following steps to connect a FTP storage with our APIs:

* Create an FTP storage account.
* Log into [Dashboard](https://dashboard.groupdocs.cloud).
* Access the [Storages](https://dashboard.groupdocs.cloud/storages) Page.
* Select [FTP Storage](https://dashboard.groupdocs.cloud/storages/ftp/create) from the 'Create New Storage' menu.
* Enter **Storage Name** (any name of your choice), **FTP Server**, **User**, **Password**, **Confirm Password** and **Port** number and check if the connection **Require explicit SSL over TLS**.
* Save Storage.

Now you can use this storage with Aspose REST APIs. For instance:

https://api.aspose.cloud/v4.0/words/storage/file/testfile.txt?storage=MyFTPStorage
