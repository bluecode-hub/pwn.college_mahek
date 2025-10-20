# chal3 
the challenge is about modular matns completey.

## Flag
idek{charles_and_the_chocolate_factory!!!}

## Solve
- first part of the challeneg is understanding how it was encyted that took we a lot of time we look at tthe code we encrypt the flag using the given conditions
- we get the remain funtion which the encryption of secret and decret -1
- after that we solve two equation and get the value of x and y that we need to give to solve the exqustion
- in the end we use discrete log to find the value of the flag 
- this is the solution file 
- this is the solution file where we solve the two modulo terms find the x and y equation and then we use that to get the decrypted file.

```bash
from Crypto.Util.number import long_to_bytes
from sympy.ntheory import discrete_log
p = 396430433566694153228963024068183195900644000015629930982017434859080008533624204265038366113052353086248115602503012179807206251960510130759852727353283868788493357310003786807
r0 = 88952575866827947965983024351948428571644045481852955585307229868427303211803239917835211249629755846575548754617810635567272526061976590304647326424871380247801316189016325247
r1 = 67077340815509559968966395605991498895734870241569147039932716484176494534953008553337442440573747593113271897771706973941604973691227887232994456813209749283078720189994152242
y=((r1-13*r0)*pow(24,-1,p))%p
x = (r0 - y) % p
print(f" {x}")
print("\n")
print(f" {y}")
print("\n")
print("Discrete lg ")
exp = discrete_log(p, x, 13) 
secret = exp + 1
flag = long_to_bytes(secret)

print(f"{flag.decode()}")

```
- this is the encrypted file that we have and we need to make use of that to understand the code we start a counter with zero and we run the generator code with a while loop and and see which number generated the code that gave the decrypted code. we run the complete while loop on the whole to match the decrypted code. but this is taking too much time this method so we use another method
```bash
#[88952575866827947965983024351948428571644045481852955585307229868427303211803239917835211249629755846575548754617810635567272526061976590304647326424871380247801316189016325247, 67077340815509559968966395605991498895734870241569147039932716484176494534953008553337442440573747593113271897771706973941604973691227887232994456813209749283078720189994152242]


remain=[88952575866827947965983024351948428571644045481852955585307229868427303211803239917835211249629755846575548754617810635567272526061976590304647326424871380247801316189016325247, 67077340815509559968966395605991498895734870241569147039932716484176494534953008553337442440573747593113271897771706973941604973691227887232994456813209749283078720189994152242]
g_secret_minus_1=remain[0]
g_secret=remain[1]
secret=0
while True:
    if generator(secret)==g_secret:
        break
    secret+=1
    if secret%1000==0:
        print(f"flag is being obsecured:{secret}")
print(f"the flag is:{secret}")
flag=long_to_bytes(secret)
```

## Reference
saw a lot of sources to understand the math




