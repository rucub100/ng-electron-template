# ng-electron-template

This project allows you to combine two popular frameworks to build cross-platfrom desktop apps with the power of angular and electron.

## How to

The procedure is based on the [question on stackoverflow](https://stackoverflow.com/questions/41130993/electron-not-allowed-to-load-local-resource).

### Prerequisites

* [NodeJs](https://nodejs.org/en/)
* [Angular CLI](https://angular.io/guide/setup-local)

### Steps to reproduce this template

1. Initialize a new Angular project `ng new`
1. Install Electron `npm i --save-dev electron`
1. Update `index.html` with `<base href="./">` (add the full stop)
1. Update `package.json` (add two scripts):
   ```
   {
     ...
     "scripts": {
       ...
       "electron-build": "ng build --prod && electron ./build",
       "electron": "electron ./build"
     },
     ...
   }
   ```
1. New files
   1. `src/electron-main.js` - [Electron's main script file](https://www.electronjs.org/docs/tutorial/quick-start#create-the-main-script-file) 
   1. `src/package.json` - The starting point of your Electron application; Make sure the name `"main"; "electron-main.js"` is correct; Additionaly add two scripts: `"pack": "electron-builder --dir"` and `"dist": "electron-builder"`
1. Update `angular.json`
   1. Change the output path to `"outputPath": "build"`
   1. Add two assets `"src/package.json"` and `"src/electron-main.js"
1. Finally consider to adjust the .gitignore file with `/build`

### Workflow

* Develop in Angular as usual with `ng serve`
* Run `npm run electron-build` if you want to see the progress outside the browser
* `cd build`, `npm install` and `npm run dist` or `npm run pack` to get the final result (see also [electron-builder](https://github.com/electron-userland/electron-builder))
