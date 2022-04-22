# electron-vue-vite

An electron + vue + vite boilerplate

## Get started with this quick guide

- Clone this repository
- Use your prefreed package manager to install the node modules
- To start a development server, use the `npm run electron:serve` command
- You can build the app using the `npm run electron:build` command

> As an alternative to npm, you can also use yarn or pnpm.

## Overview

The electron-vue-vite boilerplate is built on vite boilerplate along with the vue router and pinia for centralized state management, and it does not change anything in the vite boilerplate except for the history mode of the vue router, which is required for vue router to work in electron. As for what this change actually means, it replaces `useWebHistory` with `useWebHashHistory` because electron cannot use the usual webhistory method, and this is all that has changed in vite's boilerplate.
Two new files were created in the boilerplate root, main.js and preload.js, based on the format outlined in the official electron documentation, but we modified the main.js file to support hot reloading by replacing

```js
win.loadFile("index.html");
```

with

> In order to let electron know wheather we are in production or development,we set the IS_DEV envoirment variable using cross-env

```js
if (process.env.IS_DEV == "true") {
  win.loadURL("http://localhost:3000/");
} else {
  win.loadFile("dist/index.html");
}
```

Because of this, we keep our changes to a minimum, so adding anything you wish to or editing the boilerplate is simple and straightforward.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.vscode-typescript-vue-plugin).

## These are all the node modules that were used in the boilerplate

| Modules                                                                    | Version     |
| -------------------------------------------------------------------------- | ----------- |
| [electron](https://www.electronjs.org/docs/latest)                         | 18.1.0      |
| [vue](https://www.npmjs.com/package/vue)                                   | 3.2.33      |
| [vite](https://www.npmjs.com/package/vite)                                 | 2.9.5       |
| [wait-on](https://github.com/jeffbski/wait-on#readme)                      | 6.0.1       |
| [cross-env](https://github.com/kentcdodds/cross-env#readme)                | 7.0.3       |
| [@vitejs/plugin-vue](https://www.npmjs.com/package/@vitejs/plugin-vue)     | 7.1.0       |
| [concurrently](https://github.com/open-cli-tools/concurrently#readme)      | 7.1.0       |
| [pinia](https://www.npmjs.com/package/pinia)                               | 2.0.13      |
| [vue-router](https://www.npmjs.com/package/vue-router)                     | 4.0.147.1.0 |
| [electron-builder](https://www.electron.build/configuration/configuration) | 23.0.3      |

## Adding custom configurations to electron, vite, and electron-builder

- See [Vite Configuration Reference](https://vitejs.dev/config/).
- See [Electron Configuration Reference](https://www.electronjs.org/docs/latest).
- See [Electron-Builder Configuration Reference](https://www.electron.build/configuration/configuration).

## Why

The purpose of this boilerplate is simply to provide a simple configuration for adding and editing configuration with vue + vite + electron. There are a couple of simple boilerplates available like [electron-vite-vue](https://github.com/electron-vite/electron-vite-vue) and [vite-electron-builder](https://github.com/cawa-93/vite-electron-builder), but I wanted to make it even easier for a new user to add and edit configuration. Considering that it is designed to adhere to the original vite boilerplate structure, new users might have an easier time comprehending what exactly is going on. Check out [electron-vite-vue](https://github.com/electron-vite/electron-vite-vue) and [vite-electron-builder](https://github.com/cawa-93/vite-electron-builder) if you need a secure boilerplate.

&emsp;

> `I will update the documents with further instructions as soon as possible because my schedule is very hectic right now.`
