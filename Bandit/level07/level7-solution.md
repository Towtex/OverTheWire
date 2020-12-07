- `find`
```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null | grep "bandit7"
/var/lib/dpkg/info/bandit7.password
```

>**_Note_**:
>
>**/dev/null** is treated as black hole in Linux/Unix, so you can put anything into this but you will not be able to get it back from **/dev/null**.
>
>Further, **2>** means that you are redirecting (i.e. >) the **stderr** (i.e. 2) into the black hole (i.e. /dev/null)
>
>Other things that we must know
>```
>0 means stdin 
>1 means stdout(useful output)
>2 means stderr(error message output)
>```
>ref: https://askubuntu.com/questions/350208/what-does-2-dev-null-mean

- `cat`
```
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

```
ssh bandit7@bandit.labs.overthewire.org -p 2220
```