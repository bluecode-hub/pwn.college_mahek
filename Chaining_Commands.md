# Module Name

Chaining Commands

## Challenge Name
chaining with semicolon
### Solve
pwn.college{0enebGSUbe8BCCzDCL6jNDf9A3O.dVTN4QDL5gDN1czW}

we needed to ren two or more commands so instead of typing them in separate lines we can chain them with semicolon sign. 
```bash
/challenge/pwn;/challenge/college
```
### New Learnings
learnt how to chain multiple commands using ; 
### References 
na



## Challenge Name
BUilding on success
### Solve
pwn.college{opuAj0jihqABwIs2xcIGcKT2_FX.QXyQzM4EDL5gDN1czW}

so we need to build the succes of our program on that of the other so we do && to have such that the success of the first file depends on the sucess of the second file
```bash
/challenge/first-success && /challenge/second

```

### New Learnings
learnt to write commands with and suc the the succes of one command will initiate the other command
### References 
na



## Challenge Name
handling failures
### Solve
pwn.college{0it1SMP6GowW3IwQ8e1-mvqFMVR.QXzQzM4EDL5gDN1czW}

we see that the second command runs only if the first command falis that is i used || between the two ommand so that is the first one failed the second one will get executed
```bash
/challenge/first-failure||/challenge/second

```

### New Learnings
learnt to handle failure of commands using || we use the second statement as a fallback

### References 
na


## Challenge Name
Your first shell
### Solve
pwn.college{gCaAx96TOykQ9QYMI8FI5l9sfYZ.dFzN4QDL5gDN1czW}

we nano the file and write the command and then press cntrl x and then y and then enter then bash x.sh
```bash
nano x.sh
.challenge/pwn && /challenge/college

```
### New Learnings
leanr shell scripting. learnt how to use nano and write into the file and then using bash to run the file

### References 
na

## Challenge Name
Redirecting SCript OUtput
### Solve
pwn.college{wC1o-8YePvroZmsWOrMrLAOWUay.dhTM5QDL5gDN1czW}

we can redirect the output of various command so we can do that using the scrip file. so first i made the x.sh file by nano it and then write the command by | piping it
```bash
nano x.sh
bash x.sh|/challenge/solve

```
### New Learnings
we learnt how to send multiple commands  output to another command
### References 
na

## Challenge Name
Executable Shell SCripts
### Solve
pwn.college{QPMHScbg8C2nFv2TIEV0cXuHDCa.dRzNyUDL5gDN1czW}

i first nanoed the x.sh file and write the command in it. then checked the permission of the file. then we chmod and chanhe the permission of the file to make it executable. and then we run ./x.sh and bash the sh shell without usinf the command bash
```bash
nano x.sh
ls -l x.sh
chmod ugo+x x.sh
ls -l x.sh
x.sh
./x.sh
```
### New Learnings
learnt how to run the sh shell withiut using the bash commandS

### References 
na

## Challenge Name
Uderstanding Shebangs
### Solve
pwn.college{QB0W_XMW-FMggtEmKRpgvvXh5kb.QX5MzM4EDL5gDN1czW}

she bangs are command that help the terminal decide what type of file it is based on the first few bytes so we nano the script.sh file and write the shebang command and then we change the permission of the file and then run the command and got the flag
```bash
nano solve.sh
/challenge/run
chmod ugo+x solve.sh
/challenge/run
```
### New Learnings
learnt about she bangs learmt that they make the terminal understand what typ of file we are running. 

### References 
na


## Challenge Name
Scripting with arguments
### Solve
pwn.college{cV_7VXjX54S5eiKqjYZwV8NJ_Ks.QX1MzM4EDL5gDN1czW}

we nano the file and write the arguments in the reversed order and then we echo the command and we get the flag
```bash
nano solve.sh
!#bin/bash
echo "$2 $1"
/challenge/run

```
### New Learnings
learnt about paaing arguments to the script and learnt to read the arguments using the variables.
### References 
na


## Challenge Name
Scripting with conditionals
### Solve
pwn.college{0c1QxZ0shU_a-Ovh0lxOWnL4jcg.QX2MzM4EDL5gDN1czW}

learnt about the if statement to apply on the scripting. wrote the syntax of the  for the implementation of the condtional argument. 
```bash
nano solve.sh
  GNU nano 8.4                        solve.sh                                  
#!bin/bash
if [ "$1" == "pwn" ]
then
   echo "college"
fi
/challenge/run
```
### New Learnings
learnt shell scritpting. and application of the if argument.

### References 
na


## Challenge Name
SCripting with DEfault Cases
### Solve
pwn.college{UflLMvkTdkV_fWFdq6MtfAdky3R.QX3MzM4EDL5gDN1czW}

in this we write the script file the if else argument statementand we run that
```bash
#!bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
else
   echo "nope"
fi

```
### New Learnings
learnt to include else statement in script file

### References 
na


## Challenge Name
Scripting with multiplt conditions`
### Solve
pwn.college{Un10-Zw6j5d1BlyYRDuOYiimMGc.QX4MzM4EDL5gDN1czW}

opened the sh file then wrote the various script text for else if command .
```bash
#!/bin/bash
if [ "$1" == "hack" ]
then
   echo "the planet"
elif [ "$1" == "pwn" ]
then
   echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
   echo "unknown"
fi


```
### New Learnings
learnt how to write else if command in the script shell file

### References 
na


## Challenge Name
Reading Shell scripts
### Solve
pwn.college{4LGMYhqKV8LJSvAwFuug1G1KRsG.QXyADO4EDL5gDN1czW}

we read the file using cat and find out the argument then run the command and pass the password to get the flag
```bash
cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
	echo "CORRECT! Your flag:"
	cat /flag
else
	echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET

```
### New Learnings
learnt about reading the script files
### References 
na


