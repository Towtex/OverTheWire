# Level 15 -> Level 16 (Solution)

- `echo, openssl, s_client`

```bash
bandit15@bandit:~$ echo "jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" | openssl s_client -ign_eof -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
...
...
...
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
```

Password: `JQttfApK4SeyHwDlI9SXGR50qclOAil1`

```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
```
