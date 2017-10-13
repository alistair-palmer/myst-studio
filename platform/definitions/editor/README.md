## {{ page.title }}

MyST holds the configuration details of a Platform Blueprint and Platform Model in a hierarchical or tree-like structure. The Platform Editor is used to view and edit Platform Blueprints and Platform Models.

### Opening a Platform Blueprint in the Platform Editor
From the side menu navigate to`Modeling` > `Platform Blueprint`, this will display a list of existing Platform Blueprints. Click on the `Actions` drop-down in the top right-hand corner of the Platform Blueprint we want to view / edit and select `Open`. This will open the Platform Blueprint in the `Platform Editor` in view mode.

![](img/platformBlueprintEditor.png)

### Opening a Platform Model in the Platform Editor

From the side menu navigate to`Modeling` > `Platform Models`, this will display a list of existing Platform Models. Select the Platform Model you are interested in and MyST will display summary details about the Platform Model and its corresponding instance as shown below.

![](img/platformModelSummary.png)

Click on the `Actions` drop-down in the top right-hand corner and select `Configuration`. This will open the Platform Model in the `Platform Editor` in view mode.

### Platform Editor Layout
The Platform Editor is split into four core sections:

1. **Control Bar** - Displays the version, revison and state of the Platform Blueprint or Model you are viewing, plus allows you to perform actions such as editing.
2. **Tree View** - Displays a hierarchical view of the Platform Blueprint. That can be used to navigate the Platform Blueprint or Model configuration. Selecting a component in the tree view will display a list of properties defined for that component in the properties view.
3. **Topology View** - Helps to visualize the configuration that is defined in the Platform Blueprint or Model. Selecting a component in the topology diagram will display a list of properties defined for that component in the properties view.
4. **Property View** - Displays the list of properties and corresponding values defined for the selected component in your Platform Blueprint. 

You can re-size each view by dragging the gray bars which separate each section. By clicking on the appropriate arrow you can close / open the corresponding view.

#### Control Bar
The Control Bar Displays the version, revision and state of the Platform Blueprint or Model. For further details on versioning see [Platform Blueprint and Model Versioning]().

By default the Platform Editor is opened in read-only mode, selecting `Edit Configuration` will put the Platform Editor into edit mode, allowing us to make and save changes. [See ...]()

In addition, the `Actions` drop down allows you to perform a number of additional actions, these are:
* `Save as new version` - Allows you to create a new version of the Platform Blueprint
* `Delete` - Allows you to delete the current version of the Platform Blueprint or Model. Note we can only delete a Platform Model that does not have an active Platform Instance and we can only delete a Platform Blueprint that does not have any dependent Platform Models.
* `Publish` - Sets the status of the Platform Blueprint or Model to `FINAL` meaning no further changes can be made against that version.

#### Tree View
MyST holds the configuration details of a Platform Blueprint and Platform Model in a hierarchical or tree-like structure, consisting of the following object types:
* `property` - Primitive type consisting of a key-value pair used to hold the value of a property.
* `component` - Complex type consisting of a pre-defined collection of object types.
* `list` - Complex type consisting of a list of zero, one or more components of the same type.
* `paramList` - List of zero, one or more `property` types.

The Tree View provides a hierarchical view of the Platform Blueprint and Platform Model, providing a simple way to navigate the configuration details of a Platform Blueprint or Model.

Clicking on the plus sign (![](img/platformBlueprintExpand.png)) of a component will expand it to show any child components. Selecting a child element will display the list of properties and values defined for that component in the properties view. 

At the top level, a Platform Blueprint or Model will consist of some or all of the following components:

* **Global Variables** - List of zero, one or more `string` property types.
* **Middleware Settings** - Defines core properties such as the Oracle Base and Oracle Middleware home directory.
* **Products** - Defines the core products that make up the Platform, such as Java, WebLogic, Oracle SOA, etc.
* **Compute Groups** - Defines the Compute Groups for the Platform.
* **Load Balancers** - Configuration details for Load Balancers
* **WebTier Configuration** - Configuration details for Oracle Http Server
* **WebLogic Domain** - Configuration details of the WebLogic domain
* **Keystores** - Holds details of any Keystores used by the Platform

