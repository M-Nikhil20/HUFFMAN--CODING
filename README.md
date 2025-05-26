# Huffman-Coding

## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7 (or any Python 3.x environment)

## Algorithm:
### Step1:
Get the input string that you want to compress.

### Step2:
Calculate the frequency of each character in the input string.

### Step3:
Create leaf nodes for each character along with their frequency.

### Step4:
Build the Huffman tree by repeatedly combining the two nodes with the smallest frequencies until only one tree remains.

### Step5:
Generate Huffman codes by traversing the tree — assign '0' for left edge and '1' for right edge, building codes for each character.

---

## Program:

```python
input_string = "huffman coding"

frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

nodes = [[char, freq] for char, freq in frequency.items()]

while len(nodes) > 1:
    nodes = sorted(nodes, key=lambda x: x[1])
    left = nodes.pop(0)
    right = nodes.pop(0)
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

huffman_tree = nodes[0]

huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

## Output: 

![image](https://github.com/user-attachments/assets/75f9792e-d77d-4519-a6b5-dd2c3a8a6db0)

## Result:
Thus, Huffman coding was implemented to compress the data using Python programming.
