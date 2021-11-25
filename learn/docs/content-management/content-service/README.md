# Content Service

The Content service uses the Graph engine to communicate with Neo4j. The Graph engine expects schema definitions for each object type. It validates the data object with the object definition during various CRUD operations.



## Object  <a href="object" id="object"></a>

This is the master definition for Types of items that are supported on sunbird.\
Example from education - _**Question set **_is an object\
Analogous example from the real-world - A _**foot wear**_ is an object

An object is the core system entity through which any type of asset is managed. Services such as creation, modification, publishing, discovery, consumption - are built around the core objects.

Since an object is the core entity that can be used across multiple use cases in multiple ways, it has to be defined, managed and support wide variety of behaviors, in a very generalized way, so that it can be easily reused in wide range of use cases.

![](<../../../../.gitbook/assets/Screenshot from 2021-11-25 08-59-20.png>) ![](<../../../../.gitbook/assets/Screenshot from 2021-11-25 08-59-32.png>)





## Category <a href="category" id="category"></a>

This represents the actual items that are defined and created based on different use cases.

Unlike an **Object**, which is a core entity of the system, a category is just a “label” tagged to an object and can defined a specific set of properties and behaviors - which are a subset of those supported by the object.

Hence, categories are completely driven by configuration, without any category specific logic implemented in the code.

Example from education - _**Exam Question paper, Practice Worksheet, Quiz**_ each one is a category of the object type **Question set**\
Analogous example from the real-world - A _**Shoe, Sandal, Flip-flops**_ each one is a category of the object type **foot wear**

Following pages provide details of the various types of objects that are part of sunbird and a default set of categories configured.

For further explanation of objects and categories can be found in the following videos:

[Understanding Content Architecture of Sunbird](https://www.youtube.com/watch?v=WxZXaTnj2D0\&t=7s)

[Understand Collection Architecture : Enabling Organised and Contextual Experience](https://www.youtube.com/watch?v=n9H87z0-7eU\&t=1709s)
