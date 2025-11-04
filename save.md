flag : v1t{duck_l0v3_w4tch1ng_p2r3}
HideTheDuck123@
we got fron thepdf that steghide then gor angri.jpg
file unzip hot the picture and the ran the mp4 got the password crackerd the steghide file,
for the polyglot challenge miscelenaneous






crypto(lost some binary)
v1t{LSB:>}
Hiii man,how r u ?Is it :))))Rawr-^^[]  LSB{><}!LSB~~LSB~~---v1t  {135900_13370}


binary_data = """01001000 01101001 01101001 01101001 00100000 01101101 01100001 01101110 00101100 01101000 01101111 01110111 00100000 01110010 00100000 01110101 00100000 00111111 01001001 01110011 00100000 01101001 01110100 00100000 00111010 00101001 00101001 00101001 00101001 01010010 01100001 01110111 01110010 00101101 01011110 01011110 01011011 01011101 00100000 00100000 01001100 01010011 01000010 01111011 00111110 00111100 01111101 00100001 01001100 01010011 01000010 01111110 01111110 01001100 01010011 01000010 01111110 01111110 00101101 00101101 00101101 01110110 00110001 01110100 00100000 00100000 01111011 00110001 00110011 00110101 00111001 00110000 00110000 01011111 00110001 00110011 00110011 00110111 00110000 01111101"""

bytes_list = binary_data.split()


lsb_bits = ''.join(b[-1] for b in bytes_list)


chars = [chr(int(lsb_bits[i:i+8], 2)) for i in range(0, len(lsb_bits), 8)]
message = ''.join(chars)

print(message)


v1t{m0dul0_pr1z3}
import random

inp = input("Enter plaintext: ")

def encrypt(pt):
    key = random.randint(1, 100)
    results = [str(ord(ch) % key) for ch in pt]
    print("Encrypted:", " ".join(results))
    with open('flag.enc', 'w') as f:
        f.write(" ".join(results))
    return key

k = encrypt(inp)
print("Key (for debug):", k)
 difference between them
 
 
 
 # decode_with_key.py
enc = [16,49,14,21,7,48,49,15,6,48,44,10,12,49,20,0,23]
key = 1
while(key<100):
   # replace with known key if you have it
 PRINTABLE_RANGE = range(32,127)

 decoded = []
 for t in enc:
    candidates = [chr(v) for v in PRINTABLE_RANGE if v % key == t]
    if len(candidates) == 1:
        decoded.append(candidates[0])
    else:
        # pick smallest printable if ambiguous (heuristic)
        decoded.append(candidates[0] if candidates else '?')
 print("".join(decoded))
 print(key)
 key=key+1


got few the first value and then saw other  comibation after that by bruteforcing that


mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/de.py
8520595641234233889906203467245297960090
v1t{RSA_101_b4by}
import sympy
p=101
q=313846144900241708687128313929756784551
n = 31698460634924412577399959706905435239651
e = 65537
c = 23648999580642514140599125257944114844209

phi=(p-1)*(q-1)
d=pow(e,-1,phi)
value=pow(c,d,n)
print(value)
actual=value+n
hex_str=hex(actual)[2:]
flag=bytes.fromhex(hex_str).decode()
print(flag)


 you meant '==' or ':=' instead of '='?
mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/modulo.py
{101: 1, 313846144900241708687128313929756784551: 1}
Traceback (most recent call last):
  File "/home/mahek/Downloads/modulo.py", line 11, in <module>
    d = mod_inverse(65537, phi)
  File "/usr/lib/python3/dist-packages/sympy/core/numbers.py", line 550, in mod_inverse
    raise ValueError('inverse of %s (mod %s) does not exist' % (a, m))
ValueError: inverse of 65537 (mod 0) does not exist
mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/modulo.py
{101: 1, 313846144900241708687128313929756784551: 1}
8520595641234233889906203467245297960090
b'\x19\n/\x07i\x0fW8k\xce7\xc0\x8e\t\xf1\x84\x9a'
mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/modulo.py
8520595641234233889906203467245297960090
b'\x19\n/\x07i\x0fW8k\xce7\xc0\x8e\t\xf1\x84\x9a'
mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/de.py
8520595641234233889906203467245297960090
v1t{RSA_101_b4by}
mahek@mahek-Inspiron-14-5430:~$ ^C




