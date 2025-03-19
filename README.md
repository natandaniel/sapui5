[Previous sections remain unchanged until XML Views section...]

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
