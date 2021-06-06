# Angular Development Troubleshooting and Must-Know things
   These are my notes for the issues in angular development and solutions. [For markdown shortcuts this cheatsheet is fine](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
 
1.
# ng : The term 'ng' is not recognized

## Issue
   I was updating angular _11_ to _12_ and after completion, this error in windows (using windows terminal).
   ### ng : The term 'ng' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if   a path was included, verify that the path is correct and try again.

## Solution
   There are many reason why one see such an error but in my case, angular and node installation was fine and issue was resolved with this command below.
   **Set-ExecutionPolicy RemoteSigned -Scope CurrentUser**
2.
# Update packages
When you are in projects root folder, now and then check if packages are outdated with
## npm outdated

If there are packages with outdated versions, check what is different in the new version and it's requirements. 
## npm update
will update those outdated packages. If packages are still in outdated list, you can manually update a single package
## npm update package/name@latest (or version number e.g. 4.2.3 instead of latest) 

3.
# Downgrade packages
During updating packages, I also updated the typescript to lates version which 4.3.2, but angular complained that it should be >=4.2.3 and <4.3

To downgrade a particular package, in this example typescript type
## npm i -D typescript@4.2.3
