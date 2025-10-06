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

let newStudent = new Student(12, "kuntal", "majee");
console.log(newStudent);
let fullname = newStudent.getFullname();
console.log(fullname);
```
