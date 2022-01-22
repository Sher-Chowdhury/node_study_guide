npm stands for Node Package Manager. 

It is the javascript's version of yum, brew, dnf, gem,...etc. 

It's central repo is - https.npmjs.com

This is node's version of rubygems.

e.g. here's an anology:

ruby -> gem -> rubygem.org

javascript (nodejs) -> npm -> npmjs.com



package (aka module): any folder (or file) that contains javascript code. 




the npm cli should come installed as part of node:

```
$ node --version     
v14.17.6
$ npm --version
6.14.15
```

You can use npm to upgrade itself:

```
npm install -g npm
```

If the above comamand gives "Error: EACCES: permission denied" error then try upgrading it with sudo. 

```
sudo npm install -g npm
```

To upgrade node itself, - follow this guide - https://medium.com/macoclock/update-your-node-js-on-your-mac-in-2020-948948c1ffb2 to install "n", then run:

```
$ sudo n stable
  installing : node-v16.13.2
       mkdir : /usr/local/n/versions/node/16.13.2
       fetch : https://nodejs.org/dist/v16.13.2/node-v16.13.2-darwin-x64.tar.xz
   installed : v16.13.2 (with npm 8.1.2)
$ node --version       
v16.13.2
```


# Create a new node project. 

To create a new node project (aka package/module):

1. create a new folder 
2. cd into the new folder
3. create a package.json file. To create this file run:

```
npm init -y
```

Note: if you omit '-y', you'll get prompts for things like, name, version,..etc. 


4. install any 3rd party pacakges your project will depend on, e.g.


```
npm install express
```

Note: to learn more about npm-install, do:

```
npm help install
```

or if it's a development dependency do:

```
npm install -D chai 
```

Note: chai is used for unit testing, and isn't need for the actual running of the app, hence it's a dev dependency. 


This ends up doing 2 things, first, it udpates the package.json file with all dependencies:

```
$ cat package.json
{
  "name": "mynodeproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "chai": "^4.3.4"
  },
  "dependencies": {
    "express": "^4.17.2"
  }
}
```

secondly, it creates a node_modules folder and downloads dependent package into it. You can use `npm ls` to view the content of this node_modules:

```
$ npm ls       
mynodeproject@1.0.0 /Users/sherchowdhury/tmp/myNodeProject
├── chai@4.3.4
└── express@4.17.2
 ```

Note: you should add this node_modules foler in your .gitignore. 

To see the full dependency tree:

```
$ npm ls -a
mynodeproject@1.0.0 /Users/sherchowdhury/tmp/myNodeProject
├─┬ chai@4.3.4
│ ├── assertion-error@1.1.0
│ ├── check-error@1.0.2
│ ├─┬ deep-eql@3.0.1
│ │ └── type-detect@4.0.8 deduped
│ ├── get-func-name@2.0.0
│ ├── pathval@1.1.1
│ └── type-detect@4.0.8
└─┬ express@4.17.2
  ├─┬ accepts@1.3.7
  │ ├─┬ mime-types@2.1.34
  │ │ └── mime-db@1.51.0
  │ └── negotiator@0.6.2
  ├── array-flatten@1.1.1
 .
 .
 .
  ...etc
```



To see the depedency hierarchy for a particular package, do:

```
$ npm ls type-detect      
mynodeproject@1.0.0 /Users/sherchowdhury/tmp/myNodeProject
└─┬ chai@4.3.4
  ├─┬ deep-eql@3.0.1
  │ └── type-detect@4.0.8 deduped
  └── type-detect@4.0.8
```


## The Package.json file

the package.json exists in all node packages. It's used to quickly install dependencies. e.g. if you clone a node package from github, then this wont include the node_modules, so you install all the dependencies by running:

```
npm install
```

the package.json file's most important section is the dependency section. 

the package-lock.json is something that takes a snapshot of the versions of each package. If that file's stored in github, then npm-install will not only install all the packages, but also the exact versions. This lock file allows other users to have the exact setup. Also if you want to do version refreshes, then delete the lock file, delete the node_modules folder, then run npm-install. this will pull down new versions, and test if everything still works. 

## Semantic version

package versions in thee package.json are written using the semnatic standard: 


version: 4.6.1
         major.minor.patch

major - big changes that aren't backward compatible. 

minor - new features, but backward compatible

patch - bug fixes and security fixes. 


package versions in package.json can start with a "~" or "^"

"~3.2.4" - tilde means you can install the latest patch version, and the patch version has to be at least 4. e.g. 
3.2.15, or 3.2.4. But not something like 3.2.3. Hence 3.2.x where x is flexible. 

"^3.2.4" - means minor can go up. hence this is more relaxed compared to using "~". 

In theory, using either "~" or "^" shouldn't introduce any breaking changes. 

To see things more visually, see this handy website - https://semver.npmjs.com/

## install packages globally

Usually packages are install locally for a project. But there are times you want to install something globally, e.g. to install a package called "standard" we do:


```
$ npm install -g standard 

$ which standard
/usr/local/bin/standard
```

In this case `standard --fix` is coammand you can run inside a node package repo to automatically fix all the linting issues. 


## using "module.exports"

see https://github.com/Sher-Chowdhury/node-exports-demo for examples on how module.exports works, to pull in javascript functions from withing the package itself. 

## using packages.json's script section and npx

Let's say you have the following scripts entry:

```
...
"scripts": {
	"start": "node server.js",
	"test": "mocha \"*/**/*Test.js\""
}
...
```

This gives a standardised way to perform various tasks against your app, so your team members can easily run them 
locally too. These are run using `npm run`, e.g. to run "start", do:

```
$ npm run start
```

there are some special script names, that comes with handy short-hand aliases. "start" is one of those names, which can also be run using:

```
npm start
```

`test` is also another one that's a special name, that be executed using these shorthands:

```
npm test

npm t
```

But in other cases, it's done by `npm run <script-name>`

By default, these scripts will use any binaries installed locally in the node_module folder rather than any global binaries. 

If you want run these script defined commands, directly, then you'll have to locate the relevant paths to binaries that are inside the the nodule_modules folder, alternatively you can just use the `npx` binary. 

npx, like npm, is another binary that's installed as part of node. So to run the above test script, can just do:

```
$ npx mocha \"*/**/*Test.js\"
```

npx then looks inside the node_module folder and find the mocha binary automatically and then uses it. 

if you don't want to use npx, and don't want to use binaries inside the node_modules folder, i.e. you just want to run:

```
mocha \"*/**/*Test.js\"
```

Then this is possible, but you would have to install dependent binaries glabally (which is bad practice):

```
npm install -g mocha
```


Sometimes, a locally stored binary needs to be configured, e.g. eslint is one of them. In those case you can do it with npx, e.g.

```
npx elint --init
```

there's also other special names, e.g. "pretest" and "posttest", to learn about them, see - https://docs.npmjs.com/cli/v7/using-npm/scripts#npm-test



## the `npm update` command


Here's how to list out all the avialable versions of the 'express' package:

```
$ npm show express versions
```

To show what packages will get updated when you run npm-update, do:

```
$ npm outdated
```

If you are happy, then do:

```
npm update
```

If you want to install a particular version of an app, then do:

```
npm install express@3.19.2
```
or to get the latest, do:
```
npm install express@latest
```

If this version is not on the package.json's ~ or ^ allowed list, then package.json will get updated by the above command. This can be handy if you want to align your local environment with a team member's setup. 



