---
layout: single
title: "Redux"
permalink: /Redux/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

\# **Redux is marked deprecated can the developer recommend using Redux toolkit [RTK](/Rtk/){: .btn .btn--info}{:target="\_blank"}**
[Redux Reference](https://redux.js.org/tutorials/fundamentals/part-1-overview){: .btn .btn--info}{:target="\_blank"}

## Example for one state

```
import {createStore} from 'redux';
...

const increment = (value) => {
    return{
        type: 'INCREMENT', //"type" is self-defined, it can be any words
        payload: value
    }
}
const decrement = (value) => {
    return{
        type: 'DECREMENT',
        payload: value
    }
}

const counter = (state = 0; action) => { // initialize state value as 0
     switch(action.type){
        case "INCREMENT":
            return state + 1;
        case "DECREMENT":
            return state - 1;
     }
};

let store= createStore(counter);
```

## Example for 2+ state

```
import {combineReducers} from "redux";
//let there are two defined reducer counterReducer and loggedReducer;
...
const allReducer = combineReducers({
    counter: counterReducer,
    isLogged : loggedReducer
});
let store = createStore(allReducer)

```

When render:

```
<Provider store = {store}>
    <App/>
</Provider>
```

## useSelector

```
import {useSelector} from 'react-redux';
...
const counter = useSelector(state => state.counter); // counter will be the value you want to get
```

## useDispatch

```
import {useDispatch} from 'react-redux;
import {increment} from './actions'; // import actions from outside
...
const onPressIncrement = {() => dispatch(increment(5))};
```
