# Level 19 -> Level 20 (Solution)

- `ls`

```bash
bandit19@bandit:~$ ls
bandit20-do
```

```bash
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
```

This file will run a command as user *bandit20*.

```bash
bandit19@bandit:~$ whoami
bandit19
bandit19@bandit:~$ ./bandit20-do whoami
bandit20
```

We already know that the password is stored in `/etc/bandit_pass/bandit20` file.
This file can only be read by the user *bandit20*.

```bash
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```

`ssh bandit20@bandit.labs.overthewire.org -p 2220`
