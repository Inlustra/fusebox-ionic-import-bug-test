# **Fusebox** Node Module issue

To run the project:

```
$ npm i
$ npm start
```

Expected issue:
```
Uncaught SyntaxError: Unexpected token import
```

Fusebox config **(fuse.js)**:
```
const { FuseBox, WebIndexPlugin, CSSPlugin, CSSResourcePlugin, SassPlugin, JSONPlugin, HTMLPlugin, TypeScriptHelpers } = require("fuse-box");

const fuse = FuseBox.init({
  homeDir: "src",
  output: "build/$name.js",
  plugins: [
    WebIndexPlugin({
      template: "src/index.html"
    }),
    [
      SassPlugin({ outputStyle: "compressed" }),
      CSSPlugin()
    ],
    [
      CSSResourcePlugin({
        inline: true
      }), CSSPlugin()
    ],
    TypeScriptHelpers(),
    JSONPlugin(),
    HTMLPlugin({ useDefault: false })
  ]
});

fuse.dev({ port: 8100 });

fuse.bundle("app")
  .instructions("> main.ts")
  .watch()
  .hmr()

fuse.run();
```
