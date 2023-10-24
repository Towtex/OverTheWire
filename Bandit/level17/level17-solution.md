# Level 16 -> Level 17 (Solution)

- `nmap`

```bash
bandit16@bandit:~$ nmap -sC -sV -p 31000-32000 localhost

Starting Nmap 7.80 ( https://nmap.org ) at 2023-10-24 04:14 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Not valid before: 2023-10-23T04:38:45
|_Not valid after:  2023-10-23T04:39:45
31691/tcp open  echo
31790/tcp open  ssl/unknown
| fingerprint-strings: 
|   FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, Kerberos, LDAPSearchReq, LPDString, RTSPRequest, SIPOptions, SSLSessionReq, TLSSessionReq, TerminalServerCookie: 
|_    Wrong! Please enter the correct current password
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Not valid before: 2023-10-23T04:38:44
|_Not valid after:  2023-10-23T04:39:44
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.80%T=SSL%I=7%D=10/24%Time=653744BC%P=x86_64-pc-linux-
SF:gnu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20c
SF:urrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20th
SF:e\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Ple
SF:ase\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest
SF:,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password
SF:\n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\
SF:x20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x2
SF:0correct\x20current\x20password\n")%r(TerminalServerCookie,31,"Wrong!\x
SF:20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(TLSSes
SF:sionReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20p
SF:assword\n")%r(Kerberos,31,"Wrong!\x20Please\x20enter\x20the\x20correct\
SF:x20current\x20password\n")%r(FourOhFourRequest,31,"Wrong!\x20Please\x20
SF:enter\x20the\x20correct\x20current\x20password\n")%r(LPDString,31,"Wron
SF:g!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(LD
SF:APSearchReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\
SF:x20password\n")%r(SIPOptions,31,"Wrong!\x20Please\x20enter\x20the\x20co
SF:rrect\x20current\x20password\n");    
```

Two ports (31518 and 31790) which speak *ssl* are found. The former with *echo protocol* will send back an identical copy of the data it received. But the latter returns an error message instead of the copy of the data it received. So 31790 may be the correct port.

- `echo, openssl, s_client`

```bash
bandit16@bandit:~$ echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -ign_eof -connect localhost:31790
CONNECTED(00000003)
...
...
...
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
```

Save the private key and give the permissions of 600.

- `chmod`

```bash
└─$ chmod 600 sshkey.private  
```

```bash
ssh -i path/to/sshkey.private bandit17@bandit.labs.overthewire.org -p 2220
```
