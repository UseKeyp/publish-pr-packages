<h1 align="left">Welcome to PR Package Publisher 👋</h1>
<p align="left">
  <a href="#" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-blue.svg" />
  </a>
</p>

> Auto-publish fresh packages for every pull request

<p align="left">
<img width="600px" src="package-published-comment.png"/>
</p>

# Prerequisites

This tool requires lerna for versioning and publishing. You must install it in the root of your repo with the following command:

```bash
yarn add --dev lerna
lerna init
```

Next ensure your `package.json` includes the packages you want to publish in the workspaces: 

```json
{
  "workspaces": [
    "packages/*"
  ]
}
```
# Usage


```yml
name: CI - Pull Request
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  ci:
    name: PR Continuous Integration
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Source
        uses: actions/checkout@v3
      - name: Publish Package
        uses: ./.github/actions/publish_pr_pkg
        with:
          token: ${{ secrets.PAT }}
          build-command: yarn build
          packages-directory: packages
          registry: github
```

## Sponsors ❤️

[<img height="65" align="left" src="https://github.com/UseKeyp/.github/blob/main/Keyp-Logo-Color.png?raw=true" alt="keyp-logo">][sponsor-keyp] Improve onboarding and payments in your games & web3 apps effortlessly with OAuth logins for wallets and debit card transactions. [Create a Keyp account; it's free!][sponsor-keyp]<br><br>

## License 📝

Copyright © 2023 Nifty Chess, Inc.<br />
This project is MIT licensed.

[sponsor-keyp]: https://UseKeyp.com