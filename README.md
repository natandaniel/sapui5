# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Application Bootstrapping](#application-bootstrapping)
3. [Controls](#controls)
4. [XML Views](#xml-views)
5. [Controllers](#controllers)
6. [Modules](#modules)
7. [JSON Model](#json-model)

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
