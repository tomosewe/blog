---
title: "Getting Started With Webpack, React, and Hot Reloading"
date: 2019-07-09T21:49:02+12:00
draft: false
---

> Inspiration for this post comes from the following links:
>
> - [Webpack 4 Tutorial: from 0 Conf to Production Mode](https://www.valentinog.com/blog/webpack/)
>
> - [How to Create a React app from scratch using Webpack 4](https://www.freecodecamp.org/news/part-1-react-app-from-scratch-using-webpack-4-562b1d231e75/)

This is essentially a **TLDR** of the first post. Compressed to just the tasks you need to get up and running. Follow along and all will work out in the end.

Let's start!

Start by making a new directory for your app.

``` bash
mkdir your-app-name-here && cd $
```

Create a new [npm](https://www.npmjs.com/) project.
``` bash
npm init -y
```

Install [webpack](https://github.com/webpack/webpack) and [wepback-cli](https://github.com/webpack/webpack-cli).

``` bash
npm i webpack --save-dev
npm i webpack-cli --save-dev
```

Add the following scripts in `package.json`

``` json
"scripts": {
  "dev": "webpack --mode development",
  "build": "webpack --mode production"
}
```

We need to install [babel](https://babeljs.io/) to help with transpiling.

Install these 4 packages:

- [babel-loader](https://github.com/babel/babel-loader)

- [@babel/core](https://babeljs.io/docs/en/next/babel-core.html)

- [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env)

- [@babel/preset-react](https://babeljs.io/docs/en/babel-preset-react)

``` bash
npm i babel-loader @babel/core @babel/preset-env @babel/preset-react --save-dev
```

Create a `.babelrc` file in your root directory with the following inside:

``` json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

To use loaders we need to create `webpack.config.js` in our root directory.

Add the following:

``` javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, // Transpile `.js` and `.jsx` files
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  }
};
```

---

## Loading HTML

Webpack needs plugins to handle `HTML`.

Install the following packages:

- [html-webpack-plugin](https://webpack.js.org/plugins/html-webpack-plugin/)

- [html-loader](https://github.com/webpack-contrib/html-loader)

``` bash
npm i html-webpack-plugin html-loader --save-dev
```

Update `webpack.config.js` with the following:

``` javascript
const HtmlWebPackPlugin = require("html-webpack-plugin");

module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, // Transpile `.js` and `.jsx` files
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: { minimize: true }
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```

Create a new `HTML` file at `./src/index.html`

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>your-app-name</title>
</head>
<body>
    <div id="app"></div>
</body>
</html>
```

Webpack will automatically add a `<script>` tag into the built `HTML` file when you build.

---

## Loading CSS

Install the following packages:

- [mini-css-extract-plugin ](https://github.com/webpack-contrib/mini-css-extract-plugin)

- [css-loader](https://github.com/webpack-contrib/css-loader)


``` bash
npm i mini-css-extract-plugin css-loader --save-dev
```

Create `./src/main.css` with the following for testing:

``` css
body {
  margin: 0 auto;
  width: 800px;
}
```

Update `webpack.config.js` with the following:

``` javascript
const HtmlWebPackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, // Transpile `.js` and `.jsx` files
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: { minimize: true }
          }
        ]
      },
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, "css-loader"]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    }),
    new MiniCssExtractPlugin({
      filename: "[name].css",
      chunkFilename: "[id].css"
    })
  ]
};
```

---

## React

Install [react](https://reactjs.org/) and [react-dom](https://reactjs.org/docs/react-dom.html).

``` bash
npm i react react-dom --save-dev
```

We need an entry point. By default webpack expects a file at `./src/index.js`

Create `./src/index.js` and add the following:

``` javascript
import React from "react";
import ReactDOM from "react-dom";
import "./main.css";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("app"));
```

Create `App.js` and add the following:

``` javascript
import React from "react";

const App = () => {
  return (
    <div>
      <p>React here!</p>
    </div>
  );
};

export default App;
```

---

## Webpack dev server

It's pretty annoying having to run `npm run dev` every time we make a change.

[webpack-dev-server](https://github.com/webpack/webpack-dev-server) allows us to see the changes we make in the browser every time we make a change.

Install [webpack-dev-server](https://github.com/webpack/webpack-dev-server).

``` bash
npm i webpack-dev-server --save-dev
```

Replace our scripts in `package.json` with the following:

``` json
"scripts": {
  "start": "webpack-dev-server --mode development --open --hot",
  "build": "webpack --mode production"
}
```

> Note: Adding `--hot` allows for [Hot Module Replacement](https://webpack.js.org/concepts/hot-module-replacement/) which means that only the changed component will be reloaded, so you won't lose your application state.

Run `npm start` and you'll see your changes update in the browser every time you make a change.

You can find a full working example of this at the following [repo](https://github.com/tomosewe/webpack-react-starter).
