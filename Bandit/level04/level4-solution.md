# Level 3 -> Level 4 (Solution)

- I ran `ls` and found a directory named **inhere**.

```bash
bandit3@bandit:~$ ls
inhere
```

- I checked this directory with `ls`.

```bash
bandit3@bandit:~$ ls inhere
```

However, nothing was displayed.

- To get a more detailed listing, I used `ls -la`

```bash
bandit3@bandit:~$ ls -la inhere
total 12
drwxr-xr-x 2 root    root    4096 Oct 16  2018 .
drwxr-xr-x 3 root    root    4096 Oct 16  2018 ..
-rw-r----- 1 bandit4 bandit3   33 Oct 16  2018 .hidden
```

- This revealed a file named **.hidden**.

```bash
bandit3@bandit:~$ cat inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

Password: `2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```
