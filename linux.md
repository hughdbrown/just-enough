# Just enough Linux to poke yourself in the eye

## Create an empty file
```bash
$ touch foo
```

## Delete a file, directory 
```bash
$ rm foo
$ rmdir foo
```

## Write out contents of file to screen
```bash
$ cat foo
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
