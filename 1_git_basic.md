# Step 0 - The setup

1.  https://git-scm.com/downloads > Download git > cli > install
2.  Create git Account

```
git config --gloal user.email "enter your email"
git config --gloal user.name "enter your name"
git config user.name : Check
git config user.email : check
```

3.  If not on a Mac/Linux OS, download HYPER or MobaXterm or use VS code Terminal(view terminal) to work with CLI

**Git** : is a SW that keeps track of your project progress by taking snaps wrt TS & saves any changes/commits in its history. Just in case if you want to revert back/revisit to those changes or commits on your local sys's repository/dir.

- Its a VCS (Version Control Sys):
  - let's say we created a file (f1.txt) in git 'VCS' & it created a save point (S1) --> Call it Version 1.
  - Later on, we modified the the file (f1.txt) & it created another save point (S2) --> call it Version 2.
  - Similarly, it creates n number of versions (Sn) --> Ver-n.
  - Down the line if anything goes wrong/unexpected, we can always rollback to earlier save points or Versions from the current version.

**Github** : is a platform that hosts git repositories/any repo/any dir or share with community

# Git BASICS:

### Terms

- **Working Dir** : git initialized repository/folder (empty) in local sys, i.e. pwd of the project (git-learn) ---> git init
  - Where u initialize your local git repository & now git keeps track of changes made between present working dir (git-learn) & local repository (.git)
- **Local repository** (on PC) : After commit is done, changes are made/history is saved on local (.git) repository in VCS. It gets a name/hash-code-id via commit msg.
- **Remote repository :** a repo/dir/folder on server like github.
- **Staging Area** : an intermediate point, where you can pick & choose which files inside your projects working dir, you wanna commit. ---> git status

- **Untracked files** : Files in Red color, i.e. inside workig dir but not in staging area --> unsateged & uncommited

  - e.g. Wedding photoSnaps, wedding guest couples will go onto 'stage' to clik a snap with the bride & bridegroom, which then later will be saved in a wedding album as a history 'respository' --> logs
  - Untrackable: guests whose snaps have not been taken yet

- **Staging**: Add files to stage, Files in Green color & start tracking them in VCS ---> git add .
- **Commit :** Save changes made/ history/ Save points in VCS ---> git commit -m "type msg in present tense by convention"

**Git Status :**

1. Untracked : a new file that git isnt trackig yet or is unaware
2. Modified : a tracked file that changes
3. Staged : file ready for commit
4. Unmodified : no chages made yet

### Step 1 : Create a project dir & files

```
git-cmds : #comments    <----   FORMAT used
```

- mkdir DevOps : open terminal & create dir
- cd DevOps > mkdir git-learn

```
git init : initialise an empty git repository e.g. 'git-learn' on your local PC
```

- ls -a > cd .git > ls : To maintain history/progress of projects git creates a hidden folder '.git'

- touch name.txt : create a file
- git status : it will tell if any chages were made in the project?

```
git add . : to add all the files in current dir & make them ready for staging area
git add file-name.ext : to add an individual file of current dir & get it ready for staging area
git status : will show files staged (in green) ready for a (snapShot) i.e. next commit or if any changes made to the files (in working dir)
git commit -m "enter your msg : like added xyz file or 1st commit"

-m is msg flag, commit the changes or take snapShot of the staged files & save in History/repo '.git'
output : added file-name, 0 lines of code inserted, 0 deleted
```

```
git status : o/p is Nothing (if no more snaps/changes to take), working tree clean
```

### Step 2 : Add some Data or Lines of code in files

- vim name.txt > i > add some code lines > Esc > :wq > y > cat name.txt
- git status : o/p : changes not staged for commit yet, modified : file-name
- you may use any of your fav editors, if not liking Vim/Nano

### Step 3 : Stage the modified files or Unstage a file

```
git add . or git add file-name : stage the changes made > git status
git restore --staged name.txt : to unstage this file, file doesn't get deleted but just unstaged for snapShot
git add file-name : to stage again/re-stage > git status
```

