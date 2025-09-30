# Model Name

Terminal multiplexing

## Challenge Name
Launching screen
### Solve
pwn.college{w8uHgLV1wtdNtk_vtX8dOGhFZxZ.QX1gjM4EDL5gDN1czW}

typed the word screen and launched the virtual terminal and got the flag
```bash
screen
```
### New Learnings
learnt hoe to open a virtual terminal within a terminal. just lie opening multiple tabs
### References 
na


## Challenge Name
Detaching and Attaching
### Solve
pwn.college{krFjRY93fqcWsZ8Brv2iP1o3INc.QX2gjM4EDL5gDN1czW}

launched the screen command and opened the virtual environment. after that i did cntrl a to detach the virtual terminal ad run the command in the background. the did secreen -r retach the terminal
```bash
screen
cntrl a d
/challenge/run
screen -r
```

### New Learnings
learnt to detach and attach the virtual terminal and run the program in the background
### References 
na


## Challenge Name
finding sessions
### Solve
pwn.college{Ap_IcvMRXHsr7PhrEsN-mtjGHdU.QX3gjM4EDL5gDN1czW}

i did screen ls to have a list of all the screens then found out the one the pid of alll the screen then did screen r till i found the correct screen which gave the flag after each wrong one i did cntrl a
```bash
screen -ls
screen -r session_3250d1d191ea9af3
screen -r session_fe99b74255972c82     
```

### New Learnings
learnt about how to recognise the correct screen among multiple of them 
### References 
na


## Challenge Name
switching windown
### Solve
Here is your flag: pwn.college{AN3LcxDRams3fyEyG_ujkugFYDO.QX4gjM4EDL5gDN1czW}

first we attach tyhe screen and the go to the windo 0 by using contrl a 0 and get the flag
```bash
screen -r
cntrl a 0
```
### New Learnings
swtch between multiple windows

### References 
na

## Challenge Name
Detaching and Attaching(tmux)
### Solve
pwn.college{gyu5PJM_axopbNzyhP0M-SXQtR3.QX5gjM4EDL5gDN1czW}

we nned to first call tmux and do contrl b instrad on cntrl a and get it to detach then ran the command and did tmux a to reatcah the file
```bash
tmux
cntrl b d
/challenge/run
tum a-
```
### New Learnings
learnt abut tmux how we can attach or detach it
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

##Challenge Name
switching window

###Solve

 pwn.college{0EV4KOeLbF1YIXVLnUpFpLey01-.QXwkjM4EDL5gDN1czW}
 
 
 so first we had to attach the tmux that was running to the shell after that the did cntrl b which was the command to switch to some other window in tmux switching so i did that. after doing that got the flag.
 
```bash
tmux a 
cntrl b 0
```

### New Learning 
leanrt switch in tmux terminal. learnt to swutch to diferent numbered terminal in tmux.

###Reference
na
