# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Application Bootstrapping](#application-bootstrapping)
3. [Controls](#controls)
4. [XML Views](#xml-views)
5. [Controllers](#controllers)
6. [Modules](#modules)
7. [JSON Model](#json-model)
8. [Resource Bundles](#resource-bundles)
9. [Component Configuration](#component-configuration)
10. [Application Descriptors](#application-descriptors)
11. [Pages and Panels](#pages-and-panels)
12. [Shell Control](#shell-control)
13. [Margins and Paddings](#margins-and-paddings)
14. [Custom CSS and Theme Colors](#custom-css-and-theme-colors)
15. [Nested Views](#nested-views)
16. [Dialogs and Fragments](#dialogs-and-fragments)
17. [Fragment Callbacks](#fragment-callbacks)
18. [Icons](#icons)

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
