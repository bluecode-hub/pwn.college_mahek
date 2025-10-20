# St3g0
first i put the picture in the hex hedictor and saw that file was png only 
after that i put it in binwalk to get enciption but this does not work for lsb so we do not get you value after that i ran exiftool to know about the meta data of the picture and after that i ran the programme and say nothing wrog with that then i ran steghide and saw that requires a passkey. after that i downloaded i tool callded zsteg and ran the command for that and got the flag

## Flag
picoCTF{7h3r3_15_n0_5p00n_a1062667}

## Solve 
- first checked in the hexeditior saw that it was png only
- then used binwals which gave nothing so the flag has to be in the lsb of the image. 
- exiftool i ran to now the metadata of the picture and saw that it was normal 
- then i ran steghide saw that i requires a passkey then i ran zsteg 
- i ran that and got the flag
```bash
cd Downloads
binwalk e- pico.flag.png
exiftool pico.flag.png
steghide extract -ff output.txt pico.flag.png
steghide extract -sf pico.flag.png -xf output.txt
sudo apt install -y ruby ruby-dev build-essential
zsteg -a pico.flag.png
zsteg -a pico.flag.png

```

## Reference 
just gpted the command for installation of the zsteg 
