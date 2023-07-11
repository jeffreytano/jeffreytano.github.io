---
layout: single
title: "Expo Router in React Native"
permalink: /expoRouter/
classes: wide
sidebar:
  title: "Quick links"
  nav: ReactAndReactNative
---

Here is the offical document [Expo Router docs](https://expo.github.io/router/docs/){: .btn .btn--info}{:target="\_blank"}

## Routing

File based routing. To access other page, use `Link` component from `expo-router`

```
import { Link } from "expo-router";
import { StyleSheet, Text, View } from "react-native";

export default function Page() {
  return (
    <View>
      <View>
        <Link href="/anotherPage?Message=Hello&M2=H">Hello</Link>
      </View>
    </View>
  );
}
```

Where anotherPage.js is place in the same directory with current page (both in app folder)

## Passing parameter

Expo router pass parameter in URL \
Example: `<Link href="/anotherPage?Message=Hello&M2=H">Hello</Link>` \
In href, / + {target} + ? + {item.key} + = + {value}

Example:

```
<Link href={\{
          pathname: "/anotherPage",
          params: {Message: 'Hello',M2: 'H'},
        }\}>Hello</Link>
//ignore the "\"character
```

These two one will render a Text Hello which will redirect to anotherPage with `Message: Hello` and `M2:H` after clicked

## Reference

[Tutorial](https://www.youtube.com/watch?v=yyGS0adZdsU&ab_channel=notJust%E2%80%A4dev){: .btn .btn--info}{:target="\_blank"}
