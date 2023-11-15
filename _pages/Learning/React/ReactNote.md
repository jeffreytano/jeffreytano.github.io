---
layout: single
title: "React notes"
permalink: /reactnote/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

go through the tutorial in [Old Reactdev](https://legacy.reactjs.org/tutorial/tutorial.html){: .btn .btn--info}{:target="\_blank"} or [Reactdev](https://react.dev/learn){: .btn .btn--info}{:target="\_blank"}

Links to different topics:\
[React component](#an-example-for-a-react-component){: .btn .btn--info} \
[Calling component](#to-call-a-component-defined-by-yourself){: .btn .btn--info} \
[Constructor and state](#constructor-of-objects-and-state){: .btn .btn--info} \
[Conditional rendering](#conditional-rendering){: .btn .btn--info} \
[Mapping](#mapping){: .btn .btn--info} \
[Hook](#hook){: .btn .btn--info} \
[interface](#interface){: .btn .btn--info}

## Running a localhost web server

go to the directory of the project and `npm run dev`

## An example for a react component

```tsx
class Square extends React.Component {
  render() {
    return (
      <button className="square"/>
    );
  }
}
```

Explanation: Class 'Square' is extending the class React.component and return html codes `<button class = "square"> </button>`

## To call a component defined by yourself

```tsx
class Board extends React.Component {
  renderSquare(i) {
    return <Square/>;
  }
}
```

Just call <Square/> if you defined a class **Square**

## Constructor of objects and state

```tsx
class Square extends React.Component {
  constructor(props){
    super(props);
    this.state = { value: null, };
  }
}
```

In the constructor of a object, you may set state by editing `this.state` by it dictionary key like `value : null`

To retrieve the state value, just call `this.state.value`, note that you can define state value by self-defined key like the following

```tsx
class Board extends React.Component {

  constructor(props){
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      P1: true,
    };
  }
}
```

The value can be array and boolean too.

React component names must start with **capital letter**, while HTML tag must be **lowercase**.

## Conditional rendering

```tsx
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```

or

```tsx
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```

if your no need the else statement, this also work

```tsx
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```

## Mapping

```tsx
function ListGroup() {
  const items = [
    "Kayamori Ruka",
    "Izumi Yuki",
    "Asakura Karen",
    "Toujo Tsukasa",
    "Aikawa Megumi",
    "Kunimi Tama",
  ];
  return (
    <>
      <h1>31A </h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
```

Use `array.map( (i) => (<li>{i}</li> )` to map each item in the array to generate array.size number of list item
Addition: `array.map( (item,index) => (<li>{index}: {item}</li> )` can also return index in mapping

## Hook

useState return an array that contains one value and one function
In a react component `ListGroup()` for example

```tsx
function ListGroup(){
  const [selectedIndex, setSelectedIndex] = useState(-1);
  //-1 being default refers to no selected item
  return(....)
}
```

another example `const [name, setName] = useState('');`

## interface

You can define data structure with interface keyword. Example:

```tsx
interface Props(){
  items: string[];
  title: string;
  onSelectItem: (item:string) => void;
  // a function takes string and return void
}
```

To call interface in a tag

```tsx
let items = ["Kayamori","Izumi","Asakura"]
let title = "31A"
const handleSelectItem = (item: string) => {
  console.log(item);
}

<ListGroup
  items={items}
  title={title}
  onSelectItem={handleSelectItem}
  />
```

## props

Use dropdown list as an example
Remember you take interface props in the function input arg but assign the value when you call the tag

```tsx
function DropdownItem(props){
  return(
    <li className = 'dropdownItem'>
      <img src={props.img} />
      <a> {props.text} />
    </li>
  );
 }

 // In the dropdown List component
 ....
 <DropdownItem img = {itemimg[0]} text = {text[0]}/>
```

## React useful

### tldr

```tsx
import {Fragment} from "react";
```

### Fragment

use `<Fragment> <Fragment/>` or `<> </>` to wrap more than one element in react components

### Styled-components

A way to applies reusable style.

```tsx
import styled from  "styled-component";

...

const Title = styled h1` 
font-size: 1.5em;
text-align: center:
color: #BF4F74;
`
//which create a h1 tag named "Title" with followed style

render(
  <Title>
  Hello
  </Title>
)
```

Used for h1, div, button etc.
style.div have same meaning with style("div)

### useEffect

**useEffect(function, dependency?)** \
useEffect trigger a function when render, if dependency is null, it is triggered every render. If dependency exist, it only rerender when the dependency changes.

Example:

```tsx
useEffect(() => {
  //Runs on every render
});
```

```tsx
useEffect(() => {
  //Runs only on the first render
}, []);
```

```tsx
useEffect(() => {
  //Runs on the first render
  //And any time any dependency value changes
}, [prop, state]); // dependency can be single var / array
```