### Step 4 : Commit Changes & Save History snaps in repo

```
git commit -m "added 3 lines of code - names.txt file modified"
git status : o/p : 1 files changed, insertions = 3 , deletions = 0
```

### Step 5 : How to know History/Logs

```
git log : opens in vim, lastest commit at top & oldest at bottom ( ref. see TS)  > Esc :q
```

- Each commit is build/stacked ontop of each other & each has a UID hash-code in the history/repo
- To del a commit/commits, copy the commit #id of the commit just below target commit that's to be removed

### Step 6 : More Commits to do | Uncommit

```
rm -rf names.txt : uncommit a file but don't del it
git add names.txt > git commit -m "names.txt file was removed from this commit"
git log
git reset #commit_id-just-below-target-commit : to remove commits from the project --> i.e. unstage , like a feature X
git status

git reset HEAD~ : to go 1 step back & uncommit the present commit/ to previous commit as head *ptr always points to preset commit,  c1--c2--C3--Cn <--Head
git restore  : for changes made by mistake ???
```

### Step 7: Stash Area | git-Staging | Don't add in project History:

- When you dont want a separate commit or changes made right now neither to be added nor to be removed in project history but to be kept & recalled whenever needed, like some new feature-X >>> stash it (neither use nor loose atm) but remove from commit history.
  e.g. send some couples guests backstage & whenever they're ready -> stage them -> snap -> save history

```
git add names.txt   : for a particular file
git add .           : for all changes made in the dir
git status
git stash
git log : see commit history > q to exit
```

- But if its in sync with github remote repo., then you've to force push it as stash will remove commit history. Hence local vs remote repositories will get outta sync i.e. remote will be ahead of local git, in this case.

```
git log : copy #_hash_id of commit just below the target commit
git reset paste-hast-id
git status
git add .
git stash
git log
git push origin main -f : -f flag is for force push, your branch name in place of main
```

Refresh github page the commits will be gone from there as well, now both repo's. in sync again.

### Step 8: Bring commits (files) from Stash area to Unstaged area & Del Permenently

```
git stash pop : from stash to unstage area
git add .
git stash : send back to stash area & remove from commit history

git stash clean
```

### Step 9 : Compare Save points | Restore

```
git diff : chk difference between current version (in Green) & last save point/ver (in Red) i.e. what is changed but not staged
git diff file-name : for a particular file
git diff --staged : diff of what is staged but not commited yet

git checkout file-name.ext : restores currrent file to previous save point under VCS & the current changes will be lost in our local repo.
```

# GitHUB

- A repo hosted on remote servers

### Terms

- **Local git repo** : repo on your local sys
- **Remote git repo** : repo on remote server like on github (usually under your personal account)
- **Origin** : url of a remote repo (main branch)
- **Upstream** : Orginal (owners) project from which you've forked under your personal github a/c

### Step 10 : Create A/C | Url | Push to remote repository

1. Create a GitHub A/C > New or Profile > craete a New Repository > Name it > Pub/Pvt > Create > Copy its URL
2. Goto PC termial:
3. Genrate toke : profile > setting > devloveper > Personal Access Token > Classic > generate
   - git remote set-url origin https://paste-token@github.com/username/repo --> follow tokenisation docs
   - or authorise github in VS via github extension

**Push**

- You can directly push the dir to Github via VS code. Also its Syc feature will do the pull & push for you.

```
git remote add origin paste-URL : Attach remote github repo to local git on sys
```

- remote : workig with urls
- add : adds new url
- origin : what will be the name of url that you're going to add (like phoneBook) but by convetion all the repo's under your personal github a/c are named as Origin

```
git remote -v : list all the URLs (origins) under your a/c in this github repo
```

```
git push -u origin main : to push the local repo to remote repo
git push : for subsequent pushes on same branch
git push origin HEAD : this also does the same, for subsequent pushes on same branch
```

