---
layout: single
title: "React Native"
permalink: /reactnative/
classes: wide
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
  run `sudo npm i -g expo-cli` &rarr; `expo init //project name//`

After creating project, open the project in vscode. For example `cd //projectName//` and `code .` \
Run `npm start` on terminal, will open a terminal window

#### Option 2 - React Native CLI

## Simulator

#### Android Studio

- SDK Platforms
  - LTS Andriod version
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
| Version | Discribe | Docs
|-|:-|:-
| TouchableWithoutFeedback | Just no visual feedback version | [TouchableWithoutFeedback](https://reactnative.dev/docs/touchablewithoutfeedback){: .btn .btn--info}
| TouchableNavtiveFeedback | Androids only | [TouchableNavtiveFeedback](https://reactnative.dev/docs/touchablenativefeedback){: .btn .btn--info}
| TouchableOpacity | The object will become half transparent for a second when touched | [TouchableOpacity](https://reactnative.dev/docs/touchableopacity){: .btn .btn--info}
| TouchableHighlight | The object will be darken for a second when touched | [TouchableHighlight](https://reactnative.dev/docs/touchablehighlight){: .btn .btn--info}
|---

### Style

|---
| Properties | Example | Explain | Internal link
|-|:-|:-|:-
| width / height | integer | No. of points |
| top / bottom | +- integer | adjust pixels away from |
| left / right | +- integer | adjust pixels away from |
| backgroundColor | color | |
| position | "relative"/ "absolute"
| flex | 1 | | [flex](#flex){: .btn .btn--info}
| flexDirection | "row-reserve" |
| flexGrow | realNumber | = flex: 1
| flexShrink | 1 | = flex: -1
| justifyContent | "center" | Based on main axis
| alignItems | "center" | Based on secondary axis
| alignContent | "center" | All children alignItems
| alignSelf | "center" | Self justifyContent
| flexWrap | "wrap" |
| aspectRatio | 1/1 | constrain it to be squared
| paddingTop | integer
| borderWidth| 1 |
| borderColor | "lightblue"|
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

```
<View style = {style.container}> </View>

const styles = StyleSheet.create({
container: {
//your style properties
},
});

```

##### Special mention

```
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

### React Navigation

Need to install react navigation package
`npm install @react-navigation/native` \
`@react-navigation/bottom-tabs` which create bottom tabs bars \
`@react-navigation/native-stack` which allow you to create a page on top of another page \
`@react-navigation/drawer` which create a pop out sidebar \
`@react-navigation/material-top-tabs react-native-tab-view` which create top tabs and slideshow different tabs

Code Example
Create a tsx file, navigation.tsx for example \
Use a `NavigationContainer` to wrap the contain you wish to have navigation function. Below is a bottom tab example

```
const Tab = createBottomTabNavigator();

function TabGroup() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="TeamBuild" component={TeamBuilding} />
      <Tab.Screen name="TeamBuild2" component={TeamBuilding} />
    </Tab.Navigator>
  );
}

function Navigation() {
  return (
    <NavigationContainer>
      <TabGroup />
    </NavigationContainer>
  );
}

export default Navigation;
```

In the App.tsx, just set up a Navigation Tab

```
export default function App() {
  return (
    <Navigation/>
  );
}
```

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

```
  const oneIetm = ({ item }: { item: ChData }) => <Item item={item} />;

  ...

  const Item = ({ item }: ItemProps) => (
    <View
      style={{
        backgroundColor: "#CCCCCC",
        padding: 10,
        marginVertical: 2,
        marginHorizontal: 4,
        flexDirection: "row",
      }}
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

Make a long list of element scrollable. If item similar items are rendered, it is recommanded to use flatlist

## Reference

[https://www.youtube.com/watch?v=0-S5a0eXPoc](https://www.youtube.com/watch?v=0-S5a0eXPoc){:target="\_blank"}
