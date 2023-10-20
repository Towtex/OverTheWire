# Level 12 -> Level 13 (Solution)

- `mkdir`

```bash
bandit12@bandit:~$ mkdir /tmp/jinx
```

- `ls`

```bash
bandit12@bandit:~$ ls
data.txt
```

- `cp, cd`

```bash
bandit12@bandit:~$ cp data.txt /tmp/jinx
bandit12@bandit:~$ cd /tmp/jinx
bandit12@bandit:/tmp/jinx$
```

- `file`

```bash
bandit12@bandit:/tmp/jinx$ file data.txt
data.txt: ASCII text
```

- `cat`

```bash
bandit12@bandit:/tmp/jinx$ cat data.txt
00000000: 1f8b 0808 6855 1e65 0203 6461 7461 322e  ....hU.e..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 5948 1b32 0200 0019 ffff faee cff7  &SYH.2..........
00000030: f6ff e4f7 bfbc ffff bff7 ffb9 39ff 7ffb  ............9...
```

I have to convert hexdump to binary

- `xxd`

```bash
bandit12@bandit:/tmp/jinx$ xxd -r data.txt > data1
```

- `file`

```bash
bandit12@bandit:/tmp/jinx$ file data1
data1: gzip compressed data, was "data2.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 573
```

- `mv`

```bash
bandit12@bandit:/tmp/jinx$ mv data1 data2.gz
```

- `gzip`

```bash
bandit12@bandit:/tmp/jinx$ gzip -d data2.gz
bandit12@bandit:/tmp/jinx$ ls
data2  data.txt
bandit12@bandit:/tmp/jinx$ file data2
data2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data2 data3.bz2
```

- `bzip2`

```bash
bandit12@bandit:/tmp/jinx$ bzip2 -d data3.bz2 
bandit12@bandit:/tmp/jinx$ ls
data3  data.txt
bandit12@bandit:/tmp/jinx$ file data3
data3: gzip compressed data, was "data4.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/jinx$ mv data3 data4.gz
```

```bash
bandit12@bandit:/tmp/jinx$ gzip -d data4.gz
bandit12@bandit:/tmp/jinx$ ls
data4  data.txt
bandit12@bandit:/tmp/jinx$ file data4
data4: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data4 data5.tar.gz
```

- `tar`

```bash
bandit12@bandit:/tmp/jinx$ tar -xvf data5.tar.gz 
data5.bin
bandit12@bandit:/tmp/jinx$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data5.bin data6.tar.gz
```

```bash
bandit12@bandit:/tmp/jinx$ tar -xvf data6.tar.gz 
data6.bin
bandit12@bandit:/tmp/jinx$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/jinx$ mv data6.bin data7.bz2

```

```bash
bandit12@bandit:/tmp/jinx$ bzip2 -d data7.bz2 
bandit12@bandit:/tmp/jinx$ ls
data7  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data7
data7: POSIX tar archive (GNU)
bandit12@bandit:/tmp/jinx$ mv data7 data8.tar.gz
```

```bash
bandit12@bandit:/tmp/jinx$ tar -xvf data8.tar.gz 
data8.bin
bandit12@bandit:/tmp/jinx$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/jinx$ mv data8.bin data9.gz
```

```bash
bandit12@bandit:/tmp/jinx$ gzip -d data9.gz 
bandit12@bandit:/tmp/jinx$ ls
data9  data.tar.gz  data.txt
bandit12@bandit:/tmp/jinx$ file data9
data9: ASCII text

```

- `cat`

```bash
bandit12@bandit:/tmp/jinx$ cat data9
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```
