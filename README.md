# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Application Bootstrapping](#application-bootstrapping)
3. [Controls](#controls)

[Previous sections remain unchanged...]

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
```javascript
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
