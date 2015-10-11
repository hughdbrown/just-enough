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
(b.) downloading another repository (known as _cloning_ in git). 

```bash 
git init knights-of-ni # Initialize new git repository called knights-of-ni. 
git init # Initialize the current working directory to be a git repository.

git clone url # This will copy an existing repository from a url. Often times
			  # this will be a url that you have grabbed from somebodys repo 
			  #  on github. 
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


