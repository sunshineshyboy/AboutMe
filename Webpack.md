# demo1

```html
index.html

<html>
  <body>
    <script type="text/javascript" src="bundle.js"></script>
  </body>
</html>
```

```javascript
main.js

document.write('<h1>Hello World</h1>');
```

```javascript
webpack.config.js

module.exports = {
  entry: './main.js',
  output: {
    filename: 'bundle.js'
  }
};
```

> webpack

```javascript
bundle.js

(function(modules) { ... })
([
  (function(module, exports) {
    document.write('<h1>Hello World</h1>');
  })
]);
```
