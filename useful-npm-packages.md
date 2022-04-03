### [nconf](https://www.npmjs.com/package/nconf) - 

You can have something like:

```
nconf.get('variable-name')
```

and nconf will look for a env-var/cli-arg/config-file-setting that has the name "variable-name". Order of precedence is done using:

```
  nconf.argv()
   .env()
   .file({ file: 'path/to/config.json' });
```

It's a bit like Puppet's hiera. 

One nice thing about this approach is that if you use are creating a service, but don't know how the consumer will provide the arguments, 
e.g. via a env-var, cli-aregumetn, or config.file, then using ncof will provide all scenarios in one go, so you don't have to do extra work to support them. 


### [async](https://www.npmjs.com/package/async) - see: https://caolan.github.io/async/v3/docs.html#each

if you have group of functions that you want to run in parrallel, and each of these function ends by calling a callback() function (where this callback is called with error argument callback(error) if it fails), and you have a final() function that runs 
either when the group of functions have ended, or as soon as one of the function fails, then you can use this to achieve that. 




### mocha (for general testing) - 

used for writing unit tests and component tests. 

### sinon (for unit testing) - used for stubbing functions for unit testing. 

### chai (for general testing) - gives human readable style of syntax for doing checks during unit and component testing .

### nock (for component testing) - used for stubbing endpoints for component testing. - https://github.com/Sher-Chowdhury/npm-supertest-and-nock-demo

nock is only for mocking external requests. It can't be used to mock internal requests. 

### supertest - used for triggering express request calls by issuing a dummy request -  https://github.com/Sher-Chowdhury/npm-supertest-and-nock-demo

### [node-mocks-http](https://www.npmjs.com/package/node-mocks-http) 
used for mocking internal requests, e.g. app.get()
 

### chalk

[chalk](https://github.com/chalk/chalk) is used for adding color to your console.log() messages. 

e.g. 

```
const chalk = require('chalk')

console.log("listening on port " + chalk.green('3000'))
console.log(`listening on port chalk.green('3000')`)
```


### Debug

[debug](https://www.npmjs.com/package/debug) let's you add console.log() statements that only get's executed when the "DEBUG" env variable is set. 


```
const debug = require('debug')('myApp')
debug("this only get's printed when debug is enabled")
```

Notice the 2 round brackets in succession. That's because the exported item from debug module is a function, that we want to execute straight away. 

on the cli, run:

```
node DEBUG=* npm start
```

This will output a lot of content, including:

```
...
myApp this only get's printed when debug is enabled
```

Here "myApp" is just a tag for us to see which debug messages relates our js file. 

You can apply filtering by running:

```
node DEBUG=* npm start
```


### morgan

[morgan](https://www.npmjs.com/package/morgan) - this gives info on the terminal everytime it recieves a requests. E.g. did it get a "Get" or "Post" request? what time was the request, which web browser issued the request, e.g. chrome or firefox....etc. 


### nodemon

can be useful when doing development work. It can restart `npm start` whenever there's a change in the javascript files. I personally don't use this though. 

### webpack and webpack-cli

This is often used for working with React based apps. Web browsers can't understand js packages that's spread across multiple .js files. So this tool rewrites all the js code into a single .js files. That includes all the code from dependency packages. 

https://jscomplete.com/learn/1rd-reactful


https://webpack.js.org/ - https://www.npmjs.com/package/webpack

https://www.npmjs.com/package/webpack-cli


### Babel

used in React based apps. It converts jsx syntax into javascript code. https://babeljs.io

### eslint and standard

Both of these packages appears to do the same kind of thing, i.e. fix lint problems.

https://standardjs.com/ - https://www.npmjs.com/package/standard
https://eslint.org/ - https://www.npmjs.com/package/eslint

The main difference between the 2 is that standard is very opinionated and can't be modified, whereas eslint can be modified. 

These should be dev-dependency packages. 

There is also - https://www.npmjs.com/package/prettier that can work well with eslint. 


