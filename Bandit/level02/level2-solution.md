- check the directory with ```ls``` and a dash(-) file is found
- to read a dash(-) file we can use ```cat``` with ```./``` or ```<``` 
  
```
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
OR
```
bandit1@bandit:~$ cat <-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

- use this password to login to the next level

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```
