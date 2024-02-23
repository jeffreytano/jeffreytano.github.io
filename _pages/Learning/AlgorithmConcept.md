---
layout: single
title: "Algorithm Concept"
permalink: /Learning/AlgoConcept/
classes: wide
sidebar:
  nav: Learning
---

### Sliding Windows

Finding max sum in **n**-sized array of consecutive integers in certain **k** size.
Example: in array A = [5, 3, 2, 6, 1, 3] find the max sum in **k** consecutive integers, where k = 3 and n = 6.

Brute force method: 
```
max_sum = 0 // if no negative integer
for i=0: n-1 do:
    temp_max = 0;
    for j=i : i+k-1 do:
        temp_max += A[j]
    max_sum = max(temp_sum,max_sum)
```    
This method use nested for loop that required O(n*k) run time


Sliding Window method: 
```
for i=0: k-1 do
    temp_sum += A[i] // initializing the first combination
max_sum = temp_sum

for j=k: n-1 do
    temp_sum -= A[j-k] += A[j]
    max_sum = max(max_sum,temp_sum)
```
This method does not use nested for loop that only need O(n) run time

In a **n**-sized array find a max length of array in consecutive that the sum of integer is within **k** 
Example: in array A = [5, 3, 2, 6, 1, 3] find the max length in consecutive that sum <= **k**, where k = 9 and n = 6.

Brute force method: 
```
longest_so_far = 0
sum = 0

for i = 0 : n-1 do:
    sum = 0
    temp_length = 0
    for j = i: n-1 do:
        if (sum+A[i] < k):
            break;
        sum += A[i]
        temp_length += 1

    longest_so_far = max(longest_so_far,temp_length)
```

Sliding Window method: 

```
longest_so_far = 0
sum = 0

for i in range(n) do:
   if A[i] > k:
    temp_length = 0
    sum = 0
    continue

    if (sum + A[i]) <= k:
        temp_length +=1
        sum += A[i]
    else:
        sum += A[i]
        temp_length +=1
        while sum > k:
            sum -= A[i-temp_length+1]
            temp_length-=1
    longest_so_far = max(longest_so_far, temp_length)
```