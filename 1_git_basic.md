# Step 0 - The setup

1.  Download git > cli > install
2.  Create git A/C
    git config --gloal user.email "enter your email"
    git config --gloal user.name "enter your name"
    - git config user.name : Check
3.  If not on a Mac/Linux OS, download HYPER or MobaXterm or use VS code Terminal(view terminal) to work with CLI

**Git** : is a SW that keeps track of your project progress by taking snaps wrt TS & saves any changes/commits in its history. Just in case if you want to revert back/revisit to those changes or commits on your local sys's repository/dir.

- Its a VCS (Version Control Sys): let's say we created a file (f1.txt) in git 'VCS' & it created a save point (S1) --> Call it Version 1
  Later on, we modified the the file (f1.txt) & it created another save point (S2) --> call it Version 2
  Similarly, it creates n number of versions (Sn) --> Ver-n
  Down the line if anything goes wrong/unexpected, we can always rollback to earlier save points or Versions from the current version.

**Github** : is a platform that hosts git repositories/any repo/any dir or share with community

--- **\_\_** ------------- **\*\***\_\_\_\_**\*\*** **\*\*\*\***\_\_**\*\*\*\*** \***\*\*\*\*\***\_\_\***\*\*\*\*\*** \***\*\*\*\*\***\

# Git BASICS:

### Terms

**Working Dir** : git initialized repository/folder (empty) in local sys, i.e. pwd of the project (git-learn) ---> git init
Where u initialize your local git repository & now git keeps track of changes made between present working dir (git-learn) & local repository (.git)
**Local repository** (on PC) : After commit is done, changes are made/history is saved on local (.git) repository in VCS. It gets a name/hash-code-id via commit msg.
**Remote repository :** a repo/dir/folder on server like github.
**Staging Area** : an intermediate point, where you can pick & choose which files inside your projects working dir, you wanna commit. ---> git status
**Untracked files** : Files in Red color, i.e. inside workig dir but not in staging area --> unsateged & uncommited
e.g. Wedding photoSnaps, wedding guest couples will go onto 'stage' to clik a snap with the bride & bridegroom, which then later will be saved in a wedding album as a history 'respository' --> logs
Untrackable: guests whose snaps have not been taken yet
**Staging**: Add files to stage, Files in Green color & start tracking them in VCS ---> git add .
**Commit :** Save changes made/ history/ Save points in VCS ---> git commit -m "type msg in present tense by convention"

**Git Status :**

1. Untracked : a new file that git isnt trackig yet or is unaware
2. Modified : a tracked file that changes
3. Staged : file ready for commit
4. Unmodified : no chages made yet

### Step 1 : Create a project dir & files

- mkdir DevOps : open terminal & create dir
- cd DevOps > mkdir git-learn
- git init : initialise an empty git repository 'git-learn'
- ls -a > cd .git > ls : To maintain history/progress of projects git creates a hidden folder '.git'

- touch name.txt : create a file
- git status : it will tell if any chages were made in the project?

- git add . : to add all the files in current dir & make them ready for staging area
- git add file-name : to add an individual file of current dir & get it ready for staging area
- git status : will show files staged (in green) ready for a snapShot or if any changes made to the files

- git commit -m "enter your msg : like added xyz file or 1st commit"
  -m is msg flag, commit the changes or take snapShot of the staged files & save in History/repo '.git'
  o/p: added file-name, 0 lines of code inserted, 0 deleted

- git status : o/p : Nothing (if no more snaps/changes to take), working tree clean

### Step 2 : Add some data or lines of code in files

- vim name.txt > i > add some code lines > Esc > :wq > y > cat name.txt
- git status : o/p : changes not staged for commit yet, modified : file-name
- you may use any of your fav editors, if not liking Vim/Nano

### Step 3 : Stage the modified files or unstage a file

- git add . or git add file-name : stage the changes made > git status
- git restore --staged name.txt : to unstage this file, file doesn't get deleted but just unstaged for snapShot
- git add file-name : to stage again/re-stage > git status

## Step 4 : Commit Changes & Save History snaps in repo\*\*

- git commit -m "added 3 lines of code - names.txt file modified"
- git status : o/p : 1 files changed, insertions = 3 , deletions = 0

## Step 5 : How to know history/logs\*\*

- git log : opens in vim, lastest commit at top & oldest at the bottom > Esc :q
- Each commit is build/stacked ontop of each other & each has a UID hash-code in the history/repo
- To del a commit/commits, copy the commit #id of the commit just below target commit that's to be removed

## Step 6 : More commits to do, Uncommit\*\*

- rm -rf names.txt : uncommit a file but don't del it
- git add names.txt > git commit -m "names.txt file was removed from this commit" > git log
- git reset #commit_id-just-below-the-target-commit : to remove commits from the project, like a feature X > git status
- git restore ??? : for changes made by mistake

## Step 7: Stash Area/ git-staging/ Dont add in project History\*\*:

- when u dont want a separate commit or changes made right now neither to be added nor to be removed in project history but to be kept & recalled whenever needed like some new feature-X >>> stash it (neither use nor loose atm)
  e.g. send some couples guests backstage & wheneva they're ready -> stage them -> snap -> save history
- git add names.txt or git add . : for a particular file or for all changes made in the dir
- git stash

## Step 8: Bring commits (files) from Stash area to Unstaged area & Del permenently\*\*

- git stash pop : from stash to unstage area
- git add .
- git stash : send back to stash area

- git stash clean

## Step 9 : Compare Save points, Restore\*\*

- git diff : chk difference between current version (in Green) & last save point/ver (in Red)
- git diff file-name : for a particular file

- git checkout file-name.ext : restores currrent file to previous save point under VCS & the current changes will be lost in our local repo.
