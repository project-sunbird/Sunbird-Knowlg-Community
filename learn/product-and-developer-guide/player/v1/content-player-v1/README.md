---
description: >-
  Content player v1 which is used to play/render the contents in both device and
  web - based on the mime types.
---

# Content Player v1

This is the classic version of the asset player. Using this player, users can play the following asset types.

* ECML
* PDF
* EPUB
* HTML and H5P
* Video (MP4, WebM)
* Youtube

![](<../../../../../.gitbook/assets/Screenshot from 2021-11-24 15-00-25.png>)

### Architecture

Content player is used to render the different types of contents. This contents are categories in terms of mime-type

### MIME Type

**What is mime-type**

MIME Types defines the what type of the content it is. According to the mimeType you can load the specific content launcher and play the different types of contents

#### Sample config to load the MIME types

```
mimetypes: [
    "application/vnd.ekstep.ecml-archive",
    "application/vnd.ekstep.html-archive",
    "application/vnd.ekstep.h5p-archive",
    "application/epub",
    "video/mp4",
    "application/pdf",
    "video/x-youtube",
    "video/webm",
    "audio/mp3"
]
```

**Supported MIME Types are:**

| Content Type                                                                                                                                                                | MIME Type                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ECML](ecml-player-v1.md)                                                                                                                                                   | [application/vnd.ekstep.ecml-archive](ecml-player-v1.md)                                                                                                                                |
| [HTML](html-h5p-player-v1.md)                                                                                                                                               | [application/vnd.ekstep.html-archive](html-h5p-player-v1.md)                                                                                                                            |
| [PDF](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/aanfWbeVT74C5lXDPde3/\~/changes/uO8tokGf3RxCXA1P4fnr/learn/product-and-developer-guide/content-player-v1/pdf-player) | [application/pdf](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/aanfWbeVT74C5lXDPde3/\~/changes/uO8tokGf3RxCXA1P4fnr/learn/product-and-developer-guide/content-player-v1/pdf-player) |
| [Epub](epub-player-v1.md)                                                                                                                                                   | [application/epub](epub-player-v1.md)                                                                                                                                                   |
| [H5P](html-h5p-player-v1.md)                                                                                                                                                | [application/vnd.ekstep.h5p-archive](html-h5p-player-v1.md)                                                                                                                             |
| YOUTUBE                                                                                                                                                                     | video/x-youtube                                                                                                                                                                         |
| WEBM                                                                                                                                                                        | video/Webm                                                                                                                                                                              |
| MP4                                                                                                                                                                         | video/mp4                                                                                                                                                                               |
| EXTERNAL CONTENT                                                                                                                                                            | text/x-url                                                                                                                                                                              |

### Content Launchers

Content player v1 is able to play the different types of contents using the configuration. You just need to provide the mimeType and plugin launchers in config. Its capable to load the content launchers according to the mimeType

#### Sample config to launch the ECML content

```
"contentLaunchers": [ // content laucher plugins for specific content mimetypes
    { // Plugin used for ECML content to launch, It is default plugin
        "mimeType": 'application/vnd.ekstep.html-archive',
        "id": 'org.sunbird.htmlrenderer',
        "ver": 1.0,
        "type": 'plugin'
    }
]
```

### White List Urls

Content player v1 will allows to play the external streaming url by adding the domain into the whiteListUrl config

**Sample config to add white listed urls**

```
whiteListUrl: [ 
    'self', 'https://.blob.core.windows.net/**',
    'https://ekstep-public-.s3-ap-south-1.amazonaws.com/**' 
]
```

## **Features**

### **Overlay**

Overlay is used to show some extra information on top of the content. This is a configurable properties

#### Sample overlay config

```
"overlay": {
    "enableUserSwitcher": true, // enable/disable user-switcher, default is true for mobile & preview
    "showUser": true, // show/hide user-switcher functionality. default is true to show user information
    "showOverlay": true, // show/hide complete overlay including next/previous buttons. default value true
    "showNext": true, // show/hide next navigation button on content. default is true
    "showPrevious": true, // show/hide previous navigation button on content. default is true
    "showSubmit": false, // show/hide submit button for assessmetns in the content. default is false
    "showReload": true, // show/hide stage reload button to reset/re-render the stage. default is true
    "menu": {
        "showTeachersInstruction": true // show/hide teacher instructions in the menu
    }
}
```

* **User switcher** _(enableUserSwitcher)_**:** Content player v1 is capable to play the one content for more one user on the same device. The _enableUserSwitcher_ is a overlay property and it used to switch the users while playing the contents

![](../../../../../.gitbook/assets/ezgif.com-gif-maker.gif)

* **Show user \_** (showUser)\_**:** Player provide the capability to hide and show the users while rendering the content. The show/hide user-switcher functionality. default is true to show user information
* **Show Overlay** _(showOverlayshowOverlay)_**:** This property enhance the content player capability to show extra information about contents. Default is true.
* **Show next** _(showNext)_**:** This is a navigation property of next button for content. You can hide and show the next navigation button. Default is true.
* **Show previous** _(showPrevious)_**:** This is a navigation property of previous button for content. You can hide and show the previous navigation button. Default is true.
* **Show Submit** _(showSubmit):_ This is used to show a submit button after attending the assessment. Default is true.
* **Show reload** _(showReload)_**:** Show reload button is used to reload or re-render the stage. This is a configurable property to show/hide this reply button. Default is true.

