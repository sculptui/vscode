# Custom Setup

If you are not using plain Creact React App (optionally using react-app-rewired or craco) or NextJs using a customized setup, you will need to extend your setup to start Sculpt.

If only the start script has been changed (i.e. to start a server as well), then you can check instructions for [Custom Script](#custom-script).

If you are using a [Custom Server](https://nextjs.org/docs/advanced-features/custom-server) in a NextJs project check out [NextJs Custom Server](#nextjs-custom-server).

If you can't find a way to get your setup to work add an issue in our [issues list](https://github.com/sculptui/vscode/issues).

## Custom Script

If you are using custom scripts to start your application in development (i.e. to also start a server), configure the needed commands in your package.json similar to the "start" script. SculptUI will use this script to run.

Just add your script to the scripts/sculpt in your [package.json](https://docs.npmjs.com/creating-a-package-json-file).

Example:

```JSON
{
  ...
  "scripts": {
    "start": "react-app-rewired start",
    "server": "node-env-run server --exec nodemon | pino-colada",
    ...
    "sculpt": "concurrently \"yarn server\" sculpt",
  },
  ...
}
```

The above example uses [concurrently](https://www.npmjs.com/package/concurrently) to start the server script and then start the client. But you can add any other commands to your script and call sculpt to start the sculpt dev server.

## NextJs Custom Server

In case you are using a [Custom Server](https://nextjs.org/docs/advanced-features/custom-server) (server.js) in your NextJs project you can add the following to run Sculpt with your server script:

- Install @sculpt-ui/server npm package as a dev dependency

  Using npm

  ```
  npm install @sculpt-ui/server --save-dev
  ```

  Using yarn

  ```
  yarn add @sculpt-ui/server --dev
  ```

- Include Sculpt Middleware in your server.js

  Add the Sculpt Middleware as middleware to your [Custom Server](https://nextjs.org/docs/advanced-features/custom-server) script (server.js) using createSculptMiddleware() from @sculpt-ui/server package, similar to following example:

  ```JavaScript
  process.env.NODE_ENV = process.env.NODE_ENV || 'development';

  const express = require('express');
  const next = require('next');
  const dev = process.env.NODE_ENV !== 'production';
  const port = process.env.PORT || 3000;
  const app = next({ dev });
  const handle = app.getRequestHandler();

  app.prepare().then(() => {
    const server = express();
    if (dev) {
      const { createSculptMiddleware } = require('@sculpt-ui/server');
      server.use(createSculptMiddleware());
    }
    server.get('*', (req, res) => {
      return handle(req, res);
    });

    server.listen(port, () => console.info(`Listening on http://localhost:${port}`));
  });

  ```

- Include Sculpt Babel Plugin in your .babelrc

  If you already have the [.babelrc](https://nextjs.org/docs/advanced-features/customizing-babel-config) file in your root folder just add "sculpt-ui/server/babel" to your plugins list. Otherwise create a <code>.babelrc</code> file in your root folder and add following content:

  ```JSON
  {
    "presets": ["next/babel"],
    "plugins": ["@sculpt-ui/server/babel"]
  }
  ```

- Configure Sculpt to run the custom server

  ```
  {
    ...
    <scripts>
      ...
      "sculpt": "node ./server.js"
    <scripts>
    ...
  }
  ```
