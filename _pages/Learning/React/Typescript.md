---
layout: single
title: "Typescript syntax"
permalink: /learning/typescript
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

### Array operation
- Array.filter ⇒ Filter array, only reserve element in `Array` that condition inside \(\) is TRUE

```typescript
const name = ['Sotheby','Druvis III', 'Sonetto', 'Vertin'];
const result = words.filter((word) => word.length == 7);
// Expected result: Array ["Sotheby", "Sonetto"]
```

- Array.reduce ⇒ Do operation along all elements and return a single value

```typescript
const array1 = [1, 2, 3, 4];    
// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
    (accumulator, currentValue) => accumulator + currentValue,
    initialValue,
);
console.log(sumWithInitial);
// Expected output: 10
```