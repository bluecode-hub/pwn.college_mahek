# Gotham 

in the beginning of te challenge first i saw the file size and trid to find out what type the file was. i found out that the file had a lot of memory filea anddump processing files. we just needed to see the process where the flag can be

## Votality2

i read on the interne that votality is the tool to be issued to search all the memory files of the computer. votality 3 is the newnest version but it cant memump whic we would need and like the profile register that we can get in votality2 that we cant get ib voltality3. we need to find the offset of the fole and the potential register and also the system that is windows or linux. and also the process that we need to dump and fing the flag.

## Steps

- first we need to install thenecessay packages and run the command to find the profile of the image and the potential registers
```bash
mahek@mahek-Inspiron-14-5430:~/Downloads$ pip2 install pycryptodome
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Collecting pycryptodome
  Downloading pycryptodome-3.23.0-cp27-cp27mu-manylinux2010_x86_64.whl (2.5 MB)
     |████████████████████████████████| 2.5 MB 2.7 MB/s 
Installing collected packages: pycryptodome
Successfully installed pycryptodome-3.23.0
mahek@mahek-Inspiron-14-5430:~/Downloads$ pip2 install distorm3
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Collecting distorm3
  Using cached distorm3-3.5.2.tar.gz (138 kB)
Using legacy 'setup.py install' for distorm3, since package 'wheel' is not installed.
Installing collected packages: distorm3
    Running setup.py install for distorm3 ... done
Successfully installed distorm3-3.5.2
mahek@mahek-Inspiron-14-5430:~/Downloads$ pip2 install yara-python
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Collecting yara-python
  Downloading yara_python-4.5.4.tar.gz (551 kB)
     |████████████████████████████████| 551 kB 2.2 MB/s 
Using legacy 'setup.py install' for yara-python, since package 'wheel' is not installed.
Installing collected packages: yara-python
    Running setup.py install for yara-python ... done
Successfully installed yara-python-4.5.4
mahek@mahek-Inspiron-14-5430:~/Downloads$ python2 vol.py -f gotham.raw imageinfo
python2: can't open file 'vol.py': [Errno 2] No such file or directory
mahek@mahek-Inspiron-14-5430:~/Downloads$ cd ~/Downloads/volatility
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ python2 vol.py -f ../gotham.raw imageinfo
Volatility Foundation Volatility Framework 2.6.1
INFO    : volatility.debug    : Determining profile based on KDBG search...
          Suggested Profile(s) : Win7SP1x64, Win7SP0x64, Win2008R2SP0x64, Win2008R2SP1x64_24000, Win2008R2SP1x64_23418, Win2008R2SP1x64, Win7SP1x64_24000, Win7SP1x64_23418
                     AS Layer1 : WindowsAMD64PagedMemory (Kernel AS)
                     AS Layer2 : FileAddressSpace (/home/mahek/Downloads/gotham.raw)
                      PAE type : No PAE
                           DTB : 0x187000L
                          KDBG : 0xf80002a48120L
          Number of Processors : 6
     Image Type (Service Pack) : 1
                KPCR for CPU 0 : 0xfffff80002a4a000L
                KPCR for CPU 1 : 0xfffff880009ea000L
                KPCR for CPU 2 : 0xfffff88002ea8000L
                KPCR for CPU 3 : 0xfffff88002f24000L
                KPCR for CPU 4 : 0xfffff88002fa0000L
                KPCR for CPU 5 : 0xfffff88002fdc000L
             KUSER_SHARED_DATA : 0xfffff78000000000L
           Image date and time : 2024-08-06 18:37:19 UTC+0000
     Image local date and time : 2024-08-06 11:37:19 -0700
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 
```

- i used votalitiy 2 it searches all the memory dump files and gives us the flag based on the process it is dumped like notepad or chrome exe and other stuff
 Win7SP1x64, Win7SP0x64, Win2008R2SP0x64, Win2008R2SP1x64_24000, Win2008R2SP1x64_23418, Win2008R2SP1x64, Win7SP1x64_24000, Win7SP1x64_23418
 we get al lot of profile that we can go and search in here we can start and check.
 
