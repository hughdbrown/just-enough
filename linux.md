# Just enough Linux to poke yourself in the eye

## Moving Around Directories
```bash 
$ cd # Move to home directory. 
$ cd .. # Move up one directory
$ cd ../foo # Move up one directory, then to foo within that
$ cd ~/foo # Move too home directory, then to foo within home
```

## Create an empty file
```bash
$ touch foo
```

## Delete a file/directory 
```bash
$ rm foo # File
$ rmdir foo # Directory 
```

## Displaying Contnents of Files to Screen
```bash
$ cat foo # Display all contents of file foo
$ less foo # Display one page at a time of file foo 
$ head file # Display the first few lines of file foo (default is first 10)
$ tail file # Display the last few lines of file foo (default is last 10)
```

## Copy a file
```bash
$ cp foo .. # Copy up a directory
$ cp foo bar # Copy to new file named bar
```

## Move a file
```bash
$ mv foo .. # Move file up a directory
```

## Rename a file
```bash
$ mv foo bar # Rename foo to bar
```

## Copy a lot of files to another machine
```bash
$ rsync --recursive --verbose --whole-file --progress . myname@192.168.1.2:/tmp/
```
