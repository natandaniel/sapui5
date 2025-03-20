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
28. [Integration Testing with OPA](#integration-testing-with-opa)
    - [Test Setup](#1-test-setup)
    - [Page Object Pattern](#2-page-object-pattern)
    - [Test Arrangements](#3-test-arrangements)
    - [Test Implementation](#4-test-implementation)
    - [Test Features](#5-test-features)
    - [Test Actions](#6-test-actions)
    - [Test Assertions](#7-test-assertions)
    - [Test Configuration](#8-test-configuration)
    - [Run Tests](#9-run-tests)
    - [Best Practices](#10-best-practices)
29. [Debugging Tools](#debugging-tools)
    - [Chrome DevTools Integration](#1-chrome-devtools-integration)
    - [SAPUI5 Debug Tools](#2-sapui5-debug-tools)
    - [Console Logging](#3-console-logging)
    - [Breakpoint Management](#4-breakpoint-management)
    - [Network Monitoring](#5-network-monitoring)
    - [Memory Management](#6-memory-management)
    - [Best Practices](#7-best-practices)
30. [Routing and Navigation](#routing-and-navigation)
    - [Router Configuration](#1-router-configuration)
    - [Router Implementation](#2-router-implementation)
    - [Route Handling](#3-route-handling)
    - [Navigation Features](#4-navigation-features)
    - [Route Parameters](#5-route-parameters)
    - [Target Display](#6-target-display)
    - [Navigation History](#7-navigation-history)
    - [Error Handling](#8-error-handling)
    - [Best Practices](#9-best-practices)
31. [Custom Controls](#custom-controls)
    - [Control Definition](#1-control-definition)
    - [Control Usage](#2-control-usage)
    - [Control Properties](#3-control-properties)
    - [Control Events](#4-control-events)
    - [Control Aggregations](#5-control-aggregations)
    - [Control Associations](#6-control-associations)
    - [Control Rendering](#7-control-rendering)
    - [Control Styling](#8-control-styling)
    - [Control Testing](#9-control-testing)
    - [Best Practices for Custom Controls](#10-best-practices-for-custom-controls)
32. [Responsive Design](#responsive-design)
    - [Responsive Grid Layout](#1-responsive-grid-layout)
    - [Responsive Split App](#2-responsive-split-app)
    - [Responsive Form Layout](#3-responsive-form-layout)
    - [Responsive Table](#4-responsive-table)
    - [Responsive Dialog](#5-responsive-dialog)
    - [Media Queries](#6-media-queries)
    - [Responsive Container](#7-responsive-container)
    - [Responsive Filter Bar](#8-responsive-filter-bar)
    - [Best Practices](#9-best-practices-for-responsive-design)
33. [Device Adaptation](#device-adaptation)
    - [Device Types](#1-device-types)
    - [Device Detection](#2-device-detection)
    - [Device-Specific Features](#3-device-specific-features)
    - [Touch Support](#4-touch-support)
    - [Device APIs](#5-device-apis)
    - [Device Orientation](#6-device-orientation)
    - [Device Storage](#7-device-storage)
    - [Device Sensors](#8-device-sensors)
    - [Best Practices](#9-best-practices-for-device-adaptation)
34. [Content Density](#content-density)
    - [Density Modes](#1-density-modes)
    - [Density Configuration](#2-density-configuration)
    - [Density Classes](#3-density-classes)
    - [Density Adaptation](#4-density-adaptation)
    - [Density Controls](#5-density-controls)
    - [Density Layouts](#6-density-layouts)
    - [Density Forms](#7-density-forms)
    - [Density Tables](#8-density-tables)
    - [Best Practices](#9-best-practices-for-content-density)
35. [Accessibility](#accessibility)
    - [ARIA Support](#1-aria-support)
    - [Keyboard Navigation](#2-keyboard-navigation)
    - [Screen Reader Support](#3-screen-reader-support)
    - [High Contrast Mode](#4-high-contrast-mode)
    - [Focus Management](#5-focus-management)
    - [Accessibility Properties](#6-accessibility-properties)
    - [Accessibility Testing](#7-accessibility-testing)
    - [Accessibility Guidelines](#8-accessibility-guidelines)
    - [Best Practices](#9-best-practices-for-accessibility)
36. [Building the Application](#building-the-application)
    - [Build Configuration](#1-build-configuration)
    - [Build Tools](#2-build-tools)
    - [Build Process](#3-build-process)
    - [Build Optimization](#4-build-optimization)
    - [Build Deployment](#5-build-deployment)
    - [Build Testing](#6-build-testing)
    - [Build Monitoring](#7-build-monitoring)
    - [Build Best Practices](#8-build-best-practices)
    - [Build Troubleshooting](#9-build-troubleshooting)

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

## Integration Testing with OPA

### 1. Test Setup
1. Create integration test directory structure:
   ```bash
   webapp/
   ├── test/
   │   ├── integration/
   │   │   ├── opaTests.qunit.html
   │   │   ├── pages/
   │   │   └── arrangements/
   ```

2. Create OPA test configuration file:
   ```html
   <!-- webapp/test/integration/opaTests.qunit.html -->
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8">
       <title>Integration Tests</title>
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
       <script src="resources/sap/ui/thirdparty/sinon.js"></script>
       <script src="resources/sap/ui/thirdparty/sinon-qunit.js"></script>
       <script src="resources/sap/ui/opa/opaTestLib.js"></script>
   </head>
   <body>
       <div id="qunit"></div>
       <div id="qunit-fixture"></div>
   </body>
   </html>
   ```

### 2. Page Object Pattern
1. Create page object:
   ```javascript
   // webapp/test/integration/pages/View1.js
   sap.ui.define([
       "sap/ui/test/Opa5",
       "sap/ui/test/actions/Press",
       "sap/ui/test/actions/EnterText"
   ], function(Opa5, Press, EnterText) {
       "use strict";
       
       var sViewName = "com.example.app.view.View1";
       
       Opa5.createPageObjects({
           onTheView1Page: {
               viewName: sViewName,
               actions: {
                   iPressTheButton: function() {
                       return this.waitFor({
                           id: "helloButton",
                           actions: new Press(),
                           errorMessage: "Button not found"
                       });
                   },
                   iEnterText: function(sText) {
                       return this.waitFor({
                           id: "inputField",
                           actions: new EnterText({
                               text: sText
                           }),
                           errorMessage: "Input field not found"
                       });
                   }
               },
               assertions: {
                   iShouldSeeTheText: function(sText) {
                       return this.waitFor({
                           id: "textLabel",
                           matchers: {
                               text: sText
                           },
                           success: function(oControl) {
                               Opa5.assert.ok(true, "Text found");
                           },
                           errorMessage: "Text not found"
                       });
                   }
               }
           }
       });
   });
   ```

### 3. Test Arrangements
1. Create test arrangements:
   ```javascript
   // webapp/test/integration/arrangements/Startup.js
   sap.ui.define([
       "sap/ui/test/Opa5"
   ], function(Opa5) {
       "use strict";
       
       Opa5.createPageObjects({
           onTheAppPage: {
               actions: {
                   iStartTheApp: function() {
                       return this.waitFor({
                           id: "app",
                           success: function() {
                               Opa5.assert.ok(true, "App started");
                           },
                           errorMessage: "App not started"
                       });
                   }
               }
           }
       });
   });
   ```

### 4. Test Implementation
1. Create test file:
   ```javascript
   // webapp/test/integration/View1Journey.js
   sap.ui.define([
       "sap/ui/test/opaQunit",
       "./pages/View1",
       "./arrangements/Startup"
   ], function(opaTest, View1Page, StartupArrangement) {
       "use strict";
       
       QUnit.module("View1 Journey");
       
       opaTest("Should show hello text", function(Given, When, Then) {
           // Arrange
           Given.iStartTheApp();
           
           // Act
           When.onTheView1Page.iEnterText("World");
           When.onTheView1Page.iPressTheButton();
           
           // Assert
           Then.onTheView1Page.iShouldSeeTheText("Hello World");
       });
   });
   ```

### 5. Test Features
- **Page Objects**: Encapsulate UI elements
- **Actions**: User interactions
- **Assertions**: State verification
- **Arrangements**: Test setup
- **Journeys**: Test scenarios

### 6. Test Actions
1. **Common Actions**:
   ```javascript
   // Press action
   new Press()
   
   // Enter text
   new EnterText({
       text: "Hello"
   })
   
   // Clear text
   new Clear()
   
   // Check action
   new Check()
   
   // Select action
   new Select({
       keys: ["Option1"]
   })
   ```

2. **Custom Actions**:
   ```javascript
   var CustomAction = sap.ui.test.Opa5.extend("CustomAction", {
       executeOn: function(oControl) {
           // Custom action implementation
           return this;
       }
   });
   ```

### 7. Test Assertions
1. **Common Assertions**:
   ```javascript
   // Property assertion
   matchers: {
       propertyName: "value"
   }
   
   // Text assertion
   matchers: {
       text: "Hello"
   }
   
   // Control state assertion
   matchers: {
       enabled: true
   }
   
   // Custom assertion
   success: function(oControl) {
       Opa5.assert.ok(true, "Custom assertion");
   }
   ```

### 8. Test Configuration
1. Configure in package.json:
   ```json
   {
     "scripts": {
       "test:integration": "ui5 test --integration"
     }
   }
   ```

2. Run integration tests:
   ```bash
   npm run test:integration
   ```

### 9. Best Practices
- Use meaningful page objects
- Implement proper actions
- Write clear assertions
- Handle async operations
- Consider test isolation
- Document test scenarios
- Maintain test independence
- Handle error cases
- Consider performance
- Regular test maintenance

## Debugging Tools

### 1. Chrome DevTools Integration
1. Enable SAPUI5 debugging:
   ```javascript
   // Add to index.html
   <script>
       window["sap-ushell-config"] = {
           debug: true
       };
   </script>
   ```

2. Access debugging features:
   - Press F12 to open Chrome DevTools
   - Use the "Elements" tab to inspect UI elements
   - Use the "Console" tab for logging
   - Use the "Network" tab to monitor requests
   - Use the "Sources" tab to debug JavaScript

### 2. SAPUI5 Debug Tools
1. Enable debug tools:
   ```javascript
   // Add to index.html
   <script>
       sap.ui.getCore().attachInit(function() {
           sap.ui.require([
               "sap/ui/debug/ControlTree",
               "sap/ui/debug/PropertyEditor"
           ]);
       });
   </script>
   ```

2. Access debug tools:
   - Press Ctrl+Alt+Shift+S to open Control Tree
   - Press Ctrl+Alt+Shift+P to open Property Editor
   - Use Control Tree to inspect UI hierarchy
   - Use Property Editor to modify properties

### 3. Console Logging
1. Configure logging:
   ```javascript
   // In your controller
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Enable logging
               sap.ui.log.setLevel(sap.ui.log.LogLevel.DEBUG);
               
               // Log messages
               sap.ui.log.debug("Debug message");
               sap.ui.log.info("Info message");
               sap.ui.log.warning("Warning message");
               sap.ui.log.error("Error message");
           }
       });
   });
   ```

2. View logs:
   - Open Chrome DevTools
   - Go to Console tab
   - Filter by "SAPUI5" to see framework logs
   - Use different log levels for different purposes

### 4. Breakpoint Management
1. Set breakpoints in JavaScript:
   ```javascript
   // In your controller
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.View1", {
           onInit: function() {
               // Set breakpoints
               sap.ui.getCore().attachInit(function() {
                   sap.ui.require([
                       "sap/ui/debug/Breakpoint"
                   ]);
               });
           }
       });
   });
   ```

2. Use breakpoints in SAPUI5:
   - Press Ctrl+Shift+B to set a breakpoint
   - Use the "Debugger" tab in Chrome DevTools to step through code

### 5. Network Monitoring
1. Monitor OData requests:
   ```javascript
   // In your controller
   var oModel = this.getView().getModel();
   oModel.attachRequestCompleted(function(oEvent) {
       var oParams = oEvent.getParameters();
       console.log("Request completed:", oParams);
   });
   ```

2. Monitor resource loading:
   ```javascript
   sap.ui.getCore().attachInit(function() {
       sap.ui.require([
           "sap/ui/debug/ResourceMonitor"
       ]);
   });
   ```

### 6. Memory Management
1. Monitor memory usage:
   ```javascript
   // In your controller
   sap.ui.getCore().attachInit(function() {
       sap.ui.require([
           "sap/ui/debug/Memory"
       ]);
   });
   ```

2. Clean up resources:
   ```javascript
   onExit: function() {
       // Clean up event listeners
       this.getView().detachModelContextChange();
       
       // Clean up models
       this.getView().setModel(null);
       
       // Clean up views
       this.getView().destroy();
   }
   ```

### 7. Best Practices
- Use appropriate log levels
- Clean up resources properly
- Monitor performance regularly
- Handle errors gracefully
- Use debug tools effectively
- Document debugging steps
- Test in different environments
- Consider security implications
- Maintain debugging code
- Regular performance checks

## Routing and Navigation

### 1. Router Configuration
1. Configure routing in manifest.json:
   ```json
   {
     "sap.ui5": {
       "routing": {
         "config": {
           "routerClass": "sap.m.routing.Router",
           "viewType": "XML",
           "viewPath": "com.example.app.view",
           "controlId": "app",
           "controlAggregation": "pages",
           "async": true
         },
         "routes": [
           {
             "pattern": "",
             "name": "home",
             "target": "home"
           },
           {
             "pattern": "detail/{id}",
             "name": "detail",
             "target": "detail"
           }
         ],
         "targets": {
           "home": {
             "viewName": "Home",
             "viewLevel": 1
           },
           "detail": {
             "viewName": "Detail",
             "viewLevel": 2
           }
         }
       }
     }
   }
   ```

### 2. Router Implementation
1. Initialize router in Component.js:
   ```javascript
   // webapp/Component.js
   sap.ui.define([
       "sap/ui/core/UIComponent",
       "sap/ui/Device",
       "sap/ui/model/json/JSONModel",
       "sap/ui/model/resource/ResourceModel",
       "com/example/app/model/formatter",
       "com/example/app/controller/Home",
       "com/example/app/controller/Detail"
   ], function(UIComponent, Device, JSONModel, ResourceModel, formatter, HomeController, DetailController) {
       "use strict";
       return UIComponent.extend("com.example.app.Component", {
           metadata: {
               manifest: "json"
           },
           init: function() {
               // Call the base component's init function
               UIComponent.prototype.init.apply(this, arguments);
               
               // Enable routing
               this.getRouter().initialize();
               
               // Set the device model
               this.setModel(new JSONModel(Device), "device");
           }
       });
   });
   ```

### 3. Route Handling
1. Implement route handlers in controllers:
   ```javascript
   // webapp/controller/Home.controller.js
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.app.controller.Home", {
           onInit: function() {
               // Get router instance
               const oRouter = this.getRouter();
               
               // Attach route matched handler
               oRouter.getRoute("detail").attachMatched(this._onRouteMatched, this);
           },
           
           // Navigate to a route
           onNavigateToDetail: function() {
               this.getRouter().navTo("detail", {
                   id: "123"  // Route parameters
               });
           },
           
           // Handle route matched
           _onRouteMatched: function(oEvent) {
               const sId = oEvent.getParameter("arguments").id;
               // Handle route parameters
           }
       });
   });
   ```

### 4. Navigation Features
1. **Basic Navigation**:
   ```javascript
   // Navigate to a route
   this.getRouter().navTo("detail", { id: "123" });
   
   // Navigate without history
   this.getRouter().navTo("detail", { id: "123" }, true);
   
   // Navigate back
   this.getRouter().navBack();
   
   // Display a target
   this.getRouter().getTargets().display("detail");
   ```

2. **Navigation Events**:
   ```javascript
   // Handle navigation events
   oRouter.attachRouteMatched(function(oEvent) {
       // Handle route matched
   });
   
   oRouter.attachBeforeRouteMatched(function(oEvent) {
       // Handle before route matched
   });
   ```

### 5. Route Parameters
1. **Define Route Parameters**:
   ```json
   {
     "routes": [
       {
         "pattern": "detail/{id}/{type}",
         "name": "detail",
         "target": "detail"
       }
     ]
   }
   ```

2. **Access Route Parameters**:
   ```javascript
   _onRouteMatched: function(oEvent) {
       const oArguments = oEvent.getParameter("arguments");
       const sId = oArguments.id;
       const sType = oArguments.type;
   }
   ```

### 6. Target Display
1. **Target Configuration**:
   ```json
   {
     "targets": {
       "detail": {
         "viewName": "Detail",
         "viewLevel": 2,
         "controlAggregation": "pages",
         "controlId": "app",
         "async": true
       }
     }
   }
   ```

2. **Target Display Options**:
   ```javascript
   // Display target
   this.getRouter().getTargets().display("detail");
   
   // Display with parameters
   this.getRouter().getTargets().display("detail", {
       id: "123"
   });
   ```

### 7. Navigation History
1. **History Management**:
   ```javascript
   // Navigate with history
   this.getRouter().navTo("detail", { id: "123" });
   
   // Navigate without history
   this.getRouter().navTo("detail", { id: "123" }, true);
   
   // Navigate back
   this.getRouter().navBack();
   ```

2. **History Events**:
   ```javascript
   // Handle history events
   sap.ui.core.routing.History.getInstance().attachDirectNav(function(oEvent) {
       // Handle direct navigation
   });
   ```

### 8. Error Handling
1. **Route Error Handling**:
   ```javascript
   // Handle navigation errors
   oRouter.attachRoutePatternMatched(function(oEvent) {
       try {
           // Navigation logic
       } catch (error) {
           // Handle error
           this.getRouter().navTo("error");
       }
   });
   ```

2. **Target Error Handling**:
   ```javascript
   // Handle target errors
   this.getRouter().getTargets().attachDisplay(function(oEvent) {
       try {
           // Target display logic
       } catch (error) {
           // Handle error
           this.getRouter().navTo("error");
       }
   });
   ```

### 9. Best Practices
- Use meaningful route names
- Implement proper error handling
- Handle route parameters safely
- Clean up event listeners
- Consider navigation history
- Use appropriate view levels
- Implement proper access control
- Handle loading states
- Consider deep linking
- Test navigation flows

## Custom Controls

### 1. Control Definition
```javascript
// webapp/controls/CustomButton.js
sap.ui.define([
    "sap/m/Button"
], function(Button) {
    "use strict";
    
    return Button.extend("com.example.controls.CustomButton", {
        metadata: {
            properties: {
                customText: { type: "string", defaultValue: "" },
                customType: { type: "string", defaultValue: "Default" }
            },
            events: {
                customPress: {}
            }
        },
        
        init: function() {
            Button.prototype.init.apply(this, arguments);
        },
        
        onAfterRendering: function() {
            Button.prototype.onAfterRendering.apply(this, arguments);
        },
        
        setCustomText: function(sText) {
            this.setProperty("customText", sText);
            this.setText(sText);
            return this;
        }
    });
});
```

### 2. Control Usage
```xml
<!-- webapp/view/MainView.xml -->
<mvc:View
    controllerName="com.example.controller.Main"
    xmlns="sap.m"
    xmlns:custom="com.example.controls">
    
    <custom:CustomButton
        customText="Custom Button"
        customType="Emphasized"
        customPress=".onCustomPress"/>
</mvc:View>
```

### 3. Control Properties
```javascript
// Define control properties
metadata: {
    properties: {
        // Simple property
        text: { type: "string", defaultValue: "" },
        
        // Complex property
        options: { type: "object", defaultValue: {} },
        
        // Array property
        items: { type: "array", defaultValue: [] },
        
        // Enum property
        type: { type: "string", defaultValue: "Default" }
    }
}
```

### 4. Control Events
```javascript
// Define control events
metadata: {
    events: {
        // Simple event
        press: {},
        
        // Event with parameters
        selectionChange: {
            parameters: {
                selectedItem: { type: "object" },
                selectedIndex: { type: "int" }
            }
        }
    }
}
```

### 5. Control Aggregations
```javascript
// Define control aggregations
metadata: {
    aggregations: {
        // Single aggregation
        header: { type: "sap.m.Title", multiple: false },
        
        // Multiple aggregation
        items: { type: "sap.m.ListItemBase", multiple: true },
        
        // Default aggregation
        content: { type: "sap.ui.core.Control", multiple: true, singularName: "content" }
    }
}
```

### 6. Control Associations
```javascript
// Define control associations
metadata: {
    associations: {
        // Single association
        label: { type: "sap.m.Label", multiple: false },
        
        // Multiple association
        relatedControls: { type: "sap.ui.core.Control", multiple: true }
    }
}
```

### 7. Control Rendering
```javascript
// Custom rendering
renderer: {
    apiVersion: 2,
    render: function(oRM, oControl) {
        oRM.openStart("div", oControl);
        oRM.class("customControl");
        oRM.openEnd();
        
        // Render content
        oControl.getContent().forEach(function(oContent) {
            oRM.renderControl(oContent);
        });
        
        oRM.close("div");
    }
}
```

### 8. Control Styling
```css
/* webapp/css/CustomControl.css */
.customControl {
    border: 1px solid #ccc;
    padding: 1rem;
    margin: 0.5rem;
}

.customControl .sapMText {
    font-size: 1.2rem;
    color: #333;
}

.customControl.sapContrast {
    border-color: #fff;
}

.customControl.sapContrast .sapMText {
    color: #fff;
}
```

### 9. Control Testing
```javascript
// webapp/test/CustomButton.qunit.js
QUnit.module("Custom Button Tests", {
    beforeEach: function() {
        this.oButton = new CustomButton({
            customText: "Test Button",
            customPress: function() {}
        });
        this.oButton.placeAt("qunit-fixture");
        sap.ui.getCore().applyChanges();
    },
    afterEach: function() {
        this.oButton.destroy();
    }
});

QUnit.test("Custom Button Creation", function(assert) {
    assert.ok(this.oButton, "Button should be created");
    assert.equal(this.oButton.getCustomText(), "Test Button", "Custom text should be set");
});
```

### 10. Best Practices for Custom Controls
- Follow SAPUI5 naming conventions
- Implement proper metadata
- Handle lifecycle methods
- Support accessibility features
- Implement proper event handling
- Support responsive design
- Handle theme changes
- Implement proper cleanup
- Support keyboard navigation
- Follow SAPUI5 design guidelines
- Implement proper error handling
- Support internationalization
- Implement proper documentation
- Support testing
- Follow performance guidelines

## Responsive Design

### 1. Responsive Grid Layout
```xml
<!-- webapp/view/MainView.xml -->
<mvc:View
    controllerName="com.example.controller.Main"
    xmlns="sap.ui.layout"
    xmlns="sap.m">
    
    <layout:Grid
        defaultSpan="L12 M12 S12"
        defaultIndent="L0 M0 S0"
        hSpacing="1"
        vSpacing="1">
        
        <layout:content>
            <Panel>
                <Text text="Responsive Panel"/>
            </Panel>
        </layout:content>
    </layout:Grid>
</mvc:View>
```

### 2. Responsive Split App
```xml
<!-- webapp/view/App.view.xml -->
<mvc:View
    controllerName="com.example.controller.App"
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc">
    
    <SplitApp id="splitApp"
        initialMaster="master"
        initialDetail="detail"
        mode="ShowHideMode">
        <masterPages>
            <Page id="master" title="Master">
                <content>
                    <List items="{/menuItems}">
                        <StandardListItem title="{title}" press="onItemPress"/>
                    </List>
                </content>
            </Page>
        </masterPages>
        <detailPages>
            <Page id="detail" title="Detail">
                <content>
                    <Text text="Detail Content"/>
                </content>
            </Page>
        </detailPages>
    </SplitApp>
</mvc:View>
```

### 3. Responsive Form Layout
```xml
<!-- webapp/view/FormView.xml -->
<mvc:View
    controllerName="com.example.controller.Form"
    xmlns="sap.ui.layout"
    xmlns="sap.m">
    
    <layout:form.SimpleForm
        editable="true"
        layout="ResponsiveGridLayout"
        labelSpanXL="4"
        labelSpanL="4"
        labelSpanM="4"
        labelSpanS="12"
        adjustLabelSpan="false"
        emptySpanXL="0"
        emptySpanL="0"
        emptySpanM="0"
        emptySpanS="0"
        columnsXL="2"
        columnsL="2"
        columnsM="2"
        columnsS="1">
        
        <layout:content>
            <Label text="Name"/>
            <Input value="{/name}"/>
            
            <Label text="Email"/>
            <Input value="{/email}"/>
        </layout:content>
    </layout:form.SimpleForm>
</mvc:View>
```

### 4. Responsive Table
```xml
<!-- webapp/view/TableView.xml -->
<mvc:View
    controllerName="com.example.controller.Table"
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc">
    
    <Table
        items="{/items}"
        growing="true"
        growingThreshold="10"
        mode="None"
        alternateRowColors="true"
        sticky="HeaderToolbar,ColumnHeaders,InfoToolbar">
        
        <headerToolbar>
            <Toolbar>
                <Title text="Responsive Table"/>
                <ToolbarSpacer/>
                <SearchField width="20%" search=".onSearch"/>
            </Toolbar>
        </headerToolbar>
        
        <columns>
            <Column>
                <Text text="Name"/>
            </Column>
            <Column>
                <Text text="Description"/>
            </Column>
        </columns>
        
        <items>
            <ColumnListItem>
                <cells>
                    <Text text="{name}"/>
                    <Text text="{description}"/>
                </cells>
            </ColumnListItem>
        </items>
    </Table>
</mvc:View>
```

### 5. Responsive Dialog
```xml
<!-- webapp/view/DialogView.xml -->
<mvc:View
    controllerName="com.example.controller.Dialog"
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc">
    
    <Dialog
        title="Responsive Dialog"
        draggable="true"
        resizable="true"
        contentWidth="50%"
        contentHeight="50%"
        showCloseButton="true"
        state="Standard"
        type="Standard">
        
        <content>
            <VBox>
                <Text text="Responsive Dialog Content"/>
                <Input value="{/input}"/>
            </VBox>
        </content>
        
        <buttons>
            <Button text="OK" press="onOK" type="Emphasized"/>
            <Button text="Cancel" press="onCancel"/>
        </buttons>
    </Dialog>
</mvc:View>
```

### 6. Media Queries
```css
/* webapp/css/styles.css */
@media screen and (max-width: 600px) {
    .sapMList {
        margin: 0;
    }
    
    .sapMPanel {
        padding: 0.5rem;
    }
    
    .sapMInput {
        width: 100%;
    }
}

@media screen and (min-width: 601px) and (max-width: 1024px) {
    .sapMList {
        margin: 1rem;
    }
    
    .sapMPanel {
        padding: 1rem;
    }
    
    .sapMInput {
        width: 50%;
    }
}

@media screen and (min-width: 1025px) {
    .sapMList {
        margin: 2rem;
    }
    
    .sapMPanel {
        padding: 2rem;
    }
    
    .sapMInput {
        width: 33.33%;
    }
}
```

### 7. Responsive Container
```xml
<!-- webapp/view/ContainerView.xml -->
<mvc:View
    controllerName="com.example.controller.Container"
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc">
    
    <Page>
        <content>
            <FlexBox
                wrap="Wrap"
                alignItems="Start"
                justifyContent="SpaceBetween"
                height="100%"
                width="100%">
                
                <items>
                    <Panel width="300px" expandable="true">
                        <Text text="Panel 1"/>
                    </Panel>
                    <Panel width="300px" expandable="true">
                        <Text text="Panel 2"/>
                    </Panel>
                    <Panel width="300px" expandable="true">
                        <Text text="Panel 3"/>
                    </Panel>
                </items>
            </FlexBox>
        </content>
    </Page>
</mvc:View>
```

### 8. Responsive Filter Bar
```xml
<!-- webapp/view/FilterView.xml -->
<mvc:View
    controllerName="com.example.controller.Filter"
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc">
    
    <Page>
        <content>
            <FilterBar
                search=".onSearch"
                useToolbar="false"
                showGoOnFB="true"
                showRestoreOnFB="true"
                showClearOnFB="true">
                
                <filterGroupItems>
                    <FilterGroupItem name="A" label="Filter 1">
                        <Input/>
                    </FilterGroupItem>
                    <FilterGroupItem name="B" label="Filter 2">
                        <Select/>
                    </FilterGroupItem>
                </filterGroupItems>
            </FilterBar>
        </content>
    </Page>
</mvc:View>
```

### 9. Best Practices for Responsive Design
- Use responsive grid layouts with appropriate breakpoints (XL, L, M, S)
- Implement flexible containers using FlexBox and Grid layouts
- Handle different screen sizes using SAPUI5's built-in responsive features
- Test on multiple devices and screen sizes
- Use media queries for custom responsive styling
- Implement responsive tables with growing and sticky features
- Handle touch interactions appropriately for mobile devices
- Optimize for performance using lazy loading and virtual scrolling
- Consider accessibility in responsive layouts
- Use responsive images with appropriate sizing
- Implement responsive forms with proper label spans
- Handle orientation changes gracefully
- Test with different browsers and devices
- Consider offline support for mobile scenarios
- Implement progressive enhancement for better user experience
- Use SAPUI5's built-in responsive features whenever possible
- Follow SAPUI5's responsive design guidelines
- Consider using SAPUI5's responsive controls (SplitApp, ResponsiveTable, etc.)
- Implement proper error handling for responsive scenarios
- Use appropriate spacing and margins for different screen sizes

## Device Adaptation

### 1. Device Types
1. Supported devices:
   - Desktop
   - Tablet
   - Mobile
   - Hybrid devices

2. Device characteristics:
   - Screen size
   - Input methods
   - Processing power
   - Memory capacity
   - Network capabilities

### 2. Device Detection
1. Detect device type:
   ```javascript
   sap.ui.Device.system.desktop;  // true/false
   sap.ui.Device.system.tablet;   // true/false
   sap.ui.Device.system.phone;    // true/false
   ```

2. Check device capabilities:
   ```javascript
   sap.ui.Device.support.touch;    // true/false
   sap.ui.Device.support.orientation; // true/false
   sap.ui.Device.support.webGL;    // true/false
   ```

### 3. Device-Specific Features
1. Adaptive controls:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <App>
           <pages>
               <Page title="Adaptive Page">
                   <content>
                       <VBox>
                           <Text text="Adaptive Content"/>
                           <Button text="Adaptive Button"/>
                       </VBox>
                   </content>
               </Page>
           </pages>
       </App>
   </mvc:View>
   ```

2. Device-specific layouts:
   ```javascript
   if (sap.ui.Device.system.phone) {
       // Phone-specific layout
   } else if (sap.ui.Device.system.tablet) {
       // Tablet-specific layout
   } else {
       // Desktop-specific layout
   }
   ```

### 4. Touch Support
1. Touch events:
   ```javascript
   oButton.attachPress(function(oEvent) {
       if (oEvent.getSource().getPressed()) {
           // Handle touch press
       }
   });
   ```

2. Touch gestures:
   ```javascript
   sap.ui.Device.support.touch && sap.ui.require([
       "sap/ui/events/KeyCodes"
   ], function(KeyCodes) {
       // Handle touch gestures
   });
   ```

### 5. Device APIs
1. Access device features:
   ```javascript
   if (sap.ui.Device.support.geolocation) {
       navigator.geolocation.getCurrentPosition(
           function(position) {
               // Handle location
           }
       );
   }
   ```

2. Device storage:
   ```javascript
   if (sap.ui.Device.support.localStorage) {
       localStorage.setItem("key", "value");
       var value = localStorage.getItem("key");
   }
   ```

### 6. Device Orientation
1. Handle orientation changes:
   ```javascript
   window.addEventListener("orientationchange", function() {
       // Handle orientation change
   });
   ```

2. Orientation-specific layouts:
   ```javascript
   if (window.orientation === 0 || window.orientation === 180) {
       // Portrait mode
   } else {
       // Landscape mode
   }
   ```

### 7. Device Storage
1. Local storage:
   ```javascript
   if (sap.ui.Device.support.localStorage) {
       // Use localStorage
   } else if (sap.ui.Device.support.sessionStorage) {
       // Use sessionStorage
   }
   ```

2. IndexedDB:
   ```javascript
   if (sap.ui.Device.support.indexeddb) {
       // Use IndexedDB
   }
   ```

### 8. Device Sensors
1. Accelerometer:
   ```javascript
   if (sap.ui.Device.support.accelerometer) {
       window.addEventListener("devicemotion", function(event) {
           // Handle accelerometer data
       });
   }
   ```

2. Gyroscope:
   ```javascript
   if (sap.ui.Device.support.gyroscope) {
       window.addEventListener("deviceorientation", function(event) {
           // Handle gyroscope data
       });
   }
   ```

### 9. Best Practices for Device Adaptation
- Use SAPUI5's built-in device detection
- Implement progressive enhancement
- Test on multiple devices
- Handle offline scenarios
- Optimize for different screen sizes
- Consider touch interactions
- Use appropriate input controls
- Implement responsive layouts
- Handle device orientation changes
- Consider device capabilities
- Use device-specific features appropriately
- Implement proper error handling
- Consider performance implications
- Test with different browsers
- Follow platform-specific guidelines
- Use appropriate storage mechanisms
- Handle network connectivity changes
- Implement proper security measures
- Consider accessibility requirements
- Use appropriate media queries

## Content Density

### 1. Density Modes
1. Available modes:
   - Compact
   - Cozy
   - Standard

2. Mode characteristics:
   ```javascript
   sap.ui.Device.support.touch ? "Cozy" : "Compact";
   ```

### 2. Density Configuration
1. Global configuration:
   ```javascript
   sap.ui.getCore().applyTheme("sap_fiori_3_dark");
   sap.ui.getCore().setCompactDensity();
   ```

2. Component-level configuration:
   ```javascript
   sap.ui.define([
       "sap/ui/core/UIComponent"
   ], function(UIComponent) {
       "use strict";
       return UIComponent.extend("com.example.Component", {
           metadata: {
               manifest: "json"
           },
           init: function() {
               UIComponent.prototype.init.apply(this, arguments);
               this.getModel().setProperty("/compactMode", true);
           }
       });
   });
   ```

### 3. Density Classes
1. CSS classes:
   ```css
   .sapUiSizeCompact {
       /* Compact mode styles */
   }
   .sapUiSizeCozy {
       /* Cozy mode styles */
   }
   ```

2. Responsive classes:
   ```xml
   <VBox class="sapUiSizeCompact">
       <Text text="Compact Content"/>
   </VBox>
   ```

### 4. Density Adaptation
1. Dynamic adaptation:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.controller.View1", {
           onInit: function() {
               this.getView().addStyleClass(
                   sap.ui.Device.support.touch ? "sapUiSizeCozy" : "sapUiSizeCompact"
               );
           }
       });
   });
   ```

2. Responsive adaptation:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m"
       class="sapUiSizeCompact">
       <Page title="Density Page">
           <content>
               <VBox>
                   <Text text="Adaptive Content"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 5. Density Controls
1. Control-specific density:
   ```xml
   <Button class="sapUiSizeCompact">
       <layoutData>
           <FlexItemData>
               <layoutData>
                   <GridItemData>
                       <layoutData>
                           <ResponsiveFlowLayoutData/>
                       </layoutData>
                   </GridItemData>
               </layoutData>
           </FlexItemData>
       </layoutData>
   </Button>
   ```

2. Density-aware controls:
   ```javascript
   new sap.m.Input({
       type: sap.m.InputType.Text,
       value: "{/value}",
       layoutData: new sap.m.FlexItemData({
           growFactor: 1
       })
   });
   ```

### 6. Density Layouts
1. Grid layout:
   ```xml
   <layout:Grid
       defaultSpan="L12 M12 S12"
       defaultIndent="L0 M0 S0"
       hSpacing="1"
       vSpacing="1"
       class="sapUiSizeCompact">
       <layout:content>
           <Panel>
               <Text text="Compact Panel"/>
           </Panel>
       </layout:content>
   </layout:Grid>
   ```

2. Form layout:
   ```xml
   <form:SimpleForm
       editable="true"
       layout="ResponsiveGridLayout"
       class="sapUiSizeCompact">
       <form:content>
           <Label text="Label"/>
           <Input value="{/value}"/>
       </form:content>
   </form:SimpleForm>
   ```

### 7. Density Forms
1. Form controls:
   ```xml
   <form:SimpleForm
       editable="true"
       layout="ResponsiveGridLayout"
       class="sapUiSizeCompact">
       <form:content>
           <Label text="Label"/>
           <Input value="{/value}"/>
           <Label text="Label"/>
           <Select>
               <items>
                   <core:Item text="Option 1"/>
                   <core:Item text="Option 2"/>
               </items>
           </Select>
       </form:content>
   </form:SimpleForm>
   ```

2. Form spacing:
   ```xml
   <form:SimpleForm
       editable="true"
       layout="ResponsiveGridLayout"
       class="sapUiSizeCompact">
       <form:content>
           <Label text="Label"/>
           <Input value="{/value}"/>
           <Label text="Label"/>
           <Input value="{/value}"/>
       </form:content>
   </form:SimpleForm>
   ```

### 8. Density Tables
1. Table configuration:
   ```xml
   <Table
       growing="true"
       growingThreshold="10"
       class="sapUiSizeCompact">
       <columns>
           <Column>
               <Text text="Column 1"/>
           </Column>
           <Column>
               <Text text="Column 2"/>
           </Column>
       </columns>
       <items>
           <ColumnListItem>
               <cells>
                   <Text text="{/value1}"/>
                   <Text text="{/value2}"/>
               </cells>
           </ColumnListItem>
       </items>
   </Table>
   ```

2. Table features:
   ```xml
   <Table
       growing="true"
       growingThreshold="10"
       class="sapUiSizeCompact">
       <headerToolbar>
           <Toolbar>
               <Title text="Table Title"/>
               <ToolbarSpacer/>
               <Button text="Action"/>
           </Toolbar>
       </headerToolbar>
       <columns>
           <Column>
               <Text text="Column"/>
           </Column>
       </columns>
       <items>
           <ColumnListItem>
               <cells>
                   <Text text="{/value}"/>
               </cells>
           </ColumnListItem>
       </items>
   </Table>
   ```

### 9. Best Practices for Content Density
- Use appropriate density mode for target devices
- Test on different screen sizes
- Consider touch vs. non-touch devices
- Maintain consistent spacing
- Use responsive layouts
- Consider accessibility requirements
- Test with different themes
- Handle density changes gracefully
- Use appropriate control sizes
- Consider form layouts
- Implement proper spacing
- Use appropriate margins and padding
- Consider table layouts
- Handle dynamic content
- Test with different browsers
- Follow SAPUI5 guidelines
- Consider performance implications
- Use appropriate font sizes
- Implement proper alignment
- Consider visual hierarchy

## Accessibility

### 1. ARIA Support
1. ARIA attributes:
   ```xml
   <Button
       ariaDescribedBy="description"
       ariaLabelledBy="label">
       <Text text="Accessible Button"/>
   </Button>
   <Text id="label" text="Button Label"/>
   <Text id="description" text="Button Description"/>
   ```

2. ARIA roles:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessible Page">
           <content>
               <VBox role="main">
                   <Text text="Main Content"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 2. Keyboard Navigation
1. Keyboard handling:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.controller.View1", {
           onKeyDown: function(oEvent) {
               if (oEvent.getParameter("keyCode") === sap.ui.core.KeyCodes.ENTER) {
                   // Handle Enter key
               }
           }
       });
   });
   ```

2. Keyboard shortcuts:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.controller.View1", {
           onInit: function() {
               this.getView().addEventDelegate({
                   onkeydown: function(oEvent) {
                       if (oEvent.ctrlKey && oEvent.keyCode === 83) {
                           // Handle Ctrl+S
                           oEvent.preventDefault();
                       }
                   }
               });
           }
       });
   });
   ```

### 3. Screen Reader Support
1. Screen reader text:
   ```xml
   <Button
       ariaLabel="Custom Label"
       tooltip="Button Tooltip">
       <Text text="Button Text"/>
   </Button>
   ```

2. Screen reader announcements:
   ```javascript
   sap.ui.require([
       "sap/ui/core/Announcement"
   ], function(Announcement) {
       Announcement.announce("Important message", "assertive");
   });
   ```

### 4. High Contrast Mode
1. High contrast support:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="High Contrast Page">
           <content>
               <VBox class="sapUiHighContrast">
                   <Text text="High Contrast Content"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

2. Theme adaptation:
   ```javascript
   sap.ui.getCore().attachThemeChanged(function() {
       // Handle theme changes
   });
   ```

### 5. Focus Management
1. Focus handling:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.controller.View1", {
           onFocus: function(oEvent) {
               // Handle focus event
           }
       });
   });
   ```

### 6. Accessibility Properties
1. Define accessibility properties:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Page">
           <content>
               <VBox>
                   <Text text="Accessible Content"/>
                   <Button text="Accessible Button"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 7. Accessibility Testing
1. Test accessibility:
   ```javascript
   sap.ui.define([
       "sap/ui/core/mvc/Controller"
   ], function(Controller) {
       "use strict";
       return Controller.extend("com.example.controller.View1", {
           onInit: function() {
               // Test accessibility
               sap.ui.getCore().attachInit(function() {
                   sap.ui.require([
                       "sap/ui/test/Accessibility"
                   ]);
               });
           }
       });
   });
   ```

### 8. Accessibility Guidelines
1. Follow accessibility guidelines:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Page">
           <content>
               <VBox>
                   <Text text="Accessible Content"/>
                   <Button text="Accessible Button"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 9. Consider User Preferences
1. Implement user preferences:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="User Preferences Page">
           <content>
               <VBox>
                   <Text text="User Preferences"/>
                   <Select>
                       <items>
                           <core:Item text="Default"/>
                           <core:Item text="High Contrast"/>
                           <core:Item text="Large Font"/>
                       </items>
                   </Select>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 10. Support Custom Accessibility Features
1. Implement custom accessibility features:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Page">
           <content>
               <VBox>
                   <Text text="Accessible Content"/>
                   <Button text="Custom Accessibility Feature"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 11. Document Accessibility Features
1. Document accessibility features:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Page">
           <content>
               <VBox>
                   <Text text="Accessible Content"/>
                   <Button text="Accessibility Features"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 12. Train Development Team
1. Train developers on accessibility:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Training">
           <content>
               <VBox>
                   <Text text="Accessibility Training"/>
                   <Button text="Accessibility Training"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 13. Regular Accessibility Audits
1. Conduct regular accessibility audits:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Audit">
           <content>
               <VBox>
                   <Text text="Accessibility Audit"/>
                   <Button text="Accessibility Audit"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

### 14. Monitor Accessibility Compliance
1. Monitor accessibility compliance:
   ```xml
   <mvc:View
       controllerName="com.example.controller.View1"
       xmlns:mvc="sap.ui.core.mvc"
       xmlns="sap.m">
       <Page title="Accessibility Compliance">
           <content>
               <VBox>
                   <Text text="Accessibility Compliance"/>
                   <Button text="Accessibility Compliance"/>
               </VBox>
           </content>
       </Page>
   </mvc:View>
   ```

## Building the Application

### 1. Build Configuration
1. Build settings in `ui5.yaml`:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   framework:
     name: SAPUI5
     version: "1.120.0"
     libraries:
       - name: sap.m
       - name: sap.ui.core
   builder:
     customTasks:
       - name: ui5-task-zipper
         afterTask: generateCachebusterInfo
         configuration:
           archiveName: "myapp"
   ```

2. Build options in `package.json`:
   ```json
   {
     "scripts": {
       "build": "ui5 build",
       "build:prod": "ui5 build --config ui5.yaml --dest dist",
       "build:dev": "ui5 build --config ui5.yaml --dest dist --dev"
     }
   }
   ```

### 2. Build Tools
1. UI5 Tooling setup:
   ```bash
   npm install --save-dev @ui5/cli
   ```

2. Build commands:
   ```bash
   # Development build
   ui5 build --config ui5.yaml --dest dist --dev
   
   # Production build
   ui5 build --config ui5.yaml --dest dist
   ```

### 3. Build Process
1. Build steps:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     resources:
       excludes:
         - "/test/**"
         - "/localService/**"
     customTasks:
       - name: ui5-task-zipper
         afterTask: generateCachebusterInfo
   ```

2. Build pipeline:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     customTasks:
       - name: ui5-task-zipper
         afterTask: generateCachebusterInfo
       - name: ui5-task-compileless
         afterTask: replaceVersion
       - name: ui5-task-uglify
         afterTask: replaceVersion
   ```

### 4. Build Optimization
1. Resource optimization:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     resources:
       excludes:
         - "/test/**"
         - "/localService/**"
     customTasks:
       - name: ui5-task-uglify
         afterTask: replaceVersion
         configuration:
           compress: true
           sourceMap: true
   ```

2. Performance optimization:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     customTasks:
       - name: ui5-task-compileless
         afterTask: replaceVersion
       - name: ui5-task-uglify
         afterTask: replaceVersion
         configuration:
           compress: true
           sourceMap: true
   ```

### 5. Build Deployment
1. Deployment configuration:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     customTasks:
       - name: ui5-task-zipper
         afterTask: generateCachebusterInfo
         configuration:
           archiveName: "myapp"
   ```

2. Deployment process:
   ```bash
   # Build for production
   ui5 build --config ui5.yaml --dest dist
   
   # Deploy to server
   # (Use your preferred deployment method)
   ```

### 6. Build Testing
1. Test configuration:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     resources:
       excludes:
         - "/test/**"
   ```

2. Test process:
   ```bash
   # Run tests before build
   npm run test
   
   # Build with tests
   ui5 build --config ui5.yaml --dest dist
   ```

### 7. Build Monitoring
1. Monitoring setup:
   ```yaml
   specVersion: '3.0'
   metadata:
     name: com.example.app
   type: application
   builder:
     customTasks:
       - name: ui5-task-compileless
         afterTask: replaceVersion
   ```

2. Monitoring tools:
   ```bash
   # Development build with monitoring
   ui5 build --config ui5.yaml --dest dist --dev
   
   # Production build with monitoring
   ui5 build --config ui5.yaml --dest dist
   ```

### 8. Build Best Practices
- Use UI5 Tooling for builds
- Configure build in ui5.yaml
- Use appropriate build tasks
- Optimize resources
- Handle dependencies properly
- Test before building
- Monitor build process
- Document build steps
- Use version control
- Implement CI/CD
- Follow security guidelines
- Consider performance implications
- Use appropriate compression
- Implement proper caching
- Handle environment variables
- Follow coding standards
- Implement proper logging
- Handle build artifacts
- Consider deployment strategy

### 9. Build Troubleshooting
1. Common issues:
   - Build failures
   - Performance issues
   - Dependency conflicts
   - Resource optimization
   - Deployment problems
   - Testing failures
   - Monitoring issues
   - Security concerns
   - Version conflicts
   - Environment issues

2. Solutions:
   - Check build logs
   - Verify dependencies
   - Test in isolation
   - Monitor performance
   - Review security
   - Update UI5 Tooling
   - Clean build
   - Check versions
   - Verify environment
   - Document issues
