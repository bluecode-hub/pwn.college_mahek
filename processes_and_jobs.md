# Module Name
processes and jobs

## Challenge Name
Listing process
### Solve
pwn.college{ES8sjaNwqu_CUt1V4mvQyandxFo.dhzM4QDL5gDN1czW}
 
 the challenge said to make use of the process thats were running so we did ps efww so the the terminal does not truncated.
 after that  we find the name of the file and launch it agian by writing the name of the file
```bash
ps -efww
/challenge/2520-run-28089

```

### New Learnings
learnt to show all the running processes of the program using two syntax ef or aux with the keyword ps.standard and bsd syntax.


### References 
na



## Challenge Name
Killing processes
### Solve
pwn.college{whK-FrYtd0VPJCPX7ltNryKiZuH.dJDN4QDL5gDN1czW}

task was to find the dont run process and kill it. so i used the ps method and then ef combined with piping to gep the process with the dont_run name
so that we could find that. then used the number given the pid used that and killed the process.
```bash
 ps  -ef|grep dont_run
/challenge/run


```

### New Learnings
learnt to kill processes and larnt about pid and then kill processes
### References 
na



## Challenge Name
interrrupting processes
### Solve
pwn.college{Yg5_5XFO84f7mMOFaFrs_UjzAAj.dNDN4QDL5gDN1czW}

goal of the challenge eas to intrupt the process that was running. we can do this by using the cntrl c button.
```bash
/challenge/run
^c
```

### New Learnings
how to interrupt a process by using cntrl c.

### References 
na


## Challenge Name
killing misbehaving processes
### Solve
pwn.college{Ej_R286xJxQ_3UP9surYDF0AiH7.QX0MzM4EDL5gDN1czW}

so did ps efww and got all the processes then so the decoy one and killed it then ran the commant and opened another terminal and ran the cat command on the fifo file that gave the flag that we needed but a lot of buffer or decoy flag came so took the last one that came cause the queue had to empty.
```bash
ps -efww
cd /root
kill 142
/challenge/run
cat flag_fifo

```
### New Learnings
so learnt hoe to deal with the missbehaving processes

### References 
na

## Challenge Name
Suspending Processes
### Solve
pwn.college{MuAsYJFDMLyKbbs_iv9QuxtmObw.dVDN4QDL5gDN1czW}

on using the cntrl z and then on relaunching it it reruns the program. the process is ushed in the background with cntrl z and when i relaunched it it formed a copy in the process list.
```bash
/challenge/run
/challenge/run
```

### New Learnings
learnt how to use cntrl z to send a process to the background
### References 
na


## Challenge Name
Resuming Processes
### Solve
pwn.college{gGKl2Yorh1p4Yjxrdic0MoOTR5u.dZDN4QDL5gDN1czW}

here er are leaning how to resume suspended commands so first we are cntrl zing to stop the programme and then we are fg to resume the process and bring it forward
```bash
/challenge/run
cntrl z
fg
```

### New Learnings
leanr how to resume suspended processes using fg command. this is resuming the process in the foreground.

### References 
na


## Challenge Name
Backgrounding Processes
### Solve
pwn.college{s6HFRzBkAJPMiSVsndQ4DZ4678t.ddDN4QDL5gDN1czW}

ran the command /challenge/run and let the process suspend and wrotr bg to run the process in the background and then call the command again to get the flag.
```bash
/challenge/run
^z
bg
/challenge/run
```
### New Learnings
it helps the process be suspended and run in the bacground will allowing some other command to work in the foreground.
### References 
na


## Challenge Name
Forgrounding Processes
### Solve

pwn.college{0EWs1uw_C7bSmVtI3Qm_duCli4X.dhDN4QDL5gDN1czW}

we need to suspend a peocess and the n we sent t to backgrounnd and then we we wote 
```bash
/challnege/run
bg
fg

```
### New Learnings
larnt to suspend a process to the background and then foreground it
### References 
na


## Challenge Name
Starting Backgroound Processes
### Solve
pwn.college{EzqUSADPDxu-V_J-2ZqyROCYM8w.dlDN4QDL5gDN1czW}

used & with the command to start the process asa background process
```bash
/challenge/run &

```
### New Learnings
run a process in the background from the get go start
### References 
na


## Challenge Name
Process exit codes
### Solve
pwn.college{c6BAlCf1wi35NCzm3JOslotfybU.dljN4UDL5gDN1czW}

ran the command echoed the variable with $? then gor the code and ran the command again
```bash
/challenge/get-code
echo $?
/challenge/submit-code 207
```
### New Learnings
leanrt about the  exit code.
### References 
na



