# Git Tutorial

## Install git
1. Open the command line (e.g. `/Applications/Utilities/Terminal` on a mac)
2. To check to see if you have git installed
```
git --version
```

2. To install on a Mac, type (this will install a pared down version of XCode that includes git)
```
xcode-select --install
```

3. For other operating systems, following [these directions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

##  Modify your global configurations
Replace these details with your information and specify what you'd like your default text editor to be (e.g. sublime text, nano, vim)
```bash
git config --global --list
git config --global user.name 'Dani Cosme'
git config --global user.email 'dani.cosme@gmail.com'
git config --global core.editor 'sublime'
```

## Create an account on GitHub and join UO Data Science organization
1. Go to [GitHub](https://github.com/) to create an account
2. Go to [UO Data Science](https://github.com/uodatascience)
3. Add username to list on Slack to be added to the organization
4. Accept email invitation

## Why version control?
* To have a backup
* To see what has changed in the document over time
* To be able to roll back to any previous version
* To work collaboratively and avoid conflicted copies
* To document your code and improve reproducibility
* To make it simple to share your code
* To avoid this:

<img src="http://www.phdcomics.com/comics/archive/phd101212s.gif" width="600">

## What can be version controlled with git?
* Plain text
* Code
* Git can't version control binary files (e.g. Word docs, images); it tracks that they've changed, but not what's different

## Key concepts and vocabulary
* **Snapshots** = records of what files look like at a given point in time
  * You decide when to take snapshots
  * History of all snapshots is retained
  * Analogy – they're kind of like photos
* **Staging** = which files to include in the snapshot
  * You decide which files you want to take snapshots of
  * Analogy – think of this step as deciding who's going to be in a group photo; you may want to include some people, but not others
* **Commit** = the act of creating a snapshot
  * Info that's been changed
  * A reference to the commit that came brefore it (parent commit)
  * Analogy – think of this step as actually taking the photo with only those you chose to be in it
* **Repository** = collection of files and file history
	* Local repository = exists only on your local machine
	* Remote repository = exists on a remote website (e.g. github.com, gitlab.com, bitbucket.org)
	* Also called a "repo" for short
	* Analogy – this is kind of like the photo album that stores all your snapshots
* **Cloning** = copying a repository
* **Pulling** = grabbing changes from a remote repository
* **Pushing** = pushing changes to a remote repository
* **Branches** = offshoots of the master branch
  * Master = typically the main branch
* **Merging** = combining branch with master repository

## Basic process for local use
<img src="https://git-scm.com/book/en/v2/images/lifecycle.png" width="600">

[Image from git-scm.com](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

1. Make changes to a file
2. Stage the file 
	* Choose to take a snapshot of the changes 
	* `git add [file]`
3. Commit the changes
	* Take a snapshot of the file
	* `git commit -m "I made these changes.." [file]`
4. Rinse, repeat.

## Tutorial
### Local use
1. Make directory on your desktop
```bash
mkdir ~/Desktop/git-test
cd ~/Desktop/git-test
```
2. Initialize the repository
```bash
git init
```
3. Check what's in the directory
```bash
ls -a
```
4. Check status
```bash
git status
```
5. Create file with some text
```bash
printf "I <3 git" > test.txt
```
6. List files and check status
```bash
ls 
git status
```
7. Add test.txt file as a tracked file in the repository
```bash
git add test.txt 
```
8. Check status and check what's different
```bash
git status
git diff
```
9. Add a new line of text
```bash
printf "\nWhy hello there" >> test.txt
```
10. Check what's different
```bash
git diff test.txt
```
11. Check status again
```bash
git status
```
12. Stage the changes made to the file
```bash
git add test.txt
```
13. Check status again
```bash
git status
```
14. Save snapshot of the file by commiting changes
```bash
git commit -m "added test file"
```
15. Check version history
```bash
git log
```

## Basic process for remote and collaborative use
<img src="https://camo.githubusercontent.com/2f9bc8ae52acf8f5bcf4217f4184fdcb0213eef6/68747470733a2f2f7777772e6769742d746f7765722e636f6d2f6c6561726e2f636f6e74656e742f30312d6769742f30312d65626f6f6b2f656e2f30312d636f6d6d616e642d6c696e652f30342d72656d6f74652d7265706f7369746f726965732f30312d696e74726f64756374696f6e2f62617369632d72656d6f74652d776f726b666c6f772e706e67" width="600">

[Image from Dirk Dunn](https://gist.github.com/dirkdunn/2ff2784e8c780f0f7c2cc2a909fc299c)

1. Pull recent changes from remote repository
	* Get most up to date version of the repository
	* This will update your local files
	* `git pull`
2. Make changes to a file
3. Stage the file 
	* Choose to take a snapshot of the changes 
	* `git add [file]`
4. Commit the changes
	* Take a snapshot of the file
	* `git commit -m "I made these changes.." [file]`
5. Push changes to remote repository
	* Apply your local changes to the remote repository
	* `git push`
6. Rinse, repeat.


### Remote use
1. If you have not already done so, clone UO Data Science git tutorial repository.
```bash
cd ~/Desktop
git clone https://github.com/uodatascience/git-tutorial.git
```
2. Change directories to the git tutorial folder
```bash
cd git_tutorial
```
3. Check status
```bash
git status
```
4. Get most up to date version of the repo
```bash
git pull
```
5. Open favs.txt file with text editor
```bash
# open in text editor app
open /Applications/TextEdit.app favs.txt

# open in terminal using vim
vim favs.txt
```
6. Add your favorite R package and save file
```bash
# add txt directly from command line
printf "\ndplyr" >> favs.txt
```
7. Add favs.txt to the staging area
```bash
git add favs.txt
```
8. Commit changes
```bash
git commit -m "added fav package"
```
9. Push changes to github repo
```bash
# single master branch
git push

# multiple branches
git push origin [branch name]
```
10. Pull newest version from the github repo
```bash
# single master branch
git pull

# multiple branches
git pull origin [branch name]
```

## Ignoring files
Sometimes you don't want git to track your files (e.g. if you have data or binary files in the repo). To ignore specific files, create a file called `.gitignore` and list the files you want to ignore.
```bash
# create .gitignore file
touch .gitignore

# add files to ignore
printf ".DS_Store" > .gitignore
```

## Merge conflicts
We're not going to go over merge conflicts in this tutorial, but they happen when two or more people change the file at the same time and the conflicts must be resolved.

More information about how to deal with merge conflicts can be found on the [Software Carpentry tutorial](http://swcarpentry.github.io/git-novice/09-conflict/)

## Commonly used commands
```bash
# initialize repository
git init

# add file(s) 
git add [file]  # single file
git add .       # all files

# remove file tracking
git rm

# make a snapshot of repository
git commit -m "[message text]"

# copy existing repository
git clone [repo address]

# get newest version of remote repository
git pull

# check newest version of remote repository without merging with your local repository
git fetch

# push changes to remote repository
git push

# view history
git log

# check changes that have been made to files in a repository
git diff

# create new branch
git checkout -b [name of new branch]

# switch branches
git checkout

# check configurations
git config --global --list
```

## Resources
* [Git 101 – HubSpot](https://www.slideshare.net/HubSpot/git-101-git-and-github-for-beginners)
* [Git Intro – Ariel Rokem](http://arokem.github.io/2013-09-16-ISI/lessons/git-notebook/git-for-scientists.slides.html#/1)
* [Version Control With Git – Software Carpentry](http://swcarpentry.github.io/git-novice/)
* [Git and Github 1 & 2 – Neurohackweek](https://github.com/neurohackweek/git-and-github)
* [Reproducible Workflows – Russ Poldrack](https://github.com/poldrack/reproducible-workflows)
* [Git: the Simple Guide – Roger Dudler](http://rogerdudler.github.io/git-guide/)
* [Git Cheatsheet – Roger Dudler](https://rogerdudler.github.io/git-guide/files/git_cheat_sheet.pdf)
* [Git Cheatsheet – NDP Software](http://ndpsoftware.com/git-cheatsheet.html#loc=remote_repo;)
* [Git Documentation](https://git-scm.com/book/en/v2)