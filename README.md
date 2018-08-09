This plugis is a fork of `mini-css-extract-plugin` but with a support for `WebpackRTLPlugin`. Namely, it allows to load async CSS files depending of page's current direction. Please check mentioned packages to learn how to use them.

```bash
npm install --save-dev mini-css-extract-plugin-with-rtl
```

<h2 align="center">Usage</h2>

### Configuration

**webpack.config.js**

```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin-with-rtl");
const WebpackRTLPlugin = require("webpack-rtl-plugin");

module.exports = {
  plugins: [
    new MiniCssExtractPlugin({
      filename: "[name].css",
      rtlEnabled: true,
      rtlGlobalVar: 'pageDir' // Value should be 'rtl' to activate RTL mode. If not specified, document.dir will be used instead
    }),
    new WebpackRTLPlugin() // You must not pass filename option
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: MiniCssExtractPlugin.loader,
          },
          "css-loader"
        ]
      }
    ]
  }
}
```

## License

#### [MIT](./LICENSE)