# Level 0 -> Level 1 (Solution)

- find the next level's password by using following commands

```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
bandit0@bandit:~$
```

- exit the shell and login again with the username of **bandit1** and the password `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```
