# Level 1 -> Level 2 (Solution)

- check the directory with ```ls``` and a dash(-) file is found
- to read a dash(-) file we can use ```cat``` with ```./``` or ```<```

```bash
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

OR

```bash
bandit1@bandit:~$ cat <-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

- use this password to login to the next level

```text
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```
