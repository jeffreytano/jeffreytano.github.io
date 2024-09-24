---
layout: single
title: "Navigation"
permalink: /reactnative/Navigation/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

## React Navigation

Need to install react navigation package
`npm install @react-navigation/native` \
`@react-navigation/bottom-tabs` which create bottom tabs bars \
`@react-navigation/native-stack` which allow you to create a page on top of another page \
`@react-navigation/drawer` which create a pop out sidebar \
`@react-navigation/material-top-tabs react-native-tab-view` which create top tabs and slideshow different tabs

Code Example
Create a tsx file, navigation.tsx for example \
Use a `NavigationContainer` to wrap the contain you wish to have navigation function. Below is a bottom tab example

```tsx
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

```tsx
export default function App() {
  return (
    <Navigation/>
  );
}
```

### Stack navigation

Render pages on top of the previous pages like stacks, pop pages from the stack when back.
