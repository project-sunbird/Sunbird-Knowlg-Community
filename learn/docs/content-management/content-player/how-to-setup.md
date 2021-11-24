# How-to-setup

Please refer to the github readme document.

{% embed url="https://github.com/project-sunbird/sunbird-video-player/tree/release-4.5.0#readme" %}

### Technical specifications

| Tech     | Version | Details                                                 |
| -------- | ------- | ------------------------------------------------------- |
| Node     | > 8.0   | To run project locally                                  |
| Cordova  | ^ 6.0   | Used expecially to communicate with mobile app(cordova) |
| HTML, JS |         |                                                         |
| Sass     |         | Used for styles                                         |

### Configuration

The common player(content-player) is customizable and configurable before launching any type of content inside any environment (preview or device) it expecting few configurations. Based on the configuration content will be rendered in the respective environment.

{% embed url="https://github.com/project-sunbird/sunbird-content-player/tree/release-4.4.0#how-to-render-the-contents" %}

### Internal Dependencies

#### [Content Service](../content-service/)&#x20;

Content service APIs are being used to read the content details using READ/GET API calls.&#x20;



### External Dependencies

#### [Sunbird Telemetry](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkM7F4oILSpCJPO0YUu/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.



#### [Sunbird QuML](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-Mk0O5w77ZnjFM6FJOvP/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.



