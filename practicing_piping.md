# Module Name

Practicing Piping

## Challenge Name
Redirecting output
### Solve
pwn.college{4u34MQoXiMxhMKxardOeVO--jYj.dRjN1QDL5gDN1czW}
 
 so i echoed the pwn command and then write it into the college file then catted the college file
```bash
echo PWN>COLLEGE

```

### New Learnings
learnt to write the output of one file into another file then read the content

### References 
na

## Challenge Name
Redirecting more output
### Solve
pwn.college{4PGa1chvCuL8glPHXXz3wrVBAoh.dVjN1QDL5gDN1czW}

 wrote /challenge/run echo> myflag to put the output in the myflag file and then cat it to get to know the flag
```bash
/challenge/run echo>myflag

```

### New Learnings
leant to redirect the output to the myflag file and then cat the file to read get the flag
### References 
na


## Challenge Name
Appending output
### Solve
pwn.college{Iy4h2mUXJptOAFSU6hwaaFgh7D_.ddDM5QDL5gDN1czW}

 
 so i echoed the pwn command and then write it into the college file then catted the college file
```bash
/challenge/run >>/home/hacker/the-flag
echo stdout>>the-flag
cat the-flag


```

### New Learnings
learnt to write the output of one file into another file then read the content

### References 
na


## Challenge Name
Redirecting errors
### Solve
 pwn.college{UvfjS3DpMqXaf61cWY3H9Y2p6kP.ddjN1QDL5gDN1czW}

so the question said to redirect the error into a file for which we use 2> andit said to redirect the output into another file for which we used > and then i read that file using cat
```bash
/challenge/run >myflag 2>instructions
cat myflag

```

### New Learnings
learnt to write the error into a separate file and then the output into a separate file and then read the flag

### References 
na

## Challenge Name
Redirecting input
### Solve
pwn.college{MTgJcLr7URvCHU2rzLV-9Sj8NNr.dBzN1QDL5gDN1czW}

 first directed the college into the pwn file using the echo cap and then with 
 redirected the input to read that
```bash
/challenge/run >PWN
echo COLLEGE>PWN
/challenge/run <PWN

```

### New Learnings
leanr to redirect the input we wrote the word in the file pwn and the gave it to the input

### References 
na


## Challenge Name
Grepping stored results
### Solve
pwn.college{ErwGgZXUOv48o7lsE1HxbXd6Iid.dhTM4QDL5gDN1czW}

so first i copid the components into the /tmp/data.txt file and then grep the pwn.college tag and get the flag
```bash
/challenge/run > /tmp/data.txt
cd /
cd tmp
grep flag data.txt
grep "pwn.college{" data.txt
```

### New Learnings
learnt to combine two different functions together which includes redirecting the output and then we can grep with pwn college and get the flag

### References 
na


## Challenge Name
greping live output
### Solve
pwn.college{MApEyoeNHilf3C_eFXM32gzS2lB.dlTM4QDL5gDN1czW}

so we can use the piping to directly search the standard output of the output we can  grep through the output directly with the piping command
```bash
/challenge/run|grep "pwn.college{"

```
### New Learnings
we can use the piping to directly store the output of the file and grep it with the | symbol

### References 
na


## Challenge Name
grepping errors
### Solve
pwn.college{8Im85AsPlRGcvq4TuMuwjPXGm_l.dVDM5QDL5gDN1czW}
so here i redirect the error to the output since directly its not allwoed for error so we use 2>& 1 and then we grep the flag with the pwn.college name.
```bash
/challenge/run 2>&1|grep "pwn.college{"

```
### New Learnings
we can lean that from here we get that howto read error with piping in shell its not possible for dirrect error reading so we convert it to the output and then read it.

### References 
na

## Challenge Name
filtering with grep -v
### Solve
pwn.college{Up_Xjqu1YNR61V7J3ebqghNHkVL.QX4ETM3EDL5gDN1czW}

in this we saw that -v will give all the files that does not have the decoy tag so we need to use piping to run the /challenge/run and then store that with | and grep -v "decoy".
```bash
/challenge/run|grep -v "DECOY"
```
### New Learnings
learnt the -v command that gives all the file that dors not have decoy word. and we get the flag
### References 
na


## Challenge Name
Duplicating piped dat with tee
### Solve
pwn.college{4BEEih6DhKV3iLXVimxhHQ5uvOl.dFjM5QDL5gDN1czW}

first i stored the error in the secret file and got the argumengt then ran tat argument and stoped the value in the output file/ first i was overrinding the value but lter got how to do it.
```bash
echo PWN>COLLEGE

```

### New Learnings
learnt to write the output of one file into another file then read the content

### References 
na

## Challenge Name
process substitution for input
### Solve
 pwn.college{ck2MDKmjHDSqykYMV9r2aLriYzE.QX2AzM4EDL5gDN1czW}

sw we had to use the diff function but for processing substitution so wrote the diff command for the two files 
```bash
diff <(/challenge/print_decoys_and_flag) <(/challenge/print_decoys)
```
### New Learnings
learnt process substitution and its uses learnt that ceates a tempory location for the file
### References 
na


## Challenge Name
writing to multiple programs
### Solve
pwn.college{04AjFTrZ6B4_Do0_yXpJ8YbDfEj.dBDO0UDL5gDN1czW}

 so i echoed the pwn command and then write it into the college file then catted the college file
```bash
echo PWN>COLLEGE

```

### New Learnings
learnt to write the output of one file into another file then read the content

### References 
na


## Challenge Name
split piping stderr and stdout
### Solve
pwn.college{oT_nAuphHQKuAYKz3Sxk-c6Ebjt.dFDNwYDL5gDN1czW}



 so in this as we can see that we nend to seaparate the output into the redirected error and the output file. we use the process substitution to directly separate the files
```bash
/challenge/hack >>(/challenge/planet)2>>(/challenge/the)

```

### New Learnings
learnt the use of redirecting the content into two files and then using them
### References 
na


## Challenge Name
Named pipes
### Solve
pwn.college{oXO-upWHhuBOJMhQ-_frwavYujP.QXzMzM4EDL5gDN1czW}

made a fifo file and then ran that fifo file and also catted the file in another terminal so that we can read and write the file. 
```bash
cd /
cd tmp
mkfifo flag_fifo
/challenge/run >/tmp/flag_fifo
cat falg_fifo

```

### New Learnings
leanr about fifo files. learnt that they have the ability to read and write only after they are opened and catted. once the files are catted we can reading and writeing in the fifo file.
### References 
na




