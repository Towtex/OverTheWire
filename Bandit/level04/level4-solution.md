- ran `ls` and I got a directory named **inhere**

```
bandit3@bandit:~$ ls
inhere
```

- check this directory with `ls`

```
bandit3@bandit:~$ ls inhere
```
- nothing showed
- how about `ls -la`

```
bandit3@bandit:~$ ls -la inhere
total 12
drwxr-xr-x 2 root    root    4096 Oct 16  2018 .
drwxr-xr-x 3 root    root    4096 Oct 16  2018 ..
-rw-r----- 1 bandit4 bandit3   33 Oct 16  2018 .hidden
```

- we get a **.hidden** file

```
bandit3@bandit:~$ cat inhere/.hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

- use this password for the next level
```
ssh bandit4@bandit.labs.overthewire.org -p 2220
