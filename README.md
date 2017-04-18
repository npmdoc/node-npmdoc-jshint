# npmdoc-jshint

#### api documentation for  [jshint (v2.9.4)](http://jshint.com/)  [![npm package](https://img.shields.io/npm/v/npmdoc-jshint.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-jshint) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-jshint.svg)](https://travis-ci.org/npmdoc/node-npmdoc-jshint)

#### Static analysis tool for JavaScript

[![NPM](https://nodei.co/npm/jshint.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/jshint)

- [https://npmdoc.github.io/node-npmdoc-jshint/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-jshint/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-jshint/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-jshint/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-jshint/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-jshint/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Anton Kovalyov",
        "url": "http://anton.kovalyov.net/"
    },
    "bin": {
        "jshint": "./bin/jshint"
    },
    "bugs": {
        "url": "https://github.com/jshint/jshint/issues"
    },
    "dependencies": {
        "cli": "~1.0.0",
        "console-browserify": "1.1.x",
        "exit": "0.1.x",
        "htmlparser2": "3.8.x",
        "lodash": "3.7.x",
        "minimatch": "~3.0.2",
        "shelljs": "0.3.x",
        "strip-json-comments": "1.0.x"
    },
    "description": "Static analysis tool for JavaScript",
    "devDependencies": {
        "browserify": "9.x",
        "conventional-changelog": "0.4.x",
        "conventional-github-releaser": "0.4.x",
        "coveralls": "2.11.x",
        "istanbul": "0.3.x",
        "jscs": "1.11.x",
        "mock-stdin": "0.3.x",
        "nodeunit": "0.9.x",
        "phantom": "~0.7.2",
        "phantomjs": "1.9.13",
        "regenerate": "1.2.x",
        "sinon": "1.12.x",
        "unicode-6.3.0": "0.1.x"
    },
    "directories": {},
    "dist": {
        "shasum": "5e3ba97848d5290273db514aee47fe24cf592934",
        "tarball": "https://registry.npmjs.org/jshint/-/jshint-2.9.4.tgz"
    },
    "files": [
        "bin",
        "data",
        "dist",
        "src"
    ],
    "gitHead": "78b79c099fc490d93cd7aef599a1528761e9498d",
    "homepage": "http://jshint.com/",
    "license": "(MIT AND JSON)",
    "main": "./src/jshint.js",
    "maintainers": [
        {
            "name": "antonkovalyov"
        },
        {
            "name": "rwaldron"
        },
        {
            "name": "jugglinmike"
        }
    ],
    "name": "jshint",
    "optionalDependencies": {},
    "preferGlobal": true,
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jshint/jshint.git"
    },
    "scripts": {
        "browser-test-server": "node tests/helpers/browser/server",
        "build": "node bin/build",
        "changelog": "conventional-changelog -p jshint -i CHANGELOG.md -w",
        "coverage": "istanbul -- cover ./node_modules/.bin/nodeunit tests/unit",
        "data": "node scripts/generate-identifier-data",
        "github-release": "conventional-github-releaser -p jshint",
        "pretest": "node ./bin/jshint src && jscs src",
        "test": "npm run test-node && npm run test-browser",
        "test-browser": "node tests/browser",
        "test-cli": "nodeunit tests/cli.js",
        "test-node": "npm run test-unit && npm run test-cli && npm run test-regression",
        "test-regression": "nodeunit tests/regression",
        "test-unit": "nodeunit tests/unit"
    },
    "version": "2.9.4"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
