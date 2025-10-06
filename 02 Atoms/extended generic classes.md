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
}

let store = new Store<Product>();
store.add({ name: "milk", price: 150 });
store.add({ name: "milk", price: 150 });
console.log(store);

// pass on the generic type parameter
class CompressableStore<T> extends Store<T> {
  compress() {}
}

let compressStore = new CompressableStore<Product>();
compressStore.add({ name: "bread", price: 25 });
console.log(compressStore);

// restric the generic type parameter
class SearchableStore<T extends { name: string }> extends Store<T> {
  find(name: string): T | undefined {
    return this._objects.find((obj) => obj.name === name);
  }
}

class ProductStore extends Store<Product> {
  filter(catagory: string): Product[] {
    return [];
  }
}
```
