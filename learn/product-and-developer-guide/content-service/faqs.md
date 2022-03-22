---
description: This page addresses frequently asked questions about Content Service.
---

# FAQs

### What is the life-cycle of a content/collection object?

Content/Collection when created will have '**Draft**' status. When the Content/Collection is submitted for Review, content status will be updated to '**Review**'. When a Content/Collection is accepted (submitted for publishing), status will first move to 'Processing' and then to '**Live**' if it is processed successfully else to '**Failed**'. When a published content is edited, a **image** node gets created with the id ending with '**.img**' (do\_Id.img). Status of the image node will be 'Draft' whereas status of non-image node will be 'Live'. Image node will follow the above life cycle.&#x20;

When a content/collection in 'Review' status is rejected in Review, status of the content/collection will be updated back to 'Draft'.

When a content/collection is submitted for delete/retire, status of the content/collection will be updated to '**Retired**'.&#x20;

### What happens when a content/collection object is Retired?

When a content/collection retire API is triggered, status of the content/collection will be updated to '**Retired**'. Please note that when a content/collection with both actual node and image node existing is retired, **image node is hard deleted** from the system and actual node's status is updated to '**Retired**'.

### Can I delete only the image node of a content/collection object?

Yes, Discard Content API and Discard Collection API can be used to delete the image node of a content/collection object. Please note that the image node will be **hard deleted** from the system.

### What happens when Discard API is used on a content/collection object with only actual node?

Actual node will be **hard deleted** from the system.

### Can I add/remove contents to/from collections without needing to update collection hierarchy using Update Hierarchy API?

