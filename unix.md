# Just enough unix to poke yourself in the eye

I wont cover all options/flags of commands/programs here, but know that those are available. 

## Notes 

```unix

* Prompts usually start with $ or %. If it starts with #, this usually
  means that you are logged in as the superuser. So be aware. 

* To revisit old commands you can typically press the up arrow, where 
  pressing it multiple times allows you to cycle through all your previous
  commands.

* To navigate single characters in a line, you can typically use your left
  and right arrows. Holding down your meta key (typically alt on mac) will 
  allow you to navigate through whole words at a time. Also, tab completion 
  is a thing in most unix shells. What this means is that you can type the 
  beginning couple of letters of a file or directory and hit tab to complete
  it (so long as the file/directory name is unique, otherwise it will complete
  up to the point it can). 

* Files prefixed with a . are almost always hidden. This usually includes 
  your .bash_profile, where you can customize your unix account/shell 
  settings. Aliases are pretty cool - you should check them out. 

```
## Basics, and Environment Variables 

Environment variables can be accessed by prefixing them with a $. Some common 
ones are $SHELL, $USER, $OSTYPE, $PATH, $HOSTNAME, $HISTFILE. 

```unix 
echo foo # Display line of text following echo command (here foo). 
echo $SHELL # Display the path to the current shell. 
echo $USER # Display the current user. 
echo $HOSTNAME # Display the systems hostname. 
echo $PATH # Display the colon separated list of directories to search for 
           # binaries. 
echo $HISTFILE # Display the path to where the command history file is saved.
echo $OSTYPE # Display the type of operating system. 

whoami # display the current user. 
who # Display basic info for each logged-on user. 
who am i # Display basic info for those users at your terminal. 

date # Display the current date and time.

/bin/bash --version # Display the verison number of your unix shell. 
                    # Here we've assumed it's bash, and its located 
                    # at /bin/bash. 

groups # On most unix systems, this will list the groups you as a user 
       # are part of. 

history # Displays a history of the commands/programs you have run at the 
        # unix terminal. 
```

## Navigating the unix terminal

#### Control-Key commands 

Note here that ^h is the same as ctrl-h on a mac, and the equivalent
on a windows system. 

```unix 
^u # Erases input from current location to beginning of line
^k # Erases input from the current locaiton to the end of the line. 
^s # Pauses output from a program thats writing to screen. 
^q # Restarts output from a ^s pause 
^a # Jump to beginning of line
^e # Jump to end of line 
^z # Suspend a program that may be running and gives you another shell prompt. 
^c # Kill a program that may be running 
^l # Clear the entire screen (works like typing 'clear' ). 
```

#### Exploring the filesytem  

Its important here to make the distinction between absolute paths, which 
always start with a / and begin from the root directory, and relative paths, 
which do not begin with a / and start from the current working directory. cd 
is the command that we use to nagivate from one directory to another. 

```unix
pwd # Display the absolute path of the current working directory. 

cd # Navigate to home directory. 
cd ~ # Navigate to home directory.
cd .. # Navigate up one directory. 
cd . # Navigate to the current directory (doesn't move you at all). 
cd /spam/ # Navigate to the spam directory, which is a subdirectory of the root. 
cd spam/ # Navigate to the spam directory, which is a subdirectory of the current         
         # working directory. 

ls # List all files and subdirectories (excluding hidden) in the current working
   # directory. 
ls -a # List all files and subdirectories (including those hidden) in the 
      # current working directory. 
ls -F # List all files and subdirectories (excluding hidden) and show which 
      # are executable for the current working directory.  
ls -R # List all files and subdirectories (excluding hidden), recursively 
      # for the current working directory.
ls -l # List all files and subdirectories (excluding hidden) with additional 
      # information (such as read/write permissions) for the current working 
      # directory. 
```

## Working with Files

#### Looking Inside Files 

```unix 
less # Allows you to read a long file on screen; typically displays 
     # one page at a time. 
more # Seems at this point to be almost the exact same as the less command.
     # Supposedly some systems even have the two linked to the same binary.

cat file1.txt # Display the contents of file1.txt to the standard output 
              # (standard output is the screen unless changed). 
cat file1.txt file2.txt # Display the contents of file1.txt and file2.txt 
                        # to the standard output, one after the other 
                        # without stopping. 

tail file1.txt # Display the last 10 lines of file1.txt. 
tail -50 file1.txt # Display the last 50 lines of tile1.txt. 

head file1.txt # Display the first 10 lines of file1.txt. 
head -30 file1.txt # Display the first 30 lines of file1.txt.

```

#### Changing permissions

```unix 

The program/command to change permissions is chmod. It has three parts: 

1.) The category of the permission you want to change. 
    u: owner/users permission 
    g: groups permission
    o: others permission 
    a: all permissions (u, g, and o)

2.) Whether you want to add (+) the permission, delete (-) it, or specify 
    it exactly (=). 

3.) What permissions you want to affect: read (r), write(w), or execute (x). 

The program/command to change the group owner of a file or directory is 
chgrp. 

Note: The method describe above is named the symbolic method of changing
permissions. You could also use the absolute method, which I avoided here 
because I think this method is more straightforward. 

Examples: 

chmod u+w filename # Add user/owner write permission to file named filename. 
chmod a-w dirname # Delete all write permissions for the directory. 
chmod u=rwx dirname # Give the user/owner full access to a directory 
                    # (read, write, execute)
chmod go= filename # Set group and others permission to nothing for file named
                   # filename. 
chgrp me myfolder # Set the group owner of myfolder to group me. 
```

#### Managing Files 

```unix

mkdir is the program/command for creating directories, cp for copying 
files/directories, mv for moving/renaming files or directories, rm 
for removing files, rmdir for removing directories. These are some of 
the most common programs/commands for managing files. I've shown some 
of these programs/commands below with the -r (recursive) option. 
BE EXTREMELY CAREFUL WITH THIS!! Especially when deleting directories 
and or subdirectories. It can be easy to accidentally wipe out an 
entire directory.  

mkdir spam # Create directory spam in the current working directory. 
mkdir spam eggs # Create two separate directories, called spam and eggs, in 
                # the current working directory. 

cp file1.txt file2.txt # Copy file1.txt to a new file called file2.txt. 
cp file1.txt file2.txt file.txt spam # Copy three seperate files all to the  
                                     # folder named spam, without 
                                     # changing their names.                                 
cp -r spam eggs # Copy folder spam recursively into folder eggs. 

mv file1.txt file2.txt # Rename file1.txt to file2.txt. 
mv file1.txt spam # Move file1.txt to folder spam. 

rm file1.txt # Delete file named file1.txt
rm file1.txt file2.txt # Delete files named file1.txt and file2.txt
rm -r spam # Delete spam directory and all files within it (i.e. recursively). 
rmdir spam # Delete spam directory - only works if this is empty (otherwise 
           # need to use the -r recursive option with rm)
```

## I/O and Redirection. 

```unix 
There are three default I/O streams: standard input, standard output, and 
standard error. Unless you have changed it, programs will read standard 
input from the keyboard and send standard output and standard error to 
the terminal display.
```

```unix 

1.) Adding ' > filename' to the end of a command line will divert the 
    program's output from the standard output to the named file. 
    For example: 

        cat file1.txt > file3.txt 

    Will take the contents from file1.txt that you would typically see 
    on the screen (since cat displays right to the screen) and divert 
    those into a file called file3.txt. Note that for this use case, 
    the results are the same as cp file1.txt file3.txt. Also note that 
    this redirection may overrwite an existing file if you divert the 
    output to it. Be careful!

    You can use this > redirection operator with any program that sends 
    text to the standard output: 

        who > users.txt
        date > today.txt 

2.) The >> redirection operator works almost exactly like the > redirection 
    operator, except that it appends to the end of the file, rather than 
    overwriting it. 

3.) The < redirection operator allows you to tell a program to read input from 
    a file. 

    cat < file1.txt

    This will tell the cat program to read its input from file1.txt. Note that 
    this does the exact same thing as cat file1.txt. 

4.) Piping output (denoted by the | character) is the process of connecting 
    two programs such that the output from one program becomes the input of 
    the next. Two programs connected in this way form a *pipe*. 

    The standard output to the command to the left of the pipe becomes the standard
    input of the command to the right of the pipe symbol. 

    ls -l | grep "Aug"

    Will run ls -l to list your directory, and then pipe that output to the grep 
    command/program (which searches for the word "Aug")
```



        
