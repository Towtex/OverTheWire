# Level 13 -> Level 14 (Solution)

- `ls`

```bash
bandit13@bandit:~$ ls
sshkey.private
```

- `cat`

```bash
bandit13@bandit:~$ cat sshkey.private 
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
...
...
...
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----
```

- `ssh`

```bash
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
bandit14@bandit:~$
```

```bash
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```

> we can continue to level15 or reconnect the server via ssh with this password

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```
