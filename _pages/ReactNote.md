---
layout: single
title: "React notes"
permalink: /reactnote/
---

### React notes
go through the tutorial in [Old Reactdev](https://legacy.reactjs.org/tutorial/tutorial.html){:target="_blank"} or [Reactdev](https://react.dev/learn){:target="_blank"}

[React Useful](/reactuseful/){: .btn .btn--primary}

Links to different topics:\
[React component](#an-example-for-a-react-component){: .btn .btn--info}
[Calling component](#to-call-a-component-defined-by-yourself){: .btn .btn--info}
[Constructor and state](#constructor-of-objects-and-state){: .btn .btn--info}
[Conditional rendering](#conditional-rendering){: .btn .btn--info}
[Mapping](#mapping){: .btn .btn--info}
[Hook](#hook){: .btn .btn--info}
[interface in typescript](#interface-in-typescript){: .btn .btn--info}

<!-- [React component](#an-example-for-a-react-component)\ -->
<!-- [Calling component](#to-call-a-component-defined-by-yourself)\
[Constructor and state](#constructor-of-objects-and-state)\
[Conditional rendering](#conditional-rendering) -->

## Running a localhost web server
go to the directory of the project and `npm run dev`

## An example for a react component
```
class Square extends React.Component {
  render() {
    return (
      <button className="square"
      </button>
    );
  }
}
```

Explaination: Class 'Square' is extending the class React.component and return html codes `<button class = "sqaure"> </button>`

## To call a component defined by yourself
```
class Board extends React.Component {
  renderSquare(i) {
    return <Square/>;
  }
```
Just call <Square/> if you defined a class **Square**

## Constructor of objects and state
```
class Square extends React.Component {
  constructor(props){
    super(props);
    this.state = { value: null, };
  }
}
```
In the constructor of a object, you may set state by editing `this.state` by it dictionary key like `value : null`

To retrieve the state value, just call `this.state.value`, note that you can define state value by self-defined key like the following
```
class Board extends React.Component {

constructor(props){
  super(props);
  this.state = {
    squares: Array(9).fill(null),
    P1: true,
  };
}
```
The value can be array and boolean too.

React component names must start with **capitial letter**, while HTML tag must be **lowercase**.

## Conditional rendering
```
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
```
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```
if your no need the else statement, this also work
```
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```

## Mapping
```
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
In a react component  `ListGroup()` for example
```
function ListGroup(){
  const [selectedIndex, setSelectedIndex] = useState(-1); 
  //-1 being default refers to no selected item
  return(....)
  }
````
another example `const [name, setName] = useState('');`

## interface in typescript
You can define data structure with interface keywork. Exmaple:
```
interface Props(){
  items: string[];
  title: string;
  onSelectItem: (item:string) => void; 
  // a function takes string and return void
}
```
To call interface in a tag
```
let items = ["Kayamori","IZumi","Asakura"]
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
