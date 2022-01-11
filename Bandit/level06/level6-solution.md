- `ls`
```
bandit5@bandit:~$ ls
inhere
```

- `cd`
```
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$
```

- `ls`
```
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
```

- `find`
```
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
```

- `cat`
```
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```


```
ssh bandit6@bandit.labs.overthewire.org -p 2220
```