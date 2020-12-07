- ran `ls` and found a file named **spaces in this filename**
- if filename has spaces, we can `cat` this with single quotes (') or double quotes (")

``` 
bandit2@bandit:~$ ls
spaces in this filename
```
```
bandit2@bandit:~$ cat 'spaces in this filename'
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
OR
```
bandit2@bandit:~$ cat "spaces in this filename"
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
- we got the password for the next level
