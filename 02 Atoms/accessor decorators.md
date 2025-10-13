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
function Capitalize(
  target: any,
  methodName: string,
  descriptor: PropertyDecorator,
) {
  const original = descriptor.get;
  descriptor.get = function (...args) {
    const result = original?.call(this);
    return typeof result === "string" ? result.toUpperCase() : result;
  };
}
class Person {
  constructor(
    public firstname: string,
    public lastName: string,
  ) {}
  @Capitalize
  get fullName() {
    return `${this.firstname} ${this.lastName}`;
  }
}

let person = new Person("kuntal", "majee");
console.log(person.fullName());
```