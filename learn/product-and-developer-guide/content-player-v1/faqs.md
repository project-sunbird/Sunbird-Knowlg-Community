---
description: This page addresses frequently asked questions about Composite Search API.
---

# FAQs

### Samples of how to use filter operators in composite search API?

**Sample 1** - Find all node types that contain specific search term (content, words, assets)&#x20;

{ "request": { "query":"elephant", "limit":10 } }

**Sample 2** - Find only TextBook

{ "request": {"filters":{"primaryCategory":"Digital Textbook"}, "limit":10 } }

**Sample 3** - Find "Explanation Content" less than 1MB

{ "request": {"filters":{"primaryCategory":"Explanation Content", "size": {"<=" : "1000000"\}}, "limit":10 } }

**Sample 4** - Find resources whose 'name' starts with "A" (e.g. for alphabetic navigation)

{ "request": { "filters": { "primaryCategory":"Explanation Content", "name": { "startsWith": "A" } } } }

**Sample 5** - Find resources without 'appIcon'

{ "request": { "filters": { "primaryCategory":"Explanation Content" }, "not\_exists":\["appIcon"] } }

**Sample 6** - Find resources with 'appIcon'

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "exists":\["appIcon"] } }

**Sample 7** - Find resources and aggregate results by 'language' and 'subject'

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "facets":\["language","subject"] } }

**Sample 8** - Find resources and sort results by name ascending and size desc

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"} } }

**Sample 9** - Get first 10 results

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 0, "limit": 10 } }

**Sample 10** - Get 4th page of results. Results from 30 - 40 index.

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 30, "limit": 10 } }

**Sample 11** - Get the fields specified.

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "exists":\["appIcon"], "fields":\["name","description","identifier","mimeType","createdOn"] } }

**Sample 12** - Search for content with soft constraints

{ "request": { "filters": { "objectType": \["Content"], "primaryCategory": \["Explanation Content"], "gradeLevel" : \["Grade 1"], "ageGroup" : \["5-6"], "status": \["Live"] }, "mode" : \["soft"], "softConstraints": {"ageGroup" : 2, "gradeLevel" : 3 } } }

**Sample 13** - Find "Explanation Content" created between a time range

{ "request": { "filters": { "primaryCategory":"Explanation Content", "createdOn": {">=":"2020-07-28T01:27:16.559+0000", "<":"2021-10-28T01:27:16.559+0000"} }, "sort\_by":{"name":"asc"}, "offset": 0, "limit": 10 } }

**Sample 14** - Find published Textbooks to which a content is linked to

{ "request": { "filters": { "primaryCategory":"Digital Textbook", "leafNodes": {"contains": "do\_Id_\__content"} }, "sort\_by":{"name":"asc"} } }
