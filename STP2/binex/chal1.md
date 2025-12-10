# Binary 

- first at the start of the challenge i had to look through the main file so i put tat in ghidra an got like the decompiled code of that i got a main function that had mentioned the bffer size and that it acccepts 272 bytes. can come in that. 


## Method
```bash
undefined8 main(void)

{
  undefined1 local_108 [256];
  
  setup();
  alarm(0x3c);
  read(0,local_108,0x110);
  return 0;
}

```
- so after that i knew that i need an offset so i started searching for that i first wrote this commandwhere i had so see if there was any pie enabled or there is any nx or there is stack canaru

```bash

mahek@mahek-Inspiron-14-5430:~/Downloads/rvy3r1$ checksec --file=main
file main
readelf -h main
readelf -l main
strings -n 4 main | grep bin
[*] '/home/mahek/Downloads/rvy3r1/main'
    Arch:       amd64-64-little
    RELRO:      Partial RELRO
    Stack:      No canary found
    NX:         NX enabled
    PIE:        No PIE (0x400000)
    Stripped:   No
main: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=e65c339bd9c9dcded3af3b5a8fd62f166351edd5, for GNU/Linux 3.2.0, not stripped
ELF Header:
```
- we get to know that no pie or canry is there we have to find the offset
- we need to overflow the buffer and get the offset value 
```bash
to that we need to iverflow the buffer and get the the offset value ok
  mahek@mahek-Inspiron-14-5430:~/Downloads/rvy3r1$ python3 - << 'EOF'
from pwn import *
print(cyclic(300))
EOF
b'aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaazaabbaabcaabdaabeaabfaabgaabhaabiaabjaabkaablaabmaabnaaboaabpaabqaabraabsaabtaabuaabvaabwaabxaabyaabzaacbaaccaacdaaceaacfaacgaachaaciaacjaackaaclaacmaacnaacoaacpaacqaacraacsaactaacuaacvaacwaacxaacyaac'
mahek@mahek-Inspiron-14-5430:~/Downloads/rvy3r1$ ./main <<< $(python3 -c "from pwn import *; print(cyclic(300))")
Segmentation fault (core dumped)
mahek@mahek-Inspiron-14-5430:~/Downloads/rvy3r1$ gdb ./main
(gdb) run <<< $(python3 -c "from pwn import *; print(cyclic(300))")
(gdb) i r
(gdb) run <<< $(python3 -c "from pwn import *; print(cyclic(300))")
Starting program: /home/mahek/Downloads/rvy3r1/main <<< $(python3 -c "from pwn import *; print(cyclic(300))")
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
0x00000000004011c1 in main ()
(gdb) i r
rax            0x0                 0
rbx            0x0                 0
rcx            0x7ffff7d14852      140737351075922
rdx            0x110               272
rsi            0x7fffffffd9f0      140737488345584
rdi            0x0                 0
rbp            0x61706361616f6361  0x61706361616f6361
rsp            0x7fffffffdaf8      0x7fffffffdaf8
r8             0x7ffff7e1bf10      140737352154896
r9             0x7ffff7fc9040      140737353912384
r10            0x7ffff7c065e8      140737349969384
r11            0x246               582
r12            0x7fffffffdc08      140737488346120
r13            0x401183            4198787
r14            0x403e00            4210176
r15            0x7ffff7ffd040      140737354125376
rip            0x4011c1            0x4011c1 <main+62>
eflags         0x10203             [ CF IF RF ]
cs             0x33                51
ss             0x2b                43
ds             0x0                 0
es             0x0                 0
fs             0x0                 0
--Type <RET> for more, q to quit, c to continue without paging--
python3 - << 'EOF'
from pwn import *
print(cyclic_find(0x636161706361616f))
EOF
[!] cyclic_find() expected an integer argument <= 0xffffffff, you gave 0x636161706361616f
    Unless you specified cyclic(..., n=8), you probably just want the first 4 bytes.
    Truncating the data at 4 bytes.  Specify cyclic_find(..., n=8) to override this.
256



```
  
- since not the rip but the rbp was overflow we will use that and find the rip ka ffset as that is 8 bytes ahead of that

- next we need to find abut the gadgets which like syscall or something like that

```bash
python3 - << 'EOF'
from pwn import *
elf = ELF("./main")
rop = ROP(elf)
rop.find_gadget(["pop rdi", "ret"])
print(rop.gadgets)
EOF
[*] '/home/mahek/Downloads/rvy3r1/main'
    Arch:       amd64-64-little
    RELRO:      Partial RELRO
    Stack:      No canary found
    NX:         NX enabled
    PIE:        No PIE (0x400000)
    Stripped:   No
[*] Loading gadgets for '/home/mahek/Downloads/rvy3r1/main'
{4198419: Gadget(0x401013, ['add esp, 8', 'ret'], [8], 0xc), 4198418: Gadget(0x401012, ['add rsp, 8', 'ret'], [8], 0xc), 4198848: Gadget(0x4011c0, ['leave', 'ret'], ['ebp', 'esp'], 0x2540be403), 4198701: Gadget(0x40112d, ['pop rbp', 'ret'], ['rbp'], 0x8), 4198422: Gadget(0x401016, ['ret'], [], 0x4), 4198780: Gadget(0x40117c, ['syscall'], [], 0x0)}


```

- when we checked the gadgets we get no pop rdi or ret that tells us that we cannot have a normal rop but when we look at it we get syscall that means we cannot directly call functions like system("bin/sh") but we have syscall so we have to do SROP which is Sigreturn oriented programming(SROP)

- we need to do that for that we will need a puython file that will pivot and and infiltrate
- for that we can make use of frame
- i could reach till here i am making the correct python file for that





