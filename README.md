# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)
   - [Install Development Tools](#1-install-development-tools)
   - [Create Project Structure](#2-create-project-structure)
   - [Configure package.json](#3-configure-packagejson)
   - [Set Up Webapp Structure](#4-set-up-webapp-structure)
   - [Create Core Files](#5-create-core-files)
   - [Start Development](#6-start-development)
   - [Development Workflow](#7-development-workflow)
   - [Additional Commands](#8-additional-commands)
2. [Application Bootstrapping](#application-bootstrapping)
   - [Bootstrap Configuration](#1-bootstrap-configuration)
   - [Resource Management](#2-resource-management)
   - [Application Initialization](#3-application-initialization)
   - [Bootstrap Process](#4-bootstrap-process)
3. [Controls](#controls)
   - [Control Types](#1-control-types)
   - [Control Usage](#2-control-usage)
   - [Control Properties](#3-control-properties)
   - [Control Lifecycle](#4-control-lifecycle)
   - [Sample Code](#5-sample-code)
4. [XML Views](#xml-views)
   - [View Structure](#1-view-structure)
   - [View Naming Conventions](#2-view-naming-conventions)
   - [View Configuration](#3-view-configuration)
   - [View Elements](#4-view-elements)
   - [View Loading](#5-view-loading)
5. [Controllers](#controllers)
   - [Controller Structure](#1-controller-structure)
   - [Controller Naming Conventions](#2-controller-naming-conventions)
   - [View-Controller Relationship](#3-view-controller-relationship)
   - [Controller Configuration](#4-controller-configuration)
   - [Controller Features](#5-controller-features)
   - [Controller Integration](#6-controller-integration)
6. [Modules](#modules)
   - [Module Definition](#1-module-definition)
   - [Module Usage](#2-module-usage)
   - [Module Types](#3-module-types)
   - [Module Dependencies](#4-module-dependencies)
   - [Module Loading](#5-module-loading)
   - [Module Best Practices](#6-module-best-practices)
   - [MessageToast Example](#7-messagetoast-example)
7. [JSON Model](#json-model)
   - [Model Creation](#1-model-creation)
   - [Model Binding](#2-model-binding)
   - [Model Features](#3-model-features)
   - [Model Operations](#4-model-operations)
   - [Model Validation](#5-model-validation)
   - [Additional Examples](#6-additional-examples)
8. [Resource Bundles](#resource-bundles)
   - [Properties File Creation](#1-properties-file-creation)
   - [Resource Model Setup](#2-resource-model-setup)
   - [Resource Bundle Usage](#3-resource-bundle-usage)
   - [Resource Bundle Features](#4-resource-bundle-features)
   - [Additional Language Support](#5-additional-language-support)
9. [Component Configuration](#component-configuration)
   - [Component Container](#1-component-container)
   - [Component Configuration](#2-component-configuration)
   - [Root View Handling](#3-root-view-handling)
   - [Component Initialization](#4-component-initialization)
   - [Component Features](#5-component-features)
   - [Component Lifecycle](#6-component-lifecycle)
10. [Application Descriptors](#application-descriptors)
    - [Descriptor Structure](#1-descriptor-structure)
    - [Descriptor Sections](#2-descriptor-sections)
    - [Descriptor Features](#3-descriptor-features)
    - [Descriptor Usage](#4-descriptor-usage)
    - [Descriptor Best Practices](#5-descriptor-best-practices)
11. [Pages and Panels](#pages-and-panels)
    - [App Structure with Navigation](#1-app-structure-with-navigation)
    - [Page Navigation Controls](#2-page-navigation-controls)
    - [Navigation Features](#3-navigation-features)
12. [Shell Control](#shell-control)
    - [Shell Structure](#1-shell-structure)
    - [Shell Features](#2-shell-features)
    - [Shell Header](#3-shell-header)
    - [Shell Footer](#4-shell-footer)
    - [Shell Best Practices](#5-shell-best-practices)
13. [Margins and Paddings](#margins-and-paddings)
    - [Margin Classes](#1-margin-classes)
    - [Margin Types](#2-margin-types)
    - [Padding Classes](#3-padding-classes)
    - [Padding Types](#4-padding-types)
    - [Combined Usage](#5-combined-usage)
    - [Best Practices](#6-best-practices)
    - [Width Auto with Margins](#7-width-auto-with-margins)
    - [Width Auto Best Practices](#8-width-auto-best-practices)
    - [Common Width Classes](#9-common-width-classes)
    - [Combined Examples](#10-combined-examples)
14. [Custom CSS and Theme Colors](#custom-css-and-theme-colors)
    - [Theme Colors](#1-theme-colors)
    - [Common Theme Colors](#2-common-theme-colors)
    - [Custom CSS](#3-custom-css)
    - [CSS Variables](#4-css-variables)
    - [Theme-Aware Styling](#5-theme-aware-styling)
    - [Best Practices](#6-best-practices)
15. [Nested Views](#nested-views)
    - [View Structure](#1-view-structure)
    - [Controller Structure](#2-controller-structure)
    - [View Features](#3-view-features)
    - [Model Access](#4-model-access)
    - [Event Communication](#5-event-communication)
    - [Best Practices](#6-best-practices)
16. [Dialogs and Fragments](#dialogs-and-fragments)
    - [Dialog Creation](#1-dialog-creation)
    - [Fragment Types](#2-fragment-types)
    - [Fragment Features](#3-fragment-features)
    - [Dialog Types](#4-dialog-types)
    - [Fragment Usage](#5-fragment-usage)
    - [Best Practices](#6-best-practices)
17. [Fragment Callbacks](#fragment-callbacks)
    - [Callback Structure](#1-callback-structure)
    - [Callback Types](#2-callback-types)
    - [Callback Features](#3-callback-features)
    - [Callback Usage](#4-callback-usage)
    - [Best Practices](#5-best-practices)
18. [Icons](#icons)
    - [Icon Usage](#1-icon-usage)
    - [Icon Categories](#2-icon-categories)
    - [Icon Features](#3-icon-features)
    - [Icon Properties](#4-icon-properties)
    - [Icon Best Practices](#5-icon-best-practices)
19. [Aggregation Binding](#aggregation-binding)
    - [JSON Data Structure](#1-json-data-structure)
    - [Manifest Configuration](#2-manifest-configuration)
    - [i18n Properties](#3-i18n-properties)
    - [View Binding](#4-view-binding)
    - [Controller with Formatter](#5-controller-with-formatter)
    - [Binding Features](#6-binding-features)
    - [Best Practices](#7-best-practices)
20. [Data Types](#data-types)
    - [Basic Data Types](#1-basic-data-types)
    - [Available Data Types](#2-available-data-types)
    - [Format Options](#3-format-options)
    - [Constraints](#4-constraints)
    - [Best Practices](#5-best-practices)
21. [Expression Binding](#expression-binding)
    - [Basic Expression Binding](#1-basic-expression-binding)
    - [Expression Types](#2-expression-types)
    - [Expression Features](#3-expression-features)
    - [Complex Expressions](#4-complex-expressions)
    - [Best Practices](#5-best-practices)
22. [Custom Formatters](#custom-formatters)
    - [i18n Properties](#1-i18n-properties)
    - [Formatter Creation](#2-formatter-creation)
    - [Formatter Usage](#3-formatter-usage)
    - [Formatter Features](#4-formatter-features)
    - [Complex Formatters](#5-complex-formatters)
23. [Filtering](#filtering)
    - [Basic Filtering](#1-basic-filtering)
    - [Filter Types](#2-filter-types)
    - [Filter Operators](#3-filter-operators)
    - [Dynamic Filtering](#4-dynamic-filtering)
    - [Filter Features](#5-filter-features)
    - [Best Practices](#6-best-practices)
24. [Sorting and Grouping](#sorting-and-grouping)
    - [Basic Sorting](#1-basic-sorting)
    - [Sort Types](#2-sort-types)
    - [Sort Features](#3-sort-features)
    - [Grouping](#4-grouping)
    - [Group Features](#5-group-features)
    - [Combined Sorting and Grouping](#6-combined-sorting-and-grouping)
    - [Dynamic Sorting and Grouping](#7-dynamic-sorting-and-grouping)
    - [Best Practices](#8-best-practices)
25. [Remote OData Service](#remote-odata-service)
    - [Service Configuration](#1-service-configuration)
    - [Service Consumption](#2-service-consumption)
    - [Service Features](#3-service-features)
    - [CRUD Operations](#4-crud-operations)
    - [Batch Operations](#5-batch-operations)
    - [Service Binding](#6-service-binding)
    - [Service Parameters](#7-service-parameters)
    - [Best Practices](#8-best-practices)
26. [Mock Server Configuration](#mock-server-configuration)
    - [Mock Server Setup](#1-mock-server-setup)
    - [Mock Data Structure](#2-mock-data-structure)
    - [Metadata Configuration](#3-metadata-configuration)
    - [Mock Server Integration](#4-mock-server-integration)
    - [Mock Server Features](#5-mock-server-features)
    - [Mock Server Methods](#6-mock-server-methods)
    - [Best Practices](#7-best-practices)
27. [Unit Testing with QUnit](#unit-testing-with-qunit)
    - [Test Setup](#1-test-setup)
    - [Controller Testing](#2-controller-testing)
    - [Model Testing](#3-model-testing)
    - [Test Features](#4-test-features)
    - [Test Best Practices](#5-test-best-practices)

## Initial Setup

### 1. Install Development Tools
1. Install Node.js and npm
2. Install UI5 CLI globally:
   ```bash
   npm install -g @ui5/cli
   ```

### 2. Create Project Structure
1. Create a new directory for your project
2. Navigate to the project directory
3. Initialize the project:
   ```bash
   ui5 init
   ```
   - Follow the prompts to configure:
     - Project name
     - Description
     - Framework version
     - Namespace

### 3. Configure package.json
1. Initialize npm:
   ```bash
   npm init -y
   ```
2. Add UI5 dependencies:
   ```bash
   npm install @ui5/cli --save-dev
   ```
3. Add development scripts:
   ```json
   {
     "scripts": {
       "start": "ui5 serve",
       "build": "ui5 build"
     }
   }
   ```

### 4. Set Up Webapp Structure
1. Create webapp directory:
   ```bash
   mkdir webapp
   ```
2. Create required subdirectories:
   ```bash
   mkdir webapp/controller
   mkdir webapp/view
   mkdir webapp/i18n
   ```

### 5. Create Core Files
1. Create index.html in webapp directory:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>SAPUI5 Application</title>
       <script src="resources/sap-ui-core.js"></script>
   </head>
   <body>
       <div id="content"></div>
   </body>
   </html>
   ```

2. Create manifest.json in webapp directory:
   ```json
   {
     "_version": "1.12.0",
     "sap.app": {
       "id": "com.example.app",
       "type": "application",
       "title": "SAPUI5 Application"
     }
   }
   ```

### 6. Start Development
1. Start the development server:
   ```bash
   npm start
   ```
2. Access your application at:
   ```
   http://localhost:8080
   ```

### 7. Development Workflow
- Use `npm start` for development
- Use `npm run build` for production builds
- Use `ui5 add` to add new dependencies
- Use `ui5 use` to switch framework versions

### 8. Additional Commands
- `ui5 add sap.ui.core`: Add core dependencies
- `ui5 add sap.m`: Add mobile controls
- `ui5 build --clean`: Clean build
- `ui5 serve --open`: Open in browser

## Application Bootstrapping

### 1. Bootstrap Configuration
1. Configure bootstrap in index.html:
   ```html
   <script
       id="sap-ui-bootstrap"
       src="resources/sap-ui-core.js"
       data-sap-ui-theme="sap_fiori_3"
       data-sap-ui-resourceroots='{
           "com.example.app": "./"
       }'
       data-sap-ui-compatVersion="edge"
       data-sap-ui-async="true"
       data-sap-ui-frameOptions="allow">
   </script>
   ```

### 2. Resource Management
1. Create i18n properties file:
   ```properties
   # webapp/i18n/i18n.properties
   appTitle=SAPUI5 Application
   ```

### 3. Application Initialization
1. Create index.html with basic structure:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>{{appTitle}}</title>
       <script
           id="sap-ui-bootstrap"
           src="resources/sap-ui-core.js"
           data-sap-ui-theme="sap_fiori_3"
           data-sap-ui-resourceroots='{
               "com.example.app": "./"
           }'
           data-sap-ui-compatVersion="edge"
           data-sap-ui-async="true"
           data-sap-ui-frameOptions="allow">
       </script>
   </head>
   <body class="sapUiBody">
       <div id="content"></div>
   </body>
   </html>
   ```

### 4. Bootstrap Process
1. Framework loads and initializes
2. Resource bundles are loaded
3. Application starts

## Controls

### 1. Control Types
- **sap.m**: Mobile-first controls
- **sap.ui.commons**: Desktop-oriented controls
- **sap.ui.table**: Table controls
- **sap.ui.unified**: Advanced controls

### 2. Control Usage
1. Add control library to index.html:
   ```html
   <script
       id="sap-ui-bootstrap"
       src="resources/sap-ui-core.js"
       data-sap-ui-libs="sap.m,sap.ui.commons"
       data-sap-ui-theme="sap_fiori_3"
       data-sap-ui-resourceroots='{
           "com.example.app": "./"
       }'
       data-sap-ui-compatVersion="edge"
       data-sap-ui-async="true"
       data-sap-ui-frameOptions="allow">
   </script>
   ```

### 3. Control Properties
- **Properties**: Control attributes
- **Events**: User interactions
- **Aggregations**: Child controls
- **Associations**: Related controls

### 4. Control Lifecycle
1. Control initialization
2. Property binding
3. Event handling
4. Control rendering
5. Control destruction

### 5. Sample Code
1. Create index.js in webapp directory:
   ```javascript
   // webapp/index.js
   sap.ui.define([
       "sap/m/Button",
       "sap/m/Text"
   ], function(Button, Text) {
       "use strict";
       
       // Create a button
       var oButton = new Button({
           text: "Click Me"
       });
       
       // Create text
       var oText = new Text({
           text: "Hello SAPUI5!"
       });
       
       // Place controls in the content area
       oButton.placeAt("content");
       oText.placeAt("content");
   });
   ```

2. Update index.html to load index.js:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>SAPUI5 Application</title>
       <script
           id="sap-ui-bootstrap"
           src="resources/sap-ui-core.js"
           data-sap-ui-libs="sap.m,sap.ui.commons"
           data-sap-ui-theme="sap_fiori_3"
           data-sap-ui-resourceroots='{
               "com.example.app": "./"
           }'
           data-sap-ui-compatVersion="edge"
           data-sap-ui-async="true"
           data-sap-ui-frameOptions="allow">
       </script>
       <script src="index.js"></script>
   </head>
   <body class="sapUiBody">
       <div id="content"></div>
   </body>
   </html>
   ```

## XML Views

### 1. View Structure
1. Create XML view file:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <Text text="Hello World"/>
   </mvc:View>
   ```

### 2. View Naming Conventions
- **File Naming**: Must end with `.view.xml`
- **View Name**: Must match the file name without `.view.xml`
- **Namespace**: Must match the application namespace
- **Naming Pattern**: `{namespace}.view.{ViewName}`
- **Restrictions**:
  - No special characters in names
  - Must start with a letter
  - Can only contain letters, numbers, and dots
  - Must be unique within the application
  - View name must match controller name (without .view/.controller)

### 3. View Configuration
1. Add view to manifest.json:
   ```json
   {
     "sap.ui5": {
       "rootView": {
         "viewName": "com.example.app.view.View1",
         "type": "XML",
         "id": "app"
       }
     }
   }
   ```

### 4. View Elements
- **mvc:View**: Root element
- **controllerName**: Controller reference
- **xmlns**: Namespace declarations
- **Controls**: UI elements within view

### 5. View Loading
1. Update index.js to load view:
   ```javascript
   // webapp/index.js
   sap.ui.define([
       "sap/ui/core/mvc/XMLView"
   ], function(XMLView) {
       "use strict";
       
       XMLView.create({
           viewName: "com.example.app.view.View1"
       }).then(function(oView) {
           oView.placeAt("content");
       });
   });
   ```

## Controllers

### 1. Controller Structure
1. Create controller file:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Initialize controller
           }
       });
   });
   ```

### 2. Controller Naming Conventions
- **File Naming**: Must end with `.controller.js`
- **Controller Name**: Must match the file name without `.controller.js`
- **Namespace**: Must match the application namespace
- **Naming Pattern**: `{namespace}.controller.{ControllerName}`
- **Restrictions**:
  - No special characters in names
  - Must start with a letter
  - Can only contain letters, numbers, and dots
  - Must be unique within the application
  - Controller name must match view name (without .controller/.view)

### 3. View-Controller Relationship
- **Naming Correspondence**: View and controller names must match
  - View: `View1.view.xml` → Controller: `View1.controller.js`
  - View: `com.example.app.view.View1` → Controller: `com.example.app.controller.View1`
- **Namespace Consistency**: Both must use the same namespace
- **File Location**: Must be in corresponding directories (view/controller)
- **Manifest Configuration**: Both must be properly referenced in manifest.json

### 4. Controller Configuration
1. Link controller to view in manifest.json:
   ```json
   {
     "sap.ui5": {
       "rootView": {
         "viewName": "com.example.app.view.View1",
         "type": "XML",
         "controllerName": "com.example.app.controller.View1",
         "id": "app"
       }
     }
   }
   ```

### 5. Controller Features
- **Lifecycle Methods**: onInit, onExit, onBeforeRendering, onAfterRendering
- **Event Handlers**: Handle user interactions
- **View Access**: Access view elements
- **Model Management**: Handle data models

### 6. Controller Integration
1. Reference controller in XML view:
   ```xml
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <Button text="Click Me" press="onPress"/>
   </mvc:View>
   ```

## Modules

### 1. Module Definition
1. Create module file:
   ```javascript
   // webapp/model/formatter.js
   sap.ui.define([], function() {
       "use strict";
       return {
           formatDate: function(date) {
               return date ? new Date(date).toLocaleDateString() : "";
           }
       };
   });
   ```

### 2. Module Usage
1. Import module in other files:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "com/example/app/model/formatter"
   ], function(Controller, formatter) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           formatter: formatter,
           // Use formatter in controller
       });
   });
   ```

### 3. Module Types
- **UI5 Modules**: Framework modules (sap.ui.*)
- **Application Modules**: Custom application code
- **Third-party Modules**: External libraries

### 4. Module Dependencies
- **Required Dependencies**: Listed in define array
- **Optional Dependencies**: Loaded on demand
- **Circular Dependencies**: Must be handled carefully

### 5. Module Loading
- **Synchronous Loading**: Standard module loading
- **Asynchronous Loading**: Using async: true
- **Preloading**: Using preload configuration

### 6. Module Best Practices
- Use strict mode
- Clear module naming
- Proper dependency management
- Module encapsulation

### 7. MessageToast Example
1. Import MessageToast module:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "sap/m/MessageToast"
   ], function(Controller, MessageToast) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onPress: function() {
               MessageToast.show("Hello World!");
           }
       });
   });
   ```

2. Use in XML view:
   ```xml
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <Button text="Show Message" press="onPress"/>
   </mvc:View>
   ```

## JSON Model

### 1. Model Creation
1. Create data file:
   ```javascript
   // webapp/model/data.json
   {
       "recipient": {
           "name": "World"
       },
       "greeting": {
           "text": "Hello"
       }
   }
   ```

2. Initialize model in controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "sap/ui/model/json/JSONModel"
   ], function(Controller, JSONModel) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Create model from data.json
               var oModel = new JSONModel("model/data.json");
               this.getView().setModel(oModel);
           },
           
           // Example of model operations
           onUpdateName: function() {
               var oModel = this.getView().getModel();
               oModel.setProperty("/recipient/name", "SAPUI5");
           },
           
           onRefreshData: function() {
               var oModel = this.getView().getModel();
               oModel.refresh(true);
           }
       });
   });
   ```

### 2. Model Binding
1. Bind model in XML view:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap/ui/core/mvc">
       <Text text="{/greeting/text} {/recipient/name}"/>
       <Button text="Update Name" press="onUpdateName"/>
       <Button text="Refresh" press="onRefreshData"/>
   </mvc:View>
   ```

### 3. Model Features
- **Two-way Binding**: Automatic model updates
- **Property Binding**: Single property binding
- **Aggregation Binding**: List binding
- **Expression Binding**: Complex expressions

### 4. Model Operations
- **getProperty**: Get model value
- **setProperty**: Set model value
- **refresh**: Refresh model data
- **setData**: Set entire model data

### 5. Model Validation
- **validateProperty**: Validate single property
- **validateBinding**: Validate binding
- **setValidationMode**: Set validation mode

### 6. Additional Examples
1. List Binding:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <List items="{/items}">
       <items>
           <StandardListItem title="{name}" description="{description}"/>
       </items>
   </List>
   ```

2. Expression Binding:
   ```xml
   <Text text="{= ${/greeting/text} + ' ' + ${/recipient/name}}"/>
   ```

3. Model with Arrays:
   ```javascript
   // webapp/model/data.json
   {
       "items": [
           { "name": "Item 1", "description": "Description 1" },
           { "name": "Item 2", "description": "Description 2" }
       ]
   }
   ```

4. Model with Nested Data:
   ```javascript
   // webapp/model/data.json
   {
       "user": {
           "profile": {
               "name": "John",
               "settings": {
                   "theme": "dark",
                   "language": "en"
               }
           }
       }
   }
   ```

5. Model Operations in Controller:
   ```javascript
   // webapp/controller/View1.controller.js
   onInit: function() {
       var oModel = new JSONModel("model/data.json");
       this.getView().setModel(oModel);
   },
   
   onUpdateUser: function() {
       var oModel = this.getView().getModel();
       oModel.setProperty("/user/profile/name", "Jane");
   },
   
   onUpdateSettings: function() {
       var oModel = this.getView().getModel();
       oModel.setProperty("/user/profile/settings/theme", "light");
   }
   ```

## Resource Bundles

### 1. Properties File Creation
1. Create i18n properties file:
   ```properties
   # webapp/i18n/i18n.properties
   appTitle=SAPUI5 Application
   greetingText=Hello
   recipientText=World
   ```

### 2. Resource Model Setup
1. Initialize resource model in controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "sap/ui/model/resource/ResourceModel"
   ], function(Controller, ResourceModel) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               var i18nModel = new ResourceModel({
                   bundleName: "com.example.app.i18n.i18n"
               });
               this.getView().setModel(i18nModel, "i18n");
           }
       });
   });
   ```

### 3. Resource Bundle Usage
1. Use in XML view:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap/ui/core/mvc">
       <Text text="{i18n>greetingText} {i18n>recipientText}"/>
   </mvc:View>
   ```

### 4. Resource Bundle Features
- **Text Translation**: Support for multiple languages
- **Parameter Replacement**: Dynamic text values
- **Pluralization**: Handle plural forms
- **Fallback Handling**: Default text values

### 5. Additional Language Support
1. Create language-specific properties files:
   ```properties
   # webapp/i18n/i18n_de.properties
   appTitle=SAPUI5 Anwendung
   greetingText=Hallo
   recipientText=Welt
   ```

2. Configure language in manifest.json:
   ```json
   {
     "sap.app": {
       "i18n": {
         "bundleName": "com.example.app.i18n.i18n",
         "supportedLocales": ["", "de"],
         "fallbackLocale": ""
       }
     }
   }
   ```

## Component Configuration

### 1. Component Container
1. Create Component.js as the component container:
   ```javascript
   // webapp/Component.js
   sap.ui.define([
       "sap/ui/core/UIComponent"
   ], function(UIComponent) {
       "use strict";
       return UIComponent.extend("com.example.app.Component", {
           metadata: {
               manifest: "json"
           }
       });
   });
   ```

The Component.js file serves as the component container that:
- Manages the application lifecycle
- Handles the root view creation and display
- Manages application-wide models and resources
- Controls the application's configuration

### 2. Component Configuration
1. Configure in manifest.json:
   ```json
   {
     "sap.app": {
       "id": "com.example.app",
       "type": "application",
       "title": "{{appTitle}}",
       "description": "{{appDescription}}",
       "applicationVersion": {
         "version": "1.0.0"
       }
     },
     "sap.ui": {
       "technology": "UI5",
       "deviceTypes": {
         "desktop": true,
         "tablet": true,
         "phone": true
       }
     },
     "sap.ui5": {
       "rootView": {
         "viewName": "com.example.app.view.View1",
         "type": "XML",
         "id": "app"
       },
       "dependencies": {
         "minUI5Version": "1.76.0",
         "libs": {
           "sap.ui.core": {},
           "sap.m": {},
           "sap.f": {}
         }
       }
     }
   }
   ```

### 3. Root View Handling
1. Component automatically creates root view:
   ```javascript
   // webapp/Component.js
   sap.ui.define([
       "sap/ui/core/UIComponent"
   ], function(UIComponent) {
       "use strict";
       return UIComponent.extend("com.example.app.Component", {
           metadata: {
               manifest: "json"
           },
           init: function() {
               // Call parent init
               UIComponent.prototype.init.apply(this, arguments);
               
               // Create root view
               this.getRootView().then(function(oView) {
                   // Place view in DOM
                   oView.placeAt("content");
               });
           }
       });
   });
   ```

2. Root view configuration options:
   ```json
   {
     "sap.ui5": {
       "rootView": {
         "viewName": "com.example.app.view.View1",
         "type": "XML",
         "id": "app",
         "async": true,
         "controlId": "app",
         "controlAggregation": "pages"
       }
     }
   }
   ```

3. Access root view in controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Get component
               var oComponent = this.getOwnerComponent();
               // Get root view
               var oRootView = oComponent.getRootView();
           }
       });
   });
   ```

### 4. Component Initialization
1. Update index.html:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>{{appTitle}}</title>
       <script
           id="sap-ui-bootstrap"
           src="resources/sap-ui-core.js"
           data-sap-ui-theme="sap_fiori_3"
           data-sap-ui-resourceroots='{
               "com.example.app": "./"
           }'
           data-sap-ui-compatVersion="edge"
           data-sap-ui-async="true"
           data-sap-ui-frameOptions="allow"
           data-sap-ui-oninit="module:sap/ui/core/ComponentSupport">
       </script>
   </head>
   <body class="sapUiBody">
       <div data-sap-ui-component
            data-name="com.example.app"
            data-settings='{"id" : "helloapp"}'
            style="height: 100%">
       </div>
   </body>
   </html>
   ```

### 5. Component Features
- **Metadata**: Component configuration
- **Manifest**: Application descriptor
- **Dependencies**: Required libraries
- **Routing**: Navigation configuration
- **Models**: Data and resource models

### 6. Component Lifecycle
- **init**: Component initialization
- **exit**: Component cleanup
- **beforeRendering**: Before view rendering
- **afterRendering**: After view rendering
  

## Application Descriptors

### 1. Descriptor Structure
1. Create manifest.json:
   ```json
   {
     "_version": "1.12.0",
     "sap.app": {
       "id": "com.example.app",
       "type": "application",
       "title": "{{appTitle}}",
       "description": "{{appDescription}}",
       "applicationVersion": {
         "version": "1.0.0"
       }
     },
     "sap.ui": {
       "technology": "UI5",
       "deviceTypes": {
         "desktop": true,
         "tablet": true,
         "phone": true
       }
     },
     "sap.ui5": {
       "rootView": {
         "viewName": "com.example.app.view.View1",
         "type": "XML",
         "id": "app"
       },
       "dependencies": {
         "minUI5Version": "1.76.0",
         "libs": {
           "sap.ui.core": {},
           "sap.m": {},
           "sap.f": {}
         }
       }
     }
   }
   ```

### 2. Descriptor Sections
- **sap.app**: Application metadata
- **sap.ui**: UI framework settings
- **sap.ui5**: Application-specific settings
- **sap.ui.generic.app**: Fiori application settings

### 3. Descriptor Features
- **Version Control**: Application versioning
- **Dependency Management**: Library dependencies
- **Resource Management**: i18n and models
- **Routing Configuration**: Navigation settings
- **Component Configuration**: Component settings

### 4. Descriptor Usage
1. Reference in Component.js:
   ```javascript
   // webapp/Component.js
   sap.ui.define([
       "sap/ui/core/UIComponent"
   ], function(UIComponent) {
       "use strict";
       return UIComponent.extend("com.example.app.Component", {
           metadata: {
               manifest: "json"
           }
       });
   });
   ```

### 5. Descriptor Best Practices
- Use semantic versioning
- Define clear dependencies
- Configure proper resource roots
- Set appropriate device types
- Include comprehensive metadata


## Pages and Panels

### 1. App Structure with Navigation
1. Create the root App control with navigation:
   ```xml
   <!-- webapp/view/App.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.App"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <App id="app">
           <pages>
               <Page id="page1" title="First Page">
                   <content>
                       <Panel>
                           <Text text="First Page Content"/>
                           <Button 
                               text="Navigate to Second Page"
                               press="onNavigateToSecondPage"/>
                       </Panel>
                   </content>
               </Page>
               <Page id="page2" title="Second Page">
                   <content>
                       <Panel>
                           <Text text="Second Page Content"/>
                           <Button 
                               text="Navigate to First Page"
                               press="onNavigateToFirstPage"/>
                       </Panel>
                   </content>
               </Page>
           </pages>
       </App>
   </mvc:View>
   ```

2. Handle navigation in controller:
   ```javascript
   // webapp/controller/App.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.App", {
           onInit: function() {
               // Initialize app
           },
           onNavigateToSecondPage: function() {
               this.byId("app").to(this.byId("page2"));
           },
           onNavigateToFirstPage: function() {
               this.byId("app").to(this.byId("page1"));
           }
       });
   });
   ```

### 2. Page Navigation Controls
1. Add navigation buttons to pages:
   ```xml
   <Page title="First Page" showNavButton="true" navButtonPress="onNavBack">
       <headerContent>
           <Button 
               icon="sap-icon://action"
               press="onActionPress"/>
       </headerContent>
       <content>
           <Panel>
               <Text text="Page Content"/>
           </Panel>
       </content>
       <footer>
           <Toolbar>
               <ToolbarSpacer/>
               <Button 
                   text="Next"
                   press="onNavigateToSecondPage"/>
           </Toolbar>
       </footer>
   </Page>
   ```

### 3. Navigation Features
- **Back Button**: Built-in navigation
- **Header Actions**: Additional controls
- **Footer Actions**: Bottom toolbar
- **Page Transitions**: Smooth animations
- **Navigation Events**: Press handlers


## Shell Control

### 1. Shell Structure
1. Create a shell control:
   ```xml
   <!-- webapp/view/App.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.App"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Shell>
           <App>
               <pages>
                   <Page title="My Application">
                       <content>
                           <Panel>
                               <Text text="Application Content"/>
                           </Panel>
                       </content>
                   </Page>
               </pages>
           </App>
       </Shell>
   </mvc:View>
   ```

### 2. Shell Features
- **Header**: Application header area
- **Content**: Main application area
- **Footer**: Optional footer area
- **Responsive Design**: Adapts to screen size
- **Branding**: Application branding support

### 3. Shell Header
1. Configure header content:
   ```xml
   <Shell>
       <headerContent>
           <Button 
               icon="sap-icon://action"
               press="onActionPress"/>
       </headerContent>
       <App>
           <!-- App content -->
       </App>
   </Shell>
   ```

### 4. Shell Footer
1. Add footer content:
   ```xml
   <Shell>
       <App>
           <!-- App content -->
       </App>
       <footer>
           <Toolbar>
               <ToolbarSpacer/>
               <Text text="Footer Content"/>
           </Toolbar>
       </footer>
   </Shell>
   ```

### 5. Shell Best Practices
- Use for main application container
- Implement responsive design
- Handle header actions
- Maintain consistent branding
- Manage footer content

## Margins and Paddings

### 1. Margin Classes
1. Apply margins using CSS classes:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Margins and Paddings">
           <content>
               <Panel class="sapUiSmallMargin">
                   <Text text="Small Margin Panel"/>
               </Panel>
               <Panel class="sapUiMediumMargin">
                   <Text text="Medium Margin Panel"/>
               </Panel>
               <Panel class="sapUiLargeMargin">
                   <Text text="Large Margin Panel"/>
               </Panel>
           </content>
       </Page>
   </mvc:View>
   ```

### 2. Margin Types
- **Small Margin**: 0.5rem (8px)
- **Medium Margin**: 1rem (16px)
- **Large Margin**: 2rem (32px)
- **Top Margin**: sapUiTinyMarginTop
- **Bottom Margin**: sapUiTinyMarginBottom
- **Left Margin**: sapUiTinyMarginBegin
- **Right Margin**: sapUiTinyMarginEnd

### 3. Padding Classes
1. Apply padding using CSS classes:
   ```xml
   <Panel class="sapUiSmallPadding">
       <Text text="Small Padding Panel"/>
   </Panel>
   <Panel class="sapUiMediumPadding">
       <Text text="Medium Padding Panel"/>
   </Panel>
   <Panel class="sapUiLargePadding">
       <Text text="Large Padding Panel"/>
   </Panel>
   ```

### 4. Padding Types
- **Small Padding**: 0.5rem (8px)
- **Medium Padding**: 1rem (16px)
- **Large Padding**: 2rem (32px)
- **Top Padding**: sapUiTinyPaddingTop
- **Bottom Padding**: sapUiTinyPaddingBottom
- **Left Padding**: sapUiTinyPaddingBegin
- **Right Padding**: sapUiTinyPaddingEnd

### 5. Combined Usage
1. Apply both margin and padding:
   ```xml
   <Panel class="sapUiSmallMargin sapUiMediumPadding">
       <Text text="Combined Margin and Padding"/>
   </Panel>
   ```

### 6. Best Practices
- Use consistent spacing
- Follow responsive design
- Maintain visual hierarchy
- Consider content density
- Use appropriate sizes

### 7. Width Auto with Margins
1. Combine width auto with margins:
   ```xml
   <Panel class="sapUiSmallMargin sapUiWidthAuto">
       <Text text="Auto Width with Small Margin"/>
   </Panel>
   ```

2. Multiple controls with auto width:
   ```xml
   <HBox class="sapUiSmallMargin">
       <Button 
           text="Button 1"
           class="sapUiWidthAuto"/>
       <Button 
           text="Button 2"
           class="sapUiWidthAuto"/>
   </HBox>
   ```

### 8. Width Auto Best Practices
- Use for dynamic content
- Combine with appropriate margins
- Consider container width
- Handle text overflow
- Maintain responsive design

### 9. Common Width Classes
- **sapUiWidthAuto**: Automatic width
- **sapUiWidthFull**: Full width
- **sapUiWidthHalf**: Half width
- **sapUiWidthQuarter**: Quarter width
- **sapUiWidthThreeQuarters**: Three quarters width

### 10. Combined Examples
1. Complex layout with auto width:
   ```xml
   <VBox class="sapUiSmallMargin">
       <HBox class="sapUiSmallMarginBottom">
           <Button 
               text="Short Button"
               class="sapUiWidthAuto"/>
           <Button 
               text="Longer Button Text"
               class="sapUiWidthAuto"/>
       </HBox>
       <Panel class="sapUiWidthAuto">
           <Text text="Auto Width Panel with Content"/>
       </Panel>
   </VBox>
   ```

2. Responsive layout:
   ```xml
   <FlexBox class="sapUiSmallMargin">
       <items>
           <Button 
               text="Button 1"
               class="sapUiWidthAuto"/>
           <Button 
               text="Button 2"
               class="sapUiWidthAuto"/>
           <Button 
               text="Button 3"
               class="sapUiWidthAuto"/>
       </items>
   </FlexBox>
   ```

## Custom CSS and Theme Colors

### 1. Theme Colors
1. Use SAPUI5 theme colors:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Theme Colors">
           <content>
               <Panel class="sapUiGlobalBackgroundColor">
                   <Text text="Global Background"/>
               </Panel>
               <Panel class="sapUiHighlightColor">
                   <Text text="Highlight Color"/>
               </Panel>
               <Panel class="sapUiBaseColor">
                   <Text text="Base Color"/>
               </Panel>
           </content>
       </Page>
   </mvc:View>
   ```

### 2. Common Theme Colors
- **sapUiGlobalBackgroundColor**: Global background
- **sapUiHighlightColor**: Highlight color
- **sapUiBaseColor**: Base color
- **sapUiBrandColor**: Brand color
- **sapUiCriticalColor**: Critical color
- **sapUiPositiveColor**: Positive color
- **sapUiNegativeColor**: Negative color
- **sapUiNeutralColor**: Neutral color

### 3. Custom CSS
1. Create custom CSS file:
   ```css
   /* webapp/css/style.css */
   .customBackground {
       background-color: var(--sapUiGlobalBackgroundColor);
   }
   
   .customBorder {
       border: 1px solid var(--sapUiBaseColor);
   }
   
   .customText {
       color: var(--sapUiTextColor);
   }
   ```

2. Import CSS in manifest.json:
   ```json
   {
     "sap.ui5": {
       "resources": {
         "css": [
           "css/style.css"
         ]
       }
     }
   }
   ```

### 4. CSS Variables
1. Use CSS variables:
   ```css
   .customStyle {
       background-color: var(--sapUiGlobalBackgroundColor);
       border-color: var(--sapUiBaseColor);
       color: var(--sapUiTextColor);
   }
   ```

### 5. Theme-Aware Styling
1. Create theme-aware components:
   ```xml
   <Panel class="customPanel">
       <Text text="Theme-Aware Panel"/>
   </Panel>
   ```

2. Define theme-aware CSS:
   ```css
   .customPanel {
       background-color: var(--sapUiGlobalBackgroundColor);
       border: 1px solid var(--sapUiBaseColor);
       padding: var(--sapUiContentPadding);
   }
   ```

### 6. Best Practices
- Use theme variables
- Maintain consistency
- Consider high contrast
- Support RTL languages
- Test in different themes

## Nested Views

### 1. View Structure
1. Create nested views:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Parent View">
           <content>
               <mvc:View
                   viewName="com.example.app.view.NestedView"
                   controllerName="com.example.app.controller.NestedController"/>
           </content>
       </Page>
   </mvc:View>
   ```

2. Create nested view file:
   ```xml
   <!-- webapp/view/NestedView.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.NestedController"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Panel>
           <Text text="Nested View Content"/>
       </Panel>
   </mvc:View>
   ```

### 2. Controller Structure
1. Parent controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Initialize parent view
           }
       });
   });
   ```

2. Nested controller:
   ```javascript
   // webapp/controller/NestedController.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.NestedController", {
           onInit: function() {
               // Initialize nested view
           }
       });
   });
   ```

### 3. View Features
- **Independent Controllers**: Each view has its own controller
- **Model Inheritance**: Nested views inherit parent models
- **Event Handling**: Separate event handlers
- **View Lifecycle**: Independent lifecycle management
- **Resource Access**: Access to parent resources

### 4. Model Access
1. Access models in nested controller:
   ```javascript
   onInit: function() {
       var oParentModel = this.getOwnerComponent().getModel();
       // Use parent model
   }
   ```

### 5. Event Communication
1. Parent to child communication:
   ```javascript
   // Parent controller
   onParentAction: function() {
       var oNestedView = this.byId("nestedView");
       var oNestedController = oNestedView.getController();
       oNestedController.handleParentAction();
   }
   ```

2. Child to parent communication:
   ```javascript
   // Nested controller
   onChildAction: function() {
       var oParentController = this.getView().getParent().getController();
       oParentController.handleChildAction();
   }
   ```

### 6. Best Practices
- Use meaningful view names
- Maintain clear hierarchy
- Handle model inheritance
- Manage event communication
- Consider view lifecycle

## Dialogs and Fragments

### 1. Dialog Creation
1. Create a dialog fragment:
   ```xml
   <!-- webapp/fragment/Dialog.fragment.xml -->
   <core:FragmentDefinition
       xmlns="sap.m"
       xmlns:core="sap.ui.core">
       <Dialog
           title="My Dialog"
           type="Message"
           state="Warning">
           <content>
               <Text text="Dialog Content"/>
           </content>
           <buttons>
               <Button
                   text="OK"
                   press="onDialogOK"/>
               <Button
                   text="Cancel"
                   press="onDialogCancel"/>
           </buttons>
       </Dialog>
   </core:FragmentDefinition>
   ```

2. Open dialog in controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onOpenDialog: function() {
               if (!this._oDialog) {
                   this._oDialog = sap.ui.xmlfragment(
                       "com.example.app.fragment.Dialog",
                       this
                   );
               }
               this._oDialog.open();
           },
           onDialogOK: function() {
               this._oDialog.close();
           },
           onDialogCancel: function() {
               this._oDialog.close();
           }
       });
   });
   ```

### 2. Fragment Types
1. **XML Fragment**:
   ```xml
   <!-- webapp/fragment/Form.fragment.xml -->
   <core:FragmentDefinition
       xmlns="sap.m"
       xmlns:core="sap.ui.core">
       <SimpleForm>
           <Label text="Name"/>
           <Input value="{/name}"/>
       </SimpleForm>
   </core:FragmentDefinition>
   ```

2. **JS Fragment**:
   ```javascript
   // webapp/fragment/Form.fragment.js
   sap.ui.define([
       "sap/ui/core/Fragment"
   ], function(Fragment) {
       "use strict";
       return {
           createContent: function(oController) {
               return new sap.m.SimpleForm({
                   content: [
                       new sap.m.Label({text: "Name"}),
                       new sap.m.Input({value: "{/name}"})
                   ]
               });
           }
       };
   });
   ```

### 3. Fragment Features
- **Reusability**: Share UI parts
- **Controller Binding**: Event handling
- **Model Binding**: Data binding
- **Lifecycle Management**: Creation/destruction
- **Resource Loading**: Dynamic loading

### 4. Dialog Types
1. **Message Dialog**:
   ```xml
   <Dialog
       type="Message"
       state="Warning">
       <content>
           <Text text="Warning Message"/>
       </content>
   </Dialog>
   ```

2. **Input Dialog**:
   ```xml
   <Dialog
       title="Input Dialog">
       <content>
           <Input value="{/inputValue}"/>
       </content>
   </Dialog>
   ```

### 5. Fragment Usage
1. Load fragment:
   ```javascript
   Fragment.load({
       name: "com.example.app.fragment.Form",
       controller: this
   }).then(function(oFragment) {
       this.getView().addDependent(oFragment);
   }.bind(this));
   ```

### 6. Best Practices
- Use fragments for reusable UI
- Handle dialog lifecycle
- Manage fragment instances
- Clean up resources
- Consider performance

## Fragment Callbacks

### 1. Callback Structure
1. Define fragment callbacks:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onOpenDialog: function() {
               Fragment.load({
                   name: "com.example.app.fragment.Dialog",
                   controller: this,
                   onBeforeRendering: this.onBeforeRendering,
                   onAfterRendering: this.onAfterRendering,
                   onExit: this.onExit
               }).then(function(oFragment) {
                   this.getView().addDependent(oFragment);
                   oFragment.open();
               }.bind(this));
           }
       });
   });
   ```

### 2. Callback Types
1. **onBeforeRendering**:
   ```javascript
   onBeforeRendering: function() {
       // Called before fragment is rendered
       console.log("Before rendering");
   }
   ```

2. **onAfterRendering**:
   ```javascript
   onAfterRendering: function() {
       // Called after fragment is rendered
       console.log("After rendering");
   }
   ```

3. **onExit**:
   ```javascript
   onExit: function() {
       // Called when fragment is destroyed
       console.log("Fragment destroyed");
   }
   ```

### 3. Callback Features
- **Lifecycle Management**: Control fragment lifecycle
- **Resource Cleanup**: Proper cleanup on exit
- **Initialization**: Setup before rendering
- **Finalization**: Cleanup after rendering
- **Error Handling**: Handle rendering errors

### 4. Callback Usage
1. Complete callback example:
   ```javascript
   Fragment.load({
       name: "com.example.app.fragment.Dialog",
       controller: this,
       onBeforeRendering: function() {
           // Setup before rendering
           this._setupData();
       },
       onAfterRendering: function() {
           // Cleanup after rendering
           this._finalizeSetup();
       },
       onExit: function() {
           // Cleanup on destroy
           this._cleanupResources();
       }
   });
   ```

### 5. Best Practices
- Implement proper cleanup
- Handle errors gracefully
- Manage resources efficiently
- Use meaningful callback names
- Document callback purposes


## Icons

### 1. Icon Usage
1. Use icons in controls:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Icons">
           <content>
               <Button 
                   icon="sap-icon://home"
                   text="Home"/>
               <Button 
                   icon="sap-icon://settings"
                   text="Settings"/>
           </content>
       </Page>
   </mvc:View>
   ```

### 2. Icon Categories
1. **Action Icons**:
   ```xml
   <Button icon="sap-icon://add"/>
   <Button icon="sap-icon://delete"/>
   <Button icon="sap-icon://edit"/>
   ```

2. **Navigation Icons**:
   ```xml
   <Button icon="sap-icon://arrow-left"/>
   <Button icon="sap-icon://arrow-right"/>
   <Button icon="sap-icon://menu"/>
   ```

3. **Status Icons**:
   ```xml
   <ObjectStatus
       icon="sap-icon://status-positive"
       text="Success"/>
   <ObjectStatus
       icon="sap-icon://status-negative"
       text="Error"/>
   ```

### 3. Icon Features
- **Built-in Icons**: SAPUI5 icon library
- **Custom Icons**: Custom icon support
- **Icon Sizes**: Different size options
- **Icon Colors**: Theme-aware colors
- **Icon States**: Active/inactive states

### 4. Icon Properties
1. Configure icon properties:
   ```xml
   <Button 
       icon="sap-icon://home"
       iconDensityAware="true"
       iconFirst="true"
       tooltip="Home"/>
   ```

### 5. Icon Best Practices
- Use meaningful icons
- Consider accessibility
- Maintain consistency
- Handle icon states
- Provide tooltips

## Aggregation Binding

### 1. JSON Data Structure
1. Create JSON model data:
   ```javascript
   // webapp/model/Invoices.json
   {
       "Invoices": [
           {
               "ProductName": "Pineapple",
               "Quantity": 21,
               "ExtendedPrice": 87.2,
               "ShipperName": "Fun Inc.",
               "ShippedDate": "2015-04-01T00:00:00",
               "Status": "A"
           },
           {
               "ProductName": "Milk",
               "Quantity": 4,
               "ExtendedPrice": 10,
               "ShipperName": "ACME",
               "ShippedDate": "2015-02-18T00:00:00",
               "Status": "B"
           },
           {
               "ProductName": "Canned Beans",
               "Quantity": 3,
               "ExtendedPrice": 6.85,
               "ShipperName": "ACME",
               "ShippedDate": "2015-03-02T00:00:00",
               "Status": "B"
           },
           {
               "ProductName": "Salad",
               "Quantity": 2,
               "ExtendedPrice": 8.8,
               "ShipperName": "ACME",
               "ShippedDate": "2015-04-12T00:00:00",
               "Status": "C"
           },
           {
               "ProductName": "Bread",
               "Quantity": 1,
               "ExtendedPrice": 2.71,
               "ShipperName": "Fun Inc.",
               "ShippedDate": "2015-01-27T00:00:00",
               "Status": "A"
           }
       ]
   }
   ```

### 2. Manifest Configuration
1. Configure models in manifest.json:
   ```json
   {
     "sap.ui5": {
       "models": {
         "i18n": {
           "type": "sap.ui.model.resource.ResourceModel",
           "settings": {
             "bundleName": "ui5.walkthrough.i18n.i18n",
             "supportedLocales": [
               ""
             ],
             "fallbackLocale": ""
           }
         },
         "invoice": {
           "type": "sap.ui.model.json.JSONModel",
           "uri": "model/Invoices.json"
         }
       }
     }
   }
   ```

### 3. i18n Properties
1. Create i18n properties file:
   ```properties
   # webapp/i18n/i18n.properties
   # App Descriptor
   appTitle=Hello World
   appDescription=A simple walkthrough app that explains the most important concepts of SAPUI5

   # Hello Panel
   showHelloButtonText=Say Hello
   helloMsg=Hello {0}
   homePageTitle=Walkthrough
   helloPanelTitle=Hello World
   openDialogButtonText=Say Hello With Dialog
   dialogCloseButtonText=Ok

   # Invoice List
   invoiceListTitle=Invoices
   ```

### 4. View Binding
1. Create InvoiceList view:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{invoice>/Invoices}">
           <items>
               <ObjectListItem
                   title="{invoice>Quantity} x {invoice>ProductName}"
                   number="{
                       parts: [{path: 'invoice>ExtendedPrice'}],
                       type: 'sap.ui.model.type.Currency',
                       formatOptions: {showMeasure: false}
                   }"
                   numberUnit="{invoice>ExtendedPrice}"
                   numberState="{= ${invoice>Status} === 'A' ? 'Success' : ${invoice>Status} === 'B' ? 'Warning' : 'Error'}"
                   attributes="{
                       path: 'invoice>ShipperName',
                       template: new sap.m.Text({
                           text: '{invoice>ShipperName}'
                       })
                   }"
                   status="{
                       path: 'invoice>ShippedDate',
                       formatter: '.formatter.statusDate'
                   }"/>
           </items>
       </List>
   </mvc:View>
   ```

### 5. Controller with Formatter
1. Add formatter to controller:
   ```javascript
   // webapp/controller/InvoiceList.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.InvoiceList", {
           onInit: function() {
               // Model is initialized by manifest.json
           },
           formatter: {
               statusDate: function(date) {
                   if (date) {
                       var oDate = new Date(date);
                       return oDate.toLocaleDateString();
                   }
                   return "";
               }
           }
       });
   });
   ```

### 6. Binding Features
- **Path Binding**: `{invoice>/Invoices}`
- **Template**: ObjectListItem
- **Property Binding**: 
  - `{invoice>Quantity}`, `{invoice>ProductName}`
  - `{invoice>ExtendedPrice}`
  - `{invoice>ShipperName}`
  - `{invoice>ShippedDate}`
  - `{invoice>Status}`
- **Number Formatting**: Currency formatting
- **Status Colors**: Based on Status value
- **Date Formatting**: Using formatter
- **i18n Support**: `{i18n>invoiceListTitle}`
- **Responsive Design**: `sapUiResponsiveMargin`

### 7. Best Practices
- Use appropriate templates
- Handle empty states
- Implement proper sorting
- Manage data updates
- Consider performance

## Data Types

### 1. Basic Data Types
1. Use in view:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{invoice>/Invoices}">
           <items>
               <ObjectListItem
                   title="{invoice>Quantity} x {invoice>ProductName}"
                   number="{
                       parts: [{path: 'invoice>ExtendedPrice'}],
                       type: 'sap.ui.model.type.Currency',
                       formatOptions: {showMeasure: false}
                   }"
                   numberUnit="{invoice>ExtendedPrice}"
                   numberState="{= ${invoice>Status} === 'A' ? 'Success' : ${invoice>Status} === 'B' ? 'Warning' : 'Error'}"
                   attributes="{
                       path: 'invoice>ShipperName',
                       template: new sap.m.Text({
                           text: '{invoice>ShipperName}'
                       })
                   }"
                   status="{
                       path: 'invoice>ShippedDate',
                       type: 'sap.ui.model.type.Date',
                       formatOptions: {
                           style: 'medium'
                       }
                   }"/>
           </items>
       </List>
   </mvc:View>
   ```

### 2. Available Data Types
1. **String Type**:
   ```xml
   <Text text="{
       path: 'invoice>ProductName',
       type: 'sap.ui.model.type.String'
   }"/>
   ```

2. **Number Type**:
   ```xml
   <Text text="{
       path: 'invoice>Quantity',
       type: 'sap.ui.model.type.Integer'
   }"/>
   ```

3. **Currency Type**:
   ```xml
   <Text text="{
       path: 'invoice>ExtendedPrice',
       type: 'sap.ui.model.type.Currency',
       formatOptions: {
           showMeasure: false
       }
   }"/>
   ```

4. **Date Type**:
   ```xml
   <Text text="{
       path: 'invoice>ShippedDate',
       type: 'sap.ui.model.type.Date',
       formatOptions: {
           style: 'medium'
       }
   }"/>
   ```

5. **Boolean Type**:
   ```xml
   <Text text="{
       path: 'invoice>Status',
       type: 'sap.ui.model.type.Boolean',
       formatOptions: {
           trueValue: 'Active',
           falseValue: 'Inactive'
       }
   }"/>
   ```

### 3. Format Options
1. **Currency Format**:
   ```xml
   <Text text="{
       path: 'invoice>ExtendedPrice',
       type: 'sap.ui.model.type.Currency',
       formatOptions: {
           showMeasure: false,
           decimals: 2,
           currencyCode: 'USD'
       }
   }"/>
   ```

2. **Date Format**:
   ```xml
   <Text text="{
       path: 'invoice>ShippedDate',
       type: 'sap.ui.model.type.Date',
       formatOptions: {
           style: 'medium',
           strictParsing: true
       }
   }"/>
   ```

### 4. Constraints
1. **Number Constraints**:
   ```xml
   <Text text="{
       path: 'invoice>Quantity',
       type: 'sap.ui.model.type.Integer',
       constraints: {
           minimum: 0,
           maximum: 100
       }
   }"/>
   ```

2. **String Constraints**:
   ```xml
   <Text text="{
       path: 'invoice>ProductName',
       type: 'sap.ui.model.type.String',
       constraints: {
           minLength: 3,
           maxLength: 50
       }
   }"/>
   ```

### 5. Best Practices
- Use appropriate data types
- Set proper constraints
- Configure format options
- Handle validation
- Consider localization

## Expression Binding

### 1. Basic Expression Binding
1. Use in view:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{invoice>/Invoices}">
           <items>
               <ObjectListItem
                   title="{invoice>Quantity} x {invoice>ProductName}"
                   number="{
                       parts: [{path: 'invoice>ExtendedPrice'}],
                       type: 'sap.ui.model.type.Currency',
                       formatOptions: {showMeasure: false}
                   }"
                   numberUnit="{invoice>ExtendedPrice}"
                   numberState="{= ${invoice>Status} === 'A' ? 'Success' : ${invoice>Status} === 'B' ? 'Warning' : 'Error'}"
                   attributes="{
                       path: 'invoice>ShipperName',
                       template: new sap.m.Text({
                           text: '{invoice>ShipperName}'
                       })
                   }"
                   status="{
                       path: 'invoice>ShippedDate',
                       type: 'sap.ui.model.type.Date',
                       formatOptions: {
                           style: 'medium'
                       }
                   }"/>
           </items>
       </List>
   </mvc:View>
   ```

### 2. Expression Types
1. **Conditional Expression**:
   ```xml
   <Text text="{= ${invoice>Status} === 'A' ? 'Active' : 'Inactive'}"/>
   ```

2. **Mathematical Expression**:
   ```xml
   <Text text="{= ${invoice>Quantity} * ${invoice>ExtendedPrice}}"/>
   ```

3. **String Concatenation**:
   ```xml
   <Text text="{= ${invoice>ProductName} + ' - ' + ${invoice>ShipperName}}"/>
   ```

4. **Logical Expression**:
   ```xml
   <Text text="{= ${invoice>Quantity} > 10 && ${invoice>Status} === 'A' ? 'High Stock' : 'Low Stock'}"/>
   ```

### 3. Expression Features
- **Conditional Logic**: Ternary operators
- **Mathematical Operations**: Basic arithmetic
- **String Operations**: Concatenation
- **Logical Operations**: AND, OR, NOT
- **Comparison**: Equal, Not Equal, Greater Than, Less Than

### 4. Complex Expressions
1. **Nested Conditions**:
   ```xml
   <Text text="{= ${invoice>Status} === 'A' ? 'Active' : ${invoice>Status} === 'B' ? 'Pending' : 'Inactive'}"/>
   ```

2. **Multiple Operations**:
   ```xml
   <Text text="{= (${invoice>Quantity} * ${invoice>ExtendedPrice}) > 100 ? 'High Value' : 'Low Value'}"/>
   ```

3. **Combined Operations**:
   ```xml
   <Text text="{= ${invoice>Status} === 'A' && ${invoice>Quantity} > 10 ? 'In Stock' : 'Out of Stock'}"/>
   ```

### 5. Best Practices
- Use clear expressions
- Handle null values
- Consider performance
- Test edge cases
- Document complex logic

## Custom Formatters

### 1. i18n Properties
1. Add status text to i18n properties:
   ```properties
   # webapp/i18n/i18n.properties
   # App Descriptor
   appTitle=Hello World
   appDescription=A simple walkthrough app that explains the most important concepts of SAPUI5

   # Hello Panel
   showHelloButtonText=Say Hello
   helloMsg=Hello {0}
   homePageTitle=Walkthrough
   helloPanelTitle=Hello World
   openDialogButtonText=Say Hello With Dialog
   dialogCloseButtonText=Ok

   # Invoice List
   invoiceListTitle=Invoices
   invoiceStatusA=New
   invoiceStatusB=In Progress
   invoiceStatusC=Done
   ```

### 2. Formatter Creation
1. Create formatter file:
   ```javascript
   // webapp/model/formatter.js
   sap.ui.define([], function() {
       "use strict";
       return {
           statusText: function(sStatus) {
               var oResourceBundle = this.getView().getModel("i18n").getResourceBundle();
               switch (sStatus) {
                   case "A":
                       return oResourceBundle.getText("invoiceStatusA");
                   case "B":
                       return oResourceBundle.getText("invoiceStatusB");
                   case "C":
                       return oResourceBundle.getText("invoiceStatusC");
                   default:
                       return "";
               }
           },
           formatStatus: function(sStatus) {
               switch (sStatus) {
                   case "A":
                       return "Success";
                   case "B":
                       return "Warning";
                   case "C":
                       return "Error";
                   default:
                       return "None";
               }
           },
           formatDate: function(sDate) {
               if (!sDate) return "";
               var oDate = new Date(sDate);
               return oDate.toLocaleDateString();
           },
           formatPrice: function(fPrice) {
               if (!fPrice) return "0.00";
               return fPrice.toFixed(2);
           }
       };
   });
   ```

### 3. Formatter Usage
1. Use in view with core:require:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.InvoiceList"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns:core="sap.ui.core">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{invoice>/Invoices}">
           <items>
               <ObjectListItem>
                   <firstStatus>
                       <ObjectStatus
                           core:require="{
                               Formatter: 'ui5/walkthrough/model/formatter'
                           }"
                           text="{
                               path: 'invoice>Status',
                               formatter: 'Formatter.statusText.bind($controller)'
                           }"/>
                   </firstStatus>
                   <attributes>
                       <ObjectAttribute
                           title="{i18n>invoiceQuantity}"
                           text="{invoice>Quantity}"/>
                   </attributes>
               </ObjectListItem>
           </items>
       </List>
   </mvc:View>
   ```

### 4. Formatter Features
- **Status Text**: i18n-based status text
- **Status State**: Visual state indicators
- **Date Formatting**: Localized date display
- **Price Formatting**: Currency formatting
- **Resource Bundle**: i18n integration

### 5. Complex Formatters
1. **Multiple Parameters**:
   ```javascript
   formatPriceWithCurrency: function(fPrice, sCurrency) {
       if (!fPrice) return "0.00";
       return fPrice.toFixed(2) + " " + (sCurrency || "USD");
   }
   ```

2. **Conditional Logic**:
   ```javascript
   formatStockStatus: function(iQuantity, sStatus) {
       if (sStatus === "A") {
           return iQuantity > 10 ? "In Stock" : "Low Stock";
       }
       return "Out of Stock";
   }
   ```

3. **Array Handling**:
   ```javascript
   formatCategories: function(aCategories) {
       if (!aCategories || !aCategories.length) return "";
       return aCategories.join(", ");
   }
   ```

## Filtering

### 1. Basic Filtering
1. Create filter in view:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.InvoiceList"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{
               path: '/Invoices',
               filters: [
                   {
                       path: 'Status',
                       operator: 'EQ',
                       value1: 'A'
                   }
               ]
           }">
           <items>
               <ObjectListItem
                   title="{ProductName}"
                   number="{ExtendedPrice}"/>
           </items>
       </List>
   </mvc:View>
   ```

### 2. Filter Types
1. **Single Filter**:
   ```xml
   <List items="{
       path: '/Invoices',
       filters: [
           {
               path: 'Status',
               operator: 'EQ',
               value1: 'A'
           }
       ]
   }">
   ```

2. **Multiple Filters**:
   ```xml
   <List items="{
       path: '/Invoices',
       filters: [
           {
               path: 'Status',
               operator: 'EQ',
               value1: 'A'
           },
           {
               path: 'ExtendedPrice',
               operator: 'GT',
               value1: 10
           }
       ]
   }">
   ```

3. **Complex Filter**:
   ```xml
   <List items="{
       path: '/Invoices',
       filters: [
           {
               and: true,
               filters: [
                   {
                       path: 'Status',
                       operator: 'EQ',
                       value1: 'A'
                   },
                   {
                       path: 'ExtendedPrice',
                       operator: 'GT',
                       value1: 10
                   }
               ]
           }
       ]
   }">
   ```

### 3. Filter Operators
- **EQ**: Equal to
- **NE**: Not equal to
- **GT**: Greater than
- **GE**: Greater than or equal to
- **LT**: Less than
- **LE**: Less than or equal to
- **Contains**: Contains
- **StartsWith**: Starts with
- **EndsWith**: Ends with
- **Between**: Between two values

### 4. Dynamic Filtering
1. Create filter in controller:
   ```javascript
   // webapp/controller/InvoiceList.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.InvoiceList", {
           onInit: function() {
               // Initialize controller
           },
           onFilterStatus: function(oEvent) {
               var sQuery = oEvent.getParameter("query");
               var oList = this.getView().byId("invoiceList");
               var oBinding = oList.getBinding("items");
               var aFilters = [];
               
               if (sQuery) {
                   aFilters.push(new sap.ui.model.Filter("Status", sap.ui.model.FilterOperator.EQ, sQuery));
               }
               
               oBinding.filter(aFilters);
           }
       });
   });
   ```

### 5. Filter Features
- **Single Value**: Filter by one value
- **Multiple Values**: Filter by multiple values
- **Range Filtering**: Filter by ranges
- **Text Search**: Filter by text
- **Dynamic Updates**: Update filters at runtime

### 6. Best Practices
- Use appropriate operators
- Consider performance
- Handle empty states
- Test edge cases
- Document filter logic

## Sorting and Grouping

### 1. Basic Sorting
1. Create sorted list in view:
   ```xml
   <!-- webapp/view/InvoiceList.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.InvoiceList"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           headerText="{i18n>invoiceListTitle}"
           class="sapUiResponsiveMargin"
           width="auto"
           items="{
               path: '/Invoices',
               sorter: {
                   path: 'ProductName',
                   descending: false
               }
           }">
           <items>
               <ObjectListItem
                   title="{ProductName}"
                   number="{ExtendedPrice}"/>
           </items>
       </List>
   </mvc:View>
   ```

### 2. Sort Types
1. **Single Sort**:
   ```xml
   <List items="{
       path: '/Invoices',
       sorter: {
           path: 'ProductName',
           descending: false
       }
   }">
   ```

2. **Multiple Sort**:
   ```xml
   <List items="{
       path: '/Invoices',
       sorter: [
           {
               path: 'Status',
               descending: false
           },
           {
               path: 'ProductName',
               descending: false
           }
       ]
   }">
   ```

3. **Custom Sort**:
   ```javascript
   // webapp/controller/InvoiceList.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.InvoiceList", {
           onInit: function() {
               // Initialize controller
           },
           customSort: function(a, b) {
               return a.ProductName.localeCompare(b.ProductName);
           }
       });
   });
   ```

### 3. Sort Features
- **Ascending/Descending**: Control sort direction
- **Multiple Fields**: Sort by multiple properties
- **Custom Sorting**: Implement custom sort logic
- **Dynamic Sorting**: Change sort at runtime
- **Case Sensitivity**: Control case sensitivity

### 4. Grouping
1. **Basic Grouping**:
   ```xml
   <List items="{
       path: '/Invoices',
       groupHeaderFactory: '.createGroupHeader',
       sorter: {
           group: true,
           path: 'Status'
       }
   }">
   ```

2. **Group Header Factory**:
   ```javascript
   // webapp/controller/InvoiceList.controller.js
   createGroupHeader: function(oGroup) {
       return new sap.m.GroupHeaderListItem({
           title: oGroup.key,
           count: oGroup.items.length
       });
   }
   ```

### 5. Group Features
- **Group Headers**: Custom group header display
- **Group Count**: Show items in group
- **Group Sorting**: Sort groups and items
- **Collapsible Groups**: Expand/collapse groups
- **Group Functions**: Custom group functions

### 6. Combined Sorting and Grouping
1. **Sort and Group Together**:
   ```xml
   <List items="{
       path: '/Invoices',
       groupHeaderFactory: '.createGroupHeader',
       sorter: [
           {
               group: true,
               path: 'Status'
           },
           {
               path: 'ProductName',
               descending: false
           }
       ]
   }">
   ```

### 7. Dynamic Sorting and Grouping
1. **Runtime Changes**:
   ```javascript
   // webapp/controller/InvoiceList.controller.js
   onSortChange: function(oEvent) {
       var sPath = oEvent.getParameter("selectedItem").getKey();
       var oList = this.getView().byId("invoiceList");
       var oBinding = oList.getBinding("items");
       
       oBinding.sort(new sap.ui.model.Sorter(sPath, false));
   },
   
   onGroupChange: function(oEvent) {
       var sPath = oEvent.getParameter("selectedItem").getKey();
       var oList = this.getView().byId("invoiceList");
       var oBinding = oList.getBinding("items");
       
       oBinding.sort(new sap.ui.model.Sorter(sPath, false, true));
   }
   ```

### 8. Best Practices
- Use appropriate sort fields
- Consider performance impact
- Handle empty states
- Test with large datasets
- Document sort/group logic
- Consider user experience
- Implement proper error handling
- Use meaningful group headers
- Maintain consistent sorting
- Consider accessibility

## Remote OData Service

### 1. Service Configuration
1. Configure OData service in manifest.json:
   ```json
   {
     "sap.app": {
       "dataSources": {
         "mainService": {
           "uri": "/sap/opu/odata/sap/ZDEMO_SERVICE/",
           "type": "OData",
           "version": "2.0",
           "settings": {
             "odataVersion": "2.0",
             "localUri": "localService/metadata.xml"
           }
         }
       }
     },
     "sap.ui5": {
       "models": {
         "": {
           "dataSource": "mainService",
           "type": "sap.ui.model.odata.v2.ODataModel",
           "settings": {
             "defaultOperationMode": "Server",
             "defaultBindingMode": "TwoWay",
             "defaultCountMode": "Request"
           }
         }
       }
     }
   }
   ```

### 2. Service Consumption
1. Create service consumption in controller:
   ```javascript
   // webapp/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "sap/ui/model/odata/v2/ODataModel"
   ], function(Controller, ODataModel) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Get OData model
               var oModel = this.getView().getModel();
               
               // Read data from service
               oModel.read("/EntitySet", {
                   success: function(oData) {
                       // Handle success
                       console.log(oData);
                   },
                   error: function(oError) {
                       // Handle error
                       console.error(oError);
                   }
               });
           }
       });
   });
   ```

### 3. Service Features
- **CRUD Operations**: Create, Read, Update, Delete
- **Batch Operations**: Multiple operations in one request
- **Filtering**: Server-side filtering
- **Sorting**: Server-side sorting
- **Pagination**: Server-side pagination
- **Expand**: Navigation property expansion
- **Select**: Property selection
- **Search**: Full-text search

### 4. CRUD Operations
1. **Create Operation**:
   ```javascript
   oModel.create("/EntitySet", {
       // Entity data
       ProductID: "123",
       Name: "New Product"
   }, {
       success: function(oData) {
           // Handle success
       },
       error: function(oError) {
           // Handle error
       }
   });
   ```

2. **Read Operation**:
   ```javascript
   oModel.read("/EntitySet('123')", {
       success: function(oData) {
           // Handle success
       },
       error: function(oError) {
           // Handle error
       }
   });
   ```

3. **Update Operation**:
   ```javascript
   oModel.update("/EntitySet('123')", {
       // Updated data
       Name: "Updated Product"
   }, {
       success: function(oData) {
           // Handle success
       },
       error: function(oError) {
           // Handle error
       }
   });
   ```

4. **Delete Operation**:
   ```javascript
   oModel.remove("/EntitySet('123')", {
       success: function(oData) {
           // Handle success
       },
       error: function(oError) {
           // Handle error
       }
   });
   ```

### 5. Batch Operations
1. Create batch operation:
   ```javascript
   var oBatch = oModel.createBatchOperationGroup();
   
   // Add operations to batch
   oBatch.add(oModel.create("/EntitySet", {
       ProductID: "123",
       Name: "New Product"
   }));
   
   oBatch.add(oModel.update("/EntitySet('456')", {
       Name: "Updated Product"
   }));
   
   // Execute batch
   oBatch.execute({
       success: function(oData) {
           // Handle success
       },
       error: function(oError) {
           // Handle error
       }
   });
   ```

### 6. Service Binding
1. Bind service data in view:
   ```xml
   <!-- webapp/view/View1.view.xml -->
   <mvc:View
       controllerName="com.example.app.controller.View1"
       xmlns="sap.m"
       xmlns:mvc="sap.ui.core.mvc">
       <List
           items="{/EntitySet}">
           <items>
               <ObjectListItem
                   title="{ProductID}"
                   description="{Name}"/>
           </items>
       </List>
   </mvc:View>
   ```

### 7. Service Parameters
1. Configure service parameters:
   ```javascript
   var oModel = new ODataModel({
       serviceUrl: "/sap/opu/odata/sap/ZDEMO_SERVICE/",
       defaultOperationMode: "Server",
       defaultBindingMode: "TwoWay",
       defaultCountMode: "Request",
       useBatch: true,
       refreshAfterChange: true,
       tokenHandling: true,
       tokenUrl: "/sap/opu/odata/sap/ZDEMO_SERVICE/",
       headers: {
           "X-CSRF-Token": "Fetch"
       }
   });
   ```

### 8. Best Practices
- Use batch operations for multiple changes
- Implement proper error handling
- Handle offline scenarios
- Consider performance impact
- Use appropriate binding modes
- Implement proper security
- Handle service versioning
- Consider data consistency
- Implement proper caching
- Use appropriate refresh strategies

## Mock Server Configuration

### 1. Mock Server Setup
1. Create mock server configuration:
   ```javascript
   // webapp/localService/mockserver.js
   sap.ui.define([
       "sap/ui/core/util/MockServer"
   ], function(MockServer) {
       "use strict";
       return {
           init: function() {
               // Create mock server
               var oMockServer = new MockServer({
                   rootUri: "/sap/opu/odata/sap/ZDEMO_SERVICE/"
               });

               // Configure mock server
               MockServer.config({
                   autoRespond: true,
                   autoRespondAfter: 500
               });

               // Simulate the delay of the real server
               oMockServer.simulate("localService/metadata.xml", {
                   sMockdataBaseUrl: "localService/mockdata",
                   bGenerateMissingMockData: true
               });

               // Start mock server
               oMockServer.start();

               console.log("Running the app with mock data");
           }
       };
   });
   ```

### 2. Mock Data Structure
1. Create mock data files:
   ```json
   // webapp/localService/mockdata/EntitySet.json
   {
       "d": {
           "results": [
               {
                   "ProductID": "HT-1000",
                   "Name": "Notebook Basic 15",
                   "Description": "Notebook Basic 15 with 2,80 GHz quad core, 15\" LCD, 4 GB DDR3 RAM, 500 GB Hard Disc, Windows 8 Pro",
                   "Price": 956.00
               },
               {
                   "ProductID": "HT-1001",
                   "Name": "Notebook Basic 17",
                   "Description": "Notebook Basic 17 with 2,80 GHz quad core, 17\" LCD, 4 GB DDR3 RAM, 500 GB Hard Disc, Windows 8 Pro",
                   "Price": 1249.00
               }
           ]
       }
   }
   ```

### 3. Metadata Configuration
1. Create metadata file:
   ```xml
   <!-- webapp/localService/metadata.xml -->
   <?xml version="1.0" encoding="utf-8"?>
   <edmx:Edmx Version="1.0" xmlns:edmx="http://schemas.microsoft.com/ado/2007/06/edmx">
       <edmx:DataServices xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" m:DataServiceVersion="1.0">
           <Schema Namespace="ZDEMO_SERVICE" xmlns="http://schemas.microsoft.com/ado/2008/09/edm">
               <EntityType Name="Product">
                   <Key>
                       <PropertyRef Name="ProductID"/>
                   </Key>
                   <Property Name="ProductID" Type="Edm.String" Nullable="false"/>
                   <Property Name="Name" Type="Edm.String"/>
                   <Property Name="Description" Type="Edm.String"/>
                   <Property Name="Price" Type="Edm.Decimal" Precision="19" Scale="4"/>
               </EntityType>
           </Schema>
           <Schema Namespace="ZDEMO_SERVICE" xmlns="http://schemas.microsoft.com/ado/2008/09/edm">
               <EntityContainer Name="ZDEMO_SERVICE_Entities" m:IsDefaultEntityContainer="true">
                   <EntitySet Name="Products" EntityType="ZDEMO_SERVICE.Product"/>
               </EntityContainer>
           </Schema>
       </edmx:DataServices>
   </edmx:Edmx>
   ```

### 4. Mock Server Integration
1. Initialize mock server in index.html:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>SAPUI5 Application</title>
       <script
           id="sap-ui-bootstrap"
           src="resources/sap-ui-core.js"
           data-sap-ui-theme="sap_fiori_3"
           data-sap-ui-resourceroots='{
               "com.example.app": "./"
           }'
           data-sap-ui-compatVersion="edge"
           data-sap-ui-async="true"
           data-sap-ui-frameOptions="allow"
           data-sap-ui-oninit="module:sap/ui/core/ComponentSupport">
       </script>
       <script>
           window["sap-ushell-config"] = {
               defaultRenderer: "fiori2",
               applications: {
                   "display-mode": "standalone"
               }
           };
       </script>
       <script src="localService/mockserver.js"></script>
   </head>
   <body class="sapUiBody">
       <div data-sap-ui-component
            data-name="com.example.app"
            data-settings='{"id" : "helloapp"}'
            style="height: 100%">
       </div>
   </body>
   </html>
   ```

### 5. Mock Server Features
- **Auto Response**: Automatic response generation
- **Delay Simulation**: Simulate network latency
- **Missing Data Generation**: Generate missing mock data
- **Request Interception**: Intercept and mock requests
- **Response Customization**: Custom response handling

### 6. Mock Server Methods
1. **Request Handling**:
   ```javascript
   oMockServer.simulate("localService/metadata.xml", {
       sMockdataBaseUrl: "localService/mockdata",
       bGenerateMissingMockData: true,
       aEntitySetsNames: ["Products"]
   });
   ```

2. **Custom Response**:
   ```javascript
   oMockServer.attachBefore(function(oEvent) {
       var oXhr = oEvent.getParameter("oXhr");
       if (oXhr && oXhr.url.indexOf("first") > -1) {
           oEvent.getParameter("oFilteredData").results.splice(3);
       }
   });
   ```

### 7. Best Practices
- Use realistic mock data
- Simulate network conditions
- Handle error scenarios
- Test edge cases
- Document mock data structure
- Consider data relationships
- Implement proper error handling
- Use meaningful data values
- Maintain data consistency
- Test with different data sets

## Unit Testing with QUnit

### 1. Test Setup
1. Create test directory structure:
   ```bash
   webapp/
   ├── test/
   │   ├── unit/
   │   │   ├── controller/
   │   │   ├── model/
   │   │   └── formatter/
   │   └── integration/
   ```

2. Create test configuration file:
   ```javascript
   // webapp/test/unit/unitTests.qunit.html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>Unit Tests</title>
       <script
           id="sap-ui-bootstrap"
           src="resources/sap-ui-core.js"
           data-sap-ui-theme="sap_fiori_3"
           data-sap-ui-resourceroots='{
               "com.example.app": "./"
           }'
           data-sap-ui-compatVersion="edge"
           data-sap-ui-async="true"
           data-sap-ui-frameOptions="allow">
       </script>
       <script src="resources/sap/ui/thirdparty/qunit.js"></script>
       <script src="resources/sap/ui/qunit/qunit-css.js"></script>
       <script src="resources/sap/ui/qunit/qunit-junit.js"></script>
       <script src="resources/sap/ui/qunit/qunit-coverage.js"></script>
   </head>
   <body>
       <div id="qunit"></div>
       <div id="qunit-fixture"></div>
   </body>
   </html>
   ```

### 2. Controller Testing
1. Create controller test file:
   ```javascript
   // webapp/test/unit/controller/View1.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller",
       "sap/ui/qunit/QUnitUtils",
       "sap/ui/thirdparty/sinon",
       "sap/ui/thirdparty/sinon-qunit",
       "com/example/app/controller/View1"
   ], function(Controller, QUnitUtils, sinon, sinonQUnit, View1Controller) {
       "use strict";
       
       QUnit.module("View1 Controller", {
           beforeEach: function() {
               this.oView = sap.ui.xmlview("view1", {
                   viewName: "com.example.app.view.View1"
               });
               this.oController = new View1Controller({
                   view: this.oView
               });
               this.oView.setController(this.oController);
           },
           afterEach: function() {
               this.oView.destroy();
           }
       });
       
       QUnit.test("Should initialize the controller", function(assert) {
           assert.ok(this.oController);
       });
       
       QUnit.test("Should handle button press", function(assert) {
           // Arrange
           var oButton = new sap.m.Button();
           var oEvent = {
               getSource: function() {
                   return oButton;
               }
           };
           
           // Act
           this.oController.onPress(oEvent);
           
           // Assert
           assert.ok(true, "Button press handled");
       });
   });
   ```

### 3. Model Testing
1. Create model test file:
   ```javascript
   // webapp/test/unit/model/formatter.js
   sap.ui.define([
       "sap/ui/qunit/QUnitUtils",
       "sap/ui/thirdparty/sinon",
       "sap/ui/thirdparty/sinon-qunit",
       "com/example/app/model/formatter"
   ], function(QUnitUtils, sinon, sinonQUnit, formatter) {
       "use strict";
       
       QUnit.module("Formatter", {
           beforeEach: function() {
               this.oController = {
                   getView: function() {
                       return {
                           getModel: function() {
                               return {
                                   getResourceBundle: function() {
                                       return {
                                           getText: function(sKey) {
                                               return sKey;
                                           }
                                       };
                                   }
                               };
                           }
                       };
                   }
               };
           }
       });
       
       QUnit.test("Should format status text", function(assert) {
           // Act
           var sStatus = formatter.statusText.call(this.oController, "A");
           
           // Assert
           assert.strictEqual(sStatus, "invoiceStatusA");
       });
       
       QUnit.test("Should format date", function(assert) {
           // Act
           var sDate = formatter.formatDate("2023-01-01");
           
           // Assert
           assert.strictEqual(sDate, "1/1/2023");
       });
   });
   ```

### 4. Test Features
- **QUnit Assertions**: Various assertion methods
- **Sinon Mocks**: Mock objects and functions
- **Test Coverage**: Code coverage reporting
- **Test Isolation**: Independent test cases
- **Test Organization**: Modular test structure

### 5. Test Best Practices
1. **Test Organization**:
   ```javascript
   QUnit.module("Module Name", {
       beforeEach: function() {
           // Setup before each test
       },
       afterEach: function() {
           // Cleanup after each test
       }
   });
   ```

2. **Test Structure**:
   ```javascript
   QUnit.test("Test Description", function(assert) {
       // Arrange
       // Act
       // Assert
   });
   ```

3. **Mocking**:
   ```javascript
   var oMockModel = {
       getProperty: sinon.stub().returns("test")
   };
   ```

### 6. Test Coverage
1. Configure coverage in package.json:
   ```json
   {
     "scripts": {
       "test": "ui5 test",
       "test:coverage": "ui5 test --coverage"
     }
   }
   ```

2. View coverage report:
   ```bash
   npm run test:coverage
   ```

### 7. Best Practices
- Write meaningful test descriptions
- Use appropriate assertions
- Mock external dependencies
- Clean up after tests
- Maintain test independence
- Consider edge cases
- Document test requirements
- Regular test maintenance
- Proper error handling
- Test performance impact
