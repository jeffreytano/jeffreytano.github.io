---
layout: single
title: "Rust"
permalink: /learning/rustEnv
classes: wide
sidebar:
  nav: Programming
---

keywords: `rust` `cargo`

`cargo` ⇒ `npm`/`expo`? 

## Environment Setup

#### Create new project
```console
cargo new {your project name}
```

#### Setup Clippy
  tool for catching common mistake  

```console
rustup component add clippy 
```

then, on the top line of rs file, add Clippy
```
#![deny(clippy::all)]

...
The rest of you code
...
```

#### Install cargo-watch
  a hot reload component

```console
cargo install cargo-watch

// After install cargo-watch
cd {project folder}
cargo-warch -qc -x run -x clippy
```

#### Set project setting
`Ctrl+Shift+P` ⇒ `workspace json`

```
{
  "[rust]":{
    "editor.formatOnSave": true
    "editor.defaultFormatter": "rust-lang.rust-analyzer",
  }
}
```