- check the directory with ```ls``` and a dash(-) file is found
- to read a dash(-) file we can use ```cat``` with ```./``` or ```<``` 
  
```
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
OR
```
bandit1@bandit:~$ cat <-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

- use this password to login to the next level

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```
