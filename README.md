# truffle-plugin-abigen

This truffle plugin generates the required files needed to use Geths [abigen](https://geth.ethereum.org/docs/dapp/native-bindings) to generate contract bindings in golang.

## Installation
1. Install the plugin with npm
    ```sh
    npm install @darienmh/truffle-plugin-abigen
    // or
    yarn add @darienmh/truffle-plugin-abigen
    ```
2. Add the plugin to your `truffle.js` or `truffle-config.js` file
    ```js
    module.exports = {
      /* ... rest of truffle-config */

      plugins: [
        "@darienmh/truffle-plugin-abigen"
      ]
    }
    ```
3. Optional configuration in your `truffle.js` or `truffle-config.js` file
   ```js
    module.exports = {
      /* ... rest of truffle-config */

      abigen: {
        exportFolder: './abiExported/',
        extensionAbi: '.json',
        generateBin: false,
        exportConsole: true
      }
    }
    ```

## Usage
Before running ensure that you've compiled your contracts:
```sh
truffle compile
```
To generate specific contract bindings:
```sh
truffle run abigen SomeContractName AnotherContractName
```
Alternatively, to generate bindings for all your contracts:
```sh
truffle run abigen
```
You can also configure the `package.json` file to generate abi for all your contracts on compile:
```json
{
   /* ... rest of package.json */
   "scripts": {
      /* ... rest of package.json */
      "compile": "truffle compile --all && truffle run abigen"
   }
}
```
```bash
npm run compile
# or
yarn compile
```

### Debugging
You can pass an optional `--debug` flag into the plugin to display debug messages during the verification process. This is generally not necessary, but can be used to provide additional information when the plugin appears to malfunction.