# Module Name

Shell Variables


## Challenge Name
printing variables
### Solve
pwn.college{wOiLYi7tCQF6iBOI_X1OdMrztLt.ddTN1QDL5gDN1czW}
 
 as echo can also show content of variable by useing $ sign we used echo $flag
```bash
echo $FLAG

```

### New Learnings
learnt how to echo variables by using $ sign

### References 
na


## Challenge Name
setting variables
### Solve
pwn.college{YkS5ZOqWfskW1SRwGOV8zM92Ift.dlTN1QDL5gDN1czW}

as the description said hen we do PWN=COLLEGE no spaces it sets the variable with that value. $PWN is to scces the variable if in future we want to
```bash
PWN=COLLEGE

```

### New Learnings
learn to set varaible. learnt they are case sensitive
### References 
na

## Challenge Name
multi word variables
### Solve
pwn.college{oaVNvIs3d58E5k0fNgjO886j-qc.dBjN1QDL5gDN1czW}

we need to set the variable to multiple carater but on putting a space it takes the next wod as a coommand so we can put it in quote for the terminal to understand the space 
```bash
PWN="COLLEGE YEAH"
```

### New Learnings
learnt how to store multiple words to a variable with quotes

### References 
na


## Challenge Name
exporting variables
### Solve
pwn.college{g2umh8HG_mB-paPzajxKKr39Ese.dJjN1QDL5gDN1czW}

so here they told to export PWN and not COLLEGE so did that and exported the PWN but not the college then ran the  /challenge/run command by using varaiable accesor $ sign
```bash
export PWN=COLLEGE
COLLEGE=PWN
/challenge/run $PWN

```
### New Learnings
learnt the usgae of multiple ways to reach the variables and use them various terminal by exporting them

### References 
na

## Challenge Name
printing exported variables
### Solve
pwn.college{AIhLRnPSzLcldZuQ9cRZF6UAoSQ.dhTN1QDL5gDN1czW}

env is a way to print all the exported variables so i used that and print env and got the flag. iot works like echo but prints all the exported variables
```bash
env
```

### New Learnings
learnt the usage of env to print all the exported variables
### References 
na


## Challenge Name
storing command output
### Solve
pwn.college{AZ7enNksgj9DglY6BFjDverdyzd.dVzN0UDL5gDN1czW}
here we had to store the output of /challenge/run in a variable so i did that and stored the output of the directory. and then catted the file with the variable stored in witha $ sign.
```bash
PWN=$(/challenge/run)
cat $PWN
```

### New Learnings
learnt to store the content of a command run in a variable 

### References 
na


## Challenge Name
reading input
### Solve
pwn.college{Y-LActUN3rXVYScSIrzmU4SJJov.dhzN1QDL5gDN1czW}

we had to get the input frm the user so used the command of read with the variable andthe inputed the value tpo be set forthat variable
```bash
read PWN
COLLEGE	
```
### New Learnings
how to read and store user values in a variable
### References 
na


## Challenge Name
reading files
### Solve
pwn.college{gdPRFiOYicyjKy4J765m4YcCd1A.dBjM4QDL5gDN1czW}

here we readed the output of the read_me flag into a variable
```bash
read PWN </challenge/read_me

```
### New Learnings
new learning is that we leanr to read the and feed the input to another file and then read it.
### References 
na


