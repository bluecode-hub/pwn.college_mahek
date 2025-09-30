# Module Name

Perceiving Permissions


## Challenge Name
Changing file ownership
### Solve
pwn.college{ICZYQMaTLEzq4XWRv1-CSrtowha.dFTM2QDL5gDN1czW}

so we changed the ownership of the /flag to that of the hacker and first we saw ls -l and saw all the file to see the ownership so we change the root of the flag file to the  current  hacker and then we cat the file to know the flag 
```bash
ls -l
chown hacker /flag
cat/flag
```

### New Learnings
learnt how to change ownership to get the root file to a current directory
### References 
na



## Challenge Name
Groups and files
### Solve
pwn.college{sZ-WpkHg9y4K2zCJhF-lZgZCg7H.dFzNyUDL5gDN1czW}

we can also change the group of the file so we used chgrp with the link and the file name. this help change the file group.
```bash
chgrp hacker /flag
cat /flag
```

### New Learnings
learnt to change the group of the file
### References 
na



## Challenge Name
fun with group names
### Solve
pwn.college{k6vD7RC7lCzDfFIzSv-a1gNqKHk.dJzNyUDL5gDN1czW}

we type id and then we see all the uid and gid and we see the nme of the group that we need to change to so we need to use chgrp and change the group of the flag and then cat it to read the flag
```bash
chgrp grp22724 /flag
cat /flag
```

### New Learnings
practiced chaning the group of the file and learnt more about this concept

### References 
na


4)## Challenge Name
changing permissions
### Solve
pwn.college{A2IyqLZ0CmHO0YeZo3DqM9-0wzb.dNzNyUDL5gDN1czW}

we have to change the mod of the file. we nned to make the ugo to r so i did that and cat the file to get the flag
```bash
chmod ugo+r /flag
cat /flag

```
### New Learnings
leanr to change the file permission of the file so that we can read the file or change it

### References 
na



## Challenge Name
changing permissions
### Solve
pwn.college{A2IyqLZ0CmHO0YeZo3DqM9-0wzb.dNzNyUDL5gDN1czW}

we have to change the mod of the file. we nned to make the ugo to r so i did that and cat the file to get the flag
```bash
chmod ugo+r /flag
cat /flag

```
### New Learnings
leanr to change the file permission of the file so that we can read the file or change it

### References 
na

## Challenge Name
Executable files
### Solve
pwn.college{gGuE71C95maMz2-ytL0_xhE4zVP.dJTM2QDL5gDN1czW}

so we nned to make use of the file permission modification to change the permission of the file. se we make all the three so executable then we cat the file 
```bash
ls -l /challenge/run
chmod ugo+x /challenge/run
ls -l /challenge/run
/challenge/run

```
### New Learnings
learnt more about changing the file file settings

### References 
na

## Challenge Name
Permission Tweaking practice
### Solve
pwn.college{gZPpE9__r_QYBaJZ6qnBMEXGn5D.dBTM2QDL5gDN1czW}

solved a bunch of file transformation of the permission as specified by the computer. did all the computation 8 times till reached the final level then made changes to the flag file made it readable then cat it.
```bash
/challenge/run
chmod go+x /challenge/pwn
chmod go-x /challenge/pwn
chmod go+x /challenge/pwn
chmod go-r /challenge/pwn
chmod g+w /challenge/pwn
chmod go-x /challenge/pwn
chmod uo+x /challenge/pwn
chmod u-rw /challenge/pwn
chmod o-x /challenge/pwn
chmod o+x /challenge/pwn
 chmod ugo+r /flag
 cat /flag

```
### New Learnings
did more practice on file permission

### References 
na

## Challenge Name
Permission setting practice
### Solve
pwn.college{AgEYmL_8k7qY6mFJ-vjoZGw5aAl.dNTM5QDL5gDN1czW}

another way to set the value permission of the file we can make use of = operator to do that. we can again solve the 8 levels and then make the flag file readable and then cat it 
```bash
/challenge/run
chmod u=r,g=rw,o=r /challeng
chmod u=-,g=-,o=rw /challenge/pwn
chmod u=wx,g=x,o=x /challenge/pwn
chmod u=rw,g=x,o=rw /challenge/pwn
chmod u=w,g=rwx,o=rwx /challenge/pwn
chmod u=r,g=rx,o=x /challenge/pwn
chmod u=rx,g=rx,o=rwx /challenge/pwn
chmod u=rx,g=rw,o=rwx /challenge/pwn
chmod u=r,g=r,o=r /flag
cat /flag

```
### New Learnings
learnt to use = command to change the file permission.
### References 
na


## Challenge Name
The SUID bit
### Solve
pwn.college{Y1w_uktPHUVn2X6CJm4h6DWghCA.dNTM2QDL5gDN1czW}
chmod command with the u+s to change the suid bit after doinf that we open the executable shell and run the command to cat the flag
rn the 
```bash
chmod u+s/challenge/getroot
/challenge/getroot
cat /flag

```
### New Learnings
learnt how to change the suid bit
### References 
na
