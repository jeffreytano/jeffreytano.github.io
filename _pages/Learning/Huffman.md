---
layout: single
title: "Huffman Coding"
permalink: /Learning/Huffman/
classes: wide
sidebar:
  nav: Learning
---

Huffman coding is a data compression technique that optimize numbers of bit to be assigned for data.

Typically, if you need to assign bits for 4 items, let say A, B, C, D, E, F, G and H. The most straight forward method is like:

000<sub>2</sub> : A \
001<sub>2</sub> : B \
010<sub>2</sub> : C \
011<sub>2</sub> : D \
100<sub>2</sub> : E \
101<sub>2</sub> : F \
100<sub>2</sub> : G \
111<sub>2</sub> : H

Which like assigning 4 ID number for which item. \
0 - 000<sub>2</sub> \
1 - 001<sub>2</sub> \
2 - 010<sub>2</sub> \
3 - 011<sub>2</sub> \
4 - 100<sub>2</sub> \
5 - 101<sub>2</sub> \
6 - 110<sub>2</sub> \
7 - 111<sub>2</sub> \
Which is also the most optimal way if the frequency of all symbol is the same. \
Like if all of them only appear 2 twice, the usage of bit size is 2 \* 3 \* 8 = 48 bits

But, talking about an extreme case like A and H only appear 1 times, B and G appear 3 times, C and F only appear 6 times, D and E appear 9 times. \
If we keep using the method above, we will use up to ( 1 + 3 + 6 + 9 ) \* 3 \* 2 = 114 bits. \
This sounds reasonable but not really the optimal way to commit.

①In huffman coding, we need to first count the frequency of appear for all items, which is already provided

| **Symbol** | A | B | C | D | E | F | G | H
|:-
| **Frequency** | 1 | 3 | 6 | 9 | 9 | 6 | 3 | 1

②And then sort it. This is the first level of the tree

| **Symbol** | A | H | B | G | C | F | D | E
|:-
| **Frequency** | 1 | 1 | 3 | 3 | 6 | 6 | 9 | 9

③Take the smallest 2 item and group them in a pair of two, so A - H groups

| **Groups** | A - H | B | G | C | F | D | E
|:-
| **Frequency** | 2 | 3 | 3 | 6 | 6 | 9 | 9

Keep repeat ③ until all of the items are grouped \
A - H and B are the smallest, so A - H and B groups

| **Groups** | A - H = B | G | C | F | D | E
|:-
| **Frequency** | 5 | 3 | 6 | 6 | 9 | 9

A - H = B and G are the smallest, so A - H = B and G groups

| **Groups** | G ~ A - H = B| C | F | D | E
|:-
| **Frequency** | 8 | 6 | 6 | 9 | 9

C and F are the smallest, so C and F groups

| **Groups** | G ~ A - H = B | C - F | D | E
|:-
| **Frequency** | 8 | 12 | 9 | 9

G ~ A - H = B and D are the smallest, so G ~ A - H = B and D groups

| **Groups** | G ~ A - H = B ≅ D | C - F | E |
|:-
| **Frequency** | 17 | 12 | 9 |

E and C - F are the smallest, E and C - F groups

| **Groups** | G ~ A - H = B ≅ D | E = C - F |
|:-
| **Frequency** | 17 | 21

Finally, the 2 group can group together.

Then from top to down, we deform and assign 0 / 1 to the groups (here we set 0 for smaller and 1 for larger)

| **Groups** | G ~ A - H = B ≅ D | E = C - F |
|:-
| **Frequency** | 17 | 21
| **assign** | **0** | **1**

| **Groups** | G ~ A - H = B | D | E | C - F |
|:-
| **Frequency** | 8 | 9 | 9 | 12
| **assign** | 0**0** | 0**1** | 1**0** | 1**1**

| **Groups** | G | A - H = B | D | E | C | F |
|:-
| **Frequency** | 3 | 5 | 9 | 9 | 6 | 6
| **assign** | 00**0** | 00**1** | 01 | 10 | 11**0** | 11**1**

| **Groups** | G | A - H | B | D | E | C | F |
|:-
| **Frequency** | 3 | 2 | 3 | 9 | 9 | 6 | 6
| **assign** | 000 | 001**0** | 001**1** | 01 | 10 | 110 | 111

| **Groups** | G | A | H | B | D | E | C | F |
|:-
| **Frequency** | 3 | 1 | 1 | 3 | 9 | 9 | 6 | 6
| **assign** | 000 | 0010**0** | 0010**1** | 0011 | 01 | 10 | 110 | 111

Rearrange them in frequency order

| **Groups** | A | H | G | B | C | F | D | E |
|:-
| **Frequency** | 1 | 1 | 3 | 3 | 6 | 6 | 9 | 9
| **assign** | 00100 | 00101 | 000 | 0011 | 110 | 111| 01 | 10

You can see the most frequently appeared items are assign with fewer digit and least appear item are assigned with more digit.
In calculation, the space usage will be \
5 \* 1 \* 2 (for A,H) + 3 \* 3 (for G) + 4 \* 3 (for B) + 3 \* 6 \* 2 (for C,F) + 2 \* 9 \* 2 (for D,E) = 103 bits \
which is more efficient than the straight forward method that use 114 bits.

It might look not big deal, but the difference with be larger when the scale become larger
