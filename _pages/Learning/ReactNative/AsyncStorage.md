---
layout: single
title: "AsyncStorage"
permalink: /asyst/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---
Use AsyncStorage to read, write, download data from the internet


Read file from local storage
```typescript
import AsyncStorage from "@react-native-async-storage/async-storage";

...

const readFile = async (key: string) => {
    try {
        const jsonValue = await AsyncStorage.getItem(key);
        if (jsonValue !== null) {
            const data = JSON.parse(jsonValue);
            console.log(data.CharacterData[1].baseStat);
            // Use the data as needed
        }
    } catch (error) {
        console.log(error);
    }
};
```

Write file to local storage
```typescript
import AsyncStorage from "@react-native-async-storage/async-storage";

...

const writeFile = async (data: string,key:string) => {
    try {
        const jsonValue = JSON.stringify(data);
        await AsyncStorage.setItem(key, jsonValue);
    } catch (error) {
        console.log(error);
    }
};
```

Download file with axios
```typescript
import AsyncStorage from "@react-native-async-storage/async-storage";
import axios from "axios";

...

async function downloadAndSaveJSON() {
    try {
        // Make an HTTP GET request to the URL that contains the JSON data
        const response = await axios.get(
            "https://jeffreytano.github.io/image/CharacterDataBase.json"
        );

        // Extract the JSON content from the response
        const jsonContent = response.data;
        console.log(jsonContent);
        // Save the JSON content using AsyncStorage
        await AsyncStorage.setItem("jsonData", JSON.stringify(jsonContent));

        console.log("JSON content saved successfully!");
    } catch (error) {
        console.error("Error downloading and saving JSON:", error);
    }
}
```