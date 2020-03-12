![SculptUI Logo](images/sculpt-logo.png)
![VSCode Logo](images/vscode-icon.png)

# SculptUI - VS Code Extension

_"Where is that element on the page in my code?"_

This VS Code extension let's you jump right to the relevant source code lines for a React element by clicking it in your browser.

## Features

Run your application and select any component to jump right into the code section where it is defined inside the [VS Code](https://code.visualstudio.com/) editor.

<!-- TODO: Gif showing selection of element. -->
<img src="images/SculptUI-vscode-demo.gif" width="864" height="540" alt="">

This is just the start. We aim to revolutionize software development to help you create and extend software in a way that feels natural.
We are working hard on more features which you can look forward to:

- Styling directly in your runtime view (supporting [styled-components](https://styled-components.com/), [Material-UI styles](https://material-ui.com/styles/basics/), [CSS/SCSS modules](https://create-react-app.dev/docs/adding-a-css-modules-stylesheet), in-line styles, etc.)
- Full WYSWYG component editing - like inserting and moving around components using drag-and-drop, extracting component parts to a new component
- Pluggable custom property editors for component libraries
- Support for more UI frameworks and libraries (i.e. [Angular](https://angular.io/), [Vue](https://vuejs.org/), Web Components and more)

## Getting started

- `Install this extension in your VS Code`<br/>
  Install the extension by clicking on the Extensions icon in the Activity Bar on the side of VS Code, searching for "SculptUI" and then pressing the "Install" button.

- `Press the "Start SculptUI" button in the status bar`<br/>
  When you have a folder open containing a CRA project just use the "Start SculptUI" button shown at the bottom in the status bar of VS Code. Your web application is compiled, dev server started and the browser opened running your app.

- `Click element in the browser to jump to code line`<br/>
  Now you can enjoy the magic, just click on any component in the browser to select the matching code right inside your VSCode editor.

## Status

At the moment this is experimental and only React components are supported on projects based on [Create React App](https://create-react-app.dev/) (unejected or using [react-app-rewired](https://github.com/timarney/react-app-rewired)). But keep updated because we're fixing and extending fast. Please help us make this perfect for the way you work by sending us your feedbacks, issues and feature requests to our [issues list](https://github.com/sculptui/vscode/issues).

## Requirements

- Visual Studio Code Version 1.35 and higher
- Project using [react-scripts](https://github.com/facebook/create-react-app/tree/master/packages/react-scripts) (version 2.0 and above) from [Create React App](https://github.com/facebook/create-react-app/)
  - works with [react-app-rewired](https://github.com/timarney/react-app-rewired)
  - doesn't work when react-scripts has been ejected

## Extension Settings

The following can be configured in the extensions settings:

- `sculpt-ui.folderForStarting`: Set a specific sub folder to start sculpt in. This folder should be configured to your React client application if this is not in your root folder.Use relative path (i.e. '\\client').
- `sculpt-ui.port`: Override the port(s) sculpt server listens on. If nothing set the usual port for the development server (normally 3000) is used. Format can be either '9999' for a single port or '9000-9099' for a port range where the first available port is retrieved.
- `sculpt-ui.https`: Set to run the sculpt server in https mode. Only needed if the default configuration needs to be explicitly overriden.

---

## Troubleshooting

### SculptUI not showing in the status bar

- On activation SculptUI will check for [react-scripts](https://github.com/facebook/create-react-app/tree/master/packages/react-scripts) and the required version (see [Requirements](#requirements)). If one of the requirements are not matched the SculptUI status bar will not be shown. You could try running SculptUI using the extensions commands (press Ctrl/Cmd + Shift + P to display the editor’s command palette, and then type SculptUI to see the list of the available commands). But most probably the requirements are not met and SculptUI can not be used on your project.

- Make sure the react-scripts is in the ./node_modules folder and is version 2.0 or higher. Have you run "npm install" or "yarn install" already?

### Possible errors when running

- _Building in wrong folder_: By default SculptUI will start the web application in the root folder. If your application is in a subfolder you need to set the extension setting "sculpt-ui.folderForStarting" (see [Extension Settings](#extension-settings)) in your workspace.

- _Application requires specific port_: Sometimes applications, API or firewalls are configured to only work on a specific port. You can change the port used by SculptUI (by default 3000) to what you need in the [Extension Settings](#extension-settings).

- _Still not compiling_: Check the terminal window "SculptUI", where you will usually find any compilation or other errors. Also make sure your app builds correctly without SculptUI (running "npm start" or "yarn start" in the terminal).

## Issues & Feature Requests

If you have any feedbacks, issues or feature requests please post them on our [issues list](https://github.com/sculptui/vscode/issues).

---

## Release Notes

### 0.2.1

- shows feedback notification at bottom right when element has been selected successfully in IDE
- fix: overriding port and https in extensions settings now works correctly

### 0.2.0

Initial public release of SculptUI VS Code Extension

**Enjoy!**
