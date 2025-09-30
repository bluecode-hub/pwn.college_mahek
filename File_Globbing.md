# Module Name
File Globbing

## Challenge Name
matching with *
### Solve
pwn.college{EQC6iNh_tD33xTcGElGclzkskD_.dFjM4QDL5gDN1czW}

here i read the instruction and it saud four character match with * so got it to four characters went to the directory then ran the command

```bash
cd /ch*
/challnege/run
```

### New Learnings
leant matching with * learnt that * matched trailing values

### References 
na

## Challenge Name
matching with ?
### Solve
pwn.college{QgtoYe5dqDp7FshPQpD-32vSGbx.dJjM4QDL5gDN1czW}

as ? matched one character wrote cd by replacing c and l and went to the directory then ran the command

```bash
cd /?ha??enge
/challenger/run
```

### New Learnings
learnt that ? matched one character unlike * which is for a pattern of values

### References 
na

## Challenge Name
matching with []
### Solve
pwn.college{EOKRkco2P89k6Enc8uxIV5AB3i7.dNjM4QDL5gDN1czW}

here [] is used to set the file parameters we go to the directory and then we go to the directory then put the parameters of the flag
```bash
cd /challenge/files
/challenge/run file_[bahs]
```

### New Learnings
learnt the usage of [] this is used the match aeguments

### References 
na



## Challenge Name
matching paths with []
### Solve
pwn.college{4Vl97M8n_ZjtRNiG7djwyxMw3uL.dRjM4QDL5gDN1czW}

so i wrote /challenge/run and then serached the /challenge/files with the pattenrn bash
```bash
/challenge/run/challenge/files/file_[bash]
```

### New Learnings
learnt to match paths with [] from the home directory

### References 
na


## Challenge Name
multiple globs
### Solve
pwn.college{MK-li-9lIAl4Fzeeq0edLFDxiik.QXycTO2EDL5gDN1czW}

here went to the directory and then we can write /challenge/run with three charater *p*

```bash
cd /challenge/files
/challenge/run *p*
```

### New Learnings
learnt to use multiple * to match the name of the file 

### References 
na



## Challenge Name
Mixing globs
### Solve
pwn.college{0a3I76ESR1NrD2sbr-NwPzUybDV.dVjM4QDL5gDN1czW}

so we know that we need to get this to 6 characters and we know that it starts with c,e or p so we use [cep]*. * is for all the rest pattern
```bash
cd /challenge/files
/challenge/run [cep]*
```

### New Learnings
learnt to use mix globes to matching the file names

### References 
na


## Challenge Name
Exclusionary globbing
### Solve
pwn.college{g5iwq6tMBGaYni4MJqnRcYrUP1y.dZjM4QDL5gDN1czW}

so now we want to filter out files in glob [] we need to use so [!pwn]* helps filter out the value
```bash
cd /challenge/files
/challenge/run [!pwn]*
```

### New Learnings
we learnt how to use glob not operator

### References 
na



## Challenge Name
tab completion
### Solve
pwn.college{I_AELpxJr41Vdsnp83OFCG03Vgj.QX0QTM3EDL5gDN1czW}

so tab completion is like autocomplete so we can write just pwn with cat and on tabbing the computer autocompletes it and finishes the whole possiblitlity that can come

```bash
cat /challenge/pwncollege
```

### New Learnings
learnt to use the tab to autocomplete

### References 
na


## Challenge Name
multiple options for tab completion
### Solve
pwn.college{Q5223VH7p4Ab-U-4mdJZGhWwojW.QX2QTM3EDL5gDN1czW}

here we go to the directory and then in that directory cat p files pwm and then tab again will give all the list of files of the pwn and then we can find the flag
```bash
cd /challnege/files
cat p<tab>
cat pwn<tab>
cat pwncollege-flag
```

### New Learnings
we leant to use the tab funtion twice what happens on pressing it for the second time we get the whole list of files with that name

### References 
na

## Challenge Name
tab completion on commands
### Solve
pwn.college{oeRJRKqwMzLJXCWRlyCPGVwLx81.QX1QTM3EDL5gDN1czW}

so we type tab to complete commands 

```bash
pwncollege<tab>
pwncollege-17238
```

### New Learnings
learnt to use tab to complete commands

### References 
na




