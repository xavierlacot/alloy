## Alloy Release Notes

### Release 1.6.2 - (06/11/2015)

Alloy 1.6.2 is a patch release addressing high-priority issues from previous releases.

#### Fixed Issues

  * [ALOY-1272](https://jira.appcelerator.org/browse/ALOY-1272): Building an Alloy project with
    the Titanium CLI on Windows fails

---
### Release 1.6.0 - (05/21/2015)

[Full list of Issues that were addressed in Release 1.6.0](https://jira.appcelerator.org/issues/?filter=16721)

#### Behavior Changes

To prepare for forthcoming Windows Phone support, Alloy and the Titaium SDK now support the
`windows` subfolder to include assets only for Windows Phone applications.  If have existing
`windows` subfolders, you will need to rename them and update any paths.

#### New Features

##### Backbone 1.1.2 Support

Alloy 1.6.0 introduces support for Backbone 1.1.2. Due to breaking changes from
Backbone 0.9.2 to 1.1.2, Alloy still uses Backbone 0.9.2 as its default
Model and Collection implementation.  You will need to update the configuration file to use the
newer Backbone library, then update your application to fix the breaking behavior changes and take
advantage of the new Backbone features.

In the future, Backbone 1.1.2 will become the default and 0.9.2 support will be deprecated and
eventually removed.

For details, see the
[Alloy Backbone Migration guide](http://docs.appcelerator.com/platform/latest/#!/guide/Alloy_Backbone_Migration).


##### CLI extract-i18n command

The Alloy CLI extract-i18n command now extracts localized strings from the XML files, in addition to
the JavaScript and TSS files, to populate the `strings.xml` file.


##### Underscore 1.6.0 Upgrade

The underscore.js library was upgraded from version 1.4.4 to version 1.6.0.

##### Windows Phone Support

To prepare for forthcoming Windows Phone support, Alloy added several conditionals to support logic,
UI elements and assets to only be included with Windows Phone applications.

  * In controllers, use the `OS_WINDOWS` constant.
  * In XML and TSS files, assign the `platform` attribute of UI elements a `windows` value.
  * Under the component folders in the `app` folder, add `windows` subfolders to include assets only for Windows Phone.

##### XML Markup Enhancements

  * Support &lt;ActionView/&gt; as a child tag of the &lt;MenuItem&gt; object to set the `actionView` property
    of `Titanium.Android.MenuItem`.  Only supports the Android platform.


---
### Release 1.5.1 (10/2/2014)

Below are the fixes included in this release.

* [ALOY-1149](https://jira.appcelerator.org/browse/ALOY-1149). iOS: Gradient array properties are converted into objects

---
### Release 1.5.0 (09/29/2014)

[Full list of Issues that were addressed in Release 1.5.0](https://jira.appcelerator.org/issues/?filter=16426)

#### Deprecations and Removals

##### Sample Widgets

The sample widgets included in the Alloy repository have been removed.

To find replacements for these widgets, or to find other widgets,
we recommend you visit [http://gitt.io](http://gitt.io).


##### localStorage Sync Adapter

As of this Release, the `localStorage` sync adapter is deprecated and will be removed in a future
release.

Use the `properties` sync adapter instead.

#### New Features

##### Built-in Update

The moment built-in now uses version 2.7.0 of the moment.js library.

##### Data Binding Enhancements

  * Support data binding for a Picker. Add data binding attributes to the PickerColumn and map model
    attributes to the PickerRow properties.

  * Support mixture of text and data binding notation when binding model attributes to XML
    attributes, for example, `<Label text="first name: {model.first_name}"/>`.

  * Support mapping multiple model attributes to a single XML attribute, for example,
    `<Label text="{model.title} by {model.author}">`.

For more details, see [Alloy Data Binding](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Data_Binding).

##### XML Markup/TSS Enhancements

  * Support setting ActionBar properties in XML and TSS using the `ActionBar` element. For XML
    markup, add the `<ActionBar/>` tag as a child of either a `<TabGroup/>` or `<Window/>`.
    Before this Release, you defined ActionBar properties in the `Menu` element.  Do not set the same
    ActionBar properties in both the `ActionBar` and `Menu` elements.
    For more details, see the "Android ActionBar" section in
    [Alloy XML Markup](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup).

  * Support `<KeyboardToolbar/>` as a child tag of the `<TextArea/>` object to set the `keyboardToolbar`
    property of `Titanium.UI.TextArea`.  Only supports the iOS platform.

  * Support `<AndroidView/>` or `<View/>` as a child tag of the `<AlertDialog/>` and
    `<OptionDialog/>` objects to set the `androidView` property. Only supports the Android platform.

  * Support the localization function `L()` with the Label's `text` property or as node text, for
    example, `<Label text="L('foo')"/>` or `<Label>L('foo')</Label>`.

  * Support spaces with the comma-separated values in the `platform` attribute, for example,
    `<Label platform="ios, android"/>`.  Prior to this Release, placing spaces in the platform
    attribute would throw an error.

---
### Release 1.4.1 (07/28/2014)

Below are the fixes included in this release.

* [ALOY-1091](https://jira.appcelerator.org/browse/ALOY-1091). id property of <Picker> other than 'picker' is treated as a variable
* [ALOY-1094](https://jira.appcelerator.org/browse/ALOY-1094). Date or time pickers: cannot use Ti.UI.* type constants, must use Titanium.UI.* abbreviations

---
### Release 1.4.0 (07/17/2014)

[Full list of Issues that were addressed in Release 1.4.0](https://jira.appcelerator.org/issues/?filter=16137)

#### Deprecations

##### Sample Widgets

The sample widgets included in the Alloy repository are deprecated and will be removed from the repo
in a future version. There are known issues with some of the widgets, which will not be addressed.

If you would like to take over maintenance and support for any of these widgets, please contact Tim
Poulsen at [tpoulsen@appcelerator.com](mailto:tpoulsen@appcelerator.com).

To find replacements for these widgets, or to find other widgets,
we recommend you visit [http://gitt.io](http://gitt.io).

#### New Features

##### Compiler Directives for Distribution Targets

This release introduces two new compiler directives used to distinguish distribution targets:

  * `DIST_ADHOC` : true if the current compiler target is built for iOS Ad Hoc distribution,
     for example, if you set the `-T dist-adhoc` option when building with the Titanium CLI.
  * `DIST_STORE` : true if the current compiler target is built for deployment to the
     Google Play Store or iTunes App Store, for example, if you set the `-T dist-store` option when
     building with the Titanium CLI.

Use these compiler directives in your controller code or initializer file (`alloy.js`).

Note that the `ENV_PRODUCTION` constant will be true too since these deployments are only for production builds.


##### Controller-less Views

As of this Release, Alloy provides a new way to create controller-less views.  Each component in
the controller-less view needs to be assigned an `id` attribute.  Using the `Require` or `Widget`
elements to include external views in the controller-less view does not work using this procedure,
that is, you can include the external views, but the styles cannot be updated with the `updateViews`
method.

  1. Use the `Alloy.createController()` method to create a controller from the controller-less view.
  2. Use the [updateViews()](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy.Controller-method-updateViews)
     method with the controller instance to update the styles of the view components.
     Pass a style dictionary as the only argument to the method.  The style dictionary contains key-value pairs,
     where the key is the id of the view component and the value is another dictionary containing
     key-value pairs of attributes you want to set for the view component.
  3. Use the `getView()` method with the controller instance to retrieve the view of the
     controller, which can be added to another view.

See also:

  * [Alloy Guides: Views without Controllers](http://docs.appcelerator.com/titanium/latest/#!/guide/Views_without_Controllers)
  * [Controller-less View test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-362)


#### Custom Query Styles

This release introduces the ability to use a custom query to determine if a style should be
applied or not. For example, the application can query if the device is running iOS 7 or later,
then apply a style to compensate for view components appearing behind the status bar.

To use a custom query:

  1. Define a conditional statement, which returns a boolean value, and assign it to a property in
     the `Alloy.Globals` namespace.
  2. Assign the `if` attribute to an element in the XML file or in the conditional block of the TSS file to
     the defined query with the `Alloy.Globals` namespace.

See also:

  * [Alloy Styles and Themes: Custom Query Styles](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Styles_and_Themes-section-35621526_AlloyStylesandThemes-CustomQueryStyles)
  * [Custom TSS queries test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/advanced/custom_tss_queries)

##### Map Module Integration

This release introduces better integration with the [ti.map module](http://docs.appcelerator.com/titanium/latest/#!/api/Modules.Map),
which includes the ability to define `Annotation` objects in XML markup and support for data-view binding.

To add `Annotation` objects in the XML markup, use the `<Module>` tag to load the map module
and create a map view.  Add `<Annotation>` tags as children of the `<Module>` tag.

To support data-view binding, set the `dataCollection` attribute to the name of the collection in
the `<Module>` tag.  Map attributes to bind in the `<Annotation>` tag.  The `<Module>` tag also
supports the `dataFilter` and `dataTransform` attributes.

    <Alloy>
        <Collection src="places"/>
        <Window>
            <Module id="mapview" module="ti.map" method="createView" dataCollection="places">
                <Annotation latitude="{latitude}" longitude="{longitude}" title="{title}" />
            </Module>
        </Window>
    </Alloy>

See also:

  * Alloy Example in [ti.map module](http://docs.appcelerator.com/titanium/latest/#!/api/Modules.Map)
  * [Map Module test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-800)
  * [Map Module with Data Binding test app](http://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-503)


##### Widget Component Generation

The Alloy CLI can now generate controller, view and style components for widgets.
Add the `--widgetname <WIDGET_NAME>` option to the `alloy generate` command
to create components for the specified widget.

##### Widget Themes

This release supports themes for widgets.  Widget themes work the same as project themes except for
the placement of the files.

Inside your theme folder (`app/themes/<THEME_NAME>`), create `widgets/<WIDGET_NAME>` folders,
where `<THEME_NAME>` is the name of the theme and `<WIDGET_NAME>` is the name of the widget.

Create two folders, `assets` and `styles`, to place your custom images and styles for your widget,
respectively.  The `assets` and `styles` folders need to be placed in the folder that is named after
the widget.

If the theme is enabled, the files in the widget theme folder will replace the default ones
used by the widget.

See also:

  * "Themes" section in [Alloy Widgets](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Widgets)
  * [Widget Themes test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-378)


##### XML Markup/TSS Enhancements

  * Support the Android Action Bar in XML and TSS using the `Menu` element.  To define an action bar in XML markup,
    add the `<Menu>` tag as a child of either a `<Window>` or `<TabGroup>`. To add action items in XML markup, add
    `<MenuItem>` tags as children of `<Menu>`.  The `ActionBar` attributes may be defined in the XML
    markup or TSS file. For details, see the "Android ActionBar" section in
    [Alloy XML Markup](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup).

  * Support `Button` attributes in `<LeftNavButton>` and `<RightNavButton>`.  Instead of
    creating a `Button` object for the `LeftNavButton` or `RightNavButton` elements, add the
    `Button` attributes to either `LeftNavButton` or `RightNavButton` in either the XML markup
    or the TSS file. For details, see the "iOS Navigation Button Shorthand" section in
    [Alloy XML Markup](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup).

  * Support Date Picker attributes. The
    [maxDate](http://docs.appcelerator.com/titanium/latest/#!/api/Titanium.UI.Picker-property-maxDate)
    [minDate](http://docs.appcelerator.com/titanium/latest/#!/api/Titanium.UI.Picker-property-minDate),
    and [value](http://docs.appcelerator.com/titanium/latest/#!/api/Titanium.UI.Picker-property-value)
    attributes now accept date strings. For Alloy XML and TSS files, use a date string that can
    be parsed by the [moment.js constructor](http://momentjs.com/docs/#/parsing/string/), which includes
    ISO-8601 and RFC2822 dates.

  * Support the localization function, `L()`, as node text for the `OptionDialog`'s `<Option>` tag.

  * Support [Titanium.UI.RefreshControl](http://docs.appcelerator.com/titanium/latest/#!/api/Titanium.UI.RefreshControl)
    in XML markup.  Add the `<RefreshControl>` tag as a child of either `<ListView>` or `<TableView>`.

  * Add shorthand notation for `TextField` keyboard attributes. When specifying either the `keyboardType` or
    `returnKeyType` attributes, you do not need to use `Titanium.UI.KEYBOARD_` or `Titanium.UI.RETURNKEYTYPE_`
    as part of the constant name. For details, see the "TextField Keyboard Shorthands" section in
    [Alloy XML Markup](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup).

  * Support `undefined` as a settable value in the TSS files.  Assign `undefined` to an attribute
    to unset it.  Do not encase `undefined` in quotes.

See also:

  * [Action Bar test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-784)
  * [Button Shorthand test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-714)
  * [Date Picker test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-263)
  * [Options Dialog with Localization Function test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-1009)
  * [Refresh Control test app](https://github.com/appcelerator/alloy/tree/master/test/apps/testing/ALOY-910)
  * [Text Field Keyboard Shorthand test app](https://github.com/appcelerator/alloy/tree/1_4_X/test/apps/testing/ALOY-927)


#### Known Issues

##### Alloy Plugin

Alloy 1.4.0 includes changes to the Alloy plugin, which is used by Studio to compile and launch your
project. These changes will be applied automatically the first time you build a project after
updating to 1.4.0. However, because the first build uses the old plugin, there is a small chance
that it will fail. Retrying the build should resolve the issue, or you can manually update the
plugin with the following command:

    alloy install plugin [path_to_project]

If you enter this command while in your project's folder, omit the path.

CLI users are not affected by this change.


#### New APIs

The following APIs are new in Release 1.4.0.

|API|Type|Note|
|---|----|----|
|`Alloy.Controller.updateViews`|method|Applies a dictionary of properties to the components of a view in the controller.|

---
### Release 1.3.1 (02/10/2014)

Below are the new key features and fixes in this release. Also see the
[full list of changes](https://jira.appcelerator.org/secure/IssueNavigator.jspa?mode=hide&requestId=15666).

* [ALOY-905](https://jira.appcelerator.org/browse/ALOY-905). Alloy now supports TiSDK 3.0.0+ again!
* [ALOY-907](https://jira.appcelerator.org/browse/ALOY-907). Fixed unhandled exception errors in invalid JS.
* [ALOY-912](https://jira.appcelerator.org/browse/ALOY-912). Better handling of runtime conditionals on TableView proxy properties.
* [ALOY-914](https://jira.appcelerator.org/browse/ALOY-914). Show Alloy appicon instead of Titanium default.
* [ALOY-916](https://jira.appcelerator.org/browse/ALOY-916). Copy theme assets to platform-specific folders.
* [ALOY-920](https://jira.appcelerator.org/browse/ALOY-920). Fixes compile time error when using should.js.
* [ALOY-922](https://jira.appcelerator.org/browse/ALOY-922). Fixes error when using proxy properties on a TextField in an ItemTemplate.
* [ALOY-937](https://jira.appcelerator.org/browse/ALOY-937). Fixes copying of platform-specific widget assets.

---
### Release 1.3.0 (12/20/2013)

[Full list of Issues that were address in Release 1.3.0](https://jira.appcelerator.org/secure/IssueNavigator.jspa?mode=hide&requestId=15575).

#### Breaking Changes

##### Titanium SDK Support

Due changes in the application build process for both Alloy and the Titanium SDK,
Alloy 1.3.0 only supports Titanium SDK 3.2.0 and later. You can find details on this in the following tickets:

* [TIMOB-14884](https://jira.appcelerator.org/browse/TIMOB-14884)
* [ALOY-760](https://jira.appcelerator.org/browse/ALOY-760)

#### New Features

##### XML Markup Enhancements

  * Support children elements for Widget and Require elements.  View objects created using the Widget
    and Require elements can contain child view elements, which are added as children views of the
    parent Widget or Require view object. Example: [require_children](https://github.com/appcelerator/alloy/tree/master/test/apps/advanced/require_children)

  * Support `<HeaderView>`, `<FooterView>` and `<PullView>` as children tags of the `<ListView>` object to
    specify the `headerView`, `footerView` and `pullView` properties of `Titanium.UI.ListView`.

  * Support `<SearchBar>` and `<SearchView platform="android>` as children tags of the `<ListView>` object to
    specify the `searchView` property of `Titanium.UI.ListView`.

  * Support `<HeaderView>` and `<FooterView>` as children tags of the `<ListSection>` object to
    specify the `headerView` and `footerView` properties of `Titanium.UI.ListSection`.

  * Support `<LeftButton>`, `<RightButton>` and `<KeyboardToolbar>` as children tags of the `<TextField>` object to
    specify the `leftButton`, `rightButton` and `keyboardToolbar` properties of `Titanium.UI.TextField`.
    These properties are only supported on the iOS platform.

  * Support shorthand method for declaring iOS system buttons.  When specifying the `system`
    attribute for a Button object, you do not need to use the `Ti.UI` namespace. For example, the
    following markup creates the iOS camera button:

        <Button systemButton="CAMERA"/>

##### TSS Enhancements

  * Support for bitwise operators, which includes bit shifting ('>>', '<<', and '>>>'), bitwise AND
    ('&'), bitwise OR ('|') and bitwise XOR ('^').

##### Model Enhancements

  * Support fetching a model using its ID attribute rather than an SQL query with the SQLite sync adapter.
    For example, you can fetch a model by using the attribute:

        myModel.fetch({id: 123});

    rather than using an SQL query:

        myModel.fetch({query: 'select * from ... where id = ' + 123 });

##### New Compiler Hook

This Release added a new compiler task called `pre:load` that is triggered before copying assets and
other resources to the project's `Resources` folder.  This task is executed near the beginning of
the Alloy compiliation process, after the project is cleaned.

##### Support Platform and Environment-Specific Project Configurations

In the project configuration file (`config.json`), you can combine the `os` and `env` keys together
to specify an environment and platform configuration. For example, the code below specifies
configurations for iOS test, iOS development and iOS production:

    "os:ios env:production": {
        "foo": "os:ios env:production"
    },
    "os:ios env:development": {
        "foo": "os:ios env:development"
    },
    "os:ios env:test": {
        "foo": "os:ios env:test"
    }

Previously, you could not specify both a platform and environment together.

##### New APIs

The following APIs are new in Release 1.3.0.

|API|Type|Note|
|---|----|----|
|`Alloy.builtins.animation.flip`|method|Transitions from one view to another using a 3D flip animation (iOS only).|
|`Alloy.builtins.animation.flipHorizontal`|method|Transitions from one view to another using a horizontal flip animation (iOS only).|
|`Alloy.builtins.animation.flipVertical`|method|Transitions from one view to another using a vertical flip animation (iOS only).|
|`Alloy.builtins.animation.HORIZONTAL`|constant|Constant to specify a horizontal flip (iOS only).|
|`Alloy.builtins.animation.VERTICAL`|constant|Constant to specify a vertical flip (iOS only).|

---

### Release 1.2.2 (18 September 2013)

* [ALOY-813](https://jira.appcelerator.org/browse/ALOY-813). Fixed bug handling unicode characters in XML attributes.
* [ALOY-817](https://jira.appcelerator.org/browse/ALOY-817). Fixed bug adding XML event handlers to UI components that use custom namesapces.
* [ALOY-815](https://jira.appcelerator.org/browse/ALOY-815) & [ALOY-818](https://jira.appcelerator.org/browse/ALOY-818). Support Ti.UI.iOS.NavigationWindow API in XML

---
### Release 1.2.1 (27 August 2013)

* [ALOY-789](https://jira.appcelerator.org/browse/ALOY-789). Fixed improper handling of printable escape characters in TSS.
* [ALOY-802](https://jira.appcelerator.org/browse/ALOY-802). Fixed escape character handling issue in TSS on Windows.
* [ALOY-803](https://jira.appcelerator.org/browse/ALOY-803). Fixed issue with controller subfolders on Windows.
* [ALOY-804](https://jira.appcelerator.org/browse/ALOY-804). Fixed issues with `jake` on Windows.

---
### Release 1.2.0 (15 August 2013)

* [Full list of Issues that were addressed in Release 1.2.0](https://jira.appcelerator.org/secure/IssueNavigator.jspa?mode=hide&requestId=15334)
* Fixes for a [handlful of Windows issues](https://jira.appcelerator.org/secure/IssueNavigator.jspa?mode=hide&requestId=15445) are available in the latest 1.2.1 release candidate. You can install it like this: `[sudo] npm install -g alloy@1.2.1-cr2`.

#### New Features

##### Dynamic Styling

As of this Release, Alloy supports changing styles dynamically during runtime. There are two methods
to support dynamic styling in Alloy.  You can either generate a dynamic style dictionary that can be
passed to `applyProperties` or a create method, or modify TSS class styles to an existing component on
the fly.

For more information, see:
* [Dynamic Styles guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Dynamic_Styles)
* [dynamic_styling Sample](https://github.com/appcelerator/alloy/tree/master/test/apps/advanced/dynamic_styling)
* Refer to the "New APIs" section below.

##### ListView in Markup

ListView objects can now be created in markup and with collection-view binding enabled.

For more information, see:
* [listview Sample](https://github.com/appcelerator/alloy/tree/master/test/apps/ui/listview)
* [binding_listview Sample](https://github.com/appcelerator/alloy/tree/master/test/apps/models/binding_listview)
* [ListView API Reference](http://docs.appcelerator.com/titanium/latest/#!/api/Titanium.UI.ListView)
* [Alloy Data Binding guide](https://github.com/appcelerator/alloy/tree/master/test/apps/models/binding_listview)

##### Module Markup Element

Use the new `Module` XML element to include a view from a native module.

For more information, see:
* "Module XML Element" section in the [Alloy XML Markup guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup)
* [native_modules Sample](https://github.com/appcelerator/alloy/tree/master/test/apps/advanced/native_modules)

##### CLI Command to Generate Styles

Style files can be generated using the Alloy CLI.  The Alloy CLI extracts the IDs and classes from
the markup file to create a skeleton style file.

For more information, see the "Generating a Style" section in the
[Alloy Tasks guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Tasks).

#### New APIs

The following APIs are new in Release 1.2.0.

|API|Type|Note|
|---|----|----|
|`Alloy.Controller.addClass`|method|Adds a TSS class to the specified view object.|
|`Alloy.Controller.createStyle`|method|Creates a dictionary of properties based on the specified styles.|
|`Alloy.Controller.removeClass`|method|Removes a TSS class from the specified view object.|
|`Alloy.Controller.resetClass`|method|Applies TSS classes to the specified view object and removes any applied classes that are not specified.|
|`Alloy.Controller.UI.create`|method|Creates a Titanium UI object with the specified styles.|

---
### Release 1.1.3 (17 June 2013)

#### New Features

* [ALOY-661](https://jira.appcelerator.org/browse/ALOY-661). Code Processor: Get Alloy to recompile before an analysis

---
### Release 1.1.2 (2 May 2013)

#### New Features

* [ALOY-424](https://jira.appcelerator.org/browse/ALOY-424). Blackberry support

#### Bug Fixes

* [ALOY-628](https://jira.appcelerator.org/browse/ALOY-628). Error loading platform-specific theme-based styles
* [ALOY-632](https://jira.appcelerator.org/browse/ALOY-632). Builtins being copied into Resources directory more than once causing runtime errors
* [ALOY-633](https://jira.appcelerator.org/browse/ALOY-633). Compiler directives (OS_IOS) undefined when referenced inside a widget
* [ALOY-635](https://jira.appcelerator.org/browse/ALOY-635). Styles not being sorted properly among global, controller, platform-specific, and theme

---
### Release 1.1.1 (19 April 2013)

Just 2 quick fixes to reduce the size of the Alloy distribution and fix one regression.

* [ALOY-625](https://jira.appcelerator.org/browse/ALOY-625). app.tss not being applied to views that don't have view-specific styles.
* [ALOY-626](https://jira.appcelerator.org/browse/ALOY-626). Remove unneeded resources from samples/mapping.

---
### Release 1.1.0 (April 2013)

  * [Full list of Issues that were addressed in Release 1.1.0](https://jira.appcelerator.org/secure/IssueNavigator.jspa?mode=hide&requestId=15057)

#### Breaking Changes

#### Alloy Run Command

The Alloy run command is obsoleted by the Titanium CLI build command.

If you are only using command-line tools to build your Alloy project, after using the
`alloy compile` command to convert the Alloy files to Titanium files, use the `titanium build`
command to build and run the Titanium code.


### New Features

#### Debugging in Studio

As of Titanium Studio 3.1.0, breakpoints added in Alloy Controllers and the `alloy.js` file are
recognized by the Studio Debugger.  These breakpoints map to the code in the generated Titanium
files located in the `Resources` directory.

CommonJS modules and Alloy Models will support this feature in a future release of Titanium
Studio and Alloy.  You still need to add breakpoints for these files in the generated Titanium
files located in the `Resources` directory.

Refer to [Alloy Debugging](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Debugging_and_Troubleshooting)
for more information.


#### Content Assistance in Studio

As of Titanium Studio 3.1.0, content assistance is supported in Alloy Views (XML markup and TSS
files) and Alloy Controllers.

For XML markup, start typing the XML element, attribute or `on` attribute (for events)
to receive content assistance.

For TSS files, type the name of the element, class (element prefixed with `.`) or ID name
(element prefixed with `#`) to receive content assistance.
You need to type the entire name of the element, class or ID name to receive assistance, and
the class and ID name must exist in the associated XML markup file.

For controller code, type the ID name (element prefixed by `$.`) or start typing a namespace
(Alloy, Titanium, etc.) to receive content assistance. You need to type the entire name of the ID
in order to receive assistance and it must exist in the associated XML markup file.

Some of the Alloy-specific attributes, such as `platform`, `formFactor` and the data binding
attributes, will be supported in a future release of Titanium Studio.

Refer to the "Using Content Assistance" section in
[Alloy Tasks](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Tasks) for more information.


#### Expanded Support for Collection-View Binding

ScrollableView, CoverFlowView, ButtonBar, ToolBar and TabbedBar objects support collection-view
binding.

For ButtonBar, ToolBar and TabbedBar, refer to the
[binding_bars example](https://github.com/appcelerator/alloy/tree/1_1_X/test/apps/models/binding_bars).

For CoverFlowView, refer to the
[binding_coverflow example](https://github.com/appcelerator/alloy/tree/1_1_X/test/apps/models/binding_coverflow).

For ScrollableView, refer to the
[binding_scrollableview example](https://github.com/appcelerator/alloy/tree/1_1_X/test/apps/models/binding_scrollableview).

Refer to [Alloy Data Binding](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Data_Binding)
for more information.


#### Widget Enhancements

Various enhancements to widgets:

  * Widgets have their own create methods.  Use `Widget.createController()`,
   `Widget.createWidget()`, `Widget.createModel()` and `Widget.createCollection()`
    instead of the `Alloy.create*` methods to create components relative to the
    widget context rather than the Alloy project. The method parameters
    are the same as the `Alloy.create*` methods.

  * Widgets support their own models and collections. Use models and collections the same
    as with an Alloy project except use the new Widget create methods, that is, use `Widget.createModel`
    and `Widget.createCollection` instead of `Alloy.createModel` and `Alloy.createCollection`,
    respectively to create models and collections inside a widget.

Refer to [Alloy Widgets](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Widgets) for
more information.

#### XML Markup Enhancements

Various enhancements to XML markup:

  * Support `<LeftNavButton>` and `<RightNavButton>` as children tags of the `<Popover>` object to
    specify the `leftNavButton` and `rightNavButton` properties of `Titanium.UI.iPad.Popover`.

  * Support `<HeaderView>` as a child tag of the `<TableViewSection>` object to specify the
    `headerView` property of `Titanium.UI.TableViewSection`.

  * Support the `name` attribute with the `<Widget>` and `<Require>` tags to specify a widget
    view-controller to use besides `widget.xml`/`widget.js`.

Refer to [Alloy XML Markup](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_XML_Markup)
for more information.

---
### 1.0.0 (19 February 2013)

### ** Breaking Changes **

The following changes alter the behavior of the Alloy Framework from previous versions and may
require code changes to your applications.

#### Titanium SDK Support

Alloy 1.0 only supports Titanium SDK 3.0 and later.  Previous versions of Alloy supported Titanium
SDK 2.1.x and later.


#### Backbone Events API Removed from View Proxies and Controllers

For Alloy View proxies and Controllers, that is, objects either referenced with `$.myid` or
created with `createController` and `getView` methods, you cannot use the Backbone Events
API `on`, `off` and `trigger` methods to bind and unbind event callbacks, or fire events.
Use the Titanium SDK API `addEventListener`, `removeEventListener` and `fireEvent` methods instead.

Previously, Alloy View proxies and Controllers could use the Backbone Events API.

For Alloy Collection and Model objects, use the Backbone Events API not the Titanium SDK event
listener API. This has not changed from previous versions of Alloy.


#### Alloy Model-View Binding

Model-view binding with the Ti.UI.View proxy should be considered experimental.  On the iOS
platform, the view items are not being repopulated correctly. To follow this issue, see
[ALOY-485](https://jira.appcelerator.org/browse/ALOY-485).

Model-view binding with TableViews works fine and does not suffer from any known issues.

For more information, see the [Alloy Data Binding guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Data_Binding).


#### Custom Sync Adapter

If you created a custom sync adapter, the order of the passed parameters of the
`module.exports.sync` method
has changed to match the `Backbone.sync` method.

Prior to 1.0.0, the order was:

    module.exports.sync(model, method, options)

For 1.0.0 and later, the order is now:

    module.exports.sync(method, model, options)

To update your custom sync adapter, just switch the order of the `method` and `model` arguments.

Additionally, both the `module.exports.beforeModelCreate` and `module.exports.afterModelCreate`
methods accept an additional passed parameter--the name of the model file.

Prior to 1.0.0, the methods were:

    module.exports.beforeModelCreate(config)
    module.exports.afterModelCreate(Model)

For 1.0.0 and later, the methods are:

    module.exports.beforeModelCreate(config, name)
    module.exports.afterModelCreate(Model, name)

#### SQLite Sync Adapter and Migrations

The previous `sql` sync adapter has been replaced with the `sql_new` sync adapter as mentioned in
release 0.3.5.

If you have a model that uses the `sql` sync adapter from Alloy 0.3.6 and before, you need to
migrate
your data to the new table schema of the Alloy 1.0.0 SQLite sync adapter.

First, manually remove the following files from your Alloy project:

* Resources/alloy.js
* Resources/alloy/sync/sql.js

Next, create a one-time migration file to transfer your model data to the new database schema.
Adapt the following code for your table schema.  Replace `title`, `author` and `isbn`
with your own specific table schema but leave `id` and `alloy_id` alone.  The order of fields does matter.
This migration file creates a temporary table, copies your current data to a temporary table,
deletes the old table from the database, creates a new table, then copies your data to the new table.

    migration.up = function(migrator) {
        var db = migrator.db;
        var table = migrator.table;
        db.execute('CREATE TEMPORARY TABLE book_backup(title,author,isbn,alloy_id);')
        db.execute('INSERT INTO book_backup SELECT title,author,isbn,id FROM ' + table + ';');
        migrator.dropTable();
        migrator.createTable({
            columns: {
                title:"TEXT",
                author:"TEXT",
                isbn:"INTEGER"
            },
        });
        db.execute('INSERT INTO ' + table + ' SELECT title,author,isbn,alloy_id FROM book_backup;');
        db.execute('DROP TABLE book_backup;');
    };

    migration.down = function(migrator) {

    }

Run your application once to migrate your data, then remove the migration file.

Note the `migrator.db` object in the previous example.  This object is a handle to a `Ti.Database` instance
to execute SQLite commands. DO NOT CLOSE THIS HANDLE OR OPEN A SECOND INSTANCE OF THE DATABASE.
This will cause fatal application errors.

See the [Alloy Sync Adapters and Migrations
guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Sync_Adapters_and_Migrations) for
information about the new SQLite sync adapter and the new migration features.

#### Removed ti.physicalSizeCategory Module

The `ti.physicalSizeCategory` module has been replaced by a background module part of Titanium SDK 3.0.x.
No action is needed to migrate to the new module.  However, your `tiapp.xml` file still references this module,
but does not affect the compilation or execution of the application.  You may safely remove this reference from your
`tiapp.xml` file.

Previously, this module was copied to an Alloy project as part of the `alloy new` command
and used to determine the size of an Android device.


#### Removed APIs

The following deprecated APIs have been removed in this release:

| API | Type | Notes |
|-----|------|-------|
| `Alloy.getCollection` | method | Creates a local instance of a collection. Use [Alloy.createCollection](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy-method-createCollection) instead. |
| `Alloy.getController` | method | Creates a local instance of a controller. Use [Alloy.createController](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy-method-createController) instead. |
| `Alloy.getModel` | method | Creates a local instance of a model. Use [Alloy.createModel](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy-method-createModel) instead. |
| `Alloy.getWidget` | method | Creates a local instance of a widget. Use [Alloy.createWidget](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy-method-createWidget) instead. |
| `Alloy.globals` | property | Global namespace. Use [Alloy.Globals](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy-property-Globals) instead. |
| `datatime.js` | builtin | Collection of functions for datetime formatting. Use [moment.js](http://docs.appcelerator.com/titanium/latest/#!/api/Alloy.builtins.moment) instead. |
| `size` | XML/TSS attribute | Defines size-specific view components or styles. Use the `formFactor` attribute instead. |

### New features

* [ALOY-343](https://jira.appcelerator.org/browse/ALOY-343). Facilitate Alloy code completion in Studio.
* [ALOY-437](https://jira.appcelerator.org/browse/ALOY-437). Support Android fastdev.
* [ALOY-475](https://jira.appcelerator.org/browse/ALOY-475). Create test app for testing sql adapter apps with no migrations.


### Bug fixes and improvements

* [ALOY-209](https://jira.appcelerator.org/browse/ALOY-209). Remove ti.physicalSizeCategory module for Alloy 1.0.0 (TiSDK 3.0+). Fixes [ALOY-188](https://jira.appcelerator.org/browse/ALOY-188) and [ALOY-134](https://jira.appcelerator.org/browse/ALOY-134).
* [ALOY-313](https://jira.appcelerator.org/browse/ALOY-313). Use applyProperties to assign properties to Ti.Android.MenuItem in parser.
* [ALOY-323](https://jira.appcelerator.org/browse/ALOY-323). Make Alloy support only TiSDK 3.0+.
* [ALOY-407](https://jira.appcelerator.org/browse/ALOY-407). Make `alloy generate model` calls uniform in format, regardless of adapter. Fixes [ALOY-375](https://jira.appcelerator.org/browse/ALOY-375) where models were not being generated correctly in Titanium Studio.
* [ALOY-429](https://jira.appcelerator.org/browse/ALOY-429). Convert jake app runner to use new CLI.
* [ALOY-454](https://jira.appcelerator.org/browse/ALOY-454). iOS is rebuilding apps every time with new CLI.
* [ALOY-455](https://jira.appcelerator.org/browse/ALOY-455). Remove Backbone eventing from Titanium proxies. Fixes [ALOY-460](https://jira.appcelerator.org/browse/ALOY-460) where ScrollableViews displayed noticeable lagging.
* [ALOY-457](https://jira.appcelerator.org/browse/ALOY-457). Make Alloy sync adapter sync() function signature match that of Backbone.
* [ALOY-473](https://jira.appcelerator.org/browse/ALOY-473). Abort compile process with message if trying to compile Alloy 1.0+ for anything less than Titanium 3.0.
* [ALOY-476](https://jira.appcelerator.org/browse/ALOY-476). Widgets within model-bound view get bound to unexisting `$model`.
* [ALOY-479](https://jira.appcelerator.org/browse/ALOY-479). Fix migration processing bug.
* [ALOY-480](https://jira.appcelerator.org/browse/ALOY-480). Replace `sql` adapter with `sql_new`.
* [ALOY-482](https://jira.appcelerator.org/browse/ALOY-482). View-based collection binding not properly clearing children before repopulating.
* [ALOY-486](https://jira.appcelerator.org/browse/ALOY-486). `sql` adapter does not update ID in client-side model when using AUTOINCREMENT.


### Deprecations

* [ALOY-330](https://jira.appcelerator.org/browse/ALOY-330). Make `alloy run` execute `titanium build`. The `alloy run` command will be removed in version 1.1.0 in favor of only using the `titanium build` command of the Titanium CLI.

---

## 0.3.6 (18 January 2013)

### Bug fixes and improvements

* [ALOY-474](https://jira.appcelerator.org/browse/ALOY-474). Allow extra commas in TSS files.

---
## 0.3.5 (18 January 2013)

### New features

* Tons of sql sync adapter features and fixes
    * **IMPORTANT**: Please read the [notes on the sql_new adapter](https://github.com/appcelerator/alloy/edit/master/CHANGELOG.md#additional-notes-for-035) below.
    * [ALOY-458](https://jira.appcelerator.org/browse/ALOY-458). The sql adapter now allows you to execute custom queries on fetch(). The [models/sql_queries](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_queries) test app uses this, specifically in this [controller file](https://github.com/appcelerator/alloy/blob/master/test/apps/models/sql_queries/controllers/main.js).
    * [ALOY-447](https://jira.appcelerator.org/browse/ALOY-447). Alloy Model column definitions now support SQLite keywords, like PRIMARY KEY and AUTOINCREMENT. The [models/sql_keywords](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_keywords) test app shows how to use it.
    * [ALOY-467](https://jira.appcelerator.org/browse/ALOY-467). idAttribute is now assignable from the model.js file's definition object. The [models/sql_keywords](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_keywords) test app, specifically this [model file](https://github.com/appcelerator/alloy/blob/master/test/apps/models/sql_keywords/models/fighters.js) shows how to use it to identify which column in your table is the unique identifier for syncing between SQLite and Backbone.
    * [ALOY-453](https://jira.appcelerator.org/browse/ALOY-453). Full support for up() and down() migrations in sql adapter. [models/sql_keywords](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_keywords) is also a multiple migration test app.
    * [ALOY-345](https://jira.appcelerator.org/browse/ALOY-345). sql adapter databases can now be preloaded from a database file. The [models/sql_preload](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_preload) test app shows how.
    * [ALOY-456](https://jira.appcelerator.org/browse/ALOY-456). sql adapter now supports multiple SQLite databases. The [model/sql_queries](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_queries) test app makes use of multiple SQLite databases.
    * [ALOY-468](https://jira.appcelerator.org/browse/ALOY-468). Added insertRow() and deleteRow() functions to migration object. You can see these in use for prepopulating and deleting rows in this [migration file](https://github.com/appcelerator/alloy/blob/master/test/apps/models/sql_queries/migrations/201301161234567_user.js) of the [models/sql_queries](https://github.com/appcelerator/alloy/tree/master/test/apps/models/sql_queries) test app.
* TSS parsing and features
    * [ALOY-272](https://jira.appcelerator.org/browse/ALOY-272). TSS parsing is now grammar based. Makes [code assist in TiStudio](https://jira.appcelerator.org/browse/ALOY-389) possible.
    * [ALOY-252](https://jira.appcelerator.org/browse/ALOY-252). Commas are now optional between top-level style objects in TSS files. Check this [style file](https://github.com/appcelerator/alloy/blob/master/test/apps/models/sql_queries/styles/app.tss) for an example.
    * [ALOY-452](https://jira.appcelerator.org/browse/ALOY-452). expr() syntax has been removed from TSS files. Here is the [cleaner and more powerful alternative](https://github.com/appcelerator/alloy/commit/e9fdc93c9760a1590c0abd0136662c11dc678066#commitcomment-2401085) for using runtime values in TSS files.
* [ALOY-284](https://jira.appcelerator.org/browse/ALOY-284). Titanium constants can now be used as XML attributes in markup. Check this [view xml file](https://github.com/appcelerator/alloy/blob/master/test/apps/testing/grammar/views/index.xml) for an example.

### Bug fixes and improvements

* [ALOY-191](https://jira.appcelerator.org/browse/ALOY-191). The [models/todo](https://github.com/appcelerator/alloy/tree/master/test/apps/models/todo) test app now works with all supported sync adapters \(sql, properties, localStorage\).
* [ALOY-336](https://jira.appcelerator.org/browse/ALOY-336). Mobileweb logs not showing up in console \(related to [TISTUD-2525](https://jira.appcelerator.org/browse/TISTUD-2525)\).
* [ALOY-449](https://jira.appcelerator.org/browse/ALOY-449). Parsing state not cleaned properly when processing multiple top-level UI elements.
* [ALOY-446](https://jira.appcelerator.org/browse/ALOY-446). sql adapter should open/close between all operations (best practices).

### Additional Notes for 0.3.5

Due to the massive amount of changes in the sql adapter, it is being introduced as ["sql_new"](https://github.com/appcelerator/alloy/blob/master/Alloy/lib/alloy/sync/sql_new.js). This is the "type" you would use in your model definitions, as seen in this [model from the models/sql_queries](https://github.com/appcelerator/alloy/blob/master/test/apps/models/sql_queries/models/user.js) test app. The unchanged "sql" adapter still exists temporarily for compatibility.

All freshly built apps will work with the **sql_new** adapter, including all the sql ones in the [test/apps/models folder](https://github.com/appcelerator/alloy/tree/master/test/apps/models) in the repo. There _may_ be conflicts, though, if you attempt to just drop the **sql_new** adapter on an app that has been previously using the old **sql** adapter. This is because **sql_new** uses a different, smarter, less invasive means of identifying the unique id of your sql records, adding an "alloy_id" column only if absolutely necessary. If you can delete your existing sql storage and just rebuild it, then all you need to do is delete and then you can start using the **sql_new** adapter. If not, we'll have a migration guide soon.

**One final important note** is that the old **sql** adapter will be replaced with **sql_new** when Alloy 1.0.0 is released, tentatively scheduled for mid-February. This'll give you a month to try it out and migrate data if necessary. Any questions or concerns, hit me up at the [google group](https://groups.google.com/forum/?fromgroups#!forum/appc-ti-alloy).

---
## 0.3.4 (20 December 2012)

### Important Note for Model/Collection Binding Feature

* [ALOY-432](https://jira.appcelerator.org/browse/ALOY-432). Added $.destroy() function to all controllers. When using model/collection binding in a controller, you **MUST** call this when closing a controller to prevent potential memory leaks. This is especially true if your binding makes references to global models/collections. More detailed documentation on this point will be added to the [Alloy Data Binding Guide](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Models-section-34636390_AlloyModels-DataBinding) very soon. \([TEST APP](https://github.com/appcelerator/alloy/tree/master/test/apps/models/binding_destroy)\)

### New features
* [ALOY-394](http://jira.appcelerator.org/browse/ALOY-394). Support collection binding on Views, allowing for arbitrary component repetition. \([TEST APP](https://github.com/appcelerator/alloy/tree/master/test/apps/models/journal)\)
* [ALOY-103](http://jira.appcelerator.org/browse/ALOY-103). Support model binding of models to discrete properties on UI components. \([TEST APP](https://github.com/appcelerator/alloy/tree/master/test/apps/models/login)\)
* [ALOY-382](http://jira.appcelerator.org/browse/ALOY-382), [ALOY-383](https://jira.appcelerator.org/browse/ALOY-383). Support in markup for proxy properties, like rightNavButton, leftNavButton, titleControl, etc... \([TEST APP](https://github.com/appcelerator/alloy/tree/master/test/apps/ui/proxy_properties)\)
* [ALOY-387](http://jira.appcelerator.org/browse/ALOY-387), [ALOY-388](https://jira.appcelerator.org/browse/ALOY-388). Support view (XML) and controller (JS) code completion in Titanium Studio.
* [ALOY-421](http://jira.appcelerator.org/browse/ALOY-421). Add moment.js as builtin. Deprecates datetime.s builtin.

### Bug fixes and improvements
* [ALOY-342](http://jira.appcelerator.org/browse/ALOY-342). Support '--platform' option with 'alloy generate' command to create platform-specific views and controllers.
* [ALOY-359](http://jira.appcelerator.org/browse/ALOY-359), [ALOY-423](http://jira.appcelerator.org/browse/ALOY-423). Improve buttongrid widget and fix a memory leak.
* [ALOY-361](http://jira.appcelerator.org/browse/ALOY-361). Fix a bug with style prioritization as it relates to the formFactor attribute.
* [ALOY-420](http://jira.appcelerator.org/browse/ALOY-420). Refactor TableView parser to allow model-bound tables to use proxy properties.
* [ALOY-430](https://jira.appcelerator.org/browse/ALOY-430). Collection binding now responds to the Backbone "reset" event.
* [ALOY-433](https://jira.appcelerator.org/browse/ALOY-433). Removed "unreachable code" warning in production Android builds.
* [ALOY-436](https://jira.appcelerator.org/browse/ALOY-436). Alloy compile failures will now abort the Titanium build process, as expected, with the Titanium 3.0+ SDK.
* [ALOY-438](https://jira.appcelerator.org/browse/ALOY-438). Fixed bug where the Backbone off() function on Titanium proxies created from markup was not working.


---
## 0.3.3 (6 December 2012)

### New features
* [ALOY-104](http://jira.appcelerator.org/browse/ALOY-104). Enable Model-View binding on TableViews. For more information, see the basic [tableview_binding test app](https://github.com/appcelerator/alloy/tree/master/test/apps/models/tableview_binding) or the slightly more complete [todo_binding sample app](https://github.com/appcelerator/alloy/tree/master/test/apps/models/todo_binding) which shows how to do data filtering and transformations on bound data.

    **NOTE:** This is brand new stuff with lots more functionality coming, so any feedback on the current state is very welcome. It's best to let us know at the [Alloy google group](https://groups.google.com/forum/?fromgroups#!forum/appc-ti-alloy).
* [ALOY-312](http://jira.appcelerator.org/browse/ALOY-312). Update Underscore.js to version 1.4.2 and Backbone.js to minified production 0.9.2 version.
* [ALOY-367](http://jira.appcelerator.org/browse/ALOY-367), [ALOY-377](http://jira.appcelerator.org/browse/ALOY-377). Support Soasta touch test.
* [ALOY-373](http://jira.appcelerator.org/browse/ALOY-373), [ALOY-379](http://jira.appcelerator.org/browse/ALOY-379). Add Collection tag in markup to create a singleton or instance(s) of a collection.
* [ALOY-390](http://jira.appcelerator.org/browse/ALOY-390), [ALOY-391](http://jira.appcelerator.org/browse/ALOY-391). Add Model tag in markup to create a singleton or instance(s) of a model.
* [ALOY-396](http://jira.appcelerator.org/browse/ALOY-396), [ALOY-397](http://jira.appcelerator.org/browse/ALOY-397), [ALOY-156](http://jira.appcelerator.org/browse/ALOY-156). Add completion callback to all methods in the animation.js builtin library.

### Bug fixes and improvements
* [ALOY-311](http://jira.appcelerator.org/browse/ALOY-311). Improve Ti.UI.Android.MenuItem parser.
* [ALOY-370](http://jira.appcelerator.org/browse/ALOY-370). Fix ability to assign functions with variable assigned functions in controllers.
* [ALOY-376](http://jira.appcelerator.org/browse/ALOY-376). Improve handling of Ti.Android.Menu component.
* [ALOY-393](http://jira.appcelerator.org/browse/ALOY-393). (Re-)enable optimizer.js as part of runtime JavaScript file optimization.
* [ALOY-403](http://jira.appcelerator.org/browse/ALOY-403). Improve Alloy.Collection and Alloy.Model code optimization.
* [ALOY-417](http://jira.appcelerator.org/browse/ALOY-417). Improve properties adapter.

### Deprecations
* [ALOY-401](http://jira.appcelerator.org/browse/ALOY-401). Deprecate Alloy.globals; use Alloy.Globals instead.

---
## 0.3.2 (15 November 2012)

### Bug fixes and improvements
* [ALOY-353](http://jira.appcelerator.org/browse/ALOY-353). Support all Backbone eventing in Titanium proxies, on(), off(), trigger(). Fixed multiple event firing bug with on().
* [ALOY-355](http://jira.appcelerator.org/browse/ALOY-355). Improve path handling in compiler plugin for OS X.
* [ALOY-356](http://jira.appcelerator.org/browse/ALOY-356). Remove string builtin dependency to shorten compilation time.
* [ALOY-365](http://jira.appcelerator.org/browse/ALOY-365). Add Alloy.globals namespace for global context.
* [ALOY-380](http://jira.appcelerator.org/browse/ALOY-380). Create app/alloy.js file automatically for all new projects.

---
## 0.3.1 (2 November 2012)

### New features
* [ALOY-192](http://jira.appcelerator.org/browse/ALOY-192). Add to-do sample application. Code is available on [github](https://github.com/appcelerator/alloy/tree/master/test/apps/models/todo).
* [ALOY-337](http://jira.appcelerator.org/browse/ALOY-337). Support themes to change the appearance of the entire GUI by customizing styles and assets. For more information, see:
    * [Alloy Styles and Themes](http://docs.appcelerator.com/titanium/3.0/#!/guide/Alloy_Styles_and_Themes)
    * [Themes sample application on github](https://github.com/appcelerator/alloy/tree/master/test/apps/advanced/themes)

### Bug fixes and improvements
* [ALOY-306](http://jira.appcelerator.org/browse/ALOY-306). Support platform, formFactor, and inline event attributes with abstract types in markup.
* [ALOY-340](http://jira.appcelerator.org/browse/ALOY-340). Fix Android "too deep recursion while parsing" error with Rhino runtime.
* [ALOY-341](http://jira.appcelerator.org/browse/ALOY-341). Improve adapter-backbone processing.
* [ALOY-352](http://jira.appcelerator.org/browse/ALOY-352). Fix SQL adapter to work if no migrations are present.
* [ALOY-354](http://jira.appcelerator.org/browse/ALOY-354). Fix "alloy generate jmk" command.

---
0.3.0 (beta)
------------
* Removed node-appc dependency.
* Added Alloy splash screens and icons
* Updated widgets, added new button-grid widget.

---
0.2.42
--------
* Ti.UI.OptionDialog markup parser added. Check out this link for a test app and usage: [https://github.com/appcelerator/alloy/tree/master/test/apps/ui/optiondialog](https://github.com/appcelerator/alloy/tree/master/test/apps/ui/optiondialog)
* You can get the Alloy version at runtime now with `Alloy.version`
* Tightened up XML ID restrictions. As an enforced best practice, no reserved JS words as IDs. If you try to, you'll get a compile time error message.
* Revamp of code processing, better organized, more efficient. It's all under the hood, you shouldn't notice, other than compiles might be faster.
* Quick fix to error output in compiler plugin.py
* Some minor cleanup in the test apps
