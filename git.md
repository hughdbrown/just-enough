# Just enough git to poke yourself in the eye

## Getting Started 

I'll assume you've already got git installed and downloaded. 
Git uses a name and email address to identify the author of a 
commit. Setting these will change what is shown in the logs 
(i.e. the user and associated email of whoever made each 
commit). If these are not set there are defaults that will 
be used. 

All git commands have complete references to their syntax and 
arguments using Git's help, which you can use by running 
the command followed by --help (i.e. git config --help). Googling 
things will be incredibly helpful, but be careful not to just 
copy and paste commands, as you can pretty quickly wipe out 
an entire repo. 

#### Setting your username and email. 

```bash
git config --global user.name 'Monty Python' # Set username for your OS. 
git config --global user.email mpython@gmail.com # Set email for your OS. 

git config --global user.name 'Monty Python' # Set username for the individual 
											 # git repository you are in. 
git config --global user.email mpython@gmail.com # Set email for the individual 
												 # git repository you are in.

git config --get user.name # View username. 
git config --get user.email # View email. 
```

#### Initializing a Git repository. 

A git repository is a __local__ collection of files and contains 
a .git subdirectory in its root. Git keeps track of the state of 
the files in the repository's directory on disk (so long as those 
files have been added to the index - see below). There are a couple
of different ways to create a new repository - two of those are 
through (a.) initializing an empty, new local repository, and 
(b.) downloading another repository (known as _cloning_ in git). Right 
now we are going to assume we're working locally and are using method (a). 

```bash 
git init knights-of-ni # Initialize new git repository called knights-of-ni. 
git init # Initialize the current working directory to be a git repository.
```

#### Adding a file/directory and committing it. 

The standard workflow within a git repository is that you will change 
one or more files in that repository, possibly review the changes, 
add them to the _index_ (a file that git uses to keep track 
of files), and then create a new commit with those changes.  


```bash
git status # Will give you the status of your repository (i.e. what 
		   # files have been modified/created). 

git add spam_recipe.txt # Add file spam_recipe.txt to the index staging area. 
git add eggs/ # Add folder eggs to the index staging area. 
git add . # Add files/directories to the index staging area.
git add --all # Add the files/directories to the index staging area. 
git add -A # Add the files/directories to the index staging area. 

git commit -m 'I committed!' # Commit all files in the index staging area
							 # with the commit message 'I committed!' Note
							 # the -m here is the shortened form of --message. 
```

