# SculptUI VS Code Extension

SculptUI allows visually editing component-based JavaScript/TypeScript code. The SculptUI VS Code Extension allows to easily start your application and select any component to jump right to the code section it is defined.

At the moment this is very experimental and only React components are supported on projects based on Create React App (unejected or using react-app-rewired). That said though, we are working hard on extending SculptUI to support more project types, libraries and features.

Just some the features you can look forward to:
- Styling directly in your runtime view (supporting styled-components, Material-UI styles, CSS/SCSS modules, in-line styles, etc.)
- Full WYSWYG component editing - like inserting and moving around components using drag-and-drop, extracting component parts to a new component
- Support for more UI frameworks and libraries (i.e. Angular, Vue, Web Components and more)

## Getting started

To get started with SculptUI in VS Code, install the extension first by clicking on the Extensions icon in the Activity Bar on the side of VS Code and searching for SculptUI.

Once the extension is installed, press Ctrl/Cmd + Shift + P to display the editor’s command palette, and then type SculptUI to see the list of the available commands. When you have a folder open containing a CRA project just use the "SculptUI - Start" command which will run your app in a dev server. A browser should be opened running your app.
Now you are ready to go, just click on any component in the browser to select the matching code right inside your VSCode editor. 
