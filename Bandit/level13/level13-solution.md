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
bandit12@bandit:/tmp/jinx$ xxd -r data.txt > data1
```

- `file`

```
bandit12@bandit:/tmp/jinx$ file data1
data1: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```

- `mv`

```
bandit12@bandit:/tmp/jinx$ mv data1 data2.gz
```

- `gzip`

```
bandit12@bandit:/tmp/jinx$ gzip -d data2.gz
bandit12@bandit:/tmp/jinx$ ls
data2  data.txt
bandit12@bandit:/tmp/jinx$ file data2
data2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data2 data3.bz2
```

- `bzip2`

```
bandit12@bandit:/tmp/jinx$ bzip2 -d data3.bz2 
bandit12@bandit:/tmp/jinx$ ls
data3  data.txt
bandit12@bandit:/tmp/jinx$ file data3
data3: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/jinx$ mv data3 data4.gz
```

```
bandit12@bandit:/tmp/jinx$ gzip -d data4.gz
bandit12@bandit:/tmp/jinx$ ls
data4  data.txt
bandit12@bandit:/tmp/jinx$ file data4
data4: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data4 data5.tar.gz
```

- `tar`

```
bandit12@bandit:/tmp/jinx$ tar -xvf data5.tar.gz 
data5.bin
bandit12@bandit:/tmp/jinx$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data5.bin data6.tar.gz
```

```
bandit12@bandit:/tmp/jinx$ tar -xvf data6.tar.gz 
data6.bin
bandit12@bandit:/tmp/jinx$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data6.bin data7.bz2

```

```
bandit12@bandit:/tmp/jinx$ bzip2 -d data7.bz2 
bandit12@bandit:/tmp/jinx$ ls
data7  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data7
data7: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data7 data8.tar.gz
```

```
bandit12@bandit:/tmp/jinx$ tar -xvf data8.tar.gz 
data8.bin
bandit12@bandit:/tmp/jinx$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/jinx$ mv data8.bin data9.gz
```

```
bandit12@bandit:/tmp/jinx$ gzip -d data9.gz 
bandit12@bandit:/tmp/jinx$ ls
data9  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data9
data9: ASCII text

```

- `cat`

```
bandit12@bandit:/tmp/jinx$ cat data9
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

```
ssh bandit13@bandit.labs.overthewire.org -p 2220
```
