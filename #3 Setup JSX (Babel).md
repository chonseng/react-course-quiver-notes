JavaScript XML 

(is a Language extension. Like SASS in CSS)

Babel
=====

ES6/ES7 complies to ES5

babeljs.io

Install Babel locally
---------------------

* Install Babel
* Install Presets Locally(env, react)

```sh
yarn global add babel-cli

# Test out
babel --version
```

```sh
# Install things locally, first
yarn init

# Install preset react and env
yarn add babel-preset-react babel-preset-env
```

Run Babel
---------

```sh
# General
babel [input-file-path] --out-file=[out-file-path] --presets=env,react

# eg.
babel src/app.js --out-file=public/scripts/app.js --presets=env,react

# --watch
# eg.
babel [input-file-path] --out-file=[out-file-path] --presets=env,react --watch
```