- origin : which url to push (customisable)
- main : on what branch of the remote github repo.
- -u : flag links remote repo with local --> sets upstream i.e. if we wish to continue working & pushing changes on the same branch (e.g. main) we dont've to mention it everytime but just the first time & then just this cmd "git push"

### Step 11 : Branching | Rename | Visualize

- https://learngitbranching.js.org/ : visualize branching {)
- git commit > git commit ..., > git branch featureX : create a new branch >
- git checkout featureX : ptr points now to featureX branch & commits will be done on feature branch
- git checkout main : ptr moves to main & now if u do commit, that will be done on main branch (Switch Head ptr)
- git commit : while u keep working on main, featureX branch remains unaffected & vice-versa
- git checkout : to know current branch status

---

- **Head :** ptr that points to current working branch, were commits will be done.
- **Branching :** is making commits (c1,c2,..Cn) in a project that are linked to each other on a same branch 'Main' by default

- Never commit changes to the main branch --> unless its tested & finalised, cause this is the actual working code that people are using
- Working on a bug or new feature --> always create a new branch --> branch parallel to main --> Tested --> Merge into Main branch

```
git branch : know the branch you're curretlly on <-- to which Head\* ptr points
git checkout : know current branch status
git checkout branch-name : switch head ptr to this branch
```

**Create | Rename Branch | Del**

```
git branch feature-X : create a new branch
git checkout -b feature-x : also creates a new branch
git branch -M new-name : rename a branch i.e. current branch

git branch -d branch-name : to del a branch, but you need to switch first onto a different branch. Otherwise err:'this your present branch'
```

### Step 12 : Frok | Clone | Pull Request (PR) | Contribute to an existing GitHub project

- **Fork** :
- Helps us to collab. using remote repo's to start working in a team or contribute your code to open source projects
- its making a replica of a same project/dir or someones (Owners Main/Original, who actually owns it) shared project but you can't make changes directly to his project.
- Problem you may face, is access to that specific project account, so we Fork that project under our own A/C on github > Code > copy https url
- once forked, you own it & have full permission to do the changes in your forked branch under your a/c

**Clone** : pulls/grabs a repo in its entiretity, into your local PC & stores it in your working dir

```
git clone paste-copied-url : retrive an entire repo from hosted location url
```

**Upstream url** : is the url from where you've forked (actual owners url).

```
git remote add upstream paste-Owners-url from where you've forked yours.
git remote -v
```

Project listed under your a/c will be your personal & others will be from the forked repo

```
git pull : fetch & merge any commits from the tracking remote brach/repo
git pull branch-name : in case remote repo is ahed of local git repo. Do pull & the push
```

**PULL Request** : after forking/cloning Owners main-project & making changes to your copy, you create a (PR) pull-req to the Owners upstream, requesting/suggesting him to approve the changes you've made & eventually merge it with the owner projects main branch. Then your PR gets reviewed if any changes needed, tested & finally merged.

- let people know about the changes you've pushed onto github shared project > PR > revied by senior dev > approved > merged

- Never commit on main branch.
- For every new feature/bug, always create a new PR. So that it would be easier to review & discuss.
- 1:1 (1 Branch : 1 PR) --> If a branch already has a PR assosciated with it, it will not allow you to create a new PR, as all the commits will added to the existing PR only. You need to create a new branch on your local folder, for any new PR.

### Step 13 : Merge branches | Upstream

- Make any changes in your forked branch/other branches within the same project & merge them with the main project/(Owners project) via PR using github web UI
- After merge, the forked remote repo isn't updated, to do it goto github > forked repo. name > code > Click 'Fetch Upstream'.
- This is also useful, if someone else working on xyz-feature merged his branch with main Owner's project i.e. keep the upstream & forked brach levels maitained.

- **Way 2** Doing the same via CLI

```
git checkout main : of forked project
git log : see commits present atm & compare them with upsteam (owners on github), one or the other will be behind
git fetch --all -- prune : fetches all the braches from upstream & 'prune' fetches the deleted braches as well
git reset --hard upstream/main : reset main branch of your origin(forked project in local git repo) to the main branch of Upstream project (owners)
git log : now see the local git has updated with the upstream
git push origin main : push to changes to your remote repo (forked), to keep them in sync
```

