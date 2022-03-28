# Collection Editor - V2

## :stars:How to setup

Please refer to the [README](https://github.com/Sunbird-Ed/sunbird-collection-editor/tree/release-4.8.0#readme).md of the git repository

## :stars:Configuration

Before going to the next section, you should know about [object category definition](https://project-sunbird.atlassian.net/wiki/spaces/SingleSource/pages/2696183813/How+to+configure+forms+in+primaryCategory#Overview) is the key part of the configuration to load the editor. \
\
Following are the configuration for different types of collections.

1. ****[**Digital Textbook**](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.8.0/docs/Digital%20Textbook.json)****
2. ****[**Course**](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/0b25c7d27aa559a20a58d3d204086b1f6e28141c/docs/Course.json)****

For more information, please refer to the [config section of the README.md ](https://github.com/vaibhavbhuva/sunbird-collection-editor-1/blob/release-4.8.0/docs/CONFIGURATION.md)file of the [git repository](collection-editor-v2.md#git-repo)

{% embed url="https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/d033e4d7495e63e2e0f05641491a51184dcc17fa/docs/CONFIGURATION.md" %}

## :stars:Dependencies

### Internal Dependencies

#### [Content Service](../../../learn/product-and-developer-guide/content-service/)&#x20;

Content service APIs are being used to read the content details using READ/GET API calls.&#x20;

#### <mark style="color:blue;"></mark>[<mark style="color:blue;">Content Players</mark>](../players.md)

The content players are used to playing the different types of content such as PDF, VIDEO, EPUB, etc...

### External Dependencies

#### [Sunbird Telemetry](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkM7F4oILSpCJPO0YUu/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.
