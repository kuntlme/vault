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
function Log(target: any, methodName: string, descriptor: PropertyDecorator) {
  const original = descriptor.value as Function;
  descriptor.value = function (message: string) {
    console.log("Before");
    original.call(this, message);
    console.log("After");
  };
}

class Person {
  @Log
  say(message: string) {
    console.log("Person says " + message);
  }
}

let person = new Person();
person.say("Hello");
```