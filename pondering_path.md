POndering Path
## Challenge Name
The root
### Solve
pwn.college{A2gcmzaTLAQTn_zP5l9nlcYtEPD.dhzN5QDL5gDN1czW}

the root was /pwd so i typed that and got the value

```bash
/pwd
BOOM!!!
Here is your flag:
pwn.college{A2gcmzaTLAQTn_zP5l9nlcYtEPD.dhzN5QDL5gDN1czW}
```

### New Learnings
we type thw root of the file with / follwed by the name of the file

### References 
na


## Challenge Name
program and absolute paths
### Solve
{AS46hH_bjcXPCh-pbuH6jYHHlpu.dVDN1QDL5gDN1czW}

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
position thyself
### Solve
pwn.college{0Iuh__xcUkdPgfmWm53YnxPmLp4.dZDN1QDL5gDN1czW}

i ran the command got thje directory path went to that path then i ran the command

```bash
/cd /proc
hacker@paths~position-thy-self:/proc$ cd /138
bash: cd: /138: No such file or directory
hacker@paths~position-thy-self:/proc$ cd 138
hacker@paths~position-thy-self:/proc/138$ cd fd
hacker@paths~position-thy-self:/proc/138/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{0Iuh__xcUkdPgfmWm53YnxPmLp4.dZDN1QDL5gDN1czW}
```

### New Learnings
leanerd to travel differewnt directories

### References 
na



## Challenge Name
position  elsewhere
### Solve
pwn.college{I3N0TX0-oOO7sLdXtXXKJyNfI3-.ddDN1QDL5gDN1czW}

i ran the command got thje directory path went to that path then i ran the command

```bash
d /proc
hacker@paths~position-elsewhere:/proc$ cd 138
hacker@paths~position-elsewhere:/proc/138$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{I3N0TX0-oOO7sLdXtXXKJyNfI3-.ddDN1QDL5gDN1czW}
```

### New Learnings
leanerd to travel differewnt directories

### References 
na



## Challenge Name
position  yet elsewhere
### Solve
pwn.college{wPw1hhXEM2LaSsOtci4ttcw_j6C.dhDN1QDL5gDN1czW}

i ran the command got thje directory path went to that path then i ran the command

```bash
challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wPw1hhXEM2LaSsOtci4ttcw_j6C.dhDN1QDL5gDN1czW}
```

### New Learnings
leanerd to travel differewnt directories

### References 
na


## Challenge Name
implicit relative path from/
### Solve
pwn.college{YeJl0tcETuW1aSmxsPvjDNZHmmK.dlDN1QDL5gDN1czW}

 i put / went to the directory then put the relative path to the file

```bash
ory
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YeJl0tcETuW1aSmxsPvjDNZHmmK.dlDN1QDL5gDN1czW}
```

### New Learnings
learnt about relative paths
### References 
na


## Challenge Name
explicit relative path from/
### Solve
pwn.college{ggraTwkkPPQLPY4dqrdxAQ6Gfaf.dBTN1QDL5gDN1czW}

 i put / went to the directory then put the ./challenge/run as all are 

```bash
/challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{ggraTwkkPPQLPY4dqrdxAQ6Gfaf.dBTN1QDL5gDN1czW}
```

### New Learnings
learnt about the other ways we can write relative paths 

    /challenge
    /challenge/.
    /challenge/./././././././././
    /./././challenge/././

### References 
na

## Challenge Name
implicit relative path
### Solve
pwn.college{w6RqxVB3sktWrOEH_l5NOvdZesn.dFTN1QDL5gDN1czW}

 i put in the directory of the challenge and then used the ./ flag to go to the rigjt path

```bash
./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{w6RqxVB3sktWrOEH_l5NOvdZesn.dFTN1QDL5gDN1czW}
```

### New Learnings
if we put /challenge/run we might end up executing all te file on that directory for that we make use of ./ to call the file file explicitly

### References 
na


## Challenge Name
home sweet home
### Solve
pwn.college{8_o0RhL0eqSsBypu9oDPyBEFOnn.dNzM4QDL5gDN1czW}


3 charaters so first save the file in the homewith the symbol ~ then use the file name like /f to save the file name in which the file get saved

```bash
/challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{8_o0RhL0eqSsBypu9oDPyBEFOnn.dNzM4QDL5gDN1czW}
```

### New Learnings
we learner how we ca write the name of the file with the home directory. in this we need to first start with the home directory with the ~ symbol and then the file name where we stire the value.

### References 
na















