# Git Tutorial

## Install git
1. Open the command line
2. To check to see if you have git installed
```
git --version
```

2. To install on a Mac, type (this will install a pared down version of XCode that includes git)
```
xcode-select --install
```

3. For other operating systems, following [these directions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Create an account on GitHub and join UO Data Science organization
1. Go to [GitHub](https://github.com/) to create an account
2. Go to [UO Data Science](https://github.com/uodatascience)
3. Add email to list on Slack to be added to the organization
4. Accept email invitation

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
4. Get status
```bash
git status
```
5. Create file
```bash
printf "I <3 git" > test.txt
```
6. Check status
```bash
ls 
git status
```
7. Add test.txt file to the repository
```bash
git add test.txt 
```
8. Check status
```bash
git status
```
9. Save snapshot of repo by commiting changes
```bash
git commit -m "added test file"
```
10. Check version history
```bash
git log
```

### Collaborative use
1. Clone git-tutorial repo
```bash
cd ~/Desktop
git clone https://github.com/uodatascience/git-tutorial.git
```
2. Check status
```bash
git status
```
3. Get most up to date version of the repo
```bash
git pull
```
4. Open favs.txt file with text editor
```bash
# open in text editor app
open /Applications/TextEdit.app favs.txt
# open in terminal using vim
vim favs.txt
```
5. Add your favorite R package and save file
```bash
# add txt directly from command line
printf "\ndplyr" >> favs.txt
```
6. Add favs.txt to the staging area
```bash
git add favs.txt
```
7. Commit changes
```bash
git commit -m "added fav package"
```
8. Push changes to github repo
```bash
git push origin master
```
9. Pull newest version from the github repo
```bash
git pull 
```

## Commonly used commands
```bash
# initialize repository
git init

# add file(s) 
git add [file]  # single file
git add .       # all files

# make a snapshot of repository
git commit -m "[message text]"

# copy existing repository
git clone [repo address]

# get newest version of repository
git pull

# push changes to repository
git push

# view history
git log

# check changes that have been made to files in a repository
git diff

# create new branch
git checkout -b [name of new branch]

# switch branches
git checkout
```

## Example collaborative repo with multiple branches
https://github.com/brainhack-eugene/auto-motion

### Resources
* [Git 101 – HubSpot](https://www.slideshare.net/HubSpot/git-101-git-and-github-for-beginners)
* [Git Intro – Ariel Rokem](http://arokem.github.io/2013-09-16-ISI/lessons/git-notebook/git-for-scientists.slides.html#/1)
* [Reproducible Workflows – Russ Poldrack](https://github.com/poldrack/reproducible-workflows)
* [Git Cheatsheet – NDP Software](http://ndpsoftware.com/git-cheatsheet.html#loc=remote_repo;)