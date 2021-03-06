<h1 align="center">Path To FullStack</h1>

<p align="center">This is my personal repository used to learn new technologies.</p>

### What is this README.md?

Any technology that is not code is placed here. By creating just one big file with everything in it, just the process of making it teaches you a lot, and I can always consult it.

### Structure

I'll be dividing this README in four different categories.

1. **DONE**
2. **DOING -** Technologies that I'm learning right now or will learn in the near future.
3. **TODO -** Technologies that I'm not going to study in the near future but are on my radar.
4. **EXTENSIONS**

## Table of contents

* **[EXTENSIONS](#EXTENSIONS)**
    * [EditorConfig](#EditorConfig)

* **[DONE](#DONE)**
    * [NodeJS and npm](#NodeJS)
    * [Yarn](#Yarn)
    * [Git and GitHub](#Git-and-GitHub)
    * [Express](#Express)
    * [TypeScript](#TypeScript)
    * [ESLint](#ESLint)
    * [Prettier](#Prettier)

<h1 align="center">EXTENSIONS</h1>

<p align="center">VSCode Extensions.</p>


<h2 align="center">EditorConfig</h2>

> EditorConfig helps maintain consistent coding styles for multiple developers working on the same project across various editors and IDEs.

You can save your editor configurations in a `.editorconfig` file at the root folder.

<h1 align="center">DONE</h1>

<p align="center">Technologies that I've somewhat learned and that I'm already using.</p.>


<h2 align="center">NodeJS</h2>

> [Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.](https://nodejs.org/en/)

NodeJS is your runtime, npm your package manager.
Follow through the [installation](https://nodejs.org/en/) and both will be installed and ready to use.

### Using NodeJS and npm

`npm init` - Creates a package.json file.

`npm install` - Adds dependencies to the package.json file and install them at the node_modules folder.

`node index.js` - Runs the index.js file in NodeJS.

`package.json` is your project configuration file, edit the `scripts` part and create customizable Node commands.


<h2 align="center">Yarn</h2>

> Yarn is a package manager that doubles down as project manager. Whether you work on one-shot projects or large monorepos, as a hobbyist or an enterprise user, we've got you covered.

Well, I just think Yarn is easier to use.

`npm install -g yarn` - Install Yarn globally.

If you ever use npm in your repo you can delete the package-lock.json file and run `yarn`.


<h2 align="center">Git and GitHub</h2>

> [Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.](https://git-scm.com/)

Git and GitHub are used to keep your code safe by allowing you to create multiple versions of your repo and backing it up to the cloud.

### Setup

* [Git can be downloaded here.](https://git-scm.com/download)
* [GitHub home page can be accessed here.](https://github.com/)

### Using Git

`.gitignore` is a file that you can create in the root folder of your project that tells Git the files that should be ignored

`git config credential.helper store` - This command will save your credential in plain text.

`git config --global credential.helper cache` - Will save your credential for 15 minutes by default, you can define the timeout.

`git config --global credential.helper 'cache --timeout=3600'` - Sets the timeout to 1 hour.

`git init` - Initializes a git repository locally.

`git add .` - Stores snapshot temporary in the index.

`git commit` - Permanently stores index contents.

`git log` - Logs commits.

`git branch feature/name` - Creates a branch named **feature/name**.

`git checkout feature/name` - Switchs to hte branch named **feature/name**.

`git merge feature/name` - Merges the branch named **featue/name** to the master.

`git branch -D feature/name` - Deletes the branch named **featue/name**.

`git remote add origin https://github.com/eLucis198/path-to-fullstack.git` - Syncs to your GitHub repo.

`git push -u origin master` - Pushes master branch to GitHub.

`git pull origin master` - Pulls from GitHub to the master branch .

### How I learned

* https://git-scm.com/docs/gittutorial

* https://www.youtube.com/watch?v=MW7hrQe6aYo

* https://www.youtube.com/watch?v=2T2l2rGRzXs&t


<h2 align="center">Express</h2>

> Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

Best thing ever for HTTP requests and routing.

`yarn add express` - Installs the express dependency.


<h2 align="center">TypeScript</h2>

>TypeScript is a typed superset of JavaScript that compiles to plain JavaScript.

This may be the best thing I found out here haha, makes your code much more clear, looks like OOP :laughing:

### Setting up

`yarn global add typescript` - Installs typescript globally in your machine.
`yarn add typescript --d` - Installs typescript as a development dependency.

### Transpile - sucrase + nodemon

`yarn add sucrase nodemon -D` - Installs sucrase and nodemon as a dev dependencies.

Create a nodemon.json file for configurations.
```json
{
  "watch": ["src"],
  "ext": "ts",
  "execMap": {
    "ts:": "sucrase-node src/server.ts"
  }
}
```
Alter package.json
```json
"scripts": {
  "dev": "nodemon src/server.ts",
  "build": "sucrase ./src -d ./dist --transforms typescript,imports"
},
```
`yarn dev` - Runs app.
`yarn buid` - Builds app.

### Transpile - ts-node-dev

Run `yarn tsc --init` to init a tsconfig.json file. (Only works with typescript installed globally)

Add this line to the tsconfig.json file
```json
{
    "compilerOptions": {
      "outDir": "./dist/"
    }
}
```

You can transpile your code just by running `yarn tsc` and the files should be in the dist directory.

For automated transpiles I'll use __ts-node-dev__.
Install it by running `yarn add ts-node-dev --d`.

Add this line to your packge.json file.
```json
  "scripts": {
    "dev:server": "ts-node-dev --respawn --transpileOnly src/index.ts"
  },
```
Now run `yarn dev:server`. Your project is running it transpiles automatically at every code update.

### Types

You need to install the "types" of your dependencies for the IntelliSense to work.

`npm install @types/express -D` - Install the types of express as a development dependency.

### How I learned

* https://www.youtube.com/watch?v=0mYq5LrQN1s
* https://www.youtube.com/watch?v=aTf8QTjw4RE


<h2 align="center">ESLint</h2>

> A pluggable and configurable linter tool for identifying and reporting on patterns in JavaScript. Maintain your code quality with ease.

Points out error in TS code.

### Setup

Install the extension ESLint.

Run `yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin` to install.

To initialize run `yarn eslint --init` and configure it. (Now you can delete package-lock.json and run `yarn`)

Add line to .eslintrc.js
```js
extends: [
  'plugin:@typescript-eslint/recommended',
  'standard'
],
```

Now open your vsCode preferences {{ Ctrl - Shift + P  ==>>  preferences: open settings (json) }}

Add the following lines
```json
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
},
"eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
]
```
All done, now TypeScript is running with ESLint :ok_hand:

### How I learned

* https://www.youtube.com/watch?v=aTf8QTjw4RE


<h2 align="center">Prettier</h2>

> Prettier is an opinionated code formatter. It enforces a consistent style by parsing your code and re-printing it with its own rules that take the maximum line length into account, wrapping code when necessary.

### Setup

Run `yarn add prettier eslint-config-prettier eslint-plugin-prettier -D`.

Add line to .eslintrc.js
```js
extends: [
  'plugin:@typescript-eslint/recommended',
  'prettier/@typescript-eslint',
  'standard'
],
```
