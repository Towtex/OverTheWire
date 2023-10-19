# Level 2 -> Level 3 (Solution)

- I ran `ls` and found a file named **spaces in this filename**.
- If filename has spaces, we can `cat` this with single quotes (') or double quotes (").

```bash
bandit2@bandit:~$ ls
spaces in this filename
```

```bash
bandit2@bandit:~$ cat 'spaces in this filename'
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

OR

```bash
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

OR

```bash
bandit2@bandit:~$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

Password: `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```
