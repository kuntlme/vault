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
interface Person {
  username: string;
}

function echo<T extends number | string>(value: T): T {
  return value;
}

console.log(echo("kuntal"));
console.log(echo(66));
```
