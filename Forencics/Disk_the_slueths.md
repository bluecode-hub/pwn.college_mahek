# Disk, disk, sleuth! II
made use of complete sluetkit 
first opeened in hexeditor could not figuree out the file type so must a disk file so used slueth kit tool in that first did img_stat to know the type of the file it was raw so we can confirm that it is a disc ijmage after that we do mmls to know abouut the partition of the picture in the disc and know if the piture is physical or logical if physical we not the offset value. after that we do fls -o 2048 the image name. to lis all the directory and file in the particular partition of the image then we look at the directory with each file offset value and see which contains a file the root directory contained the txt file so we icat with i which asks us the specofy the file type raw with the file name and we get the answer.

## Flag
picoCTF{f0r3ns1c4t0r_n0v1c3_ff27f139}

## Solve
- for this challenge learnt the use of sluethkit 
- first opened the hexeditior and figured out the file type but could not figure out with the hexeditior so it must be a disc typr file 
- used img_stat to know the type of he file it was raw so we can comfirm that it is a disc image. after that we do mmls to know about the partition of the picure in the disc and we have to know whether the image is physical and logical
- if physical the offset value is not there
- after that we do fls -o  2028 the file name to list all the directory and file in the particular partition of the image then we look at the directory with each file offset value and see which contains a file the root directory contained the txt file
- we then i cat the file and get the flag

```bash
cd Downloads
img_stat dds2-alpine.flag.img
mmls dds2-alpine.flag.img
fsstat -o 2048 dds2-alpine.flag.img
fls -o 2048 dds2-alpine.flag.img
fls -o 2048 dds2-alpine.flag.img.18290
icat -i raw -o 2048 dds2-alpine.flag.img 18291


```

## rference 
refered the document of slueth kit


