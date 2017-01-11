## {{ page.title }}

Within MyST, the target state of each Platform Instance is captured in the _“platform definition”_, which is divided into two layers: 
* First, the Platform Blueprint defines an environment agnostic specification used to define the platform topology and configuration of your Oracle Middleware. 
* Second, the Platform Model overlays the environment specific configurations. 

This _“platform definition”_ is used to manage the entire platform lifecycle from provisioning the initial platform instance through to managing on-going configuration changes.

This means incremental configuration changes are simple

This declarative approach to defining target state enables MyST to treat Oracle Middleware infrastructure as code. Platform Blueprints and Models are put under version control, allowing us to easily propose, review, test, promote and deploy configuration changes.

This chapter contains the following sections:

* [3.4.1 - Platform Blueprint and Model Version Control](/platform/definitions/version-control/README.md)

* [3.4.2 - Editing Platform Blueprints and Models](/platform/definitions/editor/README.md)

