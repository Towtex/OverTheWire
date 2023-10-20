# Level 9 -> Level 10 (Solution)

- `strings, grep`

```bash
bandit9@bandit:~$ strings data.txt | grep "==="
========== the*2i"4
========== password
Z)========== is
&========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

Password: `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```
