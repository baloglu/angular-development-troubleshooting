# angular-development-troubleshooting
   I will take notes for the issues in angular development and solutions. [For markdown shortcuts this cheatsheet is fine](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
## 1. ng : The term 'ng' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if   a path was included, verify that the path is correct and try again.

# Issue
   I was updating angular _11_ to _12_ and after completion, **ng** command became unrecognized in windows (using windows terminal).

## Solution
   There are many reason why one see such an error but in my case, angular and node installation was fine and issue was resolved with this command below.
   **Set-ExecutionPolicy RemoteSigned -Scope CurrentUser**
