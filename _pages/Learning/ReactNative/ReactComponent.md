---
layout: single
title: "React Component Lazy Pack"
permalink: /reactnative/component/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

## From HSBC mimic

#### Custom Input

```
import { StatusBar } from "expo-status-bar";
import { TextInput, StyleSheet, Text, View } from "react-native";

export default function CustomInput({ value, setValue, placeholder, secureTextEntry = false}
:{value: string; setValue: any; placeholder: string; secureTextEntry?: boolean;}) {
  const styles = StyleSheet.create({
    container: {
      backgroundColor: "white",
      width: "100%",
      borderColor: "#e8e8e8",
      borderWidth: 1,
      paddingHorizontal: 20,
      paddingVertical: 8,
      marginVertical: 7,
      borderRadius: 5,
    },
  });

  return (
    <View style={styles.container}>
      <TextInput
        value={value}
        onChangeText={setValue}
        placeholder={placeholder}
        secureTextEntry={secureTextEntry}
      ></TextInput>
    </View>
  );
}
```

#### Custom Button

```
import React from "react";
import { TouchableOpacity, Text, StyleSheet } from "react-native";

function CustomButton({ value, onPress }) {
  return (
    <TouchableOpacity onPress={onPress} style={styles.container}>
      <Text style={styles.text}>{value}</Text>
    </TouchableOpacity>
  );
}

const styles = StyleSheet.create({
  container: {
    backgroundColor: "lightblue",
    width: "100%",
    padding: 15,
    marginVertical: 7,
    alignItems: "center",
    borderRadius: 5,
  },
  text: {},
});

export default CustomButton;
```
