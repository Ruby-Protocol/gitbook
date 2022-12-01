# Ruby Frontend Architecture

## Framework and Technology

* Vue UI framework&#x20;
* ElementUI&#x20;
* Vuex&#x20;
* Vue router

## Project setup

```
yarn install or npm install
```

## Compiles and hot-reloads for development

```
yarn serve or npm run serve
```

## Compiles and minifies for production

```
yarn build or npm run build
```

## Customize Configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## How to Interact with the Vue Frontend

* `src/razeClient.js` exports a JS object `razeApp` , which provides all necessary APIs to interact with the contract:&#x20;
  * `initRubyEthClient` : initialize a client to interact with a specific Ruby contract that has been deployed on a chain;&#x20;
  * `razeEthLogin` : retrieve contract status from the chain for a Ruby account secret&#x20;
  * `razeEthRegister` : register a Ruby account with a provided secret&#x20;
  * `razeEthDeposit` : deposit certain amount of native tokens on the Ruby contract&#x20;
  * `razeEthWithdraw` : withdraw a certain amount of native tokens from the Ruby contract&#x20;
  * `razeEthTransfer` : transfer a certain amount of Ruby tokens from one account to another
* When the frontend project initializes, it imports `razeClient` in `src/main.js` , creates a client instance through `initRubyClient` , and stores it in a vue instance, so that the whole frontend can call the above APIs through `$raze` .
