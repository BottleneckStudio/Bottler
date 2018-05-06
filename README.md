# BOTTLER

### BUG/FEATURE TRACKER/UI KIT

### RULES

 - each project have one owner
 - each project have initially three branches called master, develop, and fix
 - each project will have feature branches preceded by feature- and then the name of the feature
 - each project will have fix branches preceded by fix- and then the name of the bug
 - the owner will create a feature/fix document by creating a markdown file
 - markdown files will be named as feature-feature-doc.md for the feature and fix-bug-doc.md for the fix
 - markdown files will only be included in the branch it belongs
 - feature documents should contain the feature description and specifics
 - fix documents should contain the description of the bug and detailed step by step on how to recreate it
 - the owner can have many contributors
 - each contributors can only work on one job at a time either a feature or a fix
 - the owner can also work on the feature/fix he has created


### INITIAL WORKFLOW

* the owner himself will create the repository for the project with a readme.md file initialized

* The system will show the newly created project repository

* The system will provide a git command that will create the two additional branches of that repository

```sh
$ git clone https://github.com/BottleneckStudio/CursorCola.git && cd CursorCola && git checkout -b develop && touch develop.md && git add -A && git 		commit -m “initial develop commit” && git push origin develop && git checkout master && git checkout -b fix && touch fix.md && git add -A && git commit -m  	“initial fix commit” && git push origin fix && git checkout master
```

COMMENT// We will automate this part with a CLI in the future since this might not be reliable

* the owner then can create a feature in the system with a feature-feature-doc.md

* The system provides a git command to make that feature a branch in GitHub
```sh
$ git checkout -b feature-feature && touch feature-feature-doc.md && git add -A && git commit -m “initial feature-feature commit” && git push origin feature-	feature && git checkout master
```
COMMENT// we will find a way in the future to transfer the feature-feature-doc created in the system to GitHub with a single command, CLI maybe?
	
* the system will create a list of unassigned features for the contributors to choose from

* if the contributor chooses a feature he will be given a git command by the system automatically

i.e if he has not cloned the repo yet use 
```sh
$ git clone https://github.com/BottleneckStudio/CursorCola.git && git checkout -b feature-feature &&  git pull origin feature-feature. 
```
if he already cloned the repo then
```sh
$ git pull origin master && git checkout -b feature-feature && git pull origin feature feature
```
COMMENT// we will try to automate this in the future so that wherever the user is in the folder tree it will automatically create a branch in the project tree

* The system updates any feature that has been taken and assign them with the contributor who choose that feature

* Everything is the same for the fix but change the command accordingly

* When a contributor has finished working he will push the changes on the feature/fix he was working

* The system will notify the owner of the change and will be given a command to pull that feature from GitHub 
	
* if it is a feature
```sh
$ git checkout develop && git checkout -b feature-feature && git pull origin feature-feature
```
* if it is a fix
```sh	
$ git checkout fix && git checkout -b fix-bug && git pull origin fix-bug
```
COMMENT// the commands here assumes that the owner is at the master branch, we will improve this in the future

* When the owner has approved a feature/fix the system will notify the contributor to create a pull request from the feature-feature/fix-bug branch that he is working to the corresponding branch develop/fix, after the contributor creates the request the owner will accept the merge and the system will mark the feature-feature/fix-bug as done

COMMENT// we will find a way how we can create a pull request without ever going to GitHub 

* The owner then creates a pull request from develop/fix to master

COMMENT// we will find a way how we can create a pull request without ever going to GitHub 

* All the contributors will be notified of the changes and will be asked to pull from the master branch to be updated, a command will be given

if he has untracked changes
```sh
$ git stash && git pull origin master && git stash pop
```
if not
```sh
$ git pull origin master
```
COMMENT// all commands here assumes that the contributor is in his branch, improve in the future
