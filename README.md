### Inspired by [Linting](https://github.com/sumitsaha/linting) by **Sumit Saha**, **[Learn With Sumit](https://github.com/learnwithsumit/)** [React](https://github.com/learnwithsumit/think-in-a-react-way/tree/lesson-3), [Next](https://github.com/learnwithsumit/nextjs-crash-course-with-heroes) and [Node](https://github.com/learnwithsumit/nodejs-basic-bangla)

- [Editor Setup](#editor-setup)
  - [Plugins](#plugins)
  - [Settings](#settings)
  - [Set Line Breaks](#set-line-breaks)
- [Auto Linting Setup](#auto-linting-setup)
- [Manual Linting Setup](#manual-linting-setup)
  - [Install Dev Dependencies](#install-dev-dependencies)
  - [Create Linting Configuration file manually](#create-linting-configuration-file-manually)
-

## Editor Setup

### Plugins

You need to install the below plugins:

- ESLint by Dirk Baeumer
- Prettier - Code formatter by Prettier
- Learn with Sumit Theme (optional)

### Settings

Follow the below settings for VS Code -

1. Create a new folder called ".vscode" inside the project root folder
2. Create a new file called "settings.json" inside that folder.
3. Paste the below json in the newly created settings.json file and save the file.

#### React

```json
{
  // Theme
  "workbench.colorTheme": "Learn with Sumit Theme",

  // config related to code formatting
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "[javascriptreact]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "javascript.validate.enable": false, //disable all built-in syntax checking
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.tslint": true,
    "source.organizeImports": true
  },
  "eslint.alwaysShowStatus": true,
  // emmet
  "emmet.triggerExpansionOnTab": true,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
}
```

#### Node

```json
{
  // config related to code formatting
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  },
  "eslint.alwaysShowStatus": true
}
```

If you followed all previous steps, the theme should change and your editor should be ready.

### Set Line Breaks

Make sure in your VS Code Editor, "LF" is selected as line feed instead of CRLF (Carriage return and line feed). To do that, just click LF/CRLF in bottom right corner of editor, click it and change it to "LF". If you dont do that, you will get errors in my setup.

## Auto Linting Setup

# [ sh ] Installation

1. Navigate to your app directory where you want to include this style configuration.

   ```bash
   cd my-app
   ```

2. Run this command inside your app's root directory. Note: this command executes the `eslint-prettier-config.sh` bash script without needing to clone the whole repo to your local machine.

   ```bash
   <!-- React -->
   exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/faisalcep/linting/master/react-eslint-prettier.sh 2> /dev/null)
   ```

   ```bash
   <!-- Next -->
   exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/faisalcep/linting/master/nextjs-eslint-prettier.sh 2> /dev/null)
   ```

   ```bash
   <!-- node -->
   exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/faisalcep/linting/master/node-eslint-prettier.sh 2> /dev/null)
   ```

   ```bash
   <!-- js -->
   exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/faisalcep/linting/master/js-eslint-prettier.sh 2> /dev/null)
   ```

## Manual Linting Setup

In order to lint and format your React project automatically according to popular airbnb style guide, I recommend you to follow the instructions below.

### Install Dev Dependencies

```sh
yarn add -D prettier
yarn add -D babel-eslint
npx install-peerdeps --dev eslint-config-airbnb
yarn add -D eslint-config-prettier eslint-plugin-prettier
```

or You can also add a new script in the scripts section like below to install everything with a single command:

```json
scripts: {
    "lint": "yarn add -D prettier && yarn add -D babel-eslint && npx install-peerdeps --dev eslint-config-airbnb && yarn add -D eslint-config-prettier eslint-plugin-prettier"
}
```

and then simply run the below command in the terminal -

```sh
yarn lint #or 'npm run lint'
```

### Create Linting Configuration file manually

Create a `.eslintrc` file in the project root and enter the below contents:

#### React

```json
{
  "extends": [
    "airbnb",
    "airbnb/hooks",
    "eslint:recommended",
    "prettier",
    "plugin:jsx-a11y/recommended"
  ],
  "parser": "babel-eslint",
  "parserOptions": {
    "ecmaVersion": 8
  },
  "env": {
    "browser": true,
    "node": true,
    "es6": true,
    "jest": true
  },
  "rules": {
    "jsx-a11y/no-onchange": 0,
    "react/react-in-jsx-scope": 0,
    "react-hooks/rules-of-hooks": "error",
    "no-console": 0,
    "react/state-in-constructor": 0,
    "indent": 0,
    "linebreak-style": 0,
    "react/prop-types": 0,
    "jsx-a11y/click-events-have-key-events": 0,
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx"]
      }
    ],
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 100,
        "tabWidth": 4,
        "semi": true,
        "endOfLine": "auto"
      }
    ],

    "no-new": 0,
    "jsx-a11y/label-has-associated-control": [
      "error",
      {
        "required": {
          "some": ["nesting", "id"]
        }
      }
    ],
    "jsx-a11y/label-has-for": [
      "error",
      {
        "required": {
          "some": ["nesting", "id"]
        }
      }
    ]
  },
  "plugins": ["prettier", "react", "react-hooks"]
}
```

#### Next

```json
{
  "extends": [
    "airbnb",
    "airbnb/hooks",
    "eslint:recommended",
    "prettier",
    "prettier/react",
    "plugin:jsx-a11y/recommended"
  ],
  "parser": "babel-eslint",
  "parserOptions": {
    "ecmaVersion": 8
  },
  "env": {
    "browser": true,
    "node": true,
    "es6": true,
    "jest": true
  },
  "rules": {
    "react/react-in-jsx-scope": 0,
    "indent": 0,
    "linebreak-style": 0,
    "react-hooks/rules-of-hooks": "error",
    "no-console": 0,
    "react/state-in-constructor": 0,
    "react/prop-types": 0,
    "jsx-a11y/click-events-have-key-events": 0,
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx"]
      }
    ],
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 100,
        "tabWidth": 4,
        "semi": true
      }
    ]
  },
  "plugins": ["prettier", "react", "react-hooks"]
}
```

#### Node

```json
{
  "extends": ["prettier", "airbnb-base"],
  "parserOptions": {
    "ecmaVersion": 12
  },
  "env": {
    "commonjs": true,
    "node": true
  },
  "rules": {
    "no-console": 0,
    "indent": 0,
    "linebreak-style": 0,
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 100,
        "tabWidth": 4,
        "semi": true
      }
    ]
  },
  "plugins": ["prettier"]
}
```
