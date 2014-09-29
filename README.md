ckstyle-plugins
===============

plugins of ckstyle


## Plugin Demo

```javascript

function handle(code, options) {
    var result = code;
    // ... handle code here using options.
    return result  // return transformed css code here.
}

module.exports = handle
```

## Demo

- npm install `ckstyle`
- npm install `ckstyle-less`
- npm install `ckstyle-autoprefixer`

then...

```javascript
var CKStyle = require('ckstyle').CKStyle

var autoprefixer = require('ckstyle-autoprefixer')
var lesser = require('ckstyle-less')

var css = '.a {.b {width: 1 + 1; box-sizing: border-box;}}'

var res = CKStyle.start(css)
    .plugin(lesser)
    .plugin(autoprefixer)
    .fix(function(fixed) {
        console.log(fixed)      // ==> .a .b {
                                // ==>    width: 2;
                                // ==>       -moz-box-sizing: border-box;
                                // ==>            box-sizing: border-box;
                                // ==> }
    })
    .compress(function(min) {
        console.log(min)        // ==> .a .b{width:2;-moz-box-sizing:border-box;box-sizing:border-box}
    })
    .output()
console.log(res);               // ==> .a .b{width:2;-moz-box-sizing:border-box;box-sizing:border-box}
```
