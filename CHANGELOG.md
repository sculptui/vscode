# Change Log

## [0.6.5] - 2021-06-07

### Added

- Preselect styles subtab depending on existing styles configured
- Support Material-UI styles using only @material-ui/styles package, without requiring @material-ui/core package

### Fixed

- After installing dependency for styling (styled-components, @material-ui/styles) it is not reloaded unless VSCode is reloaded
- Setting selector that contains dots (.) or other special characters causes error
- Tooltips sometimes not showing
- Errors when selecting Styled Component containing code structure not supported by Sculpt
- Showing parts of the styles editor (class names, pseudo selectors, create styled component links, etc.) before style data actually loaded
- Showing style module files multiple times in file selection when creating new class name
- Removing last style property in Styled Component generates incorrect code and compile error

## [0.6.4] - 2021-05-25

### Major new features

- **Styled Components**: The styles editor can now also be used to view and edit styling using [styled-components](https://styled-components.com/).

### Added

- New application bar with address (URL) of target application and commands
- Improved separation of the different styling approaches using subtabs (Classnames, Styled Components and Inline)
- Checks style packages (@materal-ui, styled-components) that are available
- Prefill file or object to use in the "Add new class name" dialog after adding a new file or object
- Improved transition when switching selected elements (less flashing)

### Fixed

- Fixed showing and reloading of styles editor when the data not yet fully loaded
- Loss of selection of classname tag when an update occurs

## [0.6.3] - 2021-05-06

### Major new features

- **Material-UI Styles**: The styles editor can now also be used to view and edit styling using [Material-UI Styles](https://material-ui.com/styles/basics/) with hook API and styled components API.

### Added

- Improved handling of loading at startup and after actions that require reloading.
- More clear layout of header with class names, path and pseudo selectors in styles editor.
- Shows info when selected class name is of an unsupported type.

### Fixed

- Hanging in blocked state if an error occurs on loading.
- Scrollbar can not be used in the autocomplete inputs for (style) property values.
- Clicking a link with ctrl key will open in a separate window and not inside Sculpt.
- On adding a new class name the name can contain invalid characters which causes errors.

## [0.6.2] - 2021-04-12

### Added

- Handle styling for css and scss files even when not imported in the module of selected element
- Show documentation on property editors when available
- Improved reloading in sculpt editor when changes in application code are made
- Separate section for positioning properties in styles editor
- CSS (scss, less) file is opened in VS Code when a classname is selected
- Color picker shows colors already used on page as suggested palette
- After creating a new file from the add new classname dialog this file is preselected
- Improved validation of properties in styles and properties editor
- Support for properties and styles editor even when no type information (type: any) is available

### Fixed

- Error when css is loaded from node modules
- Errors when projects without tsconfig file are used
- Some styling not changed when switching theme
- Children attribute can be set even when already element content available

## [0.6.1] - 2021-03-16

Fixed images for Visual Studio marketplace.

## [0.6.0] - 2021-03-16

### Major new features

- **Properties editor**: When selecting an element you can edit the properties in the browser. Changed properties are automatically saved to the source code.
- Style attributes overview: A section with all currently set style attributes provides an improved overview. Append a new attribute easily there too.

### Added

- Style attributes are validated. A message shows when the entered value is not valid.
- Improved formatting of classname property on adding or removing classnames (uses simple string, classnames() method or string literals where appropriate).
- Ability to select className from suggestions.
- Improved autosuggest for entering values of style attributes or properties.
- Indicator shows when the runtime application is still loading.
- Separate key (Ctrl) to temporarily toggle selection of elements in runtime app.-

### Fixes

- Fixed: Styles are shown even when element has no style property.
- Fixed: Classnames are shown even when element has not classname property.
- Fixed: Font size cannot be set to all possible values (i.e. smaller)
- Fixed: Unnecessary console messages from Sculpt.
- Various errors fixed that were caused by phases where the source code in the file system did not match the version in the runtime client.

## [0.5.0] - 2020-12-23

### Major new features

- **Styles editor**: When selecting an element you can edit the inline styles or the styles for css/scss/less (modules) classes referenced in classname property.
- Theming: Switch from dark to light mode depending on your preference or what's best for editing your application.

### Added

- Application runs in iFrame:
  - Errors in application code won't stop sculpt still showing
  - Avoids conflicts between application and sculpt
- No need for HTMLWebpackPlugin for injecting sculpt script to application page
- Will work without babel plugin (though columns will be missing if you are using older babel version)

### Fixes

- Fixed: When SculptUI terminal is manually closed, sculpt can't be started any more from VSCode extension.
- Fixed: When using HMR changing code can cause elements to have incorrect source line and column numbers.

## [0.4.1] - 2020-08-06

### Added

- support setting custom sculpt scripts in package.json (will be run if available)
- show element type next to element name in hover info (if different)
- Nextjs support: now reuses nextjs config if found
- Introduced devserver-middleware (injects sculpt client in html)
- Ignores yarn workspaces root for starting sculpt, unless sculpt explicitely configured in root package.json

### Changed

- ensure Controller is above all elements on page
- trim filepath in hoverinfo when too long (>60 chars)
- vscode extension: only showing relative folder for selecting project
- hover tooltip on controller not shown while moving/clicking
- SculptWebpackPlugin shows error if Babel loader is not available
- added "dontInjectScript" parameter to SculptWebpackPlugin

### Fixes

- fixed click on controller not working when browser not focused first

## [0.4.0] - 2020-05-25

### Added

- Support for projects using [Next.js](https://nextjs.org/)
- Support for projects using [craco](https://github.com/gsoft-inc/craco/) for overriding react-scripts
- Controller keeps active or inactive even after refreshing the browser tab
- Selected element stays selected even after refreshing the browser window or refresh due to hot module reload
- Detection of config overriding library used (i.e. react-app-rewired or craco)
- Secured vscode extension access using random id in Url
- Show in status bar when client(s) connected
- Retries to reconnect to devserver when controller is active

### Changed

- Improved and more efficient injection of sculpt client in html page using HtmlWebpackPlugin

### Fixed

- Bug: Sculpt injects div using space in host page causing layout changes (i.e. scroll bars)
- Bug: Elements with high z-index could be unselectable in SculptUI

## [0.3.1] - 2020-03-31

### Added

- Automatic reconnect to IDE when stopped and restarted
- Badge on controller button showing when connecting or error trying to connect to IDE or SculptUI dev server

## [0.3.0] - 2020-03-25

### Added

- automatic detection of subfolders containing react-scripts
- user selection when multiple react-scripts subfolders found
- option to save default for project folder on first run

### Changed

- IMPORTANT fix: now config-overrides when using react-app-rewired are correctly applied
- fix: proxy setting (in package.json) is now supported
- errors occuring in dev server are logged and shown to user

## [0.2.1] - 2020-03-12

### Added

- shows feedback notification at bottom right when element has been selected successfully in IDE

### Changed

- fix: overriding port and https in extensions settings now works correctly

## [0.2.0] - 2020-03-06

Initial public release of SculptUI VS Code Extension
