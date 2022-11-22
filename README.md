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
