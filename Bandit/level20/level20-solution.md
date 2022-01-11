- `ls`

```
bandit19@bandit:~$ ls
bandit20-do
```

```
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
```

This file will run a command as user *bandit20*.

```
bandit19@bandit:~$ whoami
bandit19
bandit19@bandit:~$ ./bandit20-do whoami
bandit20
```

We already know that the password is stored in `/etc/bandit_pass/bandit20` file.

```
bandit19@bandit:~$ ls -l /etc/bandit_pass/ | grep "bandit20"
-r-------- 1 bandit20 bandit20 33 May  7  2020 bandit20
```

This file can only be read by the user *bandit20*.

```
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

`ssh bandit20@bandit.labs.overthewire.org -p 2220`