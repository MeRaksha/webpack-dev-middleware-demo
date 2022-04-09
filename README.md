# webpack-dev-middleware-demo

Webpack Dev Middleware is middleware which can be mounted in an express server to serve the latest compilation of our bundle during development. This uses webpack's Node API in watch mode and instead of outputting to the file system it outputs to memory.

```sh
const express = require('express');
const webpack = require('webpack');
const webpackDevMiddleware = require('webpack-dev-middleware');

const app = express();
const config = require('./webpack.config.js');
const compiler = webpack(config);

app.use(
  webpackDevMiddleware(compiler, {
    publicPath: config.output.publicPath,
  })
);

// Serve the files on port 3000.
app.listen(3000, function () {
  console.log('Example app listening on port 3000!\n');
});
```
