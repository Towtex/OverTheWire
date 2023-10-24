# Level 18 -> Level 19 (Solution)

- `ssh`

```bash
$ ssh bandit18@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

When we try to login, the server responds:

```bash
Byebye !
Connection to bandit.labs.overthewire.org closed.
```

But we already know that the password for the next level is stored in the **readme** file.

```bash
└─$ ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat ~/readme"
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

The password for the next level is **awhqfNnAbc1naukrpqDYcF95h7HoMTrC**

`ssh bandit19@bandit.labs.overthewire.org -p 2220`