```bash
 python2 vol.py -f ../gotham.raw --profile=Win7SP1x64 cmdscan
Volatility Foundation Volatility Framework 2.6.1
**************************************************
CommandProcess: conhost.exe Pid: 4188
CommandHistory: 0x130de0 Application: cmd.exe Flags: Allocated, Reset
CommandCount: 8 LastAdded: 7 LastDisplayed: 7
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x60
Cmd #0 @ 0x12f7c0: whoami
Cmd #1 @ 0x130110: dir
Cmd #2 @ 0x12f800: bi0s
Cmd #3 @ 0x12f820: dfirlabs
Cmd #4 @ 0x12d690: Ymkwc2N0Znt3M2xjMG0zXw==
Cmd #5 @ 0x12d6d0: azr43ln1ght.github.io
Cmd #6 @ 0x125650: Azr43lKn1ght
Cmd #7 @ 0x125680: did you find flag1?
Cmd #15 @ 0xb0158: 
Cmd #16 @ 0x12ff50: 
**************************************************
CommandProcess: conhost.exe Pid: 4140
CommandHistory: 0x280e10 Application: DumpItog.exe Flags: Allocated
CommandCount: 0 LastAdded: -1 LastDisplayed: -1
FirstCommand: 0 CommandCountMax: 50
ProcessHandle: 0x10
Cmd #15 @ 0x200158: (
Cmd #16 @ 0x27ff70: (
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 
```


- cmd scan is like searching all the previous cmd commmands that were given by us. it will search all the previous commands and help us find the exact place where we can find now if we echo from the cmd we can get the flag here we will use cmd 4 as == means cmp no like comparing the flag so we echo that.

```bash
.mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ echo "Ymkwc2N0Znt3M2xjMG0zXw==" | base64 -d
bi0sctf{w3lc0m3_mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 

```
- we got the first part of the flag

- we get the first part of the flag as this the flag was encoded i first checked ascii encoding that didnt give bioctd so then i checked base 64 that gave the flag first part now we have to find the rest of the flag. the next thing we need to do is check the proces that could have the flag the check the process we do pltree .

```bash
if we look notepad exe seems like a process we could dump amd get the flag
xfffffa8003ff9060 chrome.exe             4612   4456     17      229      1      0 2024-08-06 16:36:55 UTC+0000                                 
0xfffffa8004846060 taskhost.exe           3620    552      5       96      1      0 2024-08-06 16:37:06 UTC+0000
0xfffffa8004412060 chrome.exe             4204   4456     11      191      1      0 2024-08-06 16:37:16 UTC+0000                                 
0xfffffa8004403b00 cmd.exe                3944   1172      1       20      1      0 2024-08-06 16:45:56 UTC+0000                                 
0xfffffa8006d58060 conhost.exe            4188    460      2       53      1      0 2024-08-06 16:45:56 UTC+0000                                 
0xfffffa8003c9c4f0 notepad.exe            2592   1172      1       58      1      0 2024-08-06 16:47:20 UTC+0000                                 
0xfffffa8003f3cb00 chrome.exe             3764   4456     17      253      1      0 2024-08-06 17:24:44 UTC+0000                                 
0xfffffa8003cebb00 chrome.exe             2608   4456     17      250      1      0 2024-08-06 17:24:45 UTC+0000                                 
0xfffffa800447c060 chrome.exe             3612   4456     17      253      1      0 2024-08-06 17:24:48 UTC+0000                                 
0xfffffa800446a9a0 chrome.exe             3172   4456     17      258      1      0 2024-08-06 17:24:52 UTC+0000                                 
0xfffffa800443e060 chrome.exe             3704   4456     17      253      1      0 2024-08-06 17:24:55 UTC+0000                                 
0xfffffa80047c5060 chrome.exe             4452   4456     17      270      1      0 2024-08-06 17:25:33 UTC+0000            

```
- we can see that its number is 2592 we can use that number and do pid dump
then i grep ctf nothig. the did flag so much came

```bash
id == but again too much then i 
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ strings -el 2592.dmp|grep -i "flag"
windows_tracing_flags=3
windows_tracing_flags=3
flag4 = YjNuM2YxNzVfeTB1Xw==
flag3 = aDBwM190aDE1Xw== - Google Search - Google Chrome
AppCompatFlags\Layers
\Registry\Machine\Software\Microsoft\Windows nt\currentversion\appcompatflags\AIT
PageHeapFlags
ShutdownFlags
GlobalFlag
TracingFlags
VerifierFlags
dwFlags
dwFlags
Allow flag to be passed with CreateFile call that indicates to perform downgrade if applicable.
SaferFlags
FFlags
RpcVerifierFlags
```
- then i got two flag with the == which we can use potentially if we echo this it should work because cmd pe this was 64 encoded so if we do that we can get 

