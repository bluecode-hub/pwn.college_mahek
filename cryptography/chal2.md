# chal2
when we normally run the programm it will run littl and show killed because it is running out of memory it has a complexity of o(3^n) which is huge memory storage it runs fibonacci series so we need to find out some other optimised way thay gives the same answer but optimises the process and the process is  not killed before the complete run of the programme

## flag
 CSCTF{2441d2f22fa1d5b9fc0a850dcfbbccf608cafbc22a1beaae0ac328ff6d218781}
 
## solve
```bash
from out import enc, R
from math import prod

def a_val(n):
    s = 0
    while n:
        s += n % 3
        n //= 3
    return s

flag = ''
for k in range(len(enc)):
    indices = R[k]
    p = prod(a_val(idx) for idx in indices)
    flag += chr(enc[k] ^ p)

print("FLAG:", flag)


```

- we run the base 3 of the programme that yields the same value but optimised and that gives the flag.
- when we run the code we find that its a fibonacci series and each time the array gets added and increases in length. it increases the length each time and stores in memory
- so we need to find a solution that does the same thing but in lesser space complexity
