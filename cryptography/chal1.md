# Chal1
cypher
so the given code they xorred it so i read that i we xor we need to xor it again to decrypt it according to the cypher algo that i read.
this uses a cypher algorithm where we see the flag was xored to encrupt it do we dexor it to decrypt it 
## Flag
flaggg{w0w_g0od_j0b_V3ry_gr34t_amazing_AW35OMEE}

## Solve
```bash
from itertools import cycle
key=b"djpakoda"
with open("ct","rb") as f:
    ct=f.read()
pt=bytes(x^y for x,y in zip(ct,cycle(key)))
print(pt)

```
#Reference
None

