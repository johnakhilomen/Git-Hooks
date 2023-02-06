# Setting up Git pre-commit hooks with only husky
### husky uses distinct bash files with filenames that match the workflow step they correspond to, e.g. "pre-commit".

### To install husky
```
npx husky-init && npm install
```
Or
```
npx husky-init && yarn
```

### Then add one or more commands you want git hook to run before git commit using `npx husky add`. Here are few examples that will add the following commands to pre-commit bash file inside .husky folder after you have installed husky with the command above:
```
npx husky add .husky/pre-commit "npm run lint"
npx husky add .husky/pre-commit "npm test"
npx husky add .husky/pre-commit "npx prettier --write ."
npx husky add .husky/pre-commit "eslint --fix --ext .js,.jsx"
npx husky add .husky/pre-commit "eslint --fix ."
```


# Setting up Git pre-commit hooks with husky integrated with lint-staged
### Install husky
```
npx husky-init && npm install
```
Or
```
npx husky-init && yarn
```

### Add lint-staged setup on package.json
```
"lint-staged": {
    "*.{js,jsx,ts,tsx,mjs,cjs}": [
      "eslint --fix",
      "prettier --write"
    ],
    "*.{json,md}": [
      "prettier --write"
    ]
  },
```

### Then add pre-commit script on package.json
```
"pre-commit": "npx lint-staged"
```
### Now add the pre-commit command using `npx husky add`:
```
npx husky add .husky/pre-commit "npm run pre-commit"
```
