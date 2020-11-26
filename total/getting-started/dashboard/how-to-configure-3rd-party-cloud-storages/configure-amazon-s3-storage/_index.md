---
title: "Configure Amazon S3 Storage"
type: docs
url: /getting-started/dashboard/how-to-configure-3rd-party-cloud-storages/configure-amazon-s3-storage/
weight: 10
---

To use Amazon S3 storage, you have to create your own account and create a new bucket at <https://aws.amazon.com/>.
Please follow [Sign Up for Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/gsg/SigningUpforS3.html) for more details.

You also have to configure Amazon S3 Storage using your Aspose account at <https://dashboard.aspose.cloud/>. Please follow these steps:

* Log in to [https://dashboard.aspose.cloud](https://dashboard.aspose.cloud/).
* Access the [Storages](https://dashboard.aspose.cloud/storages) Page.
* Select [Amazon S3 Storage](https://dashboard.aspose.cloud/storages/amazons3/create) from the 'Create New Storage' menu.
* Enter 'Storage Name'
* Enter 'Bucket' Name
* Enter 'AWS Access Key'
* Enter 'AWS Secret Key'
* Press 'Save' button to configure new storage

The new storage would appear under **Storages** view. Now you can use this storage with Aspose REST APIs. For instance:

https://api.aspose.cloud/v4.0/words/storage/file/testfile.txt?storage=MyAmazonS3Storage

Please note when you configure external Amazon S3 storage, The Aspose Cloud APIs need the following APIs access on the bucket:

**Required APIs access:** 

- GetObjectMetadada API
- ListObjects API 

**Optional APIs:**

- CopyObject API
- PutObject API
- GetPreSignedURL API
- PutBucket API
- PutBucketVersioning API
- DeleteObject API
- ListVersions API
- GetObject API
- DeleteBucket API

