---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
---
```ts 
type Custormer = {
  birthday: Date;
};

function getCustomer(id: number): Custormer | null {
  return id === 0 ? null : { birthday: new Date() };
}

let custormer = getCustomer(1);
console.log(custormer?.birthday);
```