**Way 3**

```
git pull upstream main : alteatively you can do this in place of fetch & reset, as pull internally does the same thing, in one cmd
git log
git push origin main : local git main & upstream git main are already in sync, it sync the origin main (i.e. our forked remote repo)
```

**More | inspect & compare**

```
git log
git log git : show commits on branch_A that are't on branch_B
git log --follow file-name : show commits that changed file, even across renames
git log branch_B...branch_A : show diff what is in branch_A thats not in branch_B
git show[SHA] : show ay object in git in human readable form
```

### Step 14 : Squashing branches | Merge conflicts | Rebase | Reset

- Squashig/Merging a lot of commits into just one single commit

```
git branch temp : create a test branch
git checkout temp : switch head \*ptr

touch f1
git add .; git commit -m "c1"

touch f2
git add .; git commit -m "c2"

touch f2
git add .; git commit -m "c3"

git log
```

Merging above 3 commits in one commit:

- Method 1 is to reset c1,c2 i.e. unstage them, add again & then commit
- Method 2 is via rebase to squash them
  - get #hash-id of a commit, so that above it all other commits will be squashed or picked

```
git rebase -i #hash-id-of-commit : -i flag is interactive env.
select a 'pick' commit & squash other by prefixing s in front of the IDs
```

- **Commit Order: oldest at TOP & NEWEST at bottom i.e. top to bottom**

```
  Rebase Output: ------> To Squash:
  pick ac123 ----------> Below 2 commits will get squashed/merged in this commit only i.e. with the previous/preceeeding Pick commit
  pick ac124 ----------> s ac124 : #prefix
  pick ac125 ----------> s ac125 : #prefix
  pick ac126 ----------> Below commit will get squashed with this (Pick commit)
  pick ac127 ----------> s ac127 : #prefix
```

Esc:x #to exit the '-i' interactive shell env & to write commit msg > i > nav inside the file to the line where it says enter commit msg to your changes, just above the rebase progress #msg like commit merged or squashed > :x

```

git log
git push origin tmp or any-branch

git reset --hard #hash-id-of-oldest-commit : if u want to remove\* other commits | BE CATIOUS as gets removed from git & VS code as well
```

**Merge Conflict**

- Conflict : an evet that takes place when git is unale to resolve differences on its own betwee two commits
- lets say, in a file you made a change at line num 5 & another person also made a change on the same line. Now the git is confused which change should it follow.
- or when change occurs in a file on 2 different branches > we've conflict
- create a conflict to see, by changing something on line 5 in a file > merge > conflict arises

```
git add .
git commit -m "Bob made this change at line 5"
git push origin tmp
```

Similary another user Ana, does the same but now Ana will have to deal with merge conflicts > open github
to see both conflicts & resolve them manually which you wana keep & del the other one from the conflict file i.e. file overide

### Step 15 : Git ignore

- prevets commiting certain files to your local & remote repo
- lets create some files : touch f1.txt f2.txt f3.txt
- touch .gitignore : create a hidden file > ls -a > start .gitigore

```
git rm --cached -r . : if staged without adding git ignore
```

- **RULES**:
- open .gitigore file > write individual file names on each new line that you wish to be ignored during stage & commit
- anything starting with #hash is a comment in '.gitigore' file
- wild cards char usage : e.g. '\*' , if u want to make commit & ignore all the files with extension '.txt' --> \*.txt

```

git add .
git commit -m "msg"
goto github.com/repo-name/ignore

```

## Fixes

- edit git.config
- github repo > copy url > clone > push changes
- git push origin head
- goto github > insights > network > to see commit history & save points
- goto github > select repo main page > commits : to see save pts & changes made to in them

## Resources:

```
https://education.github.com/git-cheat-sheet-education.pdf *page 2

```
