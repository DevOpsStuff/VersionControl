# VersionControl

## Overview Diagram

![Git workflow](https://github.com/DevOpsStuff/VersionControl/blob/master/git-transport.png)

## Git Installation
   By default git is installed in linux, if not follow this link
   [Git Installation](https://gist.github.com/derhuerst/1b15ff4652a867391f03)

### Git Configuration
    Three levels of configuration

    * Local
    * global
    * system

*Setting for global level configuation*

```
git config --global --list
git config --global user.name <username>
git config --gloabl user.email <email>
git config --gloabl color.ui true (which is default after git version)
```

*Git Alias*

```
git config --global alias.s "status -s"  #setting an alias for `git status`
git config --global alias.lg "log --oneline --all --graph --decorate"
```
*Creating a First Repo*

```
git status
git init <name>
git status
touch <file>
git status
git add <file>
touch index.css
git status
git commit -m "Added file"
git status
```

*Staging Area* 

```
touch about.css about.html contact.css contact.html
git s
git commit
```

*Git Commit undoing*

```
git reset --soft HEAD^
git commit --amend -m "Adasd"
git reset --hard HEAD^
git reset --hard HEAD^^
```
*Note:* Don't do this after you push
