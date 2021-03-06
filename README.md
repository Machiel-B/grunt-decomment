grunt-decomment
===============

Uses [decomment] to remove comments from JSON, JavaScript, CSS, HTML, etc.

## Installing

```
$ npm install grunt-decomment --save-dev
```

## Example

```js
module.exports = function (grunt) {
    grunt.initConfig({
        decomment: {
            any: {
                // use the default `decomment()`, with parsing and auto-detection;
                files: {
                    "output.js": "input.js", // decomment a JavaScript file;
                    "output.json": "input.json", // decomment a JSON file;
                    "output.html": "input.html" // decomment an HTML file;
                }
            },
            text: {
                // use `decomment.text()` to process text-like files,
                // without parsing or validation: CSS, CPP, H, etc.
                options: {
                    type: 'text' // use method `decomment.text()`;
                },
                files: {
                    "output.css": "input.css", // decomment a CSS file;
                    "output.cpp": "input.cpp", // decomment a CPP file;
                    "output.h": "input.h" // decomment a C++ header file;
                }
            },
            html: {
                // use `decomment.html()` to process HTML-like files,
                // without any parsing or validation.
                options: {
                    type: 'html' // use method `decomment.html()`;
                },
                files: {
                    "output1.html": "input1.html",
                    "index.html": "index.html", // rewrite the source file;
                    "./.tmp/index.html": "./.tmp/index.html"
                }
            },
            withCwd: {
                options: {
                    type: 'text'
                },
                src: ['./*.css', './**/*.css', '!./vendor/**/*'], // array style with globs 
                dest: './', // output folder
                cwd: './dist/' // current working directory
            }
        }
    });

    grunt.loadNpmTasks('grunt-decomment');
    grunt.registerTask('default', ['decomment']);

};
```

## Options

#### type

Changes the default call into [decomment] to one according to the value:
* `text` - use method [decomment.text]
* `html` - use method [decomment.html]

#### safe, space, trim

Options supported by [decomment]:

* [safe]
* [space]
* [trim]

## License

Copyright © 2016 [Vitaly Tomilov](https://github.com/vitaly-t);
Released under the MIT license.

[decomment]:https://github.com/vitaly-t/decomment
[safe]:https://github.com/vitaly-t/decomment#optionssafe--boolean
[space]:https://github.com/vitaly-t/decomment#optionsspace--boolean
[trim]:https://github.com/vitaly-t/decomment#optionstrim--boolean
[decomment.text]:https://github.com/vitaly-t/decomment#decommenttexttext-options--string
[decomment.html]:https://github.com/vitaly-t/decomment#decommenthtmlhtml-options--string
