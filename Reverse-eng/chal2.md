# challenge 2
this challenge is flag{key1+key2}

so first i read the file and and found that the file was ufx format so i had to change the format for that i used the ufx decomipler to convert to binary
## flag
flag{456789+KLq59U1337}


## Solve
- first step of the solution was to use upx t convert the file to binary
```bash
upx -d flag{key1+ke2}
                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2020
UPX 3.96        Markus Oberhumer, Laszlo Molnar & John Reiser   Jan 23rd 2020

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
upx: flag{key1+ke2}: FileNotFoundException: flag{key1+ke2}: No such file or directory

Unpacked 0 files.
mahek@mahek-Inspiron-14-5430:~/Downloads/Revchalls-main$ fi

```
- after it is converted to the to the binary file we can use the command  of objdump to get the hex data . i got this hex data and got the first part of the flag
```bash
806a020 76652074 68652066 69727374 20706172  ve the first par
 806a030 74206f66 206b6579 20796574 004a004b  t of key yet.J.K
 806a040 004c0071 00350039 00550031 00330037  .L.q.5.9.U.1.3.7
 806a050 00000000 596f7520 646f6e74 20686176  ....You dont hav
 806a060 65207468 6520656e 74697265 206b6579  e the entire key
 806a070 20796574 2e2e2e2e 203a2800 00000000   yet.... :(.....
 806a080 08000100 02000100 03000100 02000100  ................
 806a090 04000100 02000100 03
```
- so got the second key flag from here JKLq59U137
```bash
oid main__one(void)

{
  int in_GS_OFFSET;
  undefined1 local_4c [16];
  char *local_3c;
  undefined4 local_38;
  undefined4 local_34;
  undefined1 local_2c [16];
  undefined4 local_1c;
  undefined4 local_14;
  int local_10;
  
  local_10 = *(int *)(in_GS_OFFSET + 0x14);
  local_1c = 0xfffffffe;
  __new_array_with_default(local_4c,6,0,4);
  local_14 = 0xfffffffd;
  __new_array_with_default(local_2c,6,0,4,&local_14);
  local_3c = "You don\'t have the first part of key yet";
  local_38 = 0x28;
  local_34 = 1;
  println("You don\'t have the first part of key yet",0x28);
  if (local_10 == *(int *)(in_GS_OFFSET + 0x14)) {
    return;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail();
}
void main__two(void)

{
  int in_GS_OFFSET;
  undefined1 local_d8 [64];
  undefined4 local_98;
  int local_10;
  
  local_10 = *(int *)(in_GS_OFFSET + 0x14);
  local_98 = 0xfffffff9;
  __new_array_with_default(local_d8,7,0);
  if (local_10 == *(int *)(in_GS_OFFSET + 0x14)) {
    return;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail();
}
```

- for the first part i read the file in ghidra and got the main one and main two code and i looked into the assembly code and tried to undeerstand what the code was meaning and understood that a for loop was running that was quitting at 11 staring at 2 and it had a condition that starting from index 2 with has to give the sliced array so i got {4,5,6,7,8,9}.
fo the first flag is 456789.
