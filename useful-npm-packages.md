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

on the cli, run:

```
node DEBUG=* npm start
```

This will output a lot of content, including:

```
...
myApp this only get's printed when debug is enabled
```

You can apply filtering by running:

```
node DEBUG=* npm start
```


### morgan

[morgan](https://www.npmjs.com/package/morgan) - this gives info on the terminal everytime it recieves a requests. E.g. did it get a "Get" or "Post" request? what time was the request, which web browser issued the request, e.g. chrome or firefox....etc. 
