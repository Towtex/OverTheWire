- `ssh`

```
$ ssh bandit18@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```

When we try to login, the server responds:

```
Byebye !
Connection to bandit.labs.overthewire.org closed.
```

But we already know that the password for the next level is stored in the **readme** file.

```
$ ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat ~/readme"
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

The password for the next level is **IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x**

`ssh bandit19@bandit.labs.overthewire.org -p 2220`