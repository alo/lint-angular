# Lint Angular project

This is my Lint config for an angular project step by step.

1. Add **Prettier** and some plugins to avoid problems with tslint

```bash
npm install --save-dev tslint-plugin-prettier tslint-config-prettier prettier
```

2. Add **.prettierrs.json** and **.prettierignore** files (you have both in this repo)

.prettierrc.json

```json
{
  "printWidth": 120,
  "singleQuote": true,
  "useTabs": false,
  "tabWidth": 2,
  "semi": true,
  "bracketSpacing": true,
  "trailingComma": "none",
  "arrowParens": "avoid"
}
```

3. In tslint.json

```json
"extends": ["tslint:recommended", "tslint-plugin-prettier", "tslint-config-prettier"],
"rules": {
  "prettier": true,
  ...
}
...
```

We are installing 2 plugins:

- **tslint-plugin-prettier** to use TSLint to run Prettier
- **tslint-config-prettier** to disable rules that conflict with Prettier
- You can read more [here](https://prettier.io/docs/en/integrating-with-linters.html#tslint)

4. In Angular 9+ (tslint 6+) I manually delete this rule from tslint.json

```json
// DELETE THIS RULE FROM tslint.json
"semicolon": {
  "options": ["always"]
},
```

5. Now you can `npm run lint` your project

6. Adding **Husky** and **pretty-quick** to run prettier in your staged files

```bash
npm install --save-dev husky
```

7. Create .huckyrc to check if files 

```json
{
  "hooks": {
    "pre-commit": "npm run lint"
  }
}
```

