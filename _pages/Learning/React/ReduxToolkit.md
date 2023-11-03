---
layout: single
title: "Redux toolkit"
permalink: /Rtk/
classes: wide
sidebar:
  title: "Quick links"
  nav: Programming
---

[reference doc](https://redux-toolkit.js.org/introduction/getting-started){: .btn .btn--info}{:target="\_blank"}

## Install Redux Toolkit

```
npm install @reduxjs/toolkit react-redux
```

For each group of reducer, use createSlice()

```
import { createSlice } from "@reduxjs/toolkit"

export const counterSlice = createSlice({
  name: counter,
  initialState: {
    counter: 0,
    showCounter: False,
  },
  reducers:{
    reducerOne: (state,action) => {
      const input = action.payload.input
    },
    reducerTwo: (state,action) =>{
    },
  }
})

export const {reducerOne, reducerTwo} = counterSlice.actions; // remember to export reducer here

export default counterSlice.reducer;
```

in store.ts,

```
export default configureStore({
  reducer:{
    counter: counterReducer,
  }
})
```

Call reducer
```
import useDispatch from 'react-redux'

const dispatch = useDispatch();

const callReducerOne = (input: text) =>{
  dispatch({input: text})
}
```
or
```
const callReducerOne = (input: text) =>{
  const payload = {
    input: text
  }
  dispatch(payload)
}
```

Get redux state
```
import useSelector from 'react-redux'

const {counter, showCounter} = useSelector((state:any) => state.counter)
```