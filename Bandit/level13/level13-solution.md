- `mkdir`

```
bandit12@bandit:~$ mkdir /tmp/jinx
```

- `ls`

```
bandit12@bandit:~$ ls
data.txt
```

- `cp, cd`

```
bandit12@bandit:~$ cp data.txt /tmp/jinx
bandit12@bandit:~$ cd /tmp/jinx
bandit12@bandit:/tmp/jinx$
```

- `xxd`

```
bandit12@bandit:/tmp/jinx$ xxd data.txt 
00000000: 3030 3030 3030 3030 3a20 3166 3862 2030  00000000: 1f8b 0
00000010: 3830 3820 3036 3530 2062 3435 6520 3032  808 0650 b45e 02
00000020: 3033 2036 3436 3120 3734 3631 2033 3232  03 6461 7461 322
00000030: 6520 202e 2e2e 2e2e 502e 5e2e 2e64 6174  e  .....P.^..dat
00000040: 6132 2e0a 3030 3030 3030 3130 3a20 3632  a2..00000010: 62
...
```

> I have to convert hexdump to binary

```
bandit12@bandit:/tmp/jinx$ xxd -r data.txt > data
```

- `file`

```
bandit12@bandit:/tmp/jinx$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```

- `mv`

```
bandit12@bandit:/tmp/jinx$ mv data data.gz
```

- `gzip`

```
bandit12@bandit:/tmp/jinx$ gzip -d data.gz
bandit12@bandit:/tmp/jinx$ ls
data  data.txt
bandit12@bandit:/tmp/jinx$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data data.bz2
```

- `bzip2`

```
bandit12@bandit:/tmp/jinx$ bzip2 -d data.bz2 
bandit12@bandit:/tmp/jinx$ ls
data  data.txt
bandit12@bandit:/tmp/jinx$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/jinx$ mv data data.gz
```

```
bandit12@bandit:/tmp/jinx$ gzip -d data.gz
bandit12@bandit:/tmp/jinx$ ls
data  data.txt
bandit12@bandit:/tmp/jinx$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data data.tar.gz
```

- `tar`

```
bandit12@bandit:/tmp/jinx$ tar -xvf data.tar.gz 
data5.bin
bandit12@bandit:/tmp/jinx$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data5.bin data.tar.gz
```

```
bandit12@bandit:/tmp/jinx$ tar -xvf data.tar.gz 
data6.bin
bandit12@bandit:/tmp/jinx$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data6.bin data.bz2

```

```
bandit12@bandit:/tmp/jinx$ bzip2 -d data.bz2 
bandit12@bandit:/tmp/jinx$ ls
data  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data data.tar.gz
```

```
bandit12@bandit:/tmp/jinx$ tar -xvf data.tar.gz 
data8.bin
bandit12@bandit:/tmp/jinx$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/jinx$ mv data8.bin data.gz
```

```
bandit12@bandit:/tmp/jinx$ gzip -d data.gz 
bandit12@bandit:/tmp/jinx$ ls
data  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data
data: ASCII text

```

- `cat`

```
bandit12@bandit:/tmp/jinx$ cat data
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

```
ssh bandit13@bandit.labs.overthewire.org -p 2220
```