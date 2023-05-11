- `find`
```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null | grep "bandit7"
/var/lib/dpkg/info/bandit7.password
```
`find`: This is the command we are running.

`/`: This specifies the starting directory for the search. In this case, we are searching the entire file system.

`-type f`: This option tells find to only look for files (not directories or other types of files).

`-user bandit7`: This option tells find to only look for files owned by the user bandit7.

`-group bandit6`: This option tells find to only look for files owned by the group bandit6.

`-size 33c`: This option tells find to only look for files that are exactly 33 bytes in size. The c indicates that the size is specified in bytes.

`2>/dev/null`: This part of the command redirects any error messages sent to standard error (file descriptor 2) to the null device (/dev/null). This effectively discards any error messages and prevents them from being displayed on the terminal.

So all together, this command searches the entire file system for files owned by user bandit7 and group bandit6, that are exactly 33 bytes in size, and prints the full path of any matching files to the terminal. Any error messages generated during the search are discarded and not displayed.

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
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

Password: `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`

```
ssh bandit7@bandit.labs.overthewire.org -p 2220
```
