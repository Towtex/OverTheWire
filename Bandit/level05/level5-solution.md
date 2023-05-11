- `ls`
```
bandit4@bandit:~$ ls
inhere
```

- `cd`
```
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$
```

- `ls -la`
```
bandit4@bandit:~/inhere$ ls -la
total 48
drwxr-xr-x 2 root    root    4096 Oct 16  2018 .
drwxr-xr-x 3 root    root    4096 Oct 16  2018 ..
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file00
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file01
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file02
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file03
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file04
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file05
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file06
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file07
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file08
-rw-r----- 1 bandit5 bandit4   33 Oct 16  2018 -file09
```

We can check a file whether it's human-readable or not with `file` command.

- `file`
```
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
```

But it's so boring to check all the files manually. So, we will use the `find` command with the `-type` and `-exec` options along with the `file` command.

- `find . -type f -exec sh -c 'file "$0" | grep -q "text"' {} \; -print`

In this command, the `.` specifies the current directory as the starting point for the search. The `-type f` option specifies that only regular files should be included in the search.

The `-exec` option is used to execute the file command on each file found by `find`. The `sh -c 'file "$0" | grep -q "text"' {} \;` part of the command runs the `file` command on each file and pipes its output to `grep`, which searches for the word "text" in the output. The `{} \;` part of the command is used to substitute the filename found by `find` into the command.

Finally, the `-print` option is used to print the filename of each human-readable file that is found.

Note that this command may produce false positives, as some non-text files (such as HTML or XML files) may also be considered human-readable by the `file` command. To exclude these files, you can modify the `grep` command to look for a specific type of text file, such as "ASCII text" or "UTF-8 Unicode text".

```
bandit4@bandit:~/inhere$ find . -type f -exec sh -c 'file "$0" | grep -q "text"' {} \; -print
./-file07
./-file09
```

```
bandit4@bandit:~/inhere$ file ./-file07
./-file07: ASCII text
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

bandit4@bandit:~/inhere$ file ./-file09
./-file09: Non-ISO extended-ASCII text, with no line terminators
bandit4@bandit:~/inhere$ cat ./-file09
?3��[ٲN|?�G|b�G�[8�y�
```

- `cat`
```
bandit4@bandit:~/inhere$ cat <-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

OR

```
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

Password: `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`

```
ssh bandit5@bandit.labs.overthewire.org -p 2220
```
