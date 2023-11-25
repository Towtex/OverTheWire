# Bandit Level 20 -> Level 21 (Solution)

- `ls`

```bash
bandit20@bandit:~$ ls
suconnect
```

```bash
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
```

First, we will set up a simple TCP server which listens to port **1337** and let the process running in the background.

- `echo, nc`

```bash
bandit20@bandit:~$ echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -nvlp localhost -p 1337 &
[1] 20971

bandit20@bandit:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
bandit20  3171  0.0  0.1  21148  4924 pts/18   Ss+  04:02   0:00 -bash
bandit20 12852  0.0  0.1  21148  4956 pts/15   Ss+  04:18   0:00 -bash
bandit20 18369  0.0  0.1  21148  5048 pts/41   Ss   04:25   0:00 -bash
bandit20 20971  0.0  0.0   6300  1696 pts/41   S    04:30   0:00 nc -nvlp localhost -p 1337
bandit20 21005  0.0  0.0  19188  2484 pts/41   R+   04:30   0:00 ps aux
```

Now we will execute the setuid binary to connect the localhost by port 1337.

```
bandit20@bandit:~$ ./suconnect 1337
Connection received on 127.0.0.1 48474
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
[1]+  Done                    echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -nvlp localhost -p 1337
```

- password `NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`

`ssh bandit21@bandit.labs.overthewire.org -p 2220`