#### Topology View
The topology view provides a summary visualization of your Platform Blueprint or Model and provides a quick shortcut for referencing key components. Specifically, it displays:
* **Load Balancer** - Clicking on this will select the LoadBalancer component located at `[Blueprint|Model] > Load Balancers > LoadBalancer` and display its corresponding properties in the Property View.
* **Compute Groups** - The topology view shows each Compute Group and the components it contains. Clicking on a Compute Group will select the corresponding Compute Group element in the Platform Blueprint or Model located at `[Blueprint|Model] > Compute Groups > [Compute Group Name]` and display its corresponding properties in the Property View.
* **Clusters** - The topology view shows each WebLogic Cluster and the corresponding Product Components. Clicking on a WebLogic Cluster will select the corresponding component in the Platform located at `[Blueprint|Model] > WebLogic Domains > [domain_name] > WebLogic Clusters > [Cluster Name] ` and display its corresponding properties in the Property View.
* **Product** - Clicking on a Product will select the corresponding component in the Platform located at `[Blueprint|Model] > Products > [component_name]` and display its corresponding properties in the Property View.

#### Property View
The `Property View` displays the properties and values for the selected component. A component may also contain other components. For example, the screenshot below shows the properties for the *soa_domain* component. This contains the component `Credentials` which has the properties `Username` and `Password`.

To expand a component within the property view click on the `+` symbol, and to collapse a component click on the `-` symbol. Alternatively to expand or collapse all components within the property view click on the corresponding `Expand All` or `Collapse All` button.

![](img/propertyValues.png)

By default, MyST only shows the core properties for a component. To see all properties, select `Show advanced properties` (outlined in red above).

MyST auto-computes many of the property values in accordance with Oracle Enterprise Deployment Guide.  The auto-computed values are highlighted in green, if we choose to change any of these, then MyST will display the user entered property in white.

### Editing Properties
To edit either a Platform Blueprint or Platform Model, click `Edit Configuration`. This will put the Platform Editor in **Edit** mode. 

When defining the value of a property, we can reference the value of one or more other properties, see [MyST Property Overview](). Once in **Edit** mode, the Property Viewer will display the property definition for calculating the property value, which may include references to other property values. Underneath that, MyST will display the actual resolved (or calculated) value of the property after property references have been substituted with actual values, as shown below.

![](img/propertyReference.png)

To edit a property, within the TreeView browse to the component where you want to make changes and click `Edit`(outlined in red below).

![](img/editComponent.png)

This will allow you to edit the property definitions for each property within the selected component. Once you have finished making your changes, click `Save`.

{% hint style='danger' %}
Important
{% endhint %}
> Saving changes at the component level only saves the changes with the current editing session. The Platform Editor allows you to make all the changes you need to the Platform Blueprint or Model, and save them to the MyST Repository all at once by clicking `Apply Changes` Alternatively, clicking `Discard Changes` will discard all the changes made within the current `Edit Session`. 

{% hint style='tip' %}
Any edits made to a Property Definition which have not yet been saved to the MyST Repository are highlighted in yellow to indicate this.
{% endhint %}

{% hint style='info' %}
Every time you apply changes to a blueprint version, a new revision is automatically created of the blueprint. From the  editor, we can only view the latest revision of the blueprint. If the latest revision of the blueprint is not the same as the last revision used to provision or change an instance, we will need to update the Platform Model before the new revision changes are applied.
{% endhint %}

### Property Expansion in MyST
To make editing and maintenance of Platform Blueprints easier, MyST supports property expansion when defining the value of a property. This allows us to define the value of a property based on the value of one or more other properties.

When a string of the format `${some.property}` appears in a property value it will be expanded to the value of the specified property.

For example, if we have the following properties:
* `oracle.base` - Defines the Oracle Home directory for installing the Oracle Middleware Platform. 
* `oui.inventory.directory` - Defines the Oracle Universal Installer (OUI) Inventory Directory

The default location for (OUI) Inventory Directory is to place this in the sub-directory `oraInventory` under the Oracle Home. MyST enables us to set the value of the property `oui.inventory.directory` to  `${var.oracle.base}/oraInventory`.

#### Referencing MyST Properties
When referencing a MyST property, in order to uniquely identify it, we need to specify the full path of the property within the Platform Blueprint or Model.

The simplest way to derive the expression to reference a property is to locate the property we wish to reference within the Property Viewer and click on the Property Name. MyST will open a speech bubble containing the expression to reference the property as shown below.

![](img/propertyExpression.png)

{% hint style='info' %}
The Platform Editor needs to be in Edit mode in order to be able to view a property reference expression.
{% endhint %}

