npm stands for Node Package Manager. 

It is the javascript's version of yum, brew, dnf, gem,...etc. 

It's central repo is - https.npmjs.com

This is node's version of rubygems.

e.g. here's an anology:

ruby -> gem -> rubygem.org

javascript (nodejs) -> npm -> npmjs.com



package (aka module): any folder that contains javascript code. 




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