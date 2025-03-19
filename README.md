# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Application Bootstrapping](#application-bootstrapping)
3. [Controls](#controls)

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

2. Create index.js in webapp directory:
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

3. Load index.js in index.html:
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
       <script src="index.js"></script>
   </head>
   <body class="sapUiBody">
       <div id="content"></div>
   </body>
   </html>
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

### 2. View Configuration
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

### 3. View Elements
- **mvc:View**: Root element
- **controllerName**: Controller reference
- **xmlns**: Namespace declarations
- **Controls**: UI elements within view

### 4. View Loading
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
