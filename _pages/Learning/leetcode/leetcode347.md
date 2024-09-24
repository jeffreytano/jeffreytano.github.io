---
layout: single
title: "Top K Frequent Elements (347 - Medium)"
permalink: /Learning/leetcode/347
classes: wide
sidebar:
  nav: Learning
---

##### Intro

Leetcode problem 347 - [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/){: .btn .btn--info}{:target="\_blank"}

##### topKFrequent(main)

Note the frequency of num in a dictionary that key = the num in nums, value = the frequency
At the same time, we record the maximum frequency as `max_so_far` for further use.

Keep the while loop going on if we are not fulfilled

```
while fulfilled <k:
```

loop through each item in the dictionary, if the key equals to `max_so_far`, it means it is only of the most frequent value and it must be in the answer since answer is guaranteed to be unique.

if we don't get the full ans after we finish looping through the dict, it means the answer included numbers that frequency is not at max, so we reduce the max_so_far by 1 and do it again until we meet were target number of answer

### My solution

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        dt= dict()
        max_so_far=1
        for num in nums:
            if num in dt:
                dt[num]+=1
                max_so_far=max(dt[num],max_so_far)
            else:
                dt[num]=1

        fulfilled = 0
        ans = []
        while fulfilled<k:
            for key in dt:
                if dt[key] == max_so_far:
                    ans.append(key)
                    fulfilled +=1
                if fulfilled == k:
                    break
            max_so_far-=1
        return ans
```
