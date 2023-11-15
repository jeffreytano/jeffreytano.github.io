---
layout: single
title: "Tauri Environment Setup"
permalink: /learning/tauriEnv/
classes: wide
sidebar:
  nav: Programming
---
## Install

Getting Started for Windows [Link](https://tauri.app/v1/guides/getting-started/prerequisites){: .btn .btn--info}{:target="\_blank"}

1. Download Microsoft Visual Studio C++ Build Tools

Go to the [Link](https://visualstudio.microsoft.com/visual-cpp-build-tools/){: .btn .btn--info}{:target="\_blank"}, select **Desktop development with C++**, and make sure to select these two in optional (RHS)

 - MSVC v143 - VS 2022 C++ x64/x86 build tools
 - Windows 10 SDK

2. WebViews2 \**Webiview2 is pre-installed in Windows 11*

Go to the [Link](https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section){: .btn .btn--info}{:target="\_blank"} to download Webview2

3. Install Rust

Go to [Rust](https://www.rust-lang.org/tools/install){: .btn .btn--info}{:target="\_blank"}

## Setup project

#### create new project

Using ReactJS, Go to the directory
```console
npx create-react-app

npm install -D @tauri-apps/cli cross-env
```

Add in package.json
```
"scripts": {
  "tauri": "tauri"
}
```
and
```
"resolutions": { "mini-css-extract-plugin": "2.4.7"}
```

```
npm run build
```

Run
```
npm run tauri init


...


npm install @tauri-apps/api
```

In the "tauri.conf.json"
```
"beforeDevCommand" : "cross-env BROWSER=none npm run start"
```

Then, we can run
```
npm run tauri dev
```
in dev stage.

aAnd
```
npm run tauri build
```