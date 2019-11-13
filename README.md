### Some steps to start new backend nodeJs project:

- "yarn init -y" to start new package.json

- "yarn add express" to add express package

#### Sucrase and Nodemon
- "yarn add sucrase nodemon -D" to add sucrase (just in dev environment)
sucrase: to use new features of javascript; 
nodemon: to auto reload our code when we change it;

- add these new lines to "package.json" to run after the server with command "yarn dev" and "yarn dev:debug":
```javascript
  "scripts": {
    "dev" : "nodemon src/server.js"
  },
```

- create a new file in root of project called "nodemon.json" with below content to execute sucrase before starts the app :

```javascript
{
	"execMap": {
		"js": "node -r sucrase/register"
	}
}
```

- configure debug of vs code, clicking on "add configuration" and put these lines inside "configurations" key:
```javascript
{
	"type": "node",
	"request": "attach",
	"name": "Launch Program",
	"restart": true,
	"protocol": "inspector"
}
```

#### ESLint and Prettier
- "yarn add eslint -D" to install an package that will help to keep a pattern in code.

- "yarn eslint --init" to start eslint choosing these options:
"To check syntax, find problems, and enforce code style"
"JavaScript modules (import/export)"
"None of these"
"Node" (Just option)
"Use a popular style guide"
"Airbnb"
"JavaScript"
"Y" (To install)

- Erase file "package-lock.json" because eslint was intalled with npm and we are using yarn

- "yarn" to map new dependencies on yarn.lock

- find ESLint on vs code extensions and install it.

- press "Ctrl+Shift+P" and type ">Open Settings (JSON)" to open settings file of vs code and add these configurations:
```javascript
    "editor.rulers": [80, 120],    
    "eslint.autoFixOnSave": true,
    "eslint.validate": [
        {
            "language": "javascript",
            "autoFix": true
        },
        {
            "language": "javascriptreact",
            "autoFix": true
        },
        {
            "language": "typescript",
            "autoFix": true
        },
        {
            "language": "typescriptreact",
            "autoFix": true
        }
    ],
    "editor.renderLineHighlight": "gutter",
    "emmet.includeLanguages": {
        "javascript": "javascriptreact"
    },
    "emmet.syntaxProfiles": {
        "javascript": "jsx"
    },
    "javascript.suggest.autoImports": false
```

- override some configurations in file ".eslintrc.js", adding these rules (line "extends" and "rules" alread exists):
```javascript
  extends: [ 'airbnb-base', 'prettier' ], 
  plugins: [ 'prettier' ],
  rules: {
    "prettier/prettier": "error",
    "class-methods-use-this": "off",
    "no-param-reassign": "off",
    "camelcase": "off",
    "no-unused-vars": ["error", { "argsIgnorePattern": "next" }],
    "linebreak-style": [0, "error", "windows"]
  },
```

- "yarn add prettier eslint-config-prettier eslint-plugin-prettier -D" to install other tool to keep our code more beautiful <3
*Add "babel-eslint" to configure this on ReactJS and React Native

- create file ".prettierrc" on root path and override some configs of prettier:
```javascript
{
	"singleQuote": true,
	"trailingComma": "es5"
}
```

- So, to fix all files in project (if alread exists), run "yarn eslint --fix src --ext .js"

#### EditorConfig
- install new extension on vs code called "editorconfig" to keep the same configuration on editors of all developers, and create a file on root called ".editorconfig" and put these lines inside:

```javascript
root = true

[-]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```
