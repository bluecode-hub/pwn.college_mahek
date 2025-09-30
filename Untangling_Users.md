
# Module Name
UNtangling_Users

## Challenge Name
Becoming root with su
### Solve
pwn.college{M98qzizJk7fPoZWCblRTX1yMUSe.dVTN0UDL5gDN1czW}

fierst ran the su command and got the prompt to add the password after adding the password i ran command and then went to the root file after that i ls to find all the underlaying files and then cat the file called not the flag to find the flag 
```bash
su
hack-the-planet
ls
cat not-the-flag

```

### New Learnings
learnt how to go to the root directory and then learnt how to go to the root directory and manipulate as the root administrator
### References 
na


## Challenge Name
other users with su
### Solve
pwn.college{sLd7A4yiEjjd6RCTmVgX3um6Zrm.dZTN0UDL5gDN1czW}

so wrote the argument of the user name given with the su command and then typed the password and ran the command and got the flag. 
```bash
su zardus
dont-hack-me
/challenge/run
```

### New Learnings
learnt about how to go to some other user not just the root
### References 
na



## Challenge Name
Cracking passwords
### Solve
pwn.college{U_TpDbDptly1Vrx4OGwyWFnamiI.ddTN0UDL5gDN1czW}

we have to crack the password using the encrypted one dimensional hash. for that we can use john challenge/shadow-leak and the  we show it to show how many password were decruted with the hash 
```bash
john /challenge/shadow-leak
john --show/challenge/shadow-leak
sudo zardus
aardvark
/challenge/run
```

### New Learnings
learnt to crack one hashed password and use that for the su command.

### References 
na


## Challenge Name
Using sudo
### Solve
pwn.college{onPLlA16wy5zsba6q-BiTmZiA-m.dhTN0UDL5gDN1czW}

so first i ls all the file and then check which file had permission denied out of all the files using cat after that i did sudo cat that file and got the flag
```bash
ls
sudo cat not-the-flag

```
### New Learnings
sudo does not launch a new shell to take to the root it autmotically sets you to the root

### References 
na