Yes, using [Add Hierarchy API](http://docs.sunbird.org/latest/apis/collectionapi/index.html#operation/Add%20Collection%20Hierarchy) and Remove Hierarchy API, one can add or remove contents/collections to/from a collection unit.

### How is Search Content API different from Composite Search API?

[Search Content API](http://docs.sunbird.org/latest/apis/contentapi/index.html#operation/Search%20Content) can be used for fetching object Types 'Content', 'ContentImage', 'Collection', 'CollectionImage', 'QuestionSet' and 'Asset' only. Whereas, [Composite search API](http://docs.sunbird.org/latest/apis/searchapi/#tag/Search-APIs) can be used for fetching all types of objects in the application ('Content', 'ContentImage', 'Collection', 'CollectionImage', 'QuestionSet', 'QuestionSetImage', 'Asset', 'Channel', 'Framework', 'ObjectCategory', 'ObjectCategoryDefintion', 'License', 'Question', etc. )

### How are the content/collection objects stored in database?

Content/Collection object metadata is stored in the Neo4j database. Uploaded Source for a content and appIcon images are stored in Cloud. Collection Hierarchy is stored in json format in Cassandra database. Metadata is synced to Elastic Search and Redis.

### How to read actual node metadata and image node metadata?

Actual node metadata can be read using 'Read Content API' URL in the format '/content/v2/read/do\_id'.&#x20;

Image node metadata can be read using 'Read Content API' URL in the format '/content/v2/read/do\_id**?mode=edit**' or '/content/v2/read/do\_id**.img**'.&#x20;

### How to read ECML content 'body'?

ECML content 'body' can be fetched using 'Read Content API' URL in the format '/content/v2/read/do\_id**?fields=body**'. &#x20;

### What happens in Content/Collection 'Publish'?&#x20;

When a Content/Collection object Publish API is invoked, after metadata validation, content-publish flink job is invoked using respective kafka topic. In the flink job, post the pkgVersion validation, a content is first updated to 'Processing' status. Later, packaging of the content starts (ECAR generation) with types ONLINE, SPINE and FULL (this type is skipped for collection). Once ECAR is generated and uploaded to cloud, status is updated to 'Live'.  &#x20;

### How to upload a content?

{% embed url="http://docs.sunbird.org/latest/developer-docs/how-to-guide/how_to_upload_existing_content" %}

### What file formats can be uploaded as content?

Currently, the platform supports the following formats for compiled content:

* Text (.pdf)
* Video (.mp4, .webm, YouTube URLs)
* HTML (as .zip)
* ECML (created using the inbuilt content editor)
* EPUB
* H5P

### How the HTML zip content needs to be packaged for upload?

* 'index.html' in the .zip is a must.
* There can be only one level of folders directly inside zip. sub folders (Folders within folders) are not allowed/may not work well.
* File names and Folder names should not contain special characters. It can only be alphanumeric.

### Which attribute of a content contains the uploaded source file path?

When a file is uploaded as a content, source file is copied to the configured cloudstorage blob path and the blob path url is saved in '**artifactUrl**' attribute. When a video content is published, as a post publish process, streaming source is generated and the path is saved in '**streamingUrl**' attribute.

### How to use operators in content search API or composite search API?

Any of the attributes of content model can be used in the filters. By default, content search API returns objects having 'status' as "Live" and "visibility" as "default". Default 'limit' is 100.&#x20;

#### **Operators:**&#x20;

Filters are by default searched based on equals match, that is case insensitive but the request can specify other operators to search against the fields. These are as follows:&#x20;

**String fields:**&#x20;

* Default - String match, contains case insensitive
* startsWith - String match, starts with
* endsWith - String match, ends with
* contains - contains match
* value - contains match
* Array - Exact match with any of the given values

**Number fields:**&#x20;

* Default - Equals
* \>= - Greater than or equals
* \> - Greater than
* <= - Less than or equals
* < - Less than
* Array - Exact match with any of the given values

#### Examples

**Sample 1** - Find all node types that contain specific search term (content, words, assets)&#x20;

{ "request": { "query":"elephant", "limit":10 } }

**Sample 2** - Find only TextBook

{ "request": {"filters":{"contentType":"Textbook"}, "limit":10 } }

**Sample 3** - Find resources less than 1MB

{ "request": {"filters":{"contentType":"Resource", "size": {"<=" : "1000000"\}}, "limit":10 } }

**Sample 4** - Find resources whose 'name' starts with "A" (e.g. for alphabetic navigation)

{ "request": { "filters": { "contentType":"Resource", "name": { "startsWith": "A" } } } }

**Sample 5** - Find resources without 'appIcon'

{ "request": { "filters": { "contentType":"Resource" }, "not\_exists":\["appIcon"] } }

**Sample 6** - Find resources with 'appIcon'

{ "request": { "filters": { "contentType":"Resource"}, "exists":\["appIcon"] } }

**Sample 7** - Find resources and aggregate results by 'language' and 'subject'

{ "request": { "filters": { "contentType":"Resource"}, "facets":\["language","subject"] } }

**Sample 8** - Find resources and sort results by name ascending and size desc

{ "request": { "filters": { "contentType":"Resource"}, "sort\_by":{"name":"asc", "size":"desc"} } }

**Sample 9** - Get first 10 results

{ "request": { "filters": { "contentType":"Resource"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 0, "limit": 10 } }

**Sample 10** - Get 4th page of results. Results from 30 - 40 index.

{ "request": { "filters": { "contentType":"Resource"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 30, "limit": 10 } }

**Sample 11** - Get the fields specified.

{ "request": { "filters": { "contentType":"Resource"}, "exists":\["appIcon"], "fields":\["name","description","identifier","mimeType","createdOn"] } }

**Sample 12** - Search for content with soft constraints

{ "request": { "filters": { "objectType": \["Content"], "contentType": \["Story"], "gradeLevel" : \["Grade 1"], "ageGroup" : \["5-6"], "status": \["Live"] }, "mode" : \["soft"], "softConstraints": {"ageGroup" : 2, "gradeLevel" : 3 } } }

**Sample 13** - Find resources created between a time range

{ "request": { "filters": { "contentType":"Resource", "createdOn": {">=":"2020-07-28T01:27:16.559+0000", "<":"2021-10-28T01:27:16.559+0000"} }, "sort\_by":{"name":"asc"}, "offset": 0, "limit": 10 } }

**Sample 14** - Find published Textbooks to which a content is linked to

{ "request": { "filters": { "contentType":"TextBook", "leafNodes": {"contains": "do\_Id_\__content"} }, "sort\_by":{"name":"asc"} } }
