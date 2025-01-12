# OpenAerialMap Frontend [![Build Status](https://travis-ci.org/hotosm/oam-browser.svg?branch=develop)](https://travis-ci.org/hotosm/oam-browser) ![BrowserStack Status](https://www.browserstack.com/automate/badge.svg?badge_key=cXlaWlgyeEhmUUlISEpjTU9OQTg3RzdLVUlqUWo0V0JsOG5sMGJ4MlNnYz0tLWhtNFRWMnBlYWJnQUd6TFFZVzJxK3c9PQ==--955a5de2e9ea1506cdeb8cebdcbca07435613863)

OpenAerialMap (OAM) is a set of tools for searching, sharing, and using openly licensed satellite and unmanned aerial vehicle (UAV) imagery. 

Built on top of the [Open Imagery Network](https://openimagerynetwork.github.io/) (OIN), OAM is an open service that provides search and access to this imagery.

![](./contrib/oam_screenshot.jpg)

## Local setup

[Create React App](https://github.com/facebookincubator/create-react-app) is used to scaffold, compile and build the project.

So you will first need recent versions of Node and Yarn on your system. Then, in the project's root, run;

```bash
yarn install
yarn start
```

以下為安裝測試筆記。安裝環境 Ubuntu 20.04

How to install Node: [安裝最新版Node.js & NPM於Ubuntu 20.04 LTS(PPA安裝)](https://blog.impochun.com/how-to-install-latest-nodejs-on-ubuntu/)
```bash
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
## Run `sudo apt-get install -y nodejs` to install Node.js 18.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
     echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn

```
check installed version

```bash
viplab@viplab-20221122:~/oam-browser-develop$ node -v
v18.12.1
viplab@viplab-20221122:~/oam-browser-develop$ npm -v
8.19.2
```

clone the project's zip, unzip.
```bash
cd oam-browser-develop/

yarn install

warning " > eslint-plugin-jsx-a11y@5.0.1" has incorrect peer dependency "eslint@^2.10.2 || 3.x".
warning " > react-validation-mixin@4.2.0" has unmet peer dependency "joi@>=5.1.0".
warning " > babel-preset-react-app@3.1.0" has unmet peer dependency "babel-runtime@^6.23.0".
warning " > eslint-config-react-app@2.0.1" has unmet peer dependency "babel-eslint@^7.2.3".
warning " > eslint-config-react-app@2.0.1" has incorrect peer dependency "eslint-plugin-jsx-a11y@^5.1.1".
[4/4] Building fresh packages...
[-/6] ⢀ waiting...
[2/6] ⢀ node-sass
[3/6] ⢀ integer
[4/6] ⢀ farmhash
warning Error running install script for optional dependency: "/home/viplab/oam-browser-develop/node_modules/integer: Command failed.

make: *** [integer.target.mk:114: Release/obj.target/integer/src/integer.o] Error 1
make: Leaving directory '/home/viplab/oam-browser-develop/node_modules/integer/build'



yarn start
```

Download [v0.2-beta](https://github.com/hotosm/oam-browser/archive/refs/tags/v0.2-beta.zip)
and build again.

```bash
yarn install
[4/4] Building fresh packages...
success Saved lockfile.
$ bundle install --path bundle/cache
/bin/sh: 1: bundle: not found
error Command failed with exit code 127.


yarn start
```
bundle requires bunder => gem
https://manpages.ubuntu.com/manpages/trusty/man1/bundle-install.1.html



```bash
sudo apt install ruby-rubygems
udo apt install ruby-bundler

yarn install

Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory: /home/viplab/oam-browser-0.2-beta/bundle/cache/ruby/3.0.0/gems/ffi-1.9.8/ext/ffi_c
/usr/bin/ruby3.0 -I /usr/lib/ruby/vendor_ruby -r ./siteconf20221122-10209-dcngni.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h

You might have to install separate package for the ruby development
environment, ruby-dev or ruby-devel for example.


An error occurred while installing ffi (1.9.8), and Bundler cannot continue.

In Gemfile:
  compass was resolved to 1.0.3, which depends on
    rb-inotify was resolved to 0.9.5, which depends on
      ffi
error Command failed with exit code 5.
info Visit https://yarnpkg.com/en/docs/cli/install for documentation about this command.

sudo apt install ruby-dev
viplab@viplab-20221122:~/oam-browser-0.2-beta$ yarn install
yarn install v1.22.19
warning package.json: No license field
warning oam-browser@1.0.0: No license field
[1/4] Resolving packages...
success Already up-to-date.
$ bundle install --path bundle/cache
[DEPRECATED] The `--path` flag is deprecated because it relies on being remembered across bundler invocations, which bundler will no longer do in future versions. Instead please use `bundle config set --local path 'bundle/cache'`, and stop using this flag
Fetching gem metadata from https://rubygems.org/.............
Using bundler 2.3.5
Using chunky_png 1.3.4
Using multi_json 1.11.0
Using sass 3.4.13
Using rb-fsevent 0.9.4
Fetching ffi 1.9.8
Using compass-import-once 1.0.5
Using compass-core 1.0.3
Installing ffi 1.9.8 with native extensions
Fetching rb-inotify 0.9.5
Installing rb-inotify 0.9.5
Fetching compass 1.0.3
Installing compass 1.0.3
Bundle complete! 2 Gemfile dependencies, 10 gems now installed.
Bundled gems are installed into `./bundle/cache`
Post-install message from compass:
    Compass is charityware. If you love it, please donate on our behalf at http://umdf.org/compass Thanks!
Done in 13.85s.

```

```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ yarn start
yarn run v1.22.19
warning package.json: No license field
error Command "start" not found.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.

```

```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ cat package.json 
{
  "name": "oam-browser",
  "version": "1.0.0",
  "description": "",
  "main": "index.html",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 0",
    "install": "bundle install --path bundle/cache"
  },

```
copy the package.json from the github
```
  "scripts": {
    "postinstall": "[ -f src/config/local.js ] || echo 'module.exports = {};' > src/config/local.js",
    "start": "NODE_PATH=src react-scripts start",
    "build": "react-scripts build",
    "analyze": "source-map-explorer build/static/js/main.*",
    "lint": "eslint --ignore-pattern src/joi.js --ignore-pattern styles/ src/ test/",
    "fix-lint": "eslint --ignore-pattern src/joi.js --fix --ignore-pattern styles/ src/ test/",
    "test": "NODE_ENV=test NODE_PATH=src:test/specs mocha --opts test/specs/mocha.opts test/specs/*_spec.js"
  },

```
Run again
```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ yarn start
yarn run v1.22.19
$ NODE_PATH=src react-scripts start
/bin/sh: 1: react-scripts: not found
error Command failed with exit code 127.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.

```
google "/bin/sh: 1: react-scripts: not found"
https://stackoverflow.com/questions/40546231/sh-react-scripts-command-not-found-after-running-npm-start
Guess I should install create-react-app

```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ npm install -g create-react-app
npm ERR! code EACCES
npm ERR! syscall mkdir
npm ERR! path /usr/lib/node_modules/create-react-app
npm ERR! errno -13
npm ERR! Error: EACCES: permission denied, mkdir '/usr/lib/node_modules/create-react-app'

```
No root privilage, try again

```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ sudo npm install -g create-react-app
[sudo] password for viplab: 
npm WARN deprecated tar@2.2.2: This version of tar is no longer supported, and will not receive security updates. Please upgrade asap.

added 67 packages, and audited 68 packages in 1s

5 packages are looking for funding
  run `npm fund` for details

2 high severity vulnerabilities

Some issues need review, and may require choosing
a different dependency.

Run `npm audit` for details.
npm notice 
npm notice New major version of npm available! 8.19.2 -> 9.1.2
npm notice Changelog: https://github.com/npm/cli/releases/tag/v9.1.2
npm notice Run npm install -g npm@9.1.2 to update!
npm notice 

```
the next command is not working
```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ sudo npm install --save react react-dom
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR! 
npm ERR! While resolving: oam-browser@2.0.0
npm ERR! Found: eslint@4.19.1
npm ERR! node_modules/eslint
npm ERR!   dev eslint@"^4.10.0" from the root project
npm ERR! 
npm ERR! Could not resolve dependency:
npm ERR! peer eslint@"^2.10.2 || 3.x" from eslint-plugin-jsx-a11y@5.0.1
npm ERR! node_modules/eslint-plugin-jsx-a11y
npm ERR!   eslint-plugin-jsx-a11y@"5.0.1" from the root project
npm ERR! 
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force, or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
npm ERR! 
npm ERR! See /root/.npm/eresolve-report.txt for a full report.

npm ERR! A complete log of this run can be found in:
npm ERR!     /root/.npm/_logs/2022-11-23T02_25_01_496Z-debug-0.log

```
try yarn start again

```

viplab@viplab-20221122:~/oam-browser-0.2-beta$ yarn start
yarn run v1.22.19
$ NODE_PATH=src react-scripts start
/bin/sh: 1: react-scripts: not found
error Command failed with exit code 127.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.

```
not working.
add the --force as suggested by the above warning message.

```
viplab@viplab-20221122:~/oam-browser-0.2-beta$ npm install --save react react-dom react-scripts --force
npm WARN using --force Recommended protections disabled.
npm WARN ERESOLVE overriding peer dependency

...
npm ERR! Please make sure you are using a supported platform and node version. If you
npm ERR! would like to compile fibers on this machine please make sure you have setup your
npm ERR! build environment--
npm ERR! Windows + OS X instructions here: https://github.com/nodejs/node-gyp
npm ERR! Ubuntu users please run: `sudo apt-get install g++ build-essential`
npm ERR! Alpine users please run: `sudo apk add python make g++`
npm ERR! sh: 1: nodejs: not found

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/viplab/.npm/_logs/2022-11-23T02_31_28_427Z-debug-0.log

```

suggest by the error message
```
sudo apt-get install g++ build-essential

```
try again npm install, same message


You should be able to see the site in your browser at `http://localhost:3000`

However, to get all functionality you will also need to point it at a running [Catalog API](https://github.com/hotosm/oam-catalog). By default the endpoint of the staging instance of the API will be used, however you can change the endpoint to a locally running API in `src/config/local.js`.

## Deployment

This is a Single Page Application and needs only a web server to serve it. Therefore it can be hosted on S3 or just
as a folder under Nginx.

The backend API URI can be changed in `src/config.js`

To prepare the files:

`yarn build`

Then copy the `build/` folder to your web server or S3.

## Testing
2 distinct test suites exist.

**Unit-like tests**, under `test/specs`    
These should be isolated and fast, with as much mocking/stubbing as possible, suitable for TDD. Run with:    
`mocha --opts test/specs/mocha.opts test/specs` or `npm test`

**Integration tests**, under `test/integration`    
These are end-to-end, cross-browser tests, that should test as much of the stack as possible. Currently they are run on Browser Stack against various browsers. They can be run locally against a Web Driver compatible browser client like [chromedriver](https://sites.google.com/a/chromium.org/chromedriver/) or [geckodriver](https://github.com/mozilla/geckodriver). 
You will need a running [Catalog API](https://github.com/hotosm/oam-catalog), the repo has a Dockerfile to quickly get
a local version of the API running. Then you can run tests with;
`wdio test/integration/wdio.local.conf.js`.

Note that Browserstack tests both a pinned version of the API (defined in `package.json` and the latest version of the API).

Because `wdio` wraps `mocha`, you can send `mocha` args via `wdio.default.conf.js`'s `mochaOpts` field. For instance `grep` has been added so you can isolate a single test run with:    
`MOCHA_MATCH='should find imagery' wdio test/integration/wdio.local.conf.js`

## Contributing

Contributions are very welcome. Please see [CONTRIBUTING.md](./CONTRIBUTING.md).

## License
OAM Browser is licensed under **BSD 3-Clause License**, see the [LICENSE](LICENSE) file for more details.
