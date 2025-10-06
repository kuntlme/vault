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
By this there no need to initialize the variable.

```ts
class Account {
  constructor(
    public readonly id: number,
    public owner: string,
    private _balance: number,
  ) {}
}
let newAcc = new Account(1, "kuntal", 23);
console.log(newAcc);
```	
