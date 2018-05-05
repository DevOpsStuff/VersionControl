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

**Setting for global level configuation**

```
git config --global --list
git config --global user.name <username>
git config --gloabl user.email <email>
git config --gloabl color.ui true (which is default after git version)
```

**Git Alias**

```
git config --global alias.s "status -s"  #setting an alias for `git status`
git config --global alias.lg "log --oneline --all --graph --decorate"
```
**Creating a First Repo**

```
git status
git init <name>
git status
notepad <file>
git status
git add <file>
touch index.css
git status
git commit -m "Added file"
git status
```

**Staging Area** 

```
touch about.css about.html contact.css contact.html
git s
git commit
```

**Git Commit undoing**

```
git reset --soft HEAD^
git commit --amend -m "Adasd"
git reset --hard HEAD^
git reset --hard HEAD^^
```
**Note:** Don't do this after you push

**Git History**

```
git log
git log --oneline
git lg
```

**Git renaming,deleting**

```
cd web1
git s
git mv about.html aboutme.html
git add .
git commit -m "renamed to aboutme.html"
touch deletethisfile.txt
git add .
git rm deletethisfile.txt
git commit -m "delete the deletethisfile"
```

**Branching**
```
git branch
git branch search
git checkout search
touch search.html search.css
git add .
git commit -m"added search page"
git lg
git checkout master
git lg
``` 

**Merging**
```
git checkout master
git merge search
git lg
git branch
git branch -d search
git branch
git lg
```

**Types of Merges**
    * Fast-Forward
    * Recursive

```
git checkout -b <somename>
git branch
touch somename.html
git add .
git commit -m "asd"
git checkout master
git checkout -b <newname>
touch newname.html
git add .
git commit -m "Asdasd"
git lg
git checkout master
git lg
git branch -d <newname>
```

**No Fast-Forward**
```
git checkout -b myaccount
touch file
git add .
git commit -m "added account.html"
touch account.css
git add .
git commit -m "added account.css"
git checkout master
git lg
git merger --no-ff myaccount
```

**Merge Conflict**
```
git checkout -b cart
touch cart.html
git add .
git commit -m "added shoping cart"
notepad index.html
"link to cart"
git commit -am "added link to shoping cart"
git checkout master
git checkout -b page_redesign
```

Write some content in the file.

```
notepad index.html
"company logo"
"links"
"adasdasdaa"
```

```
git s
git commit -am "implemented home page redesign"
git lg
git checkout master
git merge --no--ff page_redsign
git branch -d page_redsign
git branch
git lg
```

*Conflit time*
```
git branch
git merge cart
git status
notepad index.html
git add .
git status
```

*To finish Merge*
```
git commit 
git lg
git branch -d cart
```

*Another example of merge conflict*
```
git checkout -b checkout_page
notepad asd
git add and commmit
notepad index.html
"added checkout page"
git commit -am "Asdas"
git checkout master
cat index.html
git checkout -b add_home_pge_lingks
notepad index.html
"abount"
"account"
git comit -am "added few links"
git checkout master
git merge --no-ff add_home_page_links
git branch -d add_home_page_links
git merge checkout_page 
notepad index.html
```

*Resolve conflict*
```
git status
git add and commit
git lg
git branch -d checkout_page
```

**Git Diff**

```
git help diff
git branch
notepad index.html
->delete some line and add new line
git s
git diff
git add .
git diff
git diff --staged
git diff HEAD -> diff orking directory and last commit
notepad index.html
"delete some lines"
git s
git diff --staged
git diff
git diff HEAD
git add .
git s
git commit -m "asdasd"
```

**Git Tagging**
```
git tag
git checkout v0.0.1
to add a new tag
git tag -a v0.0.3 -m "version 0.0.3"
git push --tags
```

**Git Internals**
```
git init
touch index.html
git s
insert sometext in index.html
"How are you"
git add .
git commit -m "added index.html"
```

open .git directory

```
git cat-file -p 3b18 -> only show content
git cat-file -p ff46 -> filename
git cat-file -p c2d5 -> date and time
```
*Benefits of Sha-1*
```
notepad 1.txt
"hello world"
git add .
git commit -m asdas
git cat-file -p 4083
git cat-file -p 
```

**Connection to Remote server**
```
#connection to remote server
create a new repository in github "web2"
cat .git/config
git remote add origin <url>
cat .git/config
git push -u origin master

#configuring default push
git config --global push.default simple
```

**Fetch VS Pull**
```
git branch
git branch -a
create a new file in github
git lg
git pull
git lg
create a new file in github or modify the readme
git lg
git fetch -> a network operation
git lg
cat readme.md
git checkout origin/master
cat readme.md
git checkout master
git merge origin/master
cat readme.md
```

**Git Stash for Resuing**
```
git co master
notepad file
"add some new contact"
git stash
git status
git lg
git co rb1
git stash apply
##resolve conflict
git add and commit
git co rb2
git stash apply
git add . and commit
git co master
git stash pop
git add and commit
```

**Git Revert**
```
### git revert

git init undoing
touch undoing
git add .
git commit -m "added"
git lg
touch badidea
git add and commit "badidea"

create a new repo in github
and git push 
git revert <sha1ash>
two commit it is bad idea
git lg
git push
ls
```

**Git Rebasing**
```
#introducing rebasing
git lg
git checkout -b feature1
touch feature1.html
git add and commit
git checkout master
git checkout -b feature2
touch feature2.html
git add and commit
git checkout master
git merge --no-ff feature1
git branch -d feature1
```

* Rebasing feature2 
```
git checkout feature2
git rebase master
git lg
git checkout master
git merge --no-ff feature2
#integration test on feature2 
```

**Rebase Conflit**
```
git branch
git checout -b fetaure3
touch feture3.html 
git add and commit
vim index.html
"fetaure3"
git s
git commit -am "added feture 3"
git checkout master
crate same as feature 4
```

**Merge Vs Rebase when you pull**
```
#merge vs rebasse when you pull
edit a readme file on github
git lg
git fetch
now on master branch createa local commit
edit home.html
"Asdasda"
git commit -am "Asdasd"
git lg
```

**Git push**
```
##don't push too often
git commit -m "asdasdas"
git commit --amend
```

**Git Reflog**
```
##reflog
git reflog
git reset --hard <sha1>
```


**References**

* [Git Scm](https://github.com/progit/progit2/releases/download/2.1.56/progit.pdf)

* [Git Real](https://www.slideshare.net/CoutoLucas/git-real-slides) or [Git Real Drive](https://drive.google.com/drive/u/2/folders/0B5Vaq-RzahVnR0NIT0xMRDA2OFE)
