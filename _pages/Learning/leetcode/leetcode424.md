---
layout: single
title: "Longest Repeating Character Replacement (424 - Medium)"
permalink: /Learning/leetcode/424
classes: wide
sidebar:
  nav: Learning
---

##### Intro

Leetcode problem 424 - [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/description/){: .btn .btn--info}{:target="\_blank"}

Define a function `check_alphabet` to check the longest range found in `s` for the target character.

Let take Case 2 as example

```
s = "AABABBA"
k =1
```

##### check_alphabet

Take character 'A' as target

find the index in `s` which is not matching the **target** 'A' and store it into `indexes`

Add index -1 and len(s) as the **imaginary non-matching character** to bound the `indexes`

So, for target = 'A', we will get indexes = \[-1,2,4,5,7\]

if there are less or equal number of indexes than **k**, which mean all non-matching character can be replaced. So we just return the length of `s`

we start scanning with fixing window size,

k = 1, so we start from replacing the first k indexes, the 'B' in index 2.

If we fill the 'B' in index 2, we would like to get the distance after we filled it into 'AAAABBA'
We count it by taking offset from the filling charcters, so we use rear as the adj. left side index -1, and front as the adj. right side index 4. From indexes \[_-1_,**2**,_4_,5,7]
and we count the distance 4-(-1) +1 = 6 and reduct the front and rear itself 6-2 = 4

And we store the `longest_so_far` until the front reach the end of indexes 7

And we will get result

front = 4, rear = -1, 4-(-1)+1-2 = 4
front = 5, rear = 2, 5-2+1-2 = 2
front = 7, rear = 4, 7-4+1-2 = 2

so the check_alphabet('A','AABABBA') will return 4 that mean we will the longest repeating 'A' in s will be 4

##### characterReplacement(main)

And we just call the function `check_alphabet()` from 'A' to 'Z'
and return the largest result

### My solution

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        def check_alphabet(target:str, s:str) -> int:
            longest_so_far = 0
            indexes = [-1]
            for index in range(len(s)):
                if s[index] != target:
                    indexes.append(index)
            indexes.append(len(s))
            # print(target,indexes)

            if (k >=len(indexes)-2):
                return len(s)
            for i in range(k+2,len(indexes)+1):
                rear = indexes[i-k-2]
                front = indexes[i-1]
                distance = front-rear-1
                # if longest_so_far < distance:
                print(target,i-k-2,i-1,rear,front,distance)
                longest_so_far = max(distance,longest_so_far)
            return longest_so_far
        longest = 0
        for char in string.ascii_uppercase:
            longest = max(check_alphabet(target = char,s = s),longest)
        return longest
```
