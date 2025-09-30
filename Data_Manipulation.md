# Module Name

Data manipulation


## Challenge Name
Translating Characters
### Solve
pwn.college{Q_gutsRAKvBDuLB-lhAjwNCYlji.QXzETM3EDL5gDN1czW}
 
i use the tr to convert all the capital to lower and all the lower to capitall
```bash
/challenge/run |tr ABCDEFGHIJKLMNOPQRSTUVWZYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIGKLMNOPQRSTUVWXYZ
```

### New Learnings
learnt the usage of the tr function that helps to modif the character provided in the first into the other argument

### References 
na


## Challenge Name
deleting characters
### Solve
pwn.college{wYeHh2qSsL5SYR8DSqxmiCLWc5F.QX0ETM3EDL5gDN1czW}

this to remove the remove a particular character from the output or the flag -tr -d character . it can be multiple also
```bash
/challenge/run |tr -d ^%

```
### New Learnings
learnt how to delete characters from the challenge given using -d command
### References 
na


## Challenge Name
deleting newline
### Solve
pwn.college{w7HF5aGhhOwvY21NQ0-t3HU-py2.QX1ETM3EDL5gDN1czW}

so here also newline is represented by \n se we make use of that and then we use the command of tf -d to remove the newline and we give it in quotes so that we dont misinterpret it as a command.
```bash
/challenge/run |tr -d "\n"
```

### New Learnings
learnt to delete new lines

### References 
na


## Challenge Name
extracting the first lines with head
### Solve
pwn.college{MK9P1ajTbCV_2deUc8nd3gBvA0w.QX2ETM3EDL5gDN1czW}

in this instruction was given to get the first 7 lines of the head and then we had to use that and store it into another while piping it so did that
```bash
cd /
challenge/pwn |head -n 7|challenge/college

```
### New Learnings
learnt about the head command and how it helps to extract some values from the beggining of the file
### References 
na

## Challenge Name
extracting specific sections of text
### Solve
pwn.college{UhNQxt99lmVNiYsZx6DgYbeBFEX.QX3ETM3EDL5gDN1czW}

a way to extract the column two of the given field. it is used to extract the complete letter of the second column that is the letters.
```bash
/challenge/run|cut -d ""-f2|tr -d '\n'
```

### New Learnings
learnt the usage of cut to extract some information
### References 
na


## Challenge Name
storing command output
### Solve
pwn.college{smjfl8AvU6bFY17s_-HCAjhhRU0.QXwQzM4EDL5gDN1czW}

here we sort the values aplhabetically and then seee the order where the correct flag is comming
```bash
sort -r/challenge/flags.txt
```

### New Learnings
leant to sort the flag alphabetically, numerically, unique lines only,random order

### References 
na