### **Splash screen**

User can customise the loading screen of the content player using below configuration

```
"splash": {
   "text": "Powered by Sunbird", // Text to be shown on splash screen while loading content. 
   "icon": "assets/icons/icn_genie.png", // Icon to be show on above the text(full absolute path of the image in mobiew or http image link)
   "bgImage": "assets/icons/background_1.png", // backgroung image used for splash screen while loading content(absolute folder path of the image in mobie or http image link)
   "webLink": "XXXX" // weblink to be opened on click of text
}
```

### **Navigate**

This navigate feature will provide the user to view previous and next page from given page [PDF player](pdf-player-v1.md) only provides to jump to any specific location capability.

![](../../../../../.gitbook/assets/epub-navigation.png)

### **Side menu**

This is one of the property of [overlay config](./#overlay). This allows user to perform the following actions based input config provided.

![](<../../../../../.gitbook/assets/ezgif.com-gif-maker (2).gif>)

* **Replay**: Its a default feature of the side menu, by clicking on the replay user can reload the content
* **Switch user:** Side menu enables user to switch the current user by clicking on this side menu option. refer [user switcher config](./#sample-overlay-config) to configure this button.
* **Mute:** Side menu allows user to mute and unmute the sound of the content. Default is unmute.
* **Exit:** Its a default feature of the side menu options and user can exit the content bu clicking on this button
* **Read teacher instructions:** While creating the [ECML type content](ecml-player-v1.md) if creator added the instruction to the stage, each stage will show that instructions. This is a configurable property of the side menu

**Sample config to show the instructions**

```
"menu": {
    "showTeachersInstruction": true // show/hide teacher instructions in the menu
}
```

### **End page**

Content player allows to show the customise page after rendering the content. _**showEndPage**_ property defines to show this page as a end page. This end page will have the following buttons to interact with the contents

Sample config to show end page

```
"config" : {
    showEndPage: true
}
```

* **Previous:** In a collection play - the previous button will indicate the previous content of the current content on the current content end page.

![](<../../../../../.gitbook/assets/endpage (2).png>)

* **Score:** This will indicate the user assessment score on the end page
* **Time:** This will indicate - how much time user spend on the content.
* **Name :** It shows the Name of the content. This will show as per the name property of the content metadata.
* **Creator:** It shows the Name of the content creator. This will show as per the creator property of the content metadata.
* **Replay:** By clicking on the replay button user can reload the content. Its a default property of the end page.
* **Username:** Initial latter of the user will show on the end page. By clicking on the this button user switcher popup will show - witch allows you to select and switch the user.
* **Exit:** By clicking on the Exit button user can exit the content and application.
* **Next:** In a collection play - the next button will indicate the next content of the current content on the current content end page. This should be your [getRelevantContent()](https://github.com/project-sunbird/sunbird-content-player/blob/9fc06f842ff2bc0bd1b1143d288caed1075ada83/player/public/services/localservice.js#L101) API response.

Next and previous buttons are used see the next and previous slide of the content. On end page, the next and previous button can be configured.

To show these buttons on the end page, you have expose the service methods. Please refer to [these services](https://github.com/project-sunbird/sunbird-content-player/tree/9fc06f842ff2bc0bd1b1143d288caed1075ada83/player/public/services) for more information.

Sample API response to show the next and previous button

```
{
  "next": {
    "content": {
      "contentData": {
      }
    }
  },
  "prev": {
    "content": {
      "contentData": {
      }
    }
  }
}
```

## Configurations

Please refer to the [config section of README.md ](https://github.com/project-sunbird/sunbird-content-player#how-to-render-the-contents)file of the below [git repository](https://github.com/project-sunbird/sunbird-content-player)

## FAQs

Please refer to [FAQs of sunbird](http://docs.sunbird.org/latest/faqs/) documents

ans: Please refer this link to [setup the content player](../../../../../use/installation-guide/players/v1/how-to-setup.md) locally.

2\. How to configure content player v1

ans: Please refer [configuration section](./#configurations) for configuration.

3\. How to launch the different types of contents in content player v1

ans: Please refer [content launchers](./#content-launchers) section.

4\. What is mimeType

ans: Please refer [mime Type](./#mime-type) section

5\. Can we switch the user while playing the contents

ans: Yes, we can switch the user while playing the contents. Please refer refer [user switcher config](./#sample-overlay-config) section for more information.

6\. How to render the HTML file in content player v1?

ans: Please refer [HTML/h5p player](html-h5p-player-v1.md) v1 page

7\. Video can be stream in content player v1?

ans: Yes, Video can be stream using the [streamingUrl](broken-reference). for more please refer [video player v1](broken-reference) page
