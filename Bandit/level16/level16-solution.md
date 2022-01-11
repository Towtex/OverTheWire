- `echo, openssl, s_client`

```
bandit15@bandit:~$ echo "BfMYroe26WYalil77FoDi9qh59eK5xNr" | openssl s_client -ign_eof -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
...
...
...
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```

```
ssh bandit16@bandit.labs.overthewire.org -p 2220
```