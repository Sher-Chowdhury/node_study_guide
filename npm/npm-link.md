# npm link

npm link is a way you can make changes to depdendency module for development purposes. Here's how to use it:

1. clone the dependency module, e.g.
```
git clone git@github.com:Marak/colors.js.git
```

In this example, our node project contains the above package in the package.json's dependency section

3. Optional: create a new branch on the dependency module. 
4. make your code changes. 
5. run the commmand:

```
npm link
```

This creates a symlink between this repo, and some thing in the global scope. 

6. In my main node project, run:

```
npm link colors 
```

7. Later on, To unlink it, just delete the symlink:

```
ls -l nodemodules
rm -rf nodemodules/colors
```
