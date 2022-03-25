# Assets search service

The Assets **search microservice** provides ability to search and discover assets on the platform. [Composite search API](http://docs.sunbird.org/latest/apis/searchapi/#tag/Search-APIs) can be used for fetching all types of objects in the application ('Content', 'ContentImage', 'Collection', 'CollectionImage', 'QuestionSet', 'QuestionSetImage', 'Asset', 'Channel', 'Framework', 'ObjectCategory', 'ObjectCategoryDefintion', 'License', 'Question', etc. )

Any of the attributes of [object model](https://github.com/project-sunbird/knowledge-platform/tree/master/schemas) can be used in the filters. By default, composite search API returns objects having 'status' as "Live" and "visibility" as "default". Default 'limit' is 100.&#x20;

#### **Filter Operators:**&#x20;

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
