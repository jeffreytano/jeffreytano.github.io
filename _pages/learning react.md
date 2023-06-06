---
layout: single
title: "Learning React"
permalink: /Reactnote/
---

### React notes
go through the tutorial in [Old Reactdev](https://legacy.reactjs.org/tutorial/tutorial.html) or [Reactdev](https://react.dev/learn)

##An example for a react component

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

##To call a component defined by yourself
```
class Board extends React.Component {
  renderSquare(i) {
    return <Square/>;
  }
```
Just call <Square/> if you defined a class **Square**

## Constructor of objects
```
class Square extends React.Component {
  constructor(props){
    super(props);
    this.state = { value: null, };
  }
}
```
In the constructor of a object, you may set state by editing `this.state` by it dictionary key like `value : null`

To retrieve the state value, just call `this.state.value'`, note that you can define state value by self-defined key like
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