#### Understand the MyST Property Path
In general, a dot notation is used to traverse the property hierarchy. For example, `a.b.c` would mean locate `c` within `b` within `a`. 

The following table lists the property path for the top-level components in the Platform Blueprint and the Platform Model.

| Component| Property Path|
| -- | --------- |
| Global Variables | var |
| Middleware Settings | rxr.wls.Fmw-1 |
| Products | rxr.def |
| Compute Groups | rxr.infra |
| Load Balancers | rxr.infra |
| WebTier Configuration | rxr.infra |
| WebLogic Domain | rxr.wls |
| Keystores | rxr.def |

#### Referencing a `property` value within a `component`
A component is a complex type consisting of a pre-defined collection of object types. To reference a `property` value within a component we used the following syntax:

`<component-property-path>.<property-key>`

Where
* `<component-property-path>` - Is the path to the component containing the property.
* `<property-key>` - Is the key for the property whose value we are referencing within the component.

For example, within a Platform Blueprint or Model, we have the `Middleware Settings` component, to reference the `version` property value, we would use the expression: 

`${[rxr.wls.Fmw-1].version}`

In this example:
* `rxr.wls.Fmw-1` is the `<component-property-path>` as defined in the table.
* `version` is the `<property-key>`.
 
#### Referencing a child `component` within a parent `component`
Reference a child component within a parent component we use the following syntax:

`<parent-component-property-path>.<component-key>`

Where:  
* `<parent-component-property-path>` - Is the path to the component containing the child component.
* `<component-key>` - Is the key for the component that we are referencing within the parent component.

#### Referencing a `component` within a `list`
A list is a complex type consisting of a list of zero, one or more components of the same type. 
To reference a component within a list we use the following syntax:

`[<parent-component-property-path>.<list-component-type>-<component-key>]`

Where
* `<parent-component-property-path>` - Is the path to the component containing the list.
* `<list-component-type>` - Is the component type held in the list
* `<component-key>` - Is the key for the component that we are referencing within the list. 

For example, a Platform Blueprint contains a list of Products (for example Java, SOA, Service Bus, RCU) that will be installed. In this example, if we want to reference the RCU component, we would use the expression:

`[rxr.def.Product-rcu]`

Where
* `<parent-component-property-path>` is `rxr.def` as defined in the xxxx table.
* `Product` is the `<list-component-type>`.
* `rcu` is the `<component-key>` for the RCU product component in the list 

To reference the RCU product version we would use the expression:   

`${[rxr.def.Product-rcu].version}`

For many lists, the component key defaults to the index number of the object stored in the list. For example, a WebLogic Domain contains a list of WebLogic Clusters. In this example: 
* The WebLogic Domain is the object containing the list. So `<parent-component-property-path>` is `rxr.wls`
* `Cluster` is the component type stored in the list.
* `1` is the component key for the first cluster, `2` the component key for the second cluster, and so on.

Thus the component property path to the second cluster in the list would be expressed as `[rxr.wls.Cluster-2]`. To reference the cluster name we would use the expression:  
`${[rxr.wls.Cluster-2].name}`

#### Referencing a property value within a property of type `paramList`
As we mentioned earlier, a component is a complex type consisting of a **pre-defined** collection of object types. However, we often want to add additional properties to a component, that aren't defined in advance. 

We can do this using a paramList. A paramList is a list of zero, one or more `property` types. The list of properties is not fixed and can be added to using the Platform Editor.

To reference a `property` value within a`paramList` we use the following syntax:

`<paramList-property-path>.param[<property-key>]`

Where
* `<parent-component-property-path>` - Is the path to the component containing the `paramList`
* `<property-key>` - Is the key for the property stored in the paramList

For example, the Oracle SOA Suite Product object contains a Name-Value Parameter list, that contains a number of `string` properties, such as audit-level and base-port. To reference the base-port value we would use the expression:  

`${[rxr.def.Product-soa].param[base-port]}`

#### Referencing a `global variable` value
MyST supports the notion of global variables. These are essentially held as a paramList. To reference a global `property` value within a component we used the following syntax:  

`${<var>.<property-key>}`

Where
* `<var>` - Is the path to the component containing the property.  
* `<property-key>` - Is the key for the property whose value we are referencing within the component.

For example, to reference the value of global variable `install.directory`, we would use the expression:
  
`${var.install.directory}`

<!-- TODO ### Create new Platform Blueprint Version -->

<!-- TODO ### Create new Platform Model Version-->