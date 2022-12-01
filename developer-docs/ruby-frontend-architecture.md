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
  * `initRazeEthClient` : initialize a client to interact with a specific Raze contract that has been deployed on a chain;&#x20;
  * `razeEthLogin` : retrieve contract status from the chain for a Raze account secret&#x20;
  * `razeEthRegister` : register a Raze account with a provided secret&#x20;
  * `razeEthDeposit` : deposit certain amount of native tokens on the Raze contract&#x20;
  * `razeEthWithdraw` : withdraw a certain amount of native tokens from the Raze contract&#x20;
  * `razeEthTransfer` : transfer a certain amount of Raze tokens from one account to another
* When the frontend project initializes, it imports `razeClient` in `src/main.js` , creates a client instance through `initRazeClient` , and stores it in a vue instance, so that the whole frontend can call the above APIs through `$raze` .
