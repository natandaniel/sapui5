# SAPUI5 Development Guide

## Table of Contents
1. [Initial Setup](#initial-setup)

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
