# Module Name
Pondering PATH

## Challenge Name
the path variable

### Solve
pwn.college{QbhtSI5R5Hp7YRPSGOheAwXRa-U.dZzNwUDL5gDN1czW}

did echo $path which is the variable of path and got the path directory then set the path variable to some othner directory .after that i ran the programme it ran succesfully
so to remove the rm command the thought process was set another directory to the path so that we do not get access to the flag

```bash
echo $PATH
PATH="/home/hacker"
/challene/run
```
### New Lerning
i learnt the usage of path and learnt about changing the directroy of the path. this way we can hide few commands while running it or we can go int some other directory and run the commands thier if that was our path.

### Reference 
na


## Clallenge Name
Setting Path

### Solve
pwn.college{0wJXxcoEnddBGXte0z-mWqdLwNm.dVzNyUDL5gDN1czW}


so as we know here we have to change the path to the said path and run the command via a single command. this is usefull in complex programms.simply we write PATH= the required path and them launch it
 in this first we saw that we just needed to get to that path where the flag was and then run the command for the flag just by putting one word
 
```bash
PATH="/challenge/more_commands"
/challenge/run
```

### New Learning
we set the path to the required path so we can invoke the file directly without needing to type the whole fill name


### Reference
na
 
 
## Challenge Name
Finding Command

### Solve
pwn.college{EGcGxr90F3DM_mG1XQuhgX2h-_k.QX3MTM3EDL5gDN1czW}

so used the which command to get the directory where win is llocated went to that directory and cat the flag file to get the flag. so we need to first use the which win to locate the flag file directory as flag and win are in the same directroy. so then go to that directory and cat the flag file to get the flag
 
```bash
which win
cd /challenge/paths/12287
ls
 cat flag
```
### New Learning
learnt about using the wgich command in the path where ever the file is located in gives the first occurance where the file is located. so it gors thorugh the path variable and the      first occurance of the file in which dircectory it gives that.

### REference
na

## Challenge Name
Adding Commands

### Solve
pwn.college{IU2pZnbZGxooEajPDePiK40Kd1t.dZzNyUDL5gDN1czW}

so we nneded to create the win file. in tht we need to add the shebang statement for the compiler to understand that is a shell file then we need to change the permission comdition of the flag file to make it executable. after that we add the /home/hacker command in the path that exist. after that when we run the command it will fuind the win file and execut the commands inside it and give us the flag

```bash
nano win
#!bin/bash/
chmod +x flag
cat /flag

PATH=".....:/home/hacker"
/challenge/run
```

### New Learning
so in this we learnt about creating a file and adding its directoy in the given path to run the file. like this we can any custom local directory to it.

### Reference
na


##Challenge Name
hijacking Commands

### Solve
pwn.college{kFC81JVphu5sgQDVCiwgd5Y2C26.ddzNyUDL5gDN1czW}

so in this we create a fake nano rm file and in the file we add a shebang and make the file executable and cat the flag. after that we add the path of this rm file before the occueance of other files in the path directory. wgich we can find by the whhich command. so tyhe latest directory becomes the path of the made rm file. after that we run the challenge it will find the og rm file but not delete the flag cause it found my rm first and gave the flag


```bash
nano rm
#!/bin/bash
chmod +x flag
cat /flag

echo $PATH
PATH="/run/challenge/bin:/home/hacker:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
which rm
/challenge/run
```
## New Learning
learnt that the directoty of the file in the variable makes a huge contribution. learnt that the first file that we put in the path variable get executed. this can me done to confuse the terminal to make it do a custom action.

## Reference
na




