# Collection Editor - V2

As the Collection-Editor evolves to create the collection contents like(Textbook, Course, Collection etc..), we have noticed users facing some difficulty to prepare the skeleton of collection & collaborating with contributors to enrich the content.&#x20;

To overcome the above challenges the new collection-editor version-2 built with an upgraded tech stack.

Before going to the next section, You should know about [object category definition](https://project-sunbird.atlassian.net/wiki/spaces/SingleSource/pages/2696183813/How+to+configure+forms+in+primaryCategory#Overview) is the key part of the configuration to load the editor.&#x20;

### Tech Stack

* **Angular v9**
* **HTML, SCSS**
* **Typescript**

### How to setup

Please refer to the [README](https://github.com/Sunbird-Ed/sunbird-collection-editor/tree/release-4.8.0#readme).md of the below [git repository](collection-editor-v2.md#git-repo)

### Configuration

Please refer to the [config section of README.md ](https://github.com/vaibhavbhuva/sunbird-collection-editor-1/blob/release-4.8.0/docs/CONFIGURATION.md)file of the below [git repository](collection-editor-v2.md#git-repo)

### Git Repo

{% embed url="https://github.com/Sunbird-Ed/sunbird-collection-editor" %}

#### NPM Repository

{% embed url="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor" %}

### Dependencies

#### Internal Dependencies

#### [Content Service](../content-service/)&#x20;

Content service APIs are being used to read the content details using READ/GET API calls.&#x20;

#### External Dependencies

#### [Sunbird Telemetry](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkM7F4oILSpCJPO0YUu/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.

#### [Sunbird inQuiry](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/Wu4HIWGkb7dD4y0Kup4W/)

Sunbird inQuiry is used to play the questionnaire while playing the content. This is especially used to play Interactive-video content.
