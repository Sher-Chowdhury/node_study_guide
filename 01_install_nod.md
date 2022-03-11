Best way to install node is with nvm. 

Uninstall node, if it's already installed:

```
npm list -g
/usr/local/lib
├── corepack@0.10.0
├── git-open@2.1.0
├── n@8.0.2
├── npm-check-updates@11.8.5
├── npm@8.5.3
└── standard@16.0.4
npm uninstall -g a_module
brew uninstall node
```

also run the `rm` commands mentioned in - https://stackoverflow.com/a/11178106

take a backup:

```
cp ~/.zshrc ~/.zshrc-orig
```

Basically run the curl command, here:

https://github.com/nvm-sh/nvm#install--update-script

then restart your terminal (to load in .zshrc file), then run:

```
nvm install stable
```

here are some other commands. 

```
$ nvm uninstall v4.1.0
$ nvm install v8.1.2
$ nvm use v8.1.2
$ nvm list
->      v17.7.1
default -> stable (-> v17.7.1)
iojs -> N/A (default)
unstable -> N/A (default)
node -> stable (-> v17.7.1) (default)
stable -> 17.7 (-> v17.7.1) (default)
lts/* -> lts/gallium (-> N/A)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.24.1 (-> N/A)
lts/erbium -> v12.22.10 (-> N/A)
lts/fermium -> v14.19.0 (-> N/A)
lts/gallium -> v16.14.0 (-> N/A)
```
