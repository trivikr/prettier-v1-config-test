# prettier-v1-config-test

Testing npm package prettier-v1-config

## Steps to test

- Clone this repo
- Run `yarn` to install dependencies

### In terminal

- Open [index.js](./index.js), and add trailingComma at the end of array

  ```diff
    "as prettier config uses prettier@1 defaults",
  -  "using npm package prettier-v1-config"
  +  "using npm package prettier-v1-config",
  ];
  ```

- The commit creation will fail as prettier will remove trailingComma as per config

  ```console
  $ git commit -am "Testing prettier on precommit"
  husky > pre-commit (node v12.14.0)
    ✔ Preparing...
    ✔ Running tasks...
    ✖ Applying modifications...
      → Prevented an empty git commit!
    ✔ Reverting to original state because of errors...
    ✔ Cleaning up...

    ⚠ lint-staged prevented an empty git commit.
      Use the --allow-empty option to continue, or check your task configuration

  Prevented an empty git commit!
  husky > pre-commit hook failed (add --no-verify to bypass)
  ```

### In Visual Studio Code

- Open this repo in [Visual Studio Code](https://code.visualstudio.com/)
- Install [prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extension v4.0.0+
- Open [index.js](./index.js), and add trailingComma at the end of array
- Notice that prettier-vscode extension removes the trailingComma when file is saved

<details>
<summary>Screen recording</summary>

<img src="./prettier-v1-config-test.gif" />

</details>

This happens `"trailingComma": "none"` from [prettier-v1-config](https://github.com/trivikr/prettier-v1-config/blob/621215afa7275ce3b2835a10484cd0ab74dfb7c6/index.json#L5) gets preference over `"trailingComma": "es5"` [defined by prettier@2](https://prettier.io/blog/2020/03/21/2.0.0.html#change-default-value-for-trailingcomma-to-es5-6963httpsgithubcomprettierprettierpull6963-by-fiskerhttpsgithubcomfisker)
