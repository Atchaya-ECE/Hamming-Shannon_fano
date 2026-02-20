# Huffman-Shannon_fano
# Aim:
Consider a discrete memoryless source with symbols and statistics {0.125, 0.0625, 0.25, 0.0625, 0.125, 0.125, 0.25} for its output. 
Apply the Huffman and Shannon-Fano to this source. 
Show that by drawing the tree diagram, and 
Calculate the average code word length, entropy, variance, redundancy, and efficiency.
# Tools Required:
Python IDE with Numpy and Scipy.
# Program:
```
import numpy as np
import math 
L  = 0
hs = 0
p = []
lk = []
n = int(input("Enter the number of Samples : "))
for i in range (n): 
    pr = float(input(f"Enter the probability of sample values {i + 1}: "))  
    p.append(pr)
for j in range (n): 
    l = float(input(f"Enter the length of the sample values {j + 1}: "))  
    lk.append(l)
# Avg length of the code word
for k in range (n):
    Avg1 = p[k] * lk[k]
    L = L + Avg1
# Entropy
for k in range (n):
    e = p[k] * math.log(1 / p[k], 2)
    hs = hs + e
hs = round(hs,3)
# Efficiency
eff =  hs / L
eff = round(eff,3)
# Redundancy 
red =  round(1 - eff,3) 
# Variance
var = 0
for k in range(n):
    var1 = p[k] * (lk[k]-L)**2
    var = var + var1
var = round(var,3)
print(f"Average Codeword Length is : {L}")
print(f"Entropy is : {hs}")
print(f"Efficiency is : {eff}")
print(f"Redudancy is : {red}")
print(f"Variance is : {var}")
```
# Calculation:
<img width="1070" height="1600" alt="image" src="https://github.com/user-attachments/assets/53407a87-806b-4c22-949c-4b71d34912a9" />

<img width="1138" height="1600" alt="image" src="https://github.com/user-attachments/assets/1f1f2074-6cf4-4cd5-9583-4d0b69b39f6c" />

# Output
```
Enter the number of Samples : 7
Enter the probability of sample values 1: 0.25
Enter the probability of sample values 2: 0.25
Enter the probability of sample values 3: 0.125
Enter the probability of sample values 4: 0.125
Enter the probability of sample values 5: 0.125
Enter the probability of sample values 6: 0.0625
Enter the probability of sample values 7: 0.0625
Enter the length of the sample values 1: 2
Enter the length of the sample values 2: 2
Enter the length of the sample values 3: 3
Enter the length of the sample values 4: 3
Enter the length of the sample values 5: 3
Enter the length of the sample values 6: 4
Enter the length of the sample values 7: 4
Average Codeword Length is : 2.625
Entropy is : 2.625
Efficiency is : 1.0
Redudancy is : 0.0
Variance is : 0.484
```
# Results:

For the given discrete memoryless source with probabilities
{0.125,0.0625,0.25,0.0625,0.125,0.125,0.25}, both Huffman and Shannon–
Fano coding were applied. The simulation was carried out in Python
(Google Colab). Since the source probabilities are exact powers of
two, the codeword lengths match the ideal values, giving zero
redundancy and 100% coding efficiency. Both Huffman and Shannon–Fano
yield identical results.
