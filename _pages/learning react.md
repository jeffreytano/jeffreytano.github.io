---
layout: single
title: "Learning React"
permalink: /reactnote/
---

### React notes
go through the tutorial in [Old Reactdev](https://legacy.reactjs.org/tutorial/tutorial.html) or [Reactdev](https://react.dev/learn)

Links to different topics:\
[React component](#an-example-for-a-react-component){: .btn}
[Calling component](#to-call-a-component-defined-by-yourself){: .btn}
[Constructor and state](#constructor-of-objects-and-state){: .btn}
[Conditional rendering](#conditional-rendering){: .btn}

<!-- [React component](#an-example-for-a-react-component)\ -->
<!-- [Calling component](#to-call-a-component-defined-by-yourself)\
[Constructor and state](#constructor-of-objects-and-state)\
[Conditional rendering](#conditional-rendering) -->

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

