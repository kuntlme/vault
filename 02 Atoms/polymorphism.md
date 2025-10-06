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
class Person {
  constructor(
    public firstname: string,
    public lastname: string,
  ) {}
  getFullname() {
    return this.firstname + this.lastname;
  }
}

class Student extends Person {
  constructor(
    public id: number,
    firstname: string,
    lastname: string,
  ) {
    super(firstname, lastname);
  }
  getFullname() {
    return "student " + super.getFullname();
  }
}

function printNames(people: Person[]) {
  for (let person of people) {
    console.log(person.getFullname());
  }
}
printNames([new Student(23, "kuntal", "majee"), new Person("kunal", "majee")]);
```
