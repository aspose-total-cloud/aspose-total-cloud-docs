---
title: "Configure DropBox Storage"
type: docs
url: /configure-dropbox-storage/
weight: 30
---

{{% alert color="primary" %}} 

The page contains DropBox Storage configuration.

{{% /alert %}} 

You have to complete following steps to configure Dropbox Storage:

- Go to <https://dashboard.aspose.cloud/>
- Select **My Storage** tab.
- Click on **Create New Storage** dropdown menu and select **Dropbox Storage**. 
- Enter **Storage Name** and click on **Generate Access Tokens** button.
- Log into Dropbox and authorizes our app.
- Dropbox will generate your Access Token and you will be redirected to our Dashboard.
- Press **Save** button to create storage.

Now you can use this storage with Aspose REST APIs. For instance:

https://api.aspose.cloud/v1.1/storage/file/testfile.txt?storage=MyDropboxStorage
