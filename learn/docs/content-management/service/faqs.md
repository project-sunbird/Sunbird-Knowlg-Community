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

