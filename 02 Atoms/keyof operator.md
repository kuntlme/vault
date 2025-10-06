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
interface Product {
  name: string;
  price: number;
}

class Store<T> {
  protected _objects: T[] = [];
  add(object: T) {
    this._objects.push(object);
  }
  find(property: keyof T, value: unknown) {
    return this._objects.find((obj) => obj[property] === value);
  }
}

let store = new Store<Product>();
store.add({ name: "a", price: 1 });
console.log(store.find("price", 1));
```
