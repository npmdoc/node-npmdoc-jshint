# api documentation for  [jshint (v2.9.4)](http://jshint.com/)  [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-jshint.svg)](https://travis-ci.org/npmdoc/node-npmdoc-jshint)
#### Static analysis tool for JavaScript

[![NPM](https://nodei.co/npm/jshint.png?downloads=true)](https://www.npmjs.com/package/jshint)

[![apidoc](https://npmdoc.github.io/node-npmdoc-jshint/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-jshint_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-jshint/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-jshint/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "author": {
        "name": "Anton Kovalyov",
        "email": "anton@kovalyov.net",
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
            "name": "antonkovalyov",
            "email": "anton@kovalyov.net"
        },
        {
            "name": "rwaldron",
            "email": "waldron.rick@gmail.com"
        },
        {
            "name": "jugglinmike",
            "email": "mike@mikepennisi.com"
        }
    ],
    "name": "jshint",
    "optionalDependencies": {},
    "preferGlobal": true,
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module jshint](#apidoc.module.jshint)
1.  [function <span class="apidocSignatureSpan">jshint.</span>JSHINT (s, o, g)](#apidoc.element.jshint.JSHINT)

#### [module jshint.JSHINT](#apidoc.module.jshint.JSHINT)
1.  [function <span class="apidocSignatureSpan">jshint.</span>JSHINT (s, o, g)](#apidoc.element.jshint.JSHINT.JSHINT)
1.  [function <span class="apidocSignatureSpan">jshint.JSHINT.</span>addModule (func)](#apidoc.element.jshint.JSHINT.addModule)
1.  [function <span class="apidocSignatureSpan">jshint.JSHINT.</span>data ()](#apidoc.element.jshint.JSHINT.data)
1.  [function <span class="apidocSignatureSpan">jshint.JSHINT.</span>jshint (s, o, g)](#apidoc.element.jshint.JSHINT.jshint)



# <a name="apidoc.module.jshint"></a>[module jshint](#apidoc.module.jshint)

#### <a name="apidoc.element.jshint.JSHINT"></a>[function <span class="apidocSignatureSpan">jshint.</span>JSHINT (s, o, g)](#apidoc.element.jshint.JSHINT)
- description and source-code
```javascript
JSHINT = function (s, o, g) {
  var x, reIgnoreStr, reIgnore;
  var optionKeys;
  var newOptionObj = {};
  var newIgnoredObj = {};

  o = _.clone(o);
  state.reset();

  if (o && o.scope) {
    JSHINT.scope = o.scope;
  } else {
    JSHINT.errors = [];
    JSHINT.undefs = [];
    JSHINT.internals = [];
    JSHINT.blacklist = {};
    JSHINT.scope = "(main)";
  }

  predefined = Object.create(null);
  combine(predefined, vars.ecmaIdentifiers[3]);
  combine(predefined, vars.reservedVars);

  combine(predefined, g || {});

  declared = Object.create(null);
  var exported = Object.create(null); // Variables that live outside the current file

  function each(obj, cb) {
    if (!obj)
      return;

    if (!Array.isArray(obj) && typeof obj === "object")
      obj = Object.keys(obj);

    obj.forEach(cb);
  }

  if (o) {
    each(o.predef || null, function(item) {
      var slice, prop;

      if (item[0] === "-") {
        slice = item.slice(1);
        JSHINT.blacklist[slice] = slice;
        // remove from predefined if there
        delete predefined[slice];
      } else {
        prop = Object.getOwnPropertyDescriptor(o.predef, item);
        predefined[item] = prop ? prop.value : false;
      }
    });

    each(o.exported || null, function(item) {
      exported[item] = true;
    });

    delete o.predef;
    delete o.exported;

    optionKeys = Object.keys(o);
    for (x = 0; x < optionKeys.length; x++) {
      if (/^-W\d{3}$/g.test(optionKeys[x])) {
        newIgnoredObj[optionKeys[x].slice(1)] = true;
      } else {
        var optionKey = optionKeys[x];
        newOptionObj[optionKey] = o[optionKey];
      }
    }
  }

  state.option = newOptionObj;
  state.ignored = newIgnoredObj;

  state.option.indent = state.option.indent || 4;
  state.option.maxerr = state.option.maxerr || 50;

  indent = 1;

  var scopeManagerInst = scopeManager(state, predefined, exported, declared);
  scopeManagerInst.on("warning", function(ev) {
    warning.apply(null, [ ev.code, ev.token].concat(ev.data));
  });

  scopeManagerInst.on("error", function(ev) {
    error.apply(null, [ ev.code, ev.token ].concat(ev.data));
  });

  state.funct = functor("(global)", null, {
    "(global)"    : true,
    "(scope)"     : scopeManagerInst,
    "(comparray)" : arrayComprehension(),
    "(metrics)"   : createMetrics(state.tokens.next)
  });

  functions = [state.funct];
  urls = [];
  stack = null;
  member = {};
  membersOnly = null;
  inblock = false;
  lookahead = [];

  if (!isString(s) && !Array.isArray(s)) {
    errorAt("E004", 0);
    return false;
  }

  api = {
    get isJSON() {
      return state.jsonMode;
    },

    getOption: function(name) {
      return state.option[name] || null;
    },

    getCache: function(name) {
      return state.cache[name];
    },

    setCache: function(name, value) {
      state.cache[name] = value;
    },

    warn: function(code, data) {
      warningAt.apply(null, [ code, data.line, data.char ].concat(data.data));
    },

    on: function(names, listener) {
      names.split(" ").forEach(function(name) {
        emitter.on(name, listener);
      }.bind(this));
    }
  };

  emitter.removeAllListeners();
  (extraModules || []).forEach(function(func) {
    func(api);
  });

  state.tokens.prev = state.tokens.curr = state.tokens.next = state.syntax["(begin)"];

  if (o && o.ignoreDelimiters) {

    if (!Array.isArray(o.ignoreDelimiters)) {
      o.ignoreDelimiters = [o.ignoreDelimiters];
    }

    o.ignoreDelimiters.forEach(function(delimiterPair) {
      if (!delimiterPair.start || !delimiterPair.end)
          return;

      reIgnoreStr = escapeRegex(delimiterPair.start) +
                    "[\\s\\S]*?" +
                    escapeRegex(delimiterPair.end);

      reIgnore = new RegExp(reIgnoreStr, "ig");

      s = s.replace(reIgnore, function(match) {
        return match.replace(/./g, " ");
      });
    });
  }

  lex = new Lexer(s);

  lex.on("warning", function(ev) {
    warningAt.apply(null, [ ev.code, ev.line, ev.character].concat(ev.data));
  });

  lex.on("error", function(ev) {
    errorAt.apply(null ...
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.jshint.JSHINT"></a>[module jshint.JSHINT](#apidoc.module.jshint.JSHINT)

#### <a name="apidoc.element.jshint.JSHINT.JSHINT"></a>[function <span class="apidocSignatureSpan">jshint.</span>JSHINT (s, o, g)](#apidoc.element.jshint.JSHINT.JSHINT)
- description and source-code
```javascript
JSHINT = function (s, o, g) {
  var x, reIgnoreStr, reIgnore;
  var optionKeys;
  var newOptionObj = {};
  var newIgnoredObj = {};

  o = _.clone(o);
  state.reset();

  if (o && o.scope) {
    JSHINT.scope = o.scope;
  } else {
    JSHINT.errors = [];
    JSHINT.undefs = [];
    JSHINT.internals = [];
    JSHINT.blacklist = {};
    JSHINT.scope = "(main)";
  }

  predefined = Object.create(null);
  combine(predefined, vars.ecmaIdentifiers[3]);
  combine(predefined, vars.reservedVars);

  combine(predefined, g || {});

  declared = Object.create(null);
  var exported = Object.create(null); // Variables that live outside the current file

  function each(obj, cb) {
    if (!obj)
      return;

    if (!Array.isArray(obj) && typeof obj === "object")
      obj = Object.keys(obj);

    obj.forEach(cb);
  }

  if (o) {
    each(o.predef || null, function(item) {
      var slice, prop;

      if (item[0] === "-") {
        slice = item.slice(1);
        JSHINT.blacklist[slice] = slice;
        // remove from predefined if there
        delete predefined[slice];
      } else {
        prop = Object.getOwnPropertyDescriptor(o.predef, item);
        predefined[item] = prop ? prop.value : false;
      }
    });

    each(o.exported || null, function(item) {
      exported[item] = true;
    });

    delete o.predef;
    delete o.exported;

    optionKeys = Object.keys(o);
    for (x = 0; x < optionKeys.length; x++) {
      if (/^-W\d{3}$/g.test(optionKeys[x])) {
        newIgnoredObj[optionKeys[x].slice(1)] = true;
      } else {
        var optionKey = optionKeys[x];
        newOptionObj[optionKey] = o[optionKey];
      }
    }
  }

  state.option = newOptionObj;
  state.ignored = newIgnoredObj;

  state.option.indent = state.option.indent || 4;
  state.option.maxerr = state.option.maxerr || 50;

  indent = 1;

  var scopeManagerInst = scopeManager(state, predefined, exported, declared);
  scopeManagerInst.on("warning", function(ev) {
    warning.apply(null, [ ev.code, ev.token].concat(ev.data));
  });

  scopeManagerInst.on("error", function(ev) {
    error.apply(null, [ ev.code, ev.token ].concat(ev.data));
  });

  state.funct = functor("(global)", null, {
    "(global)"    : true,
    "(scope)"     : scopeManagerInst,
    "(comparray)" : arrayComprehension(),
    "(metrics)"   : createMetrics(state.tokens.next)
  });

  functions = [state.funct];
  urls = [];
  stack = null;
  member = {};
  membersOnly = null;
  inblock = false;
  lookahead = [];

  if (!isString(s) && !Array.isArray(s)) {
    errorAt("E004", 0);
    return false;
  }

  api = {
    get isJSON() {
      return state.jsonMode;
    },

    getOption: function(name) {
      return state.option[name] || null;
    },

    getCache: function(name) {
      return state.cache[name];
    },

    setCache: function(name, value) {
      state.cache[name] = value;
    },

    warn: function(code, data) {
      warningAt.apply(null, [ code, data.line, data.char ].concat(data.data));
    },

    on: function(names, listener) {
      names.split(" ").forEach(function(name) {
        emitter.on(name, listener);
      }.bind(this));
    }
  };

  emitter.removeAllListeners();
  (extraModules || []).forEach(function(func) {
    func(api);
  });

  state.tokens.prev = state.tokens.curr = state.tokens.next = state.syntax["(begin)"];

  if (o && o.ignoreDelimiters) {

    if (!Array.isArray(o.ignoreDelimiters)) {
      o.ignoreDelimiters = [o.ignoreDelimiters];
    }

    o.ignoreDelimiters.forEach(function(delimiterPair) {
      if (!delimiterPair.start || !delimiterPair.end)
          return;

      reIgnoreStr = escapeRegex(delimiterPair.start) +
                    "[\\s\\S]*?" +
                    escapeRegex(delimiterPair.end);

      reIgnore = new RegExp(reIgnoreStr, "ig");

      s = s.replace(reIgnore, function(match) {
        return match.replace(/./g, " ");
      });
    });
  }

  lex = new Lexer(s);

  lex.on("warning", function(ev) {
    warningAt.apply(null, [ ev.code, ev.line, ev.character].concat(ev.data));
  });

  lex.on("error", function(ev) {
    errorAt.apply(null ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jshint.JSHINT.addModule"></a>[function <span class="apidocSignatureSpan">jshint.JSHINT.</span>addModule (func)](#apidoc.element.jshint.JSHINT.addModule)
- description and source-code
```javascript
addModule = function (func) {
  extraModules.push(func);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jshint.JSHINT.data"></a>[function <span class="apidocSignatureSpan">jshint.JSHINT.</span>data ()](#apidoc.element.jshint.JSHINT.data)
- description and source-code
```javascript
data = function () {
  var data = {
    functions: [],
    options: state.option
  };

  var fu, f, i, j, n, globals;

  if (itself.errors.length) {
    data.errors = itself.errors;
  }

  if (state.jsonMode) {
    data.json = true;
  }

  var impliedGlobals = state.funct["(scope)"].getImpliedGlobals();
  if (impliedGlobals.length > 0) {
    data.implieds = impliedGlobals;
  }

  if (urls.length > 0) {
    data.urls = urls;
  }

  globals = state.funct["(scope)"].getUsedOrDefinedGlobals();
  if (globals.length > 0) {
    data.globals = globals;
  }

  for (i = 1; i < functions.length; i += 1) {
    f = functions[i];
    fu = {};

    for (j = 0; j < functionicity.length; j += 1) {
      fu[functionicity[j]] = [];
    }

    for (j = 0; j < functionicity.length; j += 1) {
      if (fu[functionicity[j]].length === 0) {
        delete fu[functionicity[j]];
      }
    }

    fu.name = f["(name)"];
    fu.param = f["(params)"];
    fu.line = f["(line)"];
    fu.character = f["(character)"];
    fu.last = f["(last)"];
    fu.lastcharacter = f["(lastcharacter)"];

    fu.metrics = {
      complexity: f["(metrics)"].ComplexityCount,
      parameters: f["(metrics)"].arity,
      statements: f["(metrics)"].statementCount
    };

    data.functions.push(fu);
  }

  var unuseds = state.funct["(scope)"].getUnuseds();
  if (unuseds.length > 0) {
    data.unused = unuseds;
  }

  for (n in member) {
    if (typeof member[n] === "number") {
      data.member = member;
      break;
    }
  }

  return data;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jshint.JSHINT.jshint"></a>[function <span class="apidocSignatureSpan">jshint.JSHINT.</span>jshint (s, o, g)](#apidoc.element.jshint.JSHINT.jshint)
- description and source-code
```javascript
jshint = function (s, o, g) {
  var x, reIgnoreStr, reIgnore;
  var optionKeys;
  var newOptionObj = {};
  var newIgnoredObj = {};

  o = _.clone(o);
  state.reset();

  if (o && o.scope) {
    JSHINT.scope = o.scope;
  } else {
    JSHINT.errors = [];
    JSHINT.undefs = [];
    JSHINT.internals = [];
    JSHINT.blacklist = {};
    JSHINT.scope = "(main)";
  }

  predefined = Object.create(null);
  combine(predefined, vars.ecmaIdentifiers[3]);
  combine(predefined, vars.reservedVars);

  combine(predefined, g || {});

  declared = Object.create(null);
  var exported = Object.create(null); // Variables that live outside the current file

  function each(obj, cb) {
    if (!obj)
      return;

    if (!Array.isArray(obj) && typeof obj === "object")
      obj = Object.keys(obj);

    obj.forEach(cb);
  }

  if (o) {
    each(o.predef || null, function(item) {
      var slice, prop;

      if (item[0] === "-") {
        slice = item.slice(1);
        JSHINT.blacklist[slice] = slice;
        // remove from predefined if there
        delete predefined[slice];
      } else {
        prop = Object.getOwnPropertyDescriptor(o.predef, item);
        predefined[item] = prop ? prop.value : false;
      }
    });

    each(o.exported || null, function(item) {
      exported[item] = true;
    });

    delete o.predef;
    delete o.exported;

    optionKeys = Object.keys(o);
    for (x = 0; x < optionKeys.length; x++) {
      if (/^-W\d{3}$/g.test(optionKeys[x])) {
        newIgnoredObj[optionKeys[x].slice(1)] = true;
      } else {
        var optionKey = optionKeys[x];
        newOptionObj[optionKey] = o[optionKey];
      }
    }
  }

  state.option = newOptionObj;
  state.ignored = newIgnoredObj;

  state.option.indent = state.option.indent || 4;
  state.option.maxerr = state.option.maxerr || 50;

  indent = 1;

  var scopeManagerInst = scopeManager(state, predefined, exported, declared);
  scopeManagerInst.on("warning", function(ev) {
    warning.apply(null, [ ev.code, ev.token].concat(ev.data));
  });

  scopeManagerInst.on("error", function(ev) {
    error.apply(null, [ ev.code, ev.token ].concat(ev.data));
  });

  state.funct = functor("(global)", null, {
    "(global)"    : true,
    "(scope)"     : scopeManagerInst,
    "(comparray)" : arrayComprehension(),
    "(metrics)"   : createMetrics(state.tokens.next)
  });

  functions = [state.funct];
  urls = [];
  stack = null;
  member = {};
  membersOnly = null;
  inblock = false;
  lookahead = [];

  if (!isString(s) && !Array.isArray(s)) {
    errorAt("E004", 0);
    return false;
  }

  api = {
    get isJSON() {
      return state.jsonMode;
    },

    getOption: function(name) {
      return state.option[name] || null;
    },

    getCache: function(name) {
      return state.cache[name];
    },

    setCache: function(name, value) {
      state.cache[name] = value;
    },

    warn: function(code, data) {
      warningAt.apply(null, [ code, data.line, data.char ].concat(data.data));
    },

    on: function(names, listener) {
      names.split(" ").forEach(function(name) {
        emitter.on(name, listener);
      }.bind(this));
    }
  };

  emitter.removeAllListeners();
  (extraModules || []).forEach(function(func) {
    func(api);
  });

  state.tokens.prev = state.tokens.curr = state.tokens.next = state.syntax["(begin)"];

  if (o && o.ignoreDelimiters) {

    if (!Array.isArray(o.ignoreDelimiters)) {
      o.ignoreDelimiters = [o.ignoreDelimiters];
    }

    o.ignoreDelimiters.forEach(function(delimiterPair) {
      if (!delimiterPair.start || !delimiterPair.end)
          return;

      reIgnoreStr = escapeRegex(delimiterPair.start) +
                    "[\\s\\S]*?" +
                    escapeRegex(delimiterPair.end);

      reIgnore = new RegExp(reIgnoreStr, "ig");

      s = s.replace(reIgnore, function(match) {
        return match.replace(/./g, " ");
      });
    });
  }

  lex = new Lexer(s);

  lex.on("warning", function(ev) {
    warningAt.apply(null, [ ev.code, ev.line, ev.character].concat(ev.data));
  });

  lex.on("error", function(ev) {
    errorAt.apply(null ...
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
