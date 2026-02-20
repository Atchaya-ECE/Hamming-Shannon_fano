# Huffman-Shannon_fano
# Aim:
Consider a discrete memoryless source with symbols and statistics {0.125, 0.0625, 0.25, 0.0625, 0.125, 0.125, 0.25} for its output. 
Apply the Huffman and Shannon-Fano to this source. 
Show that by drawing the tree diagram, and 
Calculate the average code word length, entropy, variance, redundancy, and efficiency.
# Tools Required:
    * Google collab with computer
# Program:
# HUFFMAN CODING
```
# ==========================
# HUFFMAN CODING (Fixed Order Output)
# ==========================

import heapq
import math

# -------- Fixed Input --------
symbols = ['A','B','C','D','E','F','G']
probabilities = [0.125,0.0625,0.25,0.0625,0.125,0.125,0.25]

n = len(symbols)

# -------- Huffman Node --------
class Node:
    def __init__(self, prob, symbol=None, left=None, right=None):
        self.prob = prob
        self.symbol = symbol
        self.left = left
        self.right = right

    def __lt__(self, other):
        return self.prob < other.prob

# -------- Build Tree --------
heap = []
for i in range(n):
    heapq.heappush(heap, Node(probabilities[i], symbols[i]))

while len(heap) > 1:
    left = heapq.heappop(heap)
    right = heapq.heappop(heap)
    merged = Node(left.prob + right.prob, None, left, right)
    heapq.heappush(heap, merged)

root = heap[0]

# -------- Generate Codes --------
codes = {}

def generate_codes(node, code=""):
    if node.symbol is not None:
        codes[node.symbol] = code
        return
    generate_codes(node.left, code + "0")
    generate_codes(node.right, code + "1")

generate_codes(root)

# -------- Sort by Probability (Descending) --------
data = list(zip(symbols, probabilities))
data.sort(key=lambda x: x[1], reverse=True)

print("Huffman Codes:\n")
for sym, prob in data:
    print(f"{sym} : {codes[sym]}")

# -------- Calculations --------
L = 0
H = 0
var = 0

for sym, prob in data:
    length = len(codes[sym])
    L += prob * length
    H += prob * math.log2(1/prob)

for sym, prob in data:
    length = len(codes[sym])
    var += prob * (length - L)**2

L = round(L,3)
H = round(H,3)
eff = round(H/L,3)
red = round(1-eff,3)
var = round(var,3)

print("\nAverage Codeword Length:", L)
print("Entropy:", H)
print("Efficiency:", eff)
print("Redundancy:", red)
print("Variance:", var)
```
# Calculation:
```
Compare the manually calculated value and the observed practical value.
```
# Output
# HUFFMAN CODING
```
<img width="395" height="346" alt="image" src="https://github.com/user-attachments/assets/575f5ee0-bf1b-4988-8f75-f44f98ad31ab" />
```


# Results:

