<span style="color:blue"># Angular Development Troubleshooting and Must-Know things</span>
   These are my notes for the issues in angular development and solutions. [For markdown shortcuts this cheatsheet is fine](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
 

# ng : The term 'ng' is not recognized

## Issue
   I was updating angular _11_ to _12_ and after completion, this error in windows appeared (using windows terminal).
   ### ng : The term 'ng' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if   a path was included, verify that the path is correct and try again.

## Solution
   There are many reason why one see such an error but in my case, angular and node installation was fine and issue was resolved with this command below.
   **Set-ExecutionPolicy RemoteSigned -Scope CurrentUser**

# Update packages
When you are in projects root folder, now and then check if packages are outdated with
## npm outdated

If there are packages with outdated versions, check what is different in the new version and it's requirements. 
## npm update
will update those outdated packages. If packages are still in outdated list, you can manually update a single package
## npm update package/name@latest (or version number e.g. 4.2.3 instead of latest) 


# Downgrade packages
During updating packages, I also updated the typescript to the latest version which is 4.3.2 at the time of writing, but angular complained that it should be >=4.2.3 and <4.3

To downgrade a particular package, in this example typescript type
## npm i -D typescript@4.2.3


# NPM not found
I am working on my ubuntu workstation, pulled the last changes here, but in my ubuntu, @angular/cli version was low and I wanted to upgrade it to the same version in my windows pc which is 12.0.3. 

## npm update @angular/cli@12.0.3 -g
This is rejected by linux due to permissions 
npm ERR! code EACCES
npm ERR! syscall rename
npm ERR! path /usr/lib/node_modules/csvtojson
npm ERR! dest /usr/lib/node_modules/.csvtojson-hT6TOSPC
npm ERR! errno -13
npm ERR! Error: EACCES: permission denied, rename '/usr/lib/node_modules/csvtojson' -> '/usr/lib/node_modules/.csvtojson-hT6TOSPC'
npm ERR!  [Error: EACCES: permission denied, rename '/usr/lib/node_modules/csvtojson' -> '/usr/lib/node_modules/.csvtojson-hT6TOSPC'] {
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'rename',
npm ERR!   path: '/usr/lib/node_modules/csvtojson',
npm ERR!   dest: '/usr/lib/node_modules/.csvtojson-hT6TOSPC'
npm ERR! }
npm ERR! 
npm ERR! The operation was rejected by your operating system.

So I added sudo 
## sudo npm update @angular/cli@12.0.3 -g

now it works
___removed 656 packages, and audited 1 package in 6s

found 0 vulnerabilities
npm notice 
npm notice New minor version of npm available! 7.10.0 -> 7.16.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v7.16.0
npm notice Run npm install -g npm@7.16.0 to update!
npm notice 

but the issue is when I wanted to use npm update for my repository I got 
bash: /usr/bin/npm: No such file or directory 


## Solution
Maybe not the nicest solution but I decided to reinstall node. 
## curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
## sudo apt-get install -y nodejs
## npm --version

6.14.13 all done :) Looking at the warnings, I see that I had npm version 7.10 and it was asking to update it to 7.16 but the last LTS version of node v14.17.0 is actually shipped with npm 6.14.13. Probably at some point I should remove everything about node and reinstall everything on ubuntu as there might be clashing packages.

# ng is not found
After working on node and npm version changes, now ng is not found.

## npm link @angular/cli

# ng serve --project project_name
An unhandled exception occurred: Class extends value undefined is not a constructor or null
See "/tmp/ng-grTrci/angular-errors.log" for further details.

## npm install
I passed above issue with npm install, as when I pulled and updated node and npm some packages in repository could be missing. Now project is compiled fine.


