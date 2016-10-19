Git Config
===

Some useful git aliases to add to your global .gitconfig

```bash
[alias]
  co = checkout
  ec = config --global -e
  up = !git pull --rebase --prune $@ && git submodule update --init --recursive
  cob = checkout -b
  cm = !git add -A && git commit -m
  save = !git add -A && git commit -m 'SAVEPOINT'
  wip = commit -am "WIP"
  undo = reset HEAD~1 --mixed
  amend = commit -a --amend
  wipe = !git add -A && git commit -qm 'WIPE SAVEPOINT' && git reset HEAD~1 --hard
  bclean = "!f() { git branch --merged ${1-master} | grep -v " ${1-master}$" | xargs git branch -d; }; f"
  bdone = "!f() { git checkout ${1-master} && git up && git bclean ${1-master}; }; f"
  graph = log --graph --date-order -C -M --pretty=format:\"<%h> %ad [%an] %Cgreen%d%Creset %s\" --all --date=short
  lasttag = describe --tags --abbrev=0
  logmerged = "!f() { git log ${1-master}..${1-development} --oneline --merges; }; f"
  logcommits = "!f() { git log ${1-master}..${1-development} --oneline --no-merges; }; f"
  logmergedall = "!f() { git log ${1-master}..${1-development} --oneline; }; f"
  deleteMerged = "!f() { git branch --merged | egrep -v '(^\\*|master|dev)' | xargs git branch -d; }; f"
  lol = log --oneline --decorate --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'
  changelog = "!f() { git shortlog ${1-master}..${2-development} --format='%h %Cgreen %s' -e; }; f"
  oldbranches = "!f() { git for-each-ref --format='%(color:cyan)%(authordate:format:%m/%d/%Y %I:%M %p)    %(align:25,left)%(color:yellow)%(authorname)%(end) %(color:reset)%(refname:strip=3)' --sort=authordate refs/remotes --merged | egrep -v '(^\\*|master|dev)' | grep \"$(git config user.name)\"; }; f"
  lol = log --oneline --decorate --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'
  assume-unchanged = update-index --assume-unchanged
  no-assume-unchanged = update-index --no-assume-unchanged
  listassume = ls-files -v|grep '^h'
```

## git co
Checkout to a branch

```bash
git co [branch name]
```

## git ec
Open up .gitconfig using your default editor

```
git ec
```

## git up
Update local branch and rebase so that any local changes come after the commits I pull down

```bash
git up
```

## git cob
Create a branch and switch to it

```bash
git cob [branch name]
```

## git cm
Add all uncommitted files and then commit them

```bash
git cm "commit message"
```

## git save
SAVE and WIP can both be used to temporarily save you progress much like stash but this way you get a proper commit you can then use git undo to remove this commit
Add all files tracked and untracked and commit them

```bash
git save
```

## git wip
Similar to save but only commits tracked files

```bash
git save
```

## git undo
Undo the last commit but keep files

```bash
git undo
```

## git ammend
Amend the last commit message

```bash
git amend
```

## git wipe
If you working on an idea and then decide that you have taken the wrong route, you can use git wipe this will remove all the work but allow you to recover the changes if you later decide that part of it was useful. To recover the code you will need to use git reflog and look for the commit with the message WIPE SAVEPOINT.

```bash
git wipe
```

## git bdone
Branch done will swap you to master or specified branch and then delete all branches that have already been merged in to the specified branch.

```bash
git bdone # delete all branches that have been merged into master
git bdone development #delete all branches that have been merged in to development
```

## git graph
Show a visual representations of the branches

```bash
git graph
```

## git logmeredall
Show all merge commit and commits that have happened on development since the last merge into master

```bash
git logmergedall
```
 
## git logmerged
Show all merge commits that have happened on development since the last merge into master

```bash
git logmerged
```

Show all merge commits that have happened on X branch since the last merge into X

```bash
git logmerged master dev
```

### git logcommits
Show all non merge commits that have happened on development since the last merge into master

```bash
git logcommits
```

## git lasttag
Shows the last tag

```bash
git lasttag
```

## git lol
This command will out the git log in graph format 

```bash
git lol
git lol -n 10 # limit to last 10 commits
```

## git assume-unchanged
Mark a file to all assume that it hasn't changed.

```bash
git assume-unchanged filename
```

## git no-assume-unchanged
Stops making git assume the file has not been changed

```bash
git no-assume-unchanged filename
```

## git listassume
Show a list of files that have been marked as assume unchanged

```bash
git listassume
```

## git changelog
This will output a log of all the commits between two branches defaults to check what is in development but not in master

```bash
git changelog
```

## git oldbranches (GIT 2.8 AND UP REQUIRED)
List users branches that have already been merged and can be deleted

```bash
git oldbranches
```