I've mentioned the _index_ file above, and understanding it isn't necessary, 
but helps. The _index_ file (which is hidden in the .git subdirectory of any 
git repository) keeps track of all files that the git repository 
is actually responsible for tracking. The 'git add' command above will 
put files into the index the first time its run on a file, and from then 
on out will only note changes. For example, if I had just
created spam_recipe.txt above, then I would have added it to the index 
(telling git to keep track of it). If I had already added spam_recipe.txt 
to the index, but made changes, then that command would have added the 
changes to the index. If I had already added spam_recipe.txt to the index
but not made changes, then that git add command would be worthless. Git commit
simply commits the files or changes to files that have been added to the _index_
to the repository (you can more or less think of it as making your changes official; 
they've now gone down in history). 

## Getting Around 

The git log command allows you to view the history of your repository. 
A _diff_ in git references the changes between commits, and the git 
diff command allows you to view changes between different commits, 
branches, etc. We'll get to branches a little later, but for now 
just know that they are different contexts/environments for the 
same repository. 

```bash 
git log # List all commits that have been made on the current branch, 
		# with the most recent first. 
git log psql.md # List only those commits that include changes to 
				# the file psql.md.
git log --patch # Lists all commits that have been made on the current
				# branch, but adds the diff for each commit output. Note 
				# you can also do this with the -p flag (short for --patch).

git diff # Displays the differences between the current working directory
		 # and the index staging area (i.e. any changes you have not yet 
		 # added with git add). 
git diff psql.md # Displays the differences between the current working 
				 # directory and the index staging area, but only for 
				 # the psql.md file (i.e. shows any changes to the psql.md
				 # file that have not been added with git add). 
git diff master~1 master # View the differences between the previous 
						 # commit and the latest on the master branch. 
git diff denver2~1 denver2 # View the differences between the previous 
						   # commit and the latest on the denver2 branch. 
						   # Note you have to have a copy of the branch on 
						   # your local to do this (or else reference its path 
						   # via the remote - something like remotes/origin/denver2). 
git diff master~1 master psql.md # View the differences between the previous 
								 # commit and the latest on the master branch, but
								 # only for the psql.md file. 
```

## Working with Remotes

#### Adding a remote repository to your local, and pushing changes to it. 

If you have initialized a local git repository, but need to send or 
receive data from another machine, you will need to add a remote 
repository. Since git is largely used in conjunction with github, we're
going to assume that we have created a remote repository on github. At the 
homepage for that remote repository, you should be able to use the url 
for that repo to add it as a remote. 

```bash
git remote add origin https://github.com/sallamander/just-enough.git # Add the just-enough.git repository 
																	 # at https://github.com/sallamander
																	 # as a remote repository for our
																	 # current git repository (assuming 
																	 # were in one). 

git remote --verbose # Display the fetch and push urls that git uses to fetch remote commits and 
					 # send new local commits. 

git push --set-upstream origin master # Push any changes from the local repository to the origin remote
									   # (here the one weve set up on github). Note that you only need 
									   # the --set-upstream origin master the first time you push to it. 
									   # From then on out you can just use git push. 
git push -u origin master # Same as the above; also only needs to be used the first time you push to the 
						  # origin remote after adding it as a remote. 
```

#### Cloning a remote/Github repository onto your local. 

While useful to know how to create a local repository, add a remote, and learn 
to push to it, often times we will just be downloading an existing repository
to use as your local. The process of creating a new local repository from an 
existing remote repository is known as _cloning_ a repository. 

```bash
git clone url # This will copy (clone) an existing repository from a url. Often times
			  # this will be a url that you have grabbed from somebodys repo 
			  #  on github. 
git clone url special-folder-name # This will clone the existing repository from the url, 
								  # but rather than putting it into a folder with the same name
								  # as given by that url, will put it into a folder called 
								  # special-folder-name. 
```

Note that after this process, the new repository that you will have created on your local 
will have the repository at that url as the __origin remote__ (you won't need any separate
configuration steps for that). This means that when you issue the git push command it will 
push to that origin remote at that url.

#### Working with new commits from the remote repository. 

Let's say that there are some commits stored in the remote repository that you would 
like to get onto your local machine. There are two options to do this... 

```bash 
git pull # This will pull any new commits from the remote into the local, and merge those
		 # commits into your local repository. 

git fetch # This will fetch any new commits from the remote, but NOT merge them into your 
		  # local repository. This allows you to view differences between the remote and 
		  # your local. 

git diff origin/master # After running git fetch, using this command will show you the 
					   # differences between your local repository and the remote repository. 
```

## The Basics of Branching 

Typically, the history of a repository continues linearly, with each commit pointing to 
the last. Branching allows two independent tracks through history to be created and 
committed to without either modifying the other. They can be particularly useful if you 
want to keep a working branch of the repository for public consumption, but work on 
making new commits for a new feature that isn't ready for public consumption. 

If you are done with a branch and want to bring all the changes made on it into another
branch, then we need to use a git _merge_. This has the possibility of introducing 
_merge conflicts_, which occur when both branches involved in the merge have altered
the same parts of the file. To resolve these, you'll have to go through the files git 
tells you have conflicts, and choose which lines from the appropriate branch you want 
to keep. 

```bash 
git branch second-branch # Create the branch second-branch. 
git checkout second-branch # Checkout the second-branch. This will checkout the contents of
						   # the second-branch into Gits working directory. 
git push --set-upstream origin second-branch # This assumes that you have checked out the 
											 # second branch, and then pushes any changes from 
											 # that branch up to a remote branch named second-branch. 
											 # If that remote branch is not created it will first create
											 # it. 

git merge second-branch # This assumes that you have checked out the master branch, and then merges
						# the branch named second-branch into it. 
```
