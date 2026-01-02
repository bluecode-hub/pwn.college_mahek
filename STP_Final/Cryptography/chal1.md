# challenge 1
we nned to find the flag from the given script. as we read the script we can figure out two kind of decryption have been used

## Flag
```bash
mahek@mahek-Inspiron-14-5430:~/Downloads/handout$ /usr/bin/python3 /home/mahek/Downloads/handout/new.py
[+] a = 10835766216613383506
[+] b = 6219413745182497707
[+] FLAG: TCP1P{prime_prime_prime_prime_prime_prime_prime_prime_prime_prime}
```
## method
- we can make out from the given code few things that
- p=a^51+51 *b^51
- now if we take mod both sides we get
- 0=a^51+51*b^51  (mode p)
- -51*b^51(mod p)=a^51
- if we take 1/51 power on both sides 
- a= (-51)^1/51*b mod p
- so we can take (-51)^1/51 as the r
- it becomes a=rb(modp)
we have a linear relation ship we can use 2 d lattice to find the shortest value of a and b which we from the vector such that
- (b,a)=b*(1,r)+k*(0,r)
- so we get this. so we find the shortest vector for that we make use of guassian thoerem hich which gives us the smallest path. 
- the guassian formula which is done by finding the value of m which is found by the dot product and norm . 
- after finding the value of m we find the value of the vectors v1 and v2. we invert in the formula. we keep the smaller value and with the help of m find v2 and then we find the value of a and b who in combination with m will give the value of p and we get the value.

### code
```bash
from Crypto.Util.number import inverse
from hashlib import sha512
from pwn import xor

# -----------------------
# Inputs
# -----------------------

P = int(
    "1cec7c3ff93ca538e71f334e83d905eabd894729a1b515b89dc2392036bc7e5d59f"
    "ad2c35dbb0a8903c8bb2e9cd5e4779a92d3f361eb1ce9fa2530c47881a8719763f"
    "828360138373ffa2ce627f8ccad08e9b5ead178c614f7899adc6a14fa33aa2216c"
    "463a04041e78cffa2c68963c6ff422a076bedd32236282eb3bd1b7ba870a3b1c8"
    "f639cd536cba329b10a6cf7b4ef78bd11052ff8a0d432fb6d3b221742aa1da6914"
    "876e94aca5abdaeef30acdfc90cbc621245ad288a634e8bdf4152ea8ed0062c87"
    "2ace7b4011dc5743fa9c424413f4e3e8fa5c5513fd4a711141f2ef68c01177f78"
    "945db623ac6cc762a6813f11cc278a143ea657bf309e281ef59048a29f279c9a"
    "d8b37f221ac06242f577bba985a2aaec051d95391a9681f905472f4e7d1322da4"
    "92639ee4a5ac776a476cece55f9dfb782c1ef869deed2226691d3157fbb6b1319"
    "68ebfb1fe5bc1e44a158f1e2321c001355cc9cb3344f6b09b78d965a807cd60d5"
    "8a9efbab8c6d4f75c8e5ac7c9cf0e5409b55bb2133129272685913be02166c6bff"
    "e3747ccd186b6c26fc9f09",
    16
)

C = bytes.fromhex(
    "43edcf6275293ce97d716f49875c4bdba37f6ab30f15a53f09b72bf3816edf6b9"
    "2618fb56d569d911b2f6fe7a36d4a854022dddf671dc89b4800bc1605822aab72d3"
)

# -----------------------
# Gauss reduction
# -----------------------

def reduce_gauss(u, v):
    while True:
        if u[0]*u[0] + u[1]*u[1] > v[0]*v[0] + v[1]*v[1]:
            u, v = v, u

        proj = (u[0]*v[0] + u[1]*v[1]) // (u[0]*u[0] + u[1]*u[1])
        if proj == 0:
            return u, v

        v = (v[0] - proj*u[0], v[1] - proj*u[1])

# -----------------------
# Modular root extraction
# -----------------------

e_inv = inverse(51, P - 1)
root = pow((-51) % P, e_inv, P)

# -----------------------
# Build lattice
# (b, a) = b*(1, root) + t*(0, P)
# -----------------------

basis1 = (1, root)
basis2 = (0, P)

w1, w2 = reduce_gauss(basis1, basis2)

# -----------------------
# Recover (a, b)
# -----------------------

for x, y in (w1, w2):
    x, y = abs(x), abs(y)
    if x == 0 or y == 0:
        continue

    if y**51 + 51*x**51 == P:
        a, b = y, x
    elif x**51 + 51*y**51 == P:
        a, b = x, y
    else:
        continue

    print("[+] a =", a)
    print("[+] b =", b)

    k = sha512((str(a) + str(b)).encode()).digest()
    msg = xor(C, k)
    print("[+] FLAG:", msg.decode())
    break

```

