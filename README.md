

# Setup

Please make sure you have the following software installed before arriving at the workshop or beginning the course.

#### General Packages

Please make sure you have the following general software installed

| Required | Library | Version Range | Notes |
| ------------- | ------------- | ---| --- |
| ✔ | [Node.js](http://nodejs.com/)  | >= 7.10 | [nvm](https://github.com/creationix/nvm) is highly recommended for managing multiple node versions on a single machine |
| ✔ | [Visual Studio Code](https://code.visualstudio.com/)  | >= 1.14 | We'll be using several specific features of the VS Code editor. We can't force you to use it, but you'll miss out if you don't! |
| ✔ | [Yarn](https://yarnpkg.com/)  | >= 0.24 | An alternative to [npm](https://github.com/npm/npm) |
| ✔ | [Firefox](https://www.mozilla.org/en-US/firefox/new/)  | >= 50 | We'll need Firefox briefly in order to create certificates. |
| ✔ | [SQLite 3](http://sqlite.com/)  | >= 3 | Embedded database |

#### VS Code Extensions

Additionally, to take advantage of syntax hilighting, static code analysis and other editor features, you'll want to install the latest version of the following VS Code extensions

| Required | Extension | Notes |
| ------------- | ------------- | --- |
| ✔ | [sass-indented](https://marketplace.visualstudio.com/items?itemName=robinbentley.sass-indented) | Syntax highlighting and code completion support for [Sass](http://sass-lang.com) stylesheets |
| ✔ | [eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) | Static code analysis for JavaScript and JSX files |
| ✔ | [jest](https://marketplace.visualstudio.com/items?itemName=Orta.vscode-jest) | Syntax highlighting for [Jest snapshot testing](https://facebook.github.io/jest/docs/snapshot-testing.html) and in-editor test pass/fail statuses |
|   | [vscode-icons](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons) | Better file and folder icons |
|   | [rest-client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) | An in-editor REST client, so we can experiment with our API effortlessly |

#### Global Node.js Packages

Make sure you have these npm packages installed globally. This can be done by running

```
npm install -g <package-name>
```

| Required | Library | Version Range |
| ------------- | ------------- | ---|
| ✔ | [babel-eslint](https://github.com/babel/babel-eslint)  | ^7.0.0 |
| ✔ | [eslint](https://github.com/eslint/eslint) | ^4.0.0 |
| ✔ | [eslint-plugin-babel](https://github.com/babel/eslint-plugin-babel)  | ^4.0.0 |
| ✔ | [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react)  | ^7.1.0 |
| ✔ | [web-push](https://github.com/web-push-libs/web-push)  | ^3.0.0 |

#### Project setup

Finally, while in the top-level folder of this project, download the and install this project's dependencies by running

```
yarn
```

We'll also need some certificates so we can run a development webserver over HTTPS. You can generate them by running

```
npm run prepcerts
```

To start the server, run

```sh
npm run watch
```

(Pro tip: If everything looks like it works, but you can't access the page in your browser, make sure you're using *HTTPS*. Try [https://localhost:3000/](https://localhost:3000/).)

# Files and Folders

This is a free-standing client/server Progressive Web App system, including

* A database
* A REST API
* A web client, which starts out as a conventional single-page app, and becomes a progressive web app you progress through the workshop

````
 Project
 │
 ├─ client/            📱 React.js web client
 │  ├─ components/     📊 React components
 │  │  │
 │  │  ├─ my-thing/index.jsx        Component implementation
 │  │  ├─ my-thing/index.test.js    Component tests
 │  │  └─ my-thing/styles.scss      Component styles
 │  │
 │  ├─ routes/         🔝 Top-level React components, each corresponding to a "page" in our app
 │  ├─ sass/           💅 Global Sass stylesheets
 │  ├─ app.jsx         🎁 React "App" component  
 │  ├─ index.js        🎬 Web client entry point
 │  └─ index.ejs       📄 Template for web client index.html
 │
 ├─ db/                💾 SQLite databases
 ├─ dist/              📦 Web client development/production builds
 ├─ server/            🛒 Node.js API to support the web client
 ├─ webpack/           ⚙️ Build configuration
 └─ .vapid.json        🔐 VAPID private and public keys
````

# How to use it

#### Generate x509 Certificates for serving over HTTPS

`npm run prepcerts`

#### Start the Development Server

To start the development server, run

```sh
npm run watch
```

If you want, you can start the API and UI independently, by running

```sh
npm run watch:api # API only
npm run watch:ui # UI only
```

#### Build Development Assets in the `/dist` folder
This will be an un-minified version of an exercise, and will include some webpack-specific tooling, intended only for development use

`npm run build:dev`

#### Build Production Assets in the `/dist` folder
This will be an an optimized version of the exercise

`npm run build:dist`

#### Run tests

`npm test`

#### Clean old builds

`npm run clean`

# What are the pieces?

* [Webpack 3](https://webpack.js.org)
* [Babel](http://babeljs.io/) 7.x, setup with the [babel-preset-env](https://github.com/babel/babel/tree/7.0/packages/babel-preset-env) plugins, compiling to ES5 JavaScript
* [ESLint](https://github.com/eslint/eslint) for linting JS and JSX
* [sass-loader](https://github.com/webpack-contrib/sass-loader) for traditional management of [Sass](http://sass-lang.com/) styles
* [extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin) so compiled styles are external stylesheets instead of inline style blocks
* [React](http://facebook.github.io/react/) as a component library
* [MUI](https://www.muicss.com/) as a lightweight (6.6K) Material Design inspired UI kit
* [Jest](http://facebook.github.io/jest/) as a testing platform
* [SimpleHTTP2Server](https://github.com/GoogleChrome/simplehttp2server) as a HTTP/2 proxy (for development only)
* [SQLite3](https://www.sqlite.org/) - as a lightweight, embedded database (for API)
* [Express](http://expressjs.com/) - as a HTTP server for our API.


