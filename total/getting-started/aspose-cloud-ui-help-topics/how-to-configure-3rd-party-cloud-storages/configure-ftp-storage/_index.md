---
title: "Configure FTP Storage"
type: docs
url: /configure-ftp-storage/
weight: 40
---

{{% alert color="primary" %}} 

The page contains FTP Storage configuration.

{{% /alert %}} 

You have to complete the following steps to configure the Storage:

- Create an FTP storage account. Box.com account is used via FTP in this example.
- Log in at <https://dashboard.aspose.cloud/#/> and select **My Storage** tab.
- Select **FTP Storage** under **Create New Storage** drop-down menu.
- Enter **Storage Name** (any name of your choice), **FTP server address**, **user** name, **password** and **port** number and check if **Require explicit SSL over TLS**.
- Save Storage.

Now you can use this storage with Aspose REST APIs. For instance:

https://api.aspose.cloud/v1.1/storage/file/testfile.txt?storage=MyFTPStorage
