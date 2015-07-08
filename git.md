= Just enough git to poke yourself in the eye

== Delete branch

Delete a local branch `foobar` like this:

```bash
$ git branch -D foobar
```

Delete the remote branch  `foobar` like this (using git 1.7.0 and later):

```bash
$ git push origin --delete foobar
```

== Clone a repository

```bash
$ git clone url <destination>
```

url has three different formats
1. git@HOST:PATH
2. git://HOST/PATH
3. https://HOST/PATH

== Push new branch to origin

Try sending it like this:

```bash
$ git push
```

git will fail but give you the correct command in the error message.

== Rebase local changes onto remote

```bash
$ git fetch
$ git rebase -p origin/master
```

== Edit commit message

```bash
$ git commit --amend
```

== Change diff output

```bash
$ git config merge.conflictstyle diff3
```

== Undo last commit

```bash
$ git reset --hard HEAD~1
```

```bash
$ git reset --soft HEAD~1
```

```bash
$ git revert HEAD~1
```

== Fix merge conflicts

```bash
$ git mergetool
```

== Find lost commit

```bash
$ git reflog
```

== Squash merge

```bash
$ git merge --squash branch-name
```

== Making a branch

```bash
$ git checkout -b branch-name
```

== Merging a branch

```bash
$ git merge branch-name
```

== Saving changes before working on different branch

```bash
$ git stash
```

== Finding where breaking code was added

```bash
$ git bisect
```

== Squashing local commits

```bash
$ git rebase -i HEAD~n```

== Ignore files in directories

```bash
$ touch .gitignore
```

== Add files/directories to git repo

```bash
$ git add filename
```

```bash
$ git add directory
```

== Install git

=== On ubuntu

```bash
$ sudo apt-get install git
```

=== From source code

```bash
$ wget https://github.com/git/git/archive/master.zip && \
    unzip master.zip && cd git-master && \
    ./configure && make && sudo make install
```

== Rebase changes on top of remote

When I work with a fork of a github repo, I occasionally want to rebase my code on top
of the latest code. Here is what I do:
- make a remote that points to the original code
- fetch the code
- rebase my code on top of the FETCH_HEAD

Here is an example from when I forked causes/overcommit:
```bash
$ git remote add causes git://github.com/causes/overcommit.git
$ git checkout master
$ git fetch causes/master
$ git rebase -p FETCH_HEAD
```

Here is an example from when I forked disco/disco_eggs_template:
```bash
$ git remote add disco git@github.wgenhq.net:Disco/disco_eggs_template.git
$ git remote update
$ git rebase -p FETCH_HEAD
```

== Common ancestor for two branches

```bash
$ git merge-base A B
```

Here is a [source for this](http://stackoverflow.com/questions/1549146/find-common-ancestor-of-two-branches).
