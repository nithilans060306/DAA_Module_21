# EX 3D Pattern Matching
## DATE: 15/04/2025
## AIM: To write a python program to implement pattern matching on the given string using Brute Force algorithm.



## Algorithm:

1. **Input**
   - Read two strings:
     - `s1` → the main text string.
     - `s2` → the pattern string to search within `s1`.

2. **Initialize Pointers**
   - Set two pointers: `i = 0` for traversing `s1`, and `j = 0` for traversing `s2`.

3. **Start Matching**
   - While both pointers are within bounds:
     - If `s1[i] == s2[j]`:
       - Move both `i` and `j` one step forward.
     - Else:
       - Reset `i` to `i - j + 1` (start checking from next position in `s1`).
       - Reset `j = 0` (start checking `s2` from beginning).

4. **Check for Match Completion**
   - If `j == len(s2)`, all characters in `s2` matched — return the starting index: `i - j`.

5. **If Not Found**
   - If loop ends without full match, return `-1`.

6. **Output**
   - Print the result which is the index where `s2` first occurs in `s1`, or `-1` if not found.
 

## Program:
```python
/*
Program to implement the Pattern Matching.
Developed by: Nithilan S
Register Number: 212223240108
*/
def BF(s1,s2):
##############  Add your code here #############
    i = j = 0
    while(i < len(s1) and j < len(s2)):
        if (s1[i] == s2[j]):
            i += 1
            j += 1
        else:
            i = i - j + 1
            j = 0
    if (j >= len(s2)):
        return i - j
    else:
        return -1
        
if __name__ == "__main__":
    a1=input() 
    a2=input() 
    b=BF(a1,a2)
    print(b)

```

## Output:
![image](https://github.com/user-attachments/assets/d8ef0390-4b89-4b41-b51a-ecae00c14e4f)



## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
