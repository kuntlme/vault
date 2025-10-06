---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
  - TypeScript
---
```ts
class Account {
  private _balance;
  constructor() {
    this._balance = 0;
  }
  get balance() {
    return this._balance;
  }
}
let newAcc = new Account();
console.log(newAcc.balance);
```
