1. [nconf](https://www.npmjs.com/package/nconf) - 

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


2. [async](https://www.npmjs.com/package/async) - see: https://caolan.github.io/async/v3/docs.html#each

if you have group of functions that you want to run in parrallel, and each of these function ends by calling a callback() function (where this callback is called with error argument callback(error) if it fails), and you have a final() function that runs 
either when the group of functions have ended, or as soon as one of the function fails, then you can use this to achieve that. 




3. mocha (for general testing) - 

used for writing unit tests and component tests. 

4. sinon (for unit testing) - used for stubbing functions for unit testing. 

5. chai (for general testing) - gives human readable style of syntax for doing checks during unit and component testing .

6. nock (for component testing) - used for stubbing endpoints for component testing. 
 