```bash
ahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ echo "YjNuM2YxNzVfeTB1Xw=="|base64 -d
b3n3f175_y0u_mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 

this is flag 4 that we got 

flag 3 we get by echoing this

mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ echo "aDBwM190aDE1Xw=="|base64 -d
h0p3_th15: invalid input
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 

flag 3 i got now flag 2 is still there 
to be found out
and we dont know if flag 4 is the last there could be flag5 and flag6 also


flag5 is there cause flag5.rar it keeps saying

mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ python2 vol.py -f ../gotham.raw --profile=Win7SP1x64 filescan | grep flag5
Volatility Foundation Volatility Framework 2.6.1
0x000000011fdaff20     16      0 -W-r-- \Device\HarddiskVolume2\Users\bruce\Desktop\flag5.rarp\VirtualBox Dropped Files\2024-08-06T18_36_43.522668500Z\flag5.rar
this give s the rar file ka offset that we need to dump 

```

- like this w get the other parts of the flag but we still ned the other flag and the flag2 so for that we keep seeing a flag5.rar file for that we can use unrar which helps read the rar file

```bash
DataSectionObject 0x11fdaff20   None   \Device\HarddiskVolume2\Users\bruce\Desktop\flag5.rarp\VirtualBox Dropped Files\2024-08-06T18_36_43.522668500Z\flag5.rar
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ ls -lh | grep dat
-rw-rw-r-- 1 mahek mahek 4.0K Dec  9 12:45 file.None.0xfffffa80049f86a0.dat
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ file file.None.0x11fdaff20.dat
file.None.0x11fdaff20.dat: cannot open `file.None.0x11fdaff20.dat' (No such file or directory)
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ file file.None.0xfffffa80049f86a0.dat
file.None.0xfffffa80049f86a0.dat: RAR archive data, v5
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ mv file.None.0xfffffa80049f86a0.dat
  flag5.rar
mv: missing destination file operand after 'file.None.0xfffffa80049f86a0.dat'
Try 'mv --help' for more information.
flag5.rar: command not found
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ mv file.None.0xfffffa80049f86a0.dat flag5.rar
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ sudo apt install unrar



 unrar x flag5.rar

UNRAR 6.11 beta 1 freeware      Copyright (c) 1993-2022 Alexander Roshal


Extracting from flag5.rar

The password for the zip file is the computer's password

Enter password (will not be echoed) for flag.txt: 

unrar x flag5.rar

UNRAR 6.11 beta 1 freeware      Copyright (c) 1993-2022 Alexander Roshal


Extracting from flag5.rar

The password for the zip file is the computer's password

Enter password (will not be echoed) for flag.txt: 

The specified password is incorrect.
Enter password (will not be echoed) for flag.txt: 

Extracting  flag.txt                                                  OK 
All OK

mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ python2 vol.py -f ../gotham.raw --profile=Win7SP1x64 hashdump
Volatility Foundation Volatility Framework 2.6.1
Administrator:500:aad3b435b51404eeaad3b435b51404ee:10eca58175d4228ece151e287086e824:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
bruce:1001:aad3b435b51404eeaad3b435b51404ee:b7265f8cc4f00b58f413076ead262720:::
HomeGroupUser$:1002:aad3b435b51404eeaad3b435b51404ee:bda4ed0acc67d6d60540d1a20cf444c6:::
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 

```

- batman was the password hashcat of the bruce user gave me there were two type of hash
echo "bruce:1000:LMHASH:NTLMHASH:::" > hash.txt
hashcat -m 1000 hash.txt /usr/share/wordlists/rockyou.txt

we crack the ntlmhash with the hashcat the reason for that is 

lm hask is disabled useless nltmhash is the one we can crack

```bash
mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ cat flag.txt
bTByM18xMzMzNzQzMX0=mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ echo bTByM18xMzMzNzQzMX0="|base64 -d
m0r3_13337431}mahek@mahek-Inspiron-14-5430:~/Downloads/volatility$ 
```

- for the flag 2 i dumped the ms paint after finding its offet with file scan command and then i used gimp to get the picture also but the picture is sofflo blurry that i cannot read it. the picture i tried changinf the picle also but it was very blurry so i couldnt read that part and get the flag for that part other than that i got the flag.

## flag

bi0sctf{w3lc0m3_flag2_h0p3_th15_b3n3f175_y0u_m0r3_13337431}












