v1t{f3rm4t_l1ttl3_duck}
n = 148900953097814724338206947679223698832179691968218755697733749707084556942286184505525791780949441847197006147827388400754499224336852575956050210608024912280019773833889546324355353746095214275985515374968532505153145975517881297436944244066461866248895871696012367810254055557824874852294865749524482337551
e = 65537
c = 107217087223013352864419426588613439434708031699522027786711684217439431898186052583896596846379575153070982123347045493427454234913154021933229641985591412104222934496019950746514726800406326146713516918611779367873873294259462206805554572977819244626333164240237423211396727885901436510649294574529712562954

from sympy import factorint, mod_inverse

factors = factorint(n)
print("Factors:", factors)

if len(factors) == 1:
    print("n appears to be prime — misconfigured RSA.")
    phi = n - 1
else:
    primes = list(factors.keys())
    p, q = primes[0], primes[1]
    phi = (p - 1) * (q - 1)

d = mod_inverse(e, phi)
m = pow(c, d, n)
print("Decrypted integer:", m)

hex_m = hex(m)[2:]
if len(hex_m) % 2:
    hex_m = '0' + hex_m
print("Plaintext (raw bytes):", bytes.fromhex(hex_m))
mahek@mahek-Inspiron-14-5430:~$ /bin/python3 /home/mahek/Downloads/de.py
Factors: {148900953097814724338206947679223698832179691968218755697733749707084556942286184505525791780949441847197006147827388400754499224336852575956050210608024912280019773833889546324355353746095214275985515374968532505153145975517881297436944244066461866248895871696012367810254055557824874852294865749524482337551: 1}
n appears to be prime — misconfigured RSA.
Decrypted integer: 11320657929099562046850213072766143248835856086834834301
Plaintext (raw bytes): b'v1t{f3rm4t_l1ttl3_duck}'


In normal RSA:

n=p×q
n=p×q

is composite, not prime.

If your n is prime (as here), the RSA system is misconfigured — hence the challenge name “Misconfigured RSA”.
In that case, the private exponent d can be computed using Fermat’s little theorem with

ϕ(n)=n−1
ϕ(n)=n−1

instead of (p−1)(q−1).



resurces https://github.com/ashutosh1206/Crypton.git


v1t{p4tch_th3_b4tch_t0_g3t_th3_s3cr3t_3nd1ng}
we pathched the three fragments together and got the unlocktheduck  unlockthegoose was also there but that was the value that we got just to finish the game for getting the flag we beeded this value we also needed the hash value of the game to run the game and pass te flag password directly so we got that from the results.bat file then ran 
set "full=%frag1%%frag2%%frag3%"
set "self=%~f0"
set "hash="
for /f "skip=1 tokens=1" %%H in ('certutil -hashfile "%self%" SHA256') do (
    call set "hash=%%H"
    goto result
)

:result
call result.bat !full! !hash!
exit /b
it says here full =frag1+frag2+frag3
and we need both full anf hash
# Make sure WINE is properly configured
wine cmd /c result.bat unlocktheduck 8392dcc7b6fdebd5a70211c1e21497a553b31f2c70408b772c4a313615df7b60
mahek@mahek-Inspiron-14-5430:~/Downloads$ wine cmd /c game.bat
==========================
Battle: Duck Mage
==========================
Your HP: 3
Duck Mage HP: 30

1. Attack
v1t{p4tch_th3_b4tch_t0_g3t_th3_s3cr3t_3nd1ng}



v1t{Ivey_park}
searched the image on google by google image saw a lot of instagram photos checked that it was thames river so looked at parks in thames in london cause that picture was from london got the parks chcekd thier photo gallery and ivey park was the one that had the picture in its picture gallery



Red Banner Military Unit 61608 - 100 Years (Communication) Space
 v1t{55.592169,37.689097}



