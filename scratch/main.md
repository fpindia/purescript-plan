# Platform agnostic instructions

You can find any platform specific notes at the end of this document.

*(This document should be broken into multiple pages if it gets too long.)*

## Install prerequisites

(Note that we don't install Purescript tooling globally in these instructions. This allows easy per-project upgrades.)

1. Install NodeJS from https://nodejs.org/

2. Install an Editor.

  - I recommend Spacemacs - https://www.spacemacs.org
  - You can also use VSCode - https://code.visualstudio.com
  
3. Setup Purescript editor support.

  - Spacemacs
    - Add `(purescript :variables node-add-modules-path t)` to the layers in your `.spacemacs` configuration file.
    (The `node-add-modules-path` setting ensures that the purescript tools are picked up from the node_modules directory).
    
  - VSCode
    - Install `Purescript IDE` package by Nicholas Wolverson.
    - Go to `Settings > Purescript Configuration`. Set the following -
      - Enable `Add Npm Path`
      - Enable `Add Spago Sources`
      - Change the Build command to `spago build -- --json-errors`

## Create the project

1. Initialise a new node project

```
λ npm init
```

Follow the prompts and provide your project name. The other settings can be left at their default values.
It will create a `package.json` file for your project.

2. Install purescript and other js tooling

```
λ npm install —save-dev purescript spago parcel-bundler
```

All the three tools (`purs`, `spago`, `parcel`) can now be run using `npx <commandname>`

3. Make sure all dependencies are installed.

```
λ npm install
```

4. Initialise a purescript project with spago

```
λ npx spago init
```

5. Build the Purescript code -

```
λ spago build
```

6. Verify that everything worked as expected

```
λ npx spago run
```

If the project doesn't run, or gives you an error, then one of the above steps went wrong and you should trace your steps back to see which one.

## Further steps

1. At this point, you should also setup git and check in the initial project sources

```
λ git init
λ git add -A
λ git commit -m "Init project"
```

2. Open the `src` folder in your editor and start coding! Making sure to check in your code often!

## Working with External JS dependencies

Any external JS dependencies need to be installed with NPM, and then the corresponding purescript wrapper must be installed with SPAGO.

For example, to use React in your project.

Install react as a dependency using npm -

```
λ npm install —save react react-dom
```

Then install the purescript wrapper libraries for react -

```
λ npx spago install react react-dom web-html web-dom
```
