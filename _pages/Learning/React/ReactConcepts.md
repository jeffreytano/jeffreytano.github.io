---
layout: single
title: "React concepts"
permalink: /reactconcept/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

## Type vs interface

#### Defining syntax

`type` and `interface` have different syntax \
For type

```
type User = {
    userID: string;
    userPassword: string;
}
```

```
interface User{
    userID: string;
}
```

#### type - Union and intersection

type can do union and intersection

```
type Random = {
    Animal: 'Dog' | 'Cat'
    anything : string | number | boolean
}
```

Usage:

#### interface - Declaration merging

interface User{
name: string
}

interface User{
balance: number
}

const Me: User = {
name: "Jeffrey",
balance: 0,
}

## Promise [reference](https://javascript.info/promise-basics){: .btn .btn--info}{:target="\_blank"}
