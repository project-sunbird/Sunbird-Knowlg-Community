# Rich and Diverse Assets

### Assets

This is the master definition for types of items that are supported on Sunbird.\
Example from education - _**Question set**_ is an asset\
Analogous example from the real-world - A _**foot wear**_ is an asset

An asset is the core system entity through which any type of asset is managed. Services such as creation, modification, publishing, discovery, consumption - are built around the core assets.

Knowlg provides a generalized and externalized asset model as shown in the below diagram.

![Generalized and Externalized Asset Model](<../../.gitbook/assets/Screen Shot 2022-03-24 at 11.38.56 AM.png>)

### &#x20;**Key Capabilities of Sunbird Assets:**

* Enables you to define your own domain specific assets and their properties using configurable and extensible attributes.

![](<../../.gitbook/assets/Screen Shot 2022-03-24 at 11.48.17 AM.png>)

* Enables creation of categories to cater to domain specific solutions through configuration without any code changes.&#x20;

Unlike an **Asset**, which is a core entity of the system, a category is just a “label” tagged to an object and can defined a specific set of properties and behaviors - which are a subset of those supported by the asset.

Hence, categories are completely driven by configuration, without any category specific logic implemented in the code.

Example from education - _**Exam Question paper, Practice Worksheet, Quiz**_ each one is a category of the asset type **Question set.**\
Analogous example from the real-world - A _**Shoe, Sandal, Flip-flops**_ each one is a category of the asset type **foot wear.**

![](<../../.gitbook/assets/Screen Shot 2022-03-24 at 12.16.00 PM (1).png>)

* Provides rich and customizable tagging frameworks to efficiently organize your assets and help users discover relevant assets.

![Example - Asset tagging frameworks in the Education Domain](<../../.gitbook/assets/Screen Shot 2022-03-24 at 11.58.43 AM.png>)

* Provides tools such as editors and players to create and consume these assets.

![Editors & Players](<../../.gitbook/assets/Screen Shot 2022-03-24 at 1.12.09 PM.png>)

### Types of Assets

Below assets are currently defined in Sunbird. You can define new assets basis your needs.

* Content - This asset allows you to create a variety of content enabling you to deliver rich learning experiences.
* Collections - click here to know more about this asset type
* Question(s) - click here to know more about this asset type
* Question Set - click here to know more about this asset type
* Media Resources - This asset type comprises of lowest level of reusable assets such as images, video, audio files etc



####

### ~~Asset~~

~~The asset in Knowledge management is the building block that is clustered together to form relevant information to the users. For example: In an office scenario, assets are the equipment like tables, chairs, stationery etc. Similarly, in the Sunbird context, the assets are named as content, collections, events etc.~~&#x20;

{% hint style="info" %}
~~In most of the following pages about asset management and its component, the assets are defined as content.~~ &#x20;
{% endhint %}

~~The asset management module consists of the following components:~~&#x20;

* ~~~~[~~Editors~~](../product-and-developer-guide/editors/)~~: The editor provides the tools to create and manage assets using UI on top of APIs.~~
* ~~~~[~~Players~~](../product-and-developer-guide/player/)~~: The player is used for consuming the asset by the end-user.~~
* ~~~~[~~Service~~](../product-and-developer-guide/content-service/)~~: The asset service is a set of APIs to manage asset objects (learning assets) and their lifecycle (creation, modification, reviewing, publishing, retrieval)~~
