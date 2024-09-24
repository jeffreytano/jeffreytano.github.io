---
layout: single
title: "React Native"
permalink: /reactnative/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

## Set up environment

- Recommended extension
  - Extension: React Native Tools (by microsoft)
  - Extension: React-Native/React/Redux snippets for es6/es7
  - Extension: Prettier
  - Extension: Material Icon Theme

#### Option 1 - Expo CLI

[Expo docs](https://docs.expo.dev/){: .btn .btn--info }{:target="\_blank"}

- Require node ver.12 or higher \
  ```console
  sudo npm i -g expo-cli // which is used to setup expo, no need to run every time \
  expo init //project name//
  ``` 
  or

After creating project, open the project in vscode. For example `cd //projectName//` and `code .` \
Run `npm start` on terminal, will open a terminal window

#### Option 2 - React Native CLI

## Simulator

#### Android Studio

- SDK Platforms
  - LTS Android version
- SDK Tools
  - Android SDK Build-Tools
  - Android Emulator
  - Android SDK Platform-Tools
  - Intel x86 Emulator Accelerator

In Android Studio, `Configure` &rarr; `AVD Manager` &rarr; `Create virtual device`
After install and opening the AVD, press `Run on Android device/emulator` in the terminal window

#### IOS (To be updated)

#### Actual Android phone

Requirement:

- Download **Expo Client** on your phone
- phone is connected in the same network with your computer

Metro Bundle in terminal window and scan the QR code

### Debug on chrome

Too lazy to note it.
I just put the [link with time](https://youtu.be/0-S5a0eXPoc?t=1756){:target="\_blank"} in case I need it later.

### Debug on vscode

this chapter right after the chapter "Debug on chrome"

## React / React Native shortcuts

|---
| shortcuts | Result
|-|:-
| rsf | basic functional component with multicursor enable for editing name
|---

## Fundamental

[React Native API docs](https://reactnative.dev/docs/accessibilityinfo){: .btn .btn--info}{:target="\_blank"} for reference

### SafeAreaView

Only affect on IOS. \
A component that similar to `<View>` but render in safe zone that make sure no content is overlapping the top bar

### Text [docs](https://reactnative.dev/docs/text){: .btn .btn--info}{:target="\_blank"}

|---
| Properties | Example
|-|:-
| numberOfLines | 1
|---

Example: `<Text numberOfLines={1}>`\
Used to limit the number of lines in the text component and trunc the extra text instead of wrapping it

### Image [docs](https://reactnative.dev/docs/image#source){: .btn .btn--info}{:target="\_blank"}

|---
| Properties | Example
|-|:-
| source | source={require("./image.jpg")}/>
|---

Image source

```
<Image source={require("./image.jpg")}/>
```

or

```
<Image source={ width: width, height: height, uri: "outside hyperlink"}/>
```

### Touchable

Wrap components in a Touchable component to apply event triggerer

|---
| Version | Describe | Docs
|-|:-|:-
| TouchableWithoutFeedback | Just no visual feedback version | [TouchableWithoutFeedback](https://reactnative.dev/docs/touchablewithoutfeedback){: .btn .btn--info}{:target="\_blank"}
| TouchableNativeFeedback | Androids only | [TouchableNativeFeedback](https://reactnative.dev/docs/touchablenativefeedback){: .btn .btn--info}{:target="\_blank"}
| TouchableOpacity | The object will become half transparent for a second when touched | [TouchableOpacity](https://reactnative.dev/docs/touchableopacity){: .btn .btn--info}{:target="\_blank"}
| TouchableHighlight | The object will be darken for a second when touched | [TouchableHighlight](https://reactnative.dev/docs/touchablehighlight){: .btn .btn--info}{:target="\_blank"}
|---

### Style and layout [style](https://reactnative.dev/docs/view-style-props){: .btn .btn--info}{:target="\_blank"} [layout](https://reactnative.dev/docs/layout-props){: .btn .btn--info}{:target="\_blank"}

|---
| Properties | Example | Explain | Internal link
|-|:-|:-|:-
| width / height | integer | No. of points |
| top / bottom | +- integer | adjust pixels away from |
| left / right | +- integer | adjust pixels away from |
| backgroundColor | color | |
| position | "relative"/ "absolute"
| flex | 1 | weighting of available space (can be 0.5)| [flex](#flex){: .btn .btn--info}
| flexDirection | "row-reserve" | Adjust main axis (default align items in vertical)
| flexGrow | realNumber | = flex: 1
| flexShrink | 1 | = flex: -1
| justifyContent | "center" | Based on main axis
| alignItems | "center" | Based on secondary axis
| alignContent | "center" | similar to alignItems but applies to all line
| alignSelf | "center" | Self justifyContent
| flexWrap | "nowrap" | Wrap content
| aspectRatio | 1/1 | constrain it to be squared
| borderWidth| 1 |
| borderColor | "lightblue"|
| borderRadius | 5 | make the border rounded edge
| paddingTop / paddingBottom | 20 | padding content text in vertical axis
| paddingLeft / paddingRight | 20 | padding content text in horizontal axis
| paddingHorizontal / paddingVertical | 20 | (padding top + padding bottom) for vertical etc.|
| marginVertical | 10 | keep distance with other object in vertical axis |
|---

<!--
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
-->

#### Code Example

```
<View style={backgroundColor: "orange" }></View>
```

or

```tsx
<View style = {style.container}> </View>

const styles = StyleSheet.create({
container: {
//your style properties
},
});

```

##### Special mention

```tsx
<View style = {[style.container, {backgroundColor: "orange"}]}> </View>

const styles = StyleSheet.create({
container: {
backgroundColor: "#fff",
//your style properties
},
});

```

Here the background color will be orange instead of white, because the style properties on the right will replace same properties on it lefts (like read left properties first)

#### flex

flex take weighting portion of available space

### Hooks

A react native library from react native community \
In the terminal, enter `npm i @react-native-community/hooks`

### Navigation [page](/reactnative/Navigation/){: .btn .btn--info }

### FlatList

```
  <View>
    <FlatList
      data={resultData}
      renderItem={oneCh}
      keyExtractor={(data) => data.id}
    ></FlatList>
  </View>
```

`data` receive array of data \
Example

```
const DATA: ChData[] = [
  {
    id: "1",
    chName: "Kayamori Ruka",
  },
  {
    id: "2",
    chName: "Izumi Yuki",
  },
];
```

`renderItem` receive template for each item \
Example

```tsx
  const oneItem = ({ item }: { item: ChData }) => <Item item={item} />;

  ...

  const Item = ({ item }: ItemProps) => (
    <View
      style= { {
        backgroundColor: "#CCCCCC",
        padding: 10,
        marginVertical: 2,
        marginHorizontal: 4,
        flexDirection: "row",
      } } 
    >
      <Text>
        {item.chName}
      </Text>
    </View>
  );
```

`keyExtractor` just use one properties in FlatList.data given before \
Exmaple

```
keyExtractor={(data) => data.id}
```

### ScrollView

Make a long list of element scrollable. If item similar items are rendered, it is recommended to use flatlist

## Reference

[Basic react tutorial](https://www.youtube.com/watch?v=0-S5a0eXPoc){: .btn .btn--info}{:target="\_blank"} \
[Login tutorial](https://www.youtube.com/watch?v=ALnJLbjI7EY&list=RDCMUCYSa_YLoJokZAwHhlwJntIA&index=2){:target="\_blank"}{: .btn .btn--info} This also inc navigation example \
[Expo Router](https://www.youtube.com/watch?v=yyGS0adZdsU){:target="\_blank"}{: .btn .btn--info}
