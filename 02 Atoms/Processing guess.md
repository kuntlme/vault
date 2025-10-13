---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
  - Rust
---

```rust
use std::io;

fn main() {
    println!("Guess the number!");
    println!("Please input your guess.");
    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}

```
*variables*
let apple = 5; // immutable
let mut bananas = 5; // mutable

The `::` syntax in the `::new` line indicates that new is an associated function of the String type. An associated function is a function that’s implemented on a type, in this case String . This new function creates a new, empty string. You’ll ﬁnd a new function on many types because it’s a common name for a function that makes a new value of some kind.