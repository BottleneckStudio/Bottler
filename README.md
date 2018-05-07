# BOTTLER
**BUG/FEATURE TRACKER/UI KIT**
We are aiming to eliminate or reduce human errors when inputing git commands by providing the commands ourselves

### RULES

 - each **project** have one **owner**
 - each **project** have initially three branches called **master**, **develop**, and **fix**
 - each **project** will have feature branches preceded by **feature-** and then the name of the **feature**
 - each **project** will have fix branches preceded by **fix-** and then the name of the **bug**
 - the **owne**r will create a **feature/fix document** by creating a **markdown** file
 - **markdown** files will be named as **feature-feature-doc.md** for the **feature** and **fix-bug-doc.md** for the **fix**
 - **markdown** files will only be included in the branch it belongs
 - **feature** documents should contain the feature description and specifics
 - **fix** documents should contain the description of the bug and detailed step by step on how to recreate it
 - the **owner** can have many **contributors**
 - each **contributorsx** can only work on one job at a time either a **feature** or a **fix**
 - the **owner** can also work on the **feature/fix** he has created


### Creating a repository for a project

the **owner** himself will create the **repository** for the project with a **readme.md** file initialized

**we can create a repository directly from the terminal if we have github API access**

```sh
$ touch README.md && git init && git add README.md && git commit -m "first commit" && git remote add origin git@github.com:alexpchin/<reponame>.git && git push -u origin master
```

The **system** will show the newly created project **repository**

The **system** will provide a git command that will create the **develop** and **fix** branch on that **repository**

**sample git command**
```sh
$ git clone https://github.com/BottleneckStudio/CursorCola.git && cd CursorCola && git checkout -b develop && touch develop.md && git add -A && git commit -m “initial develop commit” && git push origin develop && git checkout master && git checkout -b fix && touch fix.md && git add -A && git commit -m “initial fix commit” && git push origin fix && git checkout master
```

### Creating a feature/fix Branch
the **owner** should create a **feature/fix** branch in the system with a **feature-feature-doc.md/fix-bug-doc.md** initialized

The **system** provides a git command for the **owner** to make that **feature/fix** a branch in github
```sh
$ git checkout -b feature-feature && touch feature-feature-doc.md && git add -A && git commit -m “initial feature-feature commit” && git push origin feature-	feature && git checkout master
```
### Choosing a feature/fix task
the **system** will create a list of unassigned **features/fix** for the **contributors** to choose from

after the **contributor** chooses a **feature/fix** he will be given a git command by the system

**feature branches**
```sh
$ git checkout -b feature-feature &&  git pull origin feature-feature 
```
**fix branches**
```sh
$ git checkout -b fix-bug && git pull origin fix-bug
```
The **system** updates any **feature** that has been taken and assign them with the **contributor** who chose that **feature**

### Creating a pull request
a **contributor** will push to the branch his working and create a pull request to the corresponding branches, **develop** for the feature and **fix** for the fix

**" we will make the system create a git command that creates a pull request directly at the terminal like the one below "**

```sh
git request-pull [-p] <start> <url> [<end>]
```
The system will notify the **owner** of the change and will be given a command to pull that feature from GitHub 
**feature**
```sh
$ git checkout develop && git checkout -b feature-feature && git pull origin feature-feature
```
**fix**
```sh	
$ git checkout fix && git checkout -b fix-bug && git pull origin fix-bug
```

### Approving the feature/fix pull request

When the **owner** has approved a **feature/fix** the system will notify the **contributor** to create a pull request from the **feature-feature/fix-bug** branch that he is working to the corresponding branch **develop/fix**, 


```sh
git request-pull [-p] <start> <url> [<end>]
```

the **owner** can accept the merge and the system will mark the **feature-feature/fix-bug** as done and deletes that branch

**the system will provide a link to the pull request for now**

All the **contributors** will be notified of the changes and will be asked to pull from the **master** branch to be updated, after the **owener** merges the **develop/fix** changes to **master**

**all contributors will recieve a notification to pull from master**
```sh
$ git pull origin master
```
**COMMENT//** all commands here assumes that the contributor is in the master branch
