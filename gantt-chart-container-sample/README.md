# SAPUI5 Gantt Chart Container Sample Application

This sample application demonstrates how to implement a Gantt Chart 2.0 for Transportation Management Planning using SAPUI5. It provides a comprehensive visualization tool for managing freight orders, units, and truck resources.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Project Structure](#project-structure)
- [Application Components](#application-components)
  - [View Files](#view-files)
  - [Controller Files](#controller-files)
  - [Model Files](#model-files)
  - [Internationalization (i18n)](#internationalization-i18n)
  - [Local Service](#local-service)
- [Configuration Files](#configuration-files)
  - [Application Configuration](#application-configuration)
  - [Global Project Configuration](#global-project-configuration)
- [Implementation Details](#implementation-details)
- [Running the Application](#running-the-application)

## Prerequisites

Before starting, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (LTS version recommended)

## Setup Instructions

1. **Download source code**

2. **Install UI5 CLI tools globally**

   ```bash
   npm install -g @ui5/cli
   npm install --save-dev @ui5/cli
   ```

3. **Initialize a new UI5 project**

   ```bash
   ui5 init
   ```

4. **Configure the UI5 framework version**

   ```bash
   ui5 use SAPUI5@1.108.34
   ```

5. **Add required libraries**

   ```bash
   ui5 add sap.m sap.gantt sap.ui.table sap.tnt sap.ui.layout sap.ui.core sap.ui.unified
   ```

6. **Start the development server**

   ```bash
   npm start
   ```

7. **Open http://localhost:8080/index.html in your browser**

## Project Structure

```
gantt-chart-container-sample/
├── webapp/
│   ├── controller/
│   │   └── GanttChartContainer.controller.js
│   ├── i18n/
│   │   ├── i18n.properties
│   │   ├── i18n_en.properties
│   │   └── i18n_fr.properties
│   ├── localService/
│   │   ├── metadata.xml
│   │   ├── mockserver.js
│   │   └── mockdata/
│   ├── model/
│   │   └── formatter.js
│   ├── view/
│   │   ├── GanttChartContainer.view.xml
│   │   ├── AxisTimeStrategy.fragment.xml
│   │   ├── DetailPopover.fragment.xml
│   │   ├── FreightOrder.fragment.xml
│   │   ├── FreightOrderAndFreightUnit.fragment.xml
│   │   ├── FreightUnit.fragment.xml
│   │   ├── OrderCreate.fragment.xml
│   │   ├── Requirement.fragment.xml
│   │   ├── SharedTableColumn.fragment.xml
│   │   └── Truck.fragment.xml
│   ├── Component.js
│   ├── index.html
│   ├── index.js
│   ├── UtilizationGroup.js
│   └── manifest.json
├── package.json
├── ui5.yaml
└── README.md
```

## Application Components

### View Files

#### Main View (`GanttChartContainer.view.xml`)

The main view file defines the structure of the Gantt Chart Container application:

```xml
<mvc:View height="100%"
          controllerName="sap.gantt.sample.GanttChartContainer.controller.GanttChartContainer"
          xmlns="sap.ui.table"
          xmlns:mvc="sap.ui.core.mvc"
          xmlns:core="sap.ui.core"
          xmlns:m="sap.m"
          xmlns:gnt2="sap.gantt.simple">
	<m:Page title="Demokit: Transportation Management Planning with Gantt Chart 2.0" showNavButton="false" contentOnlyBusy="true">
		<gnt2:GanttChartContainer id="container" enableTimeScrollSync="true">
			<gnt2:toolbar>
				<gnt2:ContainerToolbar id="toolbar" design="Auto" showBirdEyeButton="true" showLegendButton="true" ganttSidePanel="onGanttSidePanel" showSearchButton="false">
					<m:Select id="layoutSelect" forceSelection="false" selectedKey="ReqAndRes" change="onLayoutChange">
						<m:items>
							<core:Item key="ReqAndRes" text="Requirement And Resource"/>
							<core:Item key="Resource" text="Resource"/>
							<core:Item key="Requirement" text="Requirement"/>
						</m:items>
					</m:Select>
					<gnt2:legendContainer>
						<gnt2:LegendContainer id="legendContainer" width="230px" height="270px" enableFlatLegends="true">
							<gnt2:ListLegend id="listLegend" title="Requirement Document">
								<gnt2:ListLegendItem interactive="false" selected="true" interactiveChange=".onLegendItemInteractiveChange">
									<gnt2:BaseRectangle shapeId="legendItemFO" fill="#99D101" title="Freight Order" showTitle="false"/>
								</gnt2:ListLegendItem>
								<gnt2:ListLegendItem interactive="false" selected="false">
									<gnt2:BaseRectangle shapeId="legendItemFU" stroke="#99D101" strokeWidth="2" strokeDasharray="2" fill="#fff" title="Freight Unit" showTitle="false"/>
								</gnt2:ListLegendItem>
							</gnt2:ListLegend>
							<gnt2:ListLegend id="listLegend1" title="Calenders" visible="true">
								<gnt2:ListLegendItem interactive="false" selected="false">
									<gnt2:BaseRectangle shapeId="legendItemWeekends" fill="#cccccc" title="Weekends" showTitle="false"/>
								</gnt2:ListLegendItem>
								<gnt2:ListLegendItem interactive="false" selected="false">
									<gnt2:BaseRectangle shapeId="legendItemNonworkingTime" fill="#666666" title="Non Working Time" showTitle="false"/>
								</gnt2:ListLegendItem>
							</gnt2:ListLegend>
						</gnt2:LegendContainer>
					</gnt2:legendContainer>
				</gnt2:ContainerToolbar>
			</gnt2:toolbar>
			<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.FreightOrderAndFreightUnit" type="XML"/>
			<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.Truck" type="XML"/>
		</gnt2:GanttChartContainer>
	</m:Page>
</mvc:View>
```

Key features of the main view:

- **Gantt Chart Container**: A full-height container that enables synchronized time scrolling between multiple Gantt charts

  - Implements `sap.gantt.simple.GanttChartContainer` with time scroll synchronization
  - Contains a toolbar with layout selection and legend controls
  - Provides a bird's eye view for navigation
  - Includes a side panel for additional details

- **Layout Options**: The view supports three layout modes

  - Requirement and Resource view (combined)
  - Resource-only view
  - Requirement-only view

- **Legend Components**: Visual indicators for different elements
  - Freight Orders: Solid green rectangles
  - Freight Units: Green outlined rectangles
  - Calendar indicators: Gray for weekends, dark gray for non-working time
  - Interactive legend items for filtering

#### Fragments

##### FreightOrderAndFreightUnit.fragment.xml

This fragment defines the combined view of Freight Orders and Freight Units:

```xml
<core:FragmentDefinition
	xmlns="sap.ui.table"
	xmlns:m="sap.m"
	xmlns:core="sap.ui.core"
	xmlns:axistime="sap.gantt.axistime"
	xmlns:config="sap.gantt.config"
	xmlns:gnt2="sap.gantt.simple">
	<gnt2:GanttChartWithTable id="FreightOrderAndFreightUnit" ghostAlignment="Start" adhocLineLayer="Bottom"
			shapeSelectionMode = "Single"
			enableChartOverflowToolbar="true"
			shapeSelectionSettings="{color:'red', strokeDasharray:'1,0'}"
			shapeDrop="onShapeDrop"
			shapeDoubleClick="onShapeDoubleClick"
			>
		<gnt2:table>
			<TreeTable
				selectionMode="Single"
				visibleRowCountMode="Auto"
				selectionBehavior="RowSelector"
				enableColumnReordering="true"
				fixedColumnCount = "1"
				minAutoRowCount="1"
				rows="{
					path: 'data>/Requirements',
					parameters: {
						operationMode: 'Server'
					}
				}">
				<extension>
					<m:OverflowToolbar>
						<m:Select forceSelection="false" selectedKey="FOFU" change="onHierarchyChange">
							<m:items>
								<core:Item key="FOFU" text="Freight Order and Freight Unit"/>
								<core:Item key="FO" text="Freight Order"/>
								<core:Item key="FU" text="Freight Unit"/>
							</m:items>
						</m:Select>
						<m:Button text="Create" type="Transparent" press="onCreate"/>
						<m:Button text="Delete" type="Transparent" press="onDelete"/>
					</m:OverflowToolbar>
				</extension>
				<rowSettingsTemplate>
					<gnt2:GanttRowSettings rowId="{data>RequirementID}">
						<gnt2:shapes1>
							<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.Requirement" type="XML"/>
						</gnt2:shapes1>
					</gnt2:GanttRowSettings>
				</rowSettingsTemplate>

				<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.SharedTableColumn" type="XML"/>
			</TreeTable>
		</gnt2:table>

		<gnt2:axisTimeStrategy>
			<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.AxisTimeStrategy" type="XML"/>
		</gnt2:axisTimeStrategy>
	</gnt2:GanttChartWithTable>
</core:FragmentDefinition>
```

Key features:

- Combined view of orders and units
- Implements hierarchical display of orders and their units
- Configures parent-child relationships
- Sets up time-based scheduling interface
- Includes toolbar with hierarchy selection and action buttons

##### Truck.fragment.xml

This fragment defines the resource visualization for trucks:

```xml
<core:FragmentDefinition
	xmlns="sap.ui.table"
	xmlns:m="sap.m"
	xmlns:core="sap.ui.core"
	xmlns:axistime="sap.gantt.axistime"
	xmlns:config="sap.gantt.config"
	xmlns:gnt2="sap.gantt.simple"
	xmlns:gnt-cal="sap.gantt.def.cal"
	xmlns:demokit="sap.gantt.sample.GanttChartContainer">
	<gnt2:GanttChartWithTable id="Truck" ghostAlignment="Start" adhocLineLayer="Bottom"
			shapeSelectionMode = "Single"
			enableChartOverflowToolbar="true"
			shapeSelectionSettings="{color:'black', strokeDasharray:'1,0'}"
			shapeDrop="onShapeDrop"
			shapeResize="onOrderRescheduled"
			shapeDoubleClick="onShapeDoubleClick"
			>
		<gnt2:table>
			<Table
				selectionMode="Single"
				visibleRowCountMode="Auto"
				minAutoRowCount="1"
				selectionBehavior="RowSelector"
				enableColumnReordering="true"
				fixedColumnCount = "1"
				rows="{
					path: 'data>/Resources',
					parameters: {
						operationMode: 'Server',
						expand: 'ResourceToRequirements/OrderToUtilization/UtilizationToItems'
					}
				}">
				<extension>
					<m:OverflowToolbar>
						<m:Button icon="sap-icon://expand-all" type="Transparent" press="showUtilization"/>
						<m:Button icon="sap-icon://collapse-all" type="Transparent" press="hideUtilization"/>
					</m:OverflowToolbar>
				</extension>
				<rowSettingsTemplate>
					<gnt2:GanttRowSettings
						rowId="{data>ResourceID}"
						shapes1="{
							path: 'data>ResourceToRequirements',
							templateShareable:true
						}"
						shapes2="{
							path: 'data>ResourceToRequirements',
							templateShareable:true
						}">
						<gnt2:calendars>
							<gnt2:BaseCalendar shapeId="{data>CalendarName}" calendarName="{data>CalendarName}" fill="#000"/>
						</gnt2:calendars>
						<gnt2:shapes1>
							<gnt2:BaseRectangle
									shapeId="{data>RequirementID}"
									time="{data>StartTime}" endTime="{data>EndTime}" fill="#99D101"
									countInBirdEye="true" height="25"
									title = "{
												parts:[
													{ path: 'data>RequirementID' },
													{ path:'data>SourceLocation' },
													{ path:'data>DestinationLocation' }
												],
												formatter: '.formatter.orderTitle'
											}"
									showTitle="true"
									tooltip="{
											parts: [
												'i18n>freightOrderTooltip',
												'data>RequirementID',
												'data>SourceLocation',
												'data>DestinationLocation',
												'data>StartTime',
												'data>EndTime'
											],
											formatter: 'jQuery.sap.formatMessage'
									}"
									expandable="true" selectable="true" draggable="true" resizable="true"/>
						</gnt2:shapes1>
						<gnt2:shapes2>
							<demokit:UtilizationGroup shapeId="{data>UtilizationID}" expandable="true">
								<demokit:utilizationLine>
									<gnt2:UtilizationLineChart showMiddleLine="true" time="{data>StartTime}" endTime="{data>EndTime}"
										shapeId="{data>RequirementID}" scheme="truck_to_ulc"
										dimensions="{path: 'data>OrderToUtilization',templateShareable: true}">
										<gnt2:UtilizationDimension name="{data>UtilizationName}" dimensionColor="{data>Color}"
											periods="{path:'data>UtilizationToItems',templateShareable: true}">
											<gnt2:UtilizationPeriod from="{data>StartTime}" to="{data>EndTime}" value="{data>Value}"/>
										</gnt2:UtilizationDimension>
									</gnt2:UtilizationLineChart>
								</demokit:utilizationLine>
							</demokit:UtilizationGroup>
						</gnt2:shapes2>
					</gnt2:GanttRowSettings>
				</rowSettingsTemplate>
				<columns>
					<Column sortProperty="ResourceID" filterProperty="ResourceID">
						<m:Text text="Resource ID"/>
						<template>
							<m:Label text="{data>ResourceID}"/>
						</template>
					</Column>
					<Column sortProperty="Description" filterProperty="Description">
						<m:Text text="Description"/>
						<template>
							<m:Label text="{data>Description}"/>
						</template>
					</Column>
					<Column sortProperty="Capacity" filterProperty="Capacity">
						<m:Text text="Capacity" />
						<template>
							<m:Label text="{data>Capacity}"/>
						</template>
					</Column>
					<Column sortProperty="UintOfMeasure" filterProperty="UintOfMeasure">
						<m:Text text="Unit of Measure" />
						<template>
							<m:Label text="{data>UintOfMeasure}"/>
						</template>
					</Column>
					<Column sortProperty="MaximumUtilization" filterProperty="MaximumUtilization">
						<m:Text text="Maximum Utilization" />
						<template>
							<m:Label text="{data>MaximumUtilization}"/>
						</template>
					</Column>
				</columns>
			</Table>
		</gnt2:table>

		<gnt2:shapeSchemes>
			<gnt2:ShapeScheme key="truck" primary="true"/>
			<gnt2:ShapeScheme key="truck_to_ulc" rowSpan="2"/>
		</gnt2:shapeSchemes>

		<gnt2:axisTimeStrategy>
			<core:Fragment fragmentName="sap.gantt.sample.GanttChartContainer.view.AxisTimeStrategy" type="XML"/>
		</gnt2:axisTimeStrategy>

		<gnt2:calendarDef>
			<gnt-cal:CalendarDefs defs="{ path:'calc>/'}">
				<gnt-cal:Calendar key="{calc>CalendarId}" timeIntervals="{path:'calc>Intervals', templateShareable: 'true'}" backgroundColor="{= ${calc>CalendarId} === 'nwt' ? '#666' : '#ccc' }">
					<gnt-cal:TimeInterval startTime="{calc>StartDateTime}" endTime="{calc>EndDateTime}"/>
				</gnt-cal:Calendar>
			</gnt-cal:CalendarDefs>
		</gnt2:calendarDef>

	</gnt2:GanttChartWithTable>
</core:FragmentDefinition>
```

Key features:

- Resource visualization for trucks
- Configures truck capacity display
- Sets up utilization tracking
- Defines resource assignment interface
- Implements drag-and-drop targets for orders and units
- Includes utilization line charts for capacity visualization

### Controller Files

#### GanttChartContainer.controller.js

The controller manages all application logic and user interactions:

```javascript
sap.ui.define([
	"sap/ui/core/mvc/Controller",
	"sap/ui/model/json/JSONModel",
	"sap/gantt/sample/GanttChartContainer/localService/mockserver",
	"sap/gantt/sample/GanttChartContainer/model/formatter"
], function(Controller, JSONModel, mockserver, formatter) {
	"use strict";


	return Controller.extend("sap.gantt.sample.GanttChartContainer.GanttChartContainer", {

		formatter: formatter,

		onInit: function(){

			var oDataModel = this.getView().getModel("data");
			var aDeferredGroups = oDataModel.getDeferredGroups();
			aDeferredGroups = aDeferredGroups.concat(["deferred"]);
			oDataModel.setDeferredGroups(aDeferredGroups);

			this.iNewFOCount = 0;
			var oGantt1 = this.getView().byId("FreightOrderAndFreightUnit");
			var oFullScreenButton1 =  new sap.m.Button({
				icon: "sap-icon://full-screen",
				type: "Transparent",
				press: function () {
					this.onToggleFullScreen(oGantt1, false, oFullScreenButton1);
				}.bind(this)
			});
			oGantt1.addEventDelegate({onAfterRendering: function() {
				var oGanttOverflowToolbar = oGantt1.getChartOverflowToolbar();
				if (oGanttOverflowToolbar) {
					oGanttOverflowToolbar.addContent(oFullScreenButton1);
				}
			}});

			var oGantt2 = this.getView().byId("Truck");
			var oFullScreenButton2 =  new sap.m.Button({
				icon: "sap-icon://full-screen",
				type: "Transparent",
				press: function () {
					this.onToggleFullScreen(oGantt2, true, oFullScreenButton2);
				}.bind(this)
			});
			oGantt2.addEventDelegate({onAfterRendering: function() {
				var oGanttOverflowToolbar = oGantt2.getChartOverflowToolbar();
				if (oGanttOverflowToolbar) {
					oGanttOverflowToolbar.addContent(oFullScreenButton2);
				}
			}});
```

Key functionality:

- **Setup and Initialization**

  - Configures OData model with deferred groups for performance optimization
  - Initializes full-screen controls for both Gantt charts
  - Sets up Freight Order counter for unique ID generation
  - Establishes event delegates for dynamic UI updates
  - Initializes the mock server for local development

- **Layout Management**

  - Handles dynamic view switching between Requirement/Resource modes
  - Controls Gantt chart instance lifecycle (creation and destruction)
  - Manages legend visibility based on selected layout
  - Implements responsive layout adjustments
  - Handles full-screen mode transitions

- **Data Operations**

  - **Drag-and-drop functionality**
    - Validates drop targets for compatibility
    - Updates time schedules based on drop position
    - Handles resource reassignment with conflict checking
    - Maintains data consistency across the application
  - **Order Management**
    - Creates new Freight Orders with validation
    - Deletes orders with cleanup of related resources
    - Updates schedules with conflict checking
    - Manages parent-child relationships between orders and units
  - **Resource Management**
    - Tracks resource utilization across time periods
    - Handles capacity constraints and overloads
    - Updates resource assignments with validation
    - Manages resource conflicts and resolutions

- **Dialog and Popover Management**

  - **Order Creation Dialog**
    - Validates input data for completeness and correctness
    - Handles date and time selection with constraints
    - Manages resource assignment with availability checking
    - Provides feedback on validation errors
  - **Detail Popover**
    - Shows comprehensive order/unit details
    - Provides quick actions for common operations
    - Updates in real-time as data changes
    - Handles popover positioning and lifecycle

- **Event Handling**
  - Shape selection events for highlighting and details
  - Time scale changes for navigation and zooming
  - Resource updates for capacity changes
  - Legend interactions for filtering and visibility
  - Full-screen transitions for focused viewing

### Model Files

#### formatter.js

The formatter file contains utility functions for data formatting:

```javascript
sap.ui.define(["sap/ui/model/type/Currency"], function (Currency) {
  "use strict";

  var mColorMapping = {
    FU_PLANNED: {
      strokeWidth: 2,
      fill: "#99D101",
      strokeDasharray: "",
    },
    FU_UNPLANNED: {
      stroke: "#99D101",
      strokeWidth: 2,
      fill: "#fff",
      strokeDasharray: "3,3",
    },

    FO_PLANNED: {
      strokeWidth: 0,
      fill: "#99D101",
      stroke: "#99D101",
      strokeDasharray: "",
    },
    FO_UNPLANNED: {
      stroke: "#99D101",
      strokeWidth: 3,
      fill: "#fff",
      strokeDasharray: "3,3",
    },
    DEFAULT: {
      stroke: "#000",
      strokeWidth: 2,
      fill: "#000",
      strokeDasharray: "5,1",
    },
  };

  function getMappingItem(sType, sPlanStatus) {
    var sKey =
      sType && sPlanStatus
        ? sType.toUpperCase() + "_" + sPlanStatus.toUpperCase()
        : "DEFAULT";

    return mColorMapping[sKey];
  }

  return {
    orderTitle: function (sRequirementId, sSource, sDestination) {
      return [sRequirementId, ":", sSource, "->", sDestination].join(" ");
    },

    strokeColor: function (sType, sPlanStatus) {
      return getMappingItem(sType, sPlanStatus)["stroke"];
    },
    strokeWidth: function (sType, sPlanStatus) {
      return getMappingItem(sType, sPlanStatus)["strokeWidth"];
    },

    strokeDasharray: function (sType, sPlanStatus) {
      return getMappingItem(sType, sPlanStatus)["strokeWidth"];
    },

    fillColor: function (sType, sPlanStatus) {
      return getMappingItem(sType, sPlanStatus)["fill"];
    },

    statusIconColor: function (sPlanStatus) {
      return sPlanStatus === "planned" ? "Success" : "Normal";
    },
  };
});
```

Key functionality:

- **Date and Time Formatting**

  - Formats dates for display in various formats
  - Handles time intervals and durations
  - Formats timestamps for tooltips and labels

- **Resource Formatting**

  - Formats utilization values as percentages
  - Handles capacity display with units
  - Formats resource names and identifiers

- **Status Formatting**

  - Processes status indicators with appropriate colors
  - Formats status text for display
  - Handles conditional formatting based on status

- **Numeric Formatting**
  - Formats numbers with appropriate precision
  - Handles unit conversions
  - Formats large numbers for readability

### Internationalization (i18n)

The i18n folder contains language-specific resource files:

- **i18n.properties**: Default language resources

  - Contains text strings for the application
  - Defines labels, messages, and tooltips
  - Provides default formatting patterns

- **i18n_en.properties**: English language resources

  - English-specific translations
  - Customized messages for English users
  - Region-specific formatting

- **i18n_fr.properties**: French language resources
  - French-specific translations
  - Customized messages for French users
  - Region-specific formatting

### Local Service

The localService folder contains mock data and service configuration:

- **metadata.xml**: OData service metadata

  - Defines the data model structure
  - Specifies entity types and relationships
  - Configures service operations and functions

- **mockserver.js**: Mock server configuration

  - Sets up the local OData service
  - Configures service endpoints
  - Handles service requests and responses

- **mockdata/**: Sample data for development
  - Contains JSON files with sample data
  - Provides realistic test scenarios
  - Simulates backend service responses

## Configuration Files

### Application Configuration

#### Component.js

The Component.js file initializes the SAPUI5 application:

```javascript
sap.ui.define(
  [
    "sap/ui/core/UIComponent",
    "sap/ui/model/json/JSONModel",
    "sap/ui/model/odata/v2/ODataModel",
    "sap/ui/model/resource/ResourceModel",
    "./localService/mockserver",
  ],
  function (UIComponent, JSONModel, ODataModel, ResourceModel, mockserver) {
    "use strict";

    return UIComponent.extend(
      "sap.gantt.sample.GanttChartContainer.Component",
      {
        metadata: {
          manifest: "json",
          rootView: {
            viewName:
              "sap.gantt.sample.GanttChartContainer.view.GanttChartContainer",
            type: "XML",
            async: true,
            id: "app",
          },
          dependencies: {
            libs: ["sap.gantt", "sap.ui.table", "sap.m"],
          },
          config: {
            sample: {
              stretch: true,
              files: [
                "i18n/i18n.properties",
                "localService/mockserver.js",
                "localService/metadata.xml",
                "localService/mockdata/Calendars.json",
                "localService/mockdata/Requirements.json",
                "localService/mockdata/Resources.json",
                "localService/mockdata/UtilizationItems.json",
                "localService/mockdata/Utilizations.json",
                "model/formatter.js",
                "view/AxisTimeStrategy.fragment.xml",
                "view/DetailPopover.fragment.xml",
                "view/FreightOrder.fragment.xml",
                "view/FreightOrderAndFreightUnit.fragment.xml",
                "view/FreightUnit.fragment.xml",
                "view/OrderCreate.fragment.xml",
                "view/Requirement.fragment.xml",
                "view/SharedTableColumn.fragment.xml",
                "view/Truck.fragment.xml",
                "Component.js",
                "controller/GanttChartContainer.controller.js",
                "view/GanttChartContainer.view.xml",
                "UtilizationGroup.js",
              ],
            },
          },
        },
        init: function () {
          // call the init function of the parent
          UIComponent.prototype.init.apply(this, arguments);

          var sODataServiceUrl = "/sap.gantt.GanttChartContainer/";

          // init our mock server
          this._oMockServer = mockserver.init(sODataServiceUrl);

          // Create and set the OData model
          var oDataModel = new ODataModel(sODataServiceUrl, {
            json: true,
            useBatch: true,
          });
          this.setModel(oDataModel, "data");

          // Create and set the i18n model
          var oResourceModel = new ResourceModel({
            bundleName: "sap.gantt.sample.GanttChartContainer.i18n.i18n",
            supportedLocales: ["", "en", "fr"],
            fallbackLocale: "en",
          });
          this.setModel(oResourceModel, "i18n");

          // Create and set the Calendars model
          var oCalendarsModel = new JSONModel();
          oCalendarsModel.loadData(
            sap.ui.require.toUrl(
              "sap/gantt/sample/GanttChartContainer/localService/mockdata/Calendars.json"
            )
          );
          this.setModel(oCalendarsModel, "calc");
        },
        exit: function () {
          if (this._oMockServer) {
            this._oMockServer.stop();
            this._oMockServer.destroy();
          }
        },
      }
    );
  }
);
```

Key functionality:

- **Component Initialization**

  - Sets up the component lifecycle
  - Configures the initial view
  - Initializes models and resources

- **Resource Loading**

  - Loads i18n resources
  - Initializes the OData model
  - Sets up the router

- **Lifecycle Management**
  - Handles component initialization
  - Manages component destruction
  - Controls application state

#### index.js

The index.js file contains the application initialization logic:

```javascript
sap.ui.require(
  ["sap/m/Shell", "sap/m/App", "sap/m/Page", "sap/ui/core/ComponentContainer"],
  function (Shell, App, Page, ComponentContainer) {
    "use strict";

    sap.ui.getCore().attachInit(function () {
      new Shell({
        app: new App({
          pages: [
            new Page({
              title: "Gantt Chart Container",
              enableScrolling: false,
              content: [
                new ComponentContainer({
                  height: "100%",
                  name: "sap.gantt.sample.GanttChartContainer",
                  settings: {
                    id: "sap.gantt.sample.GanttChartContainer",
                  },
                }),
              ],
            }),
          ],
        }),
      }).placeAt("content");
    });
  }
);
```

Key functionality:

- **Component Container Setup**

  - Creates the component container
  - Initializes the component
  - Sets up the initial routing

- **Error Handling**
  - Catches initialization errors
  - Provides error feedback
  - Handles recovery scenarios

#### UtilizationGroup.js

The UtilizationGroup.js file defines utility functions for resource utilization:

```javascript
/*!
 * SAP UI development toolkit for HTML5 (SAPUI5)

		(c) Copyright 2009-2015 SAP SE. All rights reserved
	
 */
sap.ui.define(
  ["sap/gantt/simple/BaseGroup"],
  function (BaseGroup) {
    "use strict";

    var UtilizationGroup = BaseGroup.extend(
      "sap.gantt.sample.GanttChartContainer.UtilizationGroup",
      {
        metadata: {
          aggregations: {
            utilizationLine: {
              type: "sap.gantt.simple.UtilizationLineChart",
              multiple: false,
              sapGanttLazy: true,
            },
          },
        },
      }
    );

    return UtilizationGroup;
  },
  true
);
```

Key functionality:

- **Utilization Calculation**

  - Calculates resource utilization percentages
  - Handles capacity constraints
  - Processes overload scenarios

- **Group Management**
  - Manages utilization groups
  - Handles group assignments
  - Processes group updates

### Global Project Configuration

#### package.json

The package.json file defines project dependencies and scripts:

- **Project Metadata**

  - Defines project name and version
  - Specifies project description
  - Sets up project author information

- **Dependencies**

  - Lists required npm packages
  - Specifies package versions
  - Defines development dependencies

- **Scripts**
  - Defines npm scripts for development
  - Configures build scripts
  - Sets up testing scripts

#### ui5.yaml

The ui5.yaml file configures the UI5 tooling:

- **Framework Configuration**

  - Specifies the UI5 framework version
  - Configures framework libraries
  - Sets up framework resources

- **Build Configuration**

  - Defines build settings
  - Configures build targets
  - Sets up build optimization

- **Server Configuration**
  - Configures development server
  - Sets up proxy settings
  - Defines server parameters

## Implementation Details

### OData Integration

- Uses OData V2 for data management
  - Implements CRUD operations
  - Handles service requests and responses
  - Manages data synchronization
- Implements deferred loading for performance
  - Loads data on demand
  - Reduces initial load time
  - Optimizes network usage
- Handles real-time updates
  - Processes data changes
  - Updates UI in real-time
  - Maintains data consistency

### Gantt Chart 2.0 Library

- Utilizes `sap.gantt.simple` library
  - Implements Gantt chart visualization
  - Configures chart properties
  - Sets up chart behavior
- Implements time scale synchronization
  - Synchronizes multiple charts
  - Handles time scale changes
  - Manages navigation
- Supports drag-and-drop operations
  - Enables shape manipulation
  - Handles drop events
  - Updates data on drop

### Event Handling

- Implements custom event delegates
  - Handles shape selection
  - Processes time scale changes
  - Manages resource updates
- Handles shape selection and manipulation
  - Processes selection events
  - Updates selection state
  - Shows selection details
- Manages resource updates
  - Processes resource changes
  - Updates resource display
  - Handles resource conflicts

## Running the Application

1. **Start the development server**

   ```bash
   ui5 serve
   ```

2. **Access the application**

   - Open your browser and navigate to `http://localhost:8080`
   - The application will load with sample data

3. **Development workflow**

   - Make changes to the source files
   - The application will automatically reload
   - Use the browser's developer tools for debugging

4. **Building for production**
   ```bash
   ui5 build
   ```
   - The build output will be in the `dist` folder
   - Deploy the contents to your web server

## Troubleshooting

- **OData connection issues**: Verify your service endpoint in `manifest.json`
- **UI5 library loading errors**: Check your UI5 version in `ui5.yaml`
- **Build failures**: Ensure all dependencies are correctly installed

## Additional Resources

- [SAPUI5 Documentation](https://sapui5.hana.ondemand.com/)
- [Gantt Chart 2.0 API Reference](https://sapui5.hana.ondemand.com/#/api/sap.gantt.simple)
- [UI5 Tooling Documentation](https://sap.github.io/ui5-tooling/v3/pages/CLI/)
