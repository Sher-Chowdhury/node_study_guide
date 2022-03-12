1. Look at package.json for the start command. That will show the the .js file that's the starting point of the node app. Also a dockerfile can tell you this as well, if there is one. 


2. Vs code should have buttons that allows you run individual unit tests. If they don't appear, then try restarting vs code, because vs code is a bit buggy. 

3. you can run `npm test` in vs code's builtin terminal in debug. To do that, open up a javascript-debug-terminal - https://stackoverflow.com/questions/34835082/how-to-debug-using-npm-run-scripts-from-vscode

4. IMPORTANT NOTE: Unit tests can fail in debug mode, becuase it can cause the timeout to get reached, while sitting on breakpoint. 
