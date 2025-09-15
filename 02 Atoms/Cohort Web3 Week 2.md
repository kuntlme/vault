---
tags:
  - atom
  - coding
Topics:
  - Web3
  - Solana
---
## Solana Wallet

```js
const { mnemonicToSeedSync } = require("bip39");

const { generateMnemonic } = require("bip39");

const { derivePath } = require("ed25519-hd-key");

cosnt { Keypair } = require("@solana/web3.js")

const main = () => {

const nacl = require("tweetnacl");

const mnemoic = generateMnemonic();

const seed = mnemonicToSeedSync(mnemoic);



for(let i = 0; i < 4; i++){

const path = `m/44'/501'/${i}'/0'`;

const derivedSeed = derivePath(path, seed.toString("hex")).key;

const secret = nacl.sign.keyPair.fromSeed(derivedSeed).secretKey;

console.log(Keypair.fromSecretKey(secret).publicKey.toBase58())

}

main()
```

## eth Wallet

```
const { mnemonicToSeedSync } = require("bip39");

const { generateMnemonic } = require("bip39");

const { derivePath } = require("ed25519-hd-key");

const { Wallet } = require("ethers");

const nacl = require("tweetnacl");

const HDKey = require("hdkey")




const main = () => {

const mnemoic = generateMnemonic();

const seed = mnemonicToSeedSync(mnemoic);

for(let i = 0; i < 4; i++){

const path = `m/44'/60'/0'/0/${i}`;

const hdkey = HDKey.fromMasterSeed(seed);

const childPrivateKey = hdkey.derive(path).privateKey.toString("hex");



const wallet = new Wallet(childPrivateKey);

console.log(wallet.address)

}

}



main()
```
