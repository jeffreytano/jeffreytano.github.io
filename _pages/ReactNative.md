---
layout: single
title: "React Native"
permalink: /reactnative/
---
### Set up environment

- Recommanded extension
  -  Extension: React Native Tools (by microsoft)
  -  Extension: React-Native/React/Redux snippets for es6/es7
  -  Extension: Prettier
  -  Extension: Material Icon Theme
  
### Option 1 - Expo CLI
[Expo docs](https://docs.expo.dev/){.btn .btn--info} for reference

- Require node ver.12 or higher \ run
`sudo npm i -g expo-cli` 

`expo init //project name//`

After creating project, open the project in vscode. For example `cd //projectName//` and `code .`

Run `npm start` on terminal, will open a terminal window

### Option 2 - React Native CLI

### Simulator
#### Android Studio
- SDK Platforms
  - LTS Andriod version
- SDK Tools
  -  Android SDK Build-Tools
  -  Android Emulator
  -  Android SDK Platform-Tools
  -  Intel x86 Emulator Accelerator

In Android Studio,  `Configure` &rarr; `AVD Manager` &rarr; `Create virtual device`
After install and opening the AVD, press `Run on Android device/emulator` in the terminal window
# IOS (To be updated)

#### Actual Android phone
Require
- Download **Expo Client** on your phone
- phone is connected in the same network with your computer

Metro Bundle in terminal window and scan the QR code

### Debug on chrome
Too lazy to note it. 
I just put the [link with time](https://youtu.be/0-S5a0eXPoc?t=1756) in case I need it later. 

Debug on vscode chapter right after the chapter "Debug on chrome"

## Fundamental
[React Native API docs](https://reactnative.dev/docs/accessibilityinfo){.btn .btn--info} for reference

### SafeAreaView
A component that similar to `<View>` but render in safe zone that make sure no content is overlapping the top bar

### [Text](https://reactnative.dev/docs/text)
#### [numberOfLines](https://reactnative.dev/docs/text#numberoflines)
Example: `<Text numberOfLines={1}>`\ 
Used to limit the number of lines in the text component and trunc the extra text instead of wrapping it

### [Image](https://reactnative.dev/docs/image#source)
#### source
Image source
`<Image source={require("./image.jpg"}/>`\
or\
`<Image source={{ width: width, height: height, uri: "outside hyperlink"}}/>`

### Touchable
Wrap components in a Touchable component to apply event triggerer
#### [TouchableWithoutFeedback](https://reactnative.dev/docs/touchablewithoutfeedback)
Just no visual feedback version

#### [TouchableNavtiveFreedback](https://reactnative.dev/docs/touchablenativefeedback)
Androids only

#### [TouchableOpacity](https://reactnative.dev/docs/touchableopacity)
The object will become half transparent for a second when touched

#### [TouchableHightlight](https://reactnative.dev/docs/touchablehighlight)
The object will be darken for a second when touched

### Style
|---
|Properties|  Example | 
|-|:-|
|width  |  200 |
|height |  200 |
|backgroundColor |  "blue" |
|flex   |   |
|alignItems   |   |
|justifyContent   |   
|---

|---
| Default aligned | Left aligned | Center aligned | Right aligned
|-|:-|:-:|-:
| First body part | Second cell | Third cell | fourth cell
| Second line |foo | **strong** | baz
| Third line |quux | baz | bar
|---
| Second body
| 2 line
|===
| Footer row

`<View style={{width: width, height: height, backgroundColor: {color}}}></View>`\
or\
``` <View style = {style.container}> </View>

const styles = StyleSheet.create({
  container: {
  },
});
```


## Reference
https://www.youtube.com/watch?v=0-S5a0eXPoc
