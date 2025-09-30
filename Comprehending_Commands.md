# Module Name

Comprehending Commands

## Challenge Name
cat:not the pet,but the command!
### Solve
pwn.college{UCJBXi39m4csK08db3Hvt9Y32Al.dFzN1QDL5gDN1czW}
 the flag was found by cat flag
```bash
/pwd
cat flag
```

### New Learnings
learnt to read file using cat 

### References 
na


## Challenge Name
program and absolute paths
### Solve
pwn.college{AS46hH_bjcXPCh-pbuH6jYHHlpu.dVDN1QDL5gDN1czW}

the flag was in the absolute path so first i started with typing the / commands and the proceeding forward. the file was in /challenge/run

```bash
/challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{AS46hH_bjcXPCh-pbuH6jYHHlpu.dVDN1QDL5gDN1czW}
```

### New Learnings
we learned to write the absolute path of the files

### References 
na





## Challenge Name
catting absolute path
### Solve
pwn.college{gHx8aLVdjWvmOki675_CI3ALQE8.dlTM5QDL5gDN1czW}
went to the directory of the absolute path and dis cat flag

```bash
cd /
cat flag
```

### New Learnings
learnt to cat flag from absolute directory

### References 
na



## Challenge Name
more catting practice
pwn.college{I2-R1i8k4sEF_iCjqo1YTdXh_5B.dBjM5QDL5gDN1czW}

catted the flag withour changing directory
```bash
cat /lib/file/flag
```

### New Learnings
learnt to cat file without changing directory

### References 
na



## Challenge Name
grepping for a needle in a haystack
### Solve
pwn.college{0H1IKFDDZH4mg1K221Mkx0FPftM.ddTM4QDL5gDN1czW}

we need to find the file with the name of pwn.college by using grep 

```bash
grep pwn.college/challenge/data.txt
```

### New Learnings
learnt to extract the word from a huge file useing grep 

### References 
na


## Challenge Name
comparing files
### Solve
 pwn.college{AF2VKPHrgCTIfsz_YwF6ST_ggNS.QXzAzM4EDL5gDN1czW}
 
went to the challenger directory and then did diff between the two file given

```bash
cd /challenge
diff decoys_only.txt decoys_and_real.txt
```

### New Learnings
we learn to find the difference between two files 
### References 
na


## Challenge Name
listing files
### Solve
pwn.college{IYMwOiphcZKElpFs32wdarjpmm3.dhjM4QDL5gDN1czW}

went to the directory listed the file found the new name and ran that with /challenge to find the flag

```bash
ls
/challenge/12224-renamed-run-2155
```

### New Learnings
leant about listing te files in a directory

### References 
na

## Challenge Name
touching files
### Solve
pwn.college{w1VsDAWvagptkwT0ZQnCl0N1Dz7.dBzM4QDL5gDN1czW}

touch and created the two files then ran the command

```bash
touch /tmp/pwn
touch /tmp/college
```

### New Learnings
how to create new files using tiuch function

### References 
na


## Challenge Name
removing files
### Solve
pwn.college{YXDryMAeCdRk7GHCNdn24-SXfMV.dZTOwUDL5gDN1czW}

used the rm command to delte the file the root directory then put the command to check
```bash
rm delete_me
/challenge/check
```

### New Learnings
leant how to remove a file from the directory

### References 
na


## Challenge Name
moving files
### Solve
pwn.college{wvwY6ozrkSN3RYU8d9HvVow0wQd.QX5ETM3EDL5gDN1czW}
 we had to move the file so i first went to the / directory from thier i just wrote mv to move the file
```bash
cd /
mv flag tmp/hack-the-planet
```

### New Learnings
we learnt to the move one file from one directort to another or even move the content from one file to another

### References 
na


## Challenge Name
hidden files
### Solve
219012309611988 

went to the directory and then dis ls -a and found all the flag thier
```bash
cd /
ls -a
```

### New Learnings
learnt to list the hidden flag of a directory

### References 
na


## Challenge Name
an epic filesystem Quest
### Solve
It is: pwn.college{EgEjaBFu8ybvTGOrqAlq0sEgX3j.dljM4QDL5gDN1czW}

follwed the indtruction in ach setp read idf the clue is trapped hidden or delayed and then move according to that
```bash
cd /
ls -a
cat EVIDENCE
cd /usr/lib/jvm/java-11-openjdk-amd64/legal/java.sql
ls -a
cat BLUEPRINT
ls /usr/local/lib/python3.8/dist-packages/jupyter_server/prometheus
SPOILER-TRAPPED  __init__.py  __pycache__  log_functions.py  metrics.py
cat /usr/local/lib/python3.8/dist-packages/jupyter_server/prometheus/SPOILER-TRAPPED
cd /usr/share/racket/pkgs/compatibility-lib/racket/compiled
ls -a
cat .GIST
cd /opt/linux/linux-5.4/tools/power/x86
ls -a
cat .ALERT
cd /usr/local/lib/python3.8/dist-packages/werkzeug/middleware/__pycache__
ls 
cat NOTE
cd /usr/lib/jvm/java-17-openjdk-amd64/legal/jdk.random
cat NUGGET
ls /usr/share/racket/pkgs/planet-doc/planet/compiled
cat /usr/share/racket/pkgs/planet-doc/planet/compiled/MEMO-TRAPPED
cd /opt/linux/linux-5.4/include/config/have/arch/within
ls
cat SECRET
```

### New Learnings
learnt to use various commands to reach the destination used ls and cat and cd 

### References 
na


## Challenge Name
making directories
### Solve
pwn.college{sFVP-VPNeiaZt9KwxThvTftXcZ4.dFzM4QDL5gDN1czW}

used mkdir to make the directory of the files
then went to that directory and used touch to creat the file
```bash
mkdir /tmp/pwn
cd /tmp/pwn
touch collge
/challnege/run
```

### New Learnings
how to create a new directory

### References 
na


## Challenge Name
finding files
### Solve
pwn.college{8_o0RhL0eqSsBypu9oDPyBEFOnn.dNzM4QDL5gDN1czW}


used the find inte main commnd got many file did cat in one of them and got the flag
```bash
find /flag/home/hacker
cat f
```

### New Learnings
learnt to find a particualr name from the list of files

### References 
na


## Challenge Name
linking files
### Solve
pwn.college{ktyUCFqPJ7U24V3akoLZe_sDPvJ.dlTM1UDL5gDN1czW}

first removed the file present then created the symlink then cat with the given command
```bash
rm /home/hacker/not-the-flag
ln -s/flag/home/hacker/not-the-flag
/challenge/catflag
```

### New Learnings
learnt to create a symlink. learnt the difference between a hardlink and a symlink

### References 
na


