# Top JavaScript Interview Questions - Detailed Answers (1-10)

tags: #js #interviewprep

diagram: [[js interview excalidraw]]

---

### 1. **Can you explain the event loop in JavaScript and how it handles asynchronous operations?** <font color="#00b050">done</font>

**Answer:**  
The **event loop** is a mechanism in JavaScript that enables asynchronous programming by allowing non-blocking operations, despite JavaScript being single-threaded.

**Components involved:**

- **Call Stack:** Where functions are pushed and popped during execution.
    
- **Web APIs (Browser APIs):** Handles asynchronous tasks like `setTimeout`, DOM events, AJAX, etc.
    
- **Callback Queue (Task Queue):** Stores callbacks from completed async operations.
    
- **Microtask Queue:** Stores microtasks like `.then()` from Promises.
    

**How it works:**

1. JS executes code line-by-line via the **call stack**.
    
2. If it encounters an async operation (like `setTimeout` or a fetch), the call is delegated to the Web API.
    
3. Once the async operation is complete, its callback is pushed to the appropriate queue.
    
4. The **event loop** checks if the call stack is empty.
    
5. If yes, it processes microtasks from the microtask queue first, then moves to the callback queue.
    

**Interview Tip:**  
Use the example of `setTimeout` and Promises to show how the event loop prioritizes microtasks before macrotasks.

**Keywords Explained:**

- **Call Stack**: Execution context stack for synchronous functions.
    
- **Microtask**: A Promise callback (like `.then()`).
    
- **Macrotask**: A `setTimeout`, `setInterval`, etc.
    

---

### 2. **What are closures in JavaScript?** <font color="#00b050">done</font>

**Answer:**  
A **closure** is a function that remembers the variables from its outer lexical scope even after the outer function has finished executing.

```js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    return count;
  };
}
const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

In this example, `inner()` still has access to `count` even after `outer()` has returned.

**Interview Tip:**  
Mention real-world use cases like data encapsulation and event handlers.

**Keywords Explained:**

- **Lexical Scope**: Scope determined at function definition, not at execution.
    
- **Encapsulation**: Protecting internal state using closures.
    

---

### 3. **Explain the concept of "this" in JavaScript. How does its value get determined?** <font color="#00b050">done</font>

**Answer:**  
The value of `this` depends on the **execution context**:

| Context               | Value of `this`                          |
| --------------------- | ---------------------------------------- |
| In global scope       | `window` (in browsers)                   |
| In a method           | Object calling the method                |
| In a regular function | `undefined` (in strict mode) or `window` |
| In an arrow function  | Inherited from the enclosing scope       |
| In a constructor      | New instance created                     |

```js
const obj = {
  name: 'JS',
  say() {
    console.log(this.name);
  }
};
obj.say(); // 'JS'
```

**Interview Tip:**  
Explain how arrow functions don’t have their own `this`, which is key in React or asynchronous patterns.

**Keywords Explained:**

- **Execution Context**: The environment in which code is executed.
    
- **Arrow Function**: Inherits `this` from the enclosing lexical context.
    

---

### 4. **How does prototypal inheritance work in JavaScript?** <font color="#00b050">done</font>

**Answer:**  
JavaScript uses **prototypal inheritance**, where objects inherit properties and methods from other objects via a prototype chain.

```js
function Animal(name) {
  this.name = name;
}
Animal.prototype.speak = function() {
  return `${this.name} makes a noise.`;
};

const dog = new Animal("Dog");
dog.speak(); // 'Dog makes a noise.'
```

Here, `dog` inherits the `speak()` method from `Animal.prototype`.

**Interview Tip:**  
Draw the prototype chain to visually explain the lookup path.

**Keywords Explained:**

- **Prototype**: The object from which another object inherits properties.
    
- ****proto****: A reference to the object's prototype.
    

---

### 5. **What is hoisting in JavaScript?** <font color="#00b050">done</font>

**Answer:**  
**Hoisting** is JavaScript's behavior of moving variable and function declarations to the top of their scope during compilation.

```js
console.log(a); // undefined
var a = 5;
```

Function declarations are hoisted with definitions, while variables declared with `var` are hoisted without initial value.

**let** and **const** are hoisted too but stay in a **Temporal Dead Zone** until initialized.

**Interview Tip:**  
Explain hoisting separately for `var`, `let`, `const`, and function declarations vs expressions.

**Keywords Explained:**

- **Temporal Dead Zone (TDZ)**: Time between hoisting and variable declaration where access results in error.
    

---

### 6. **What is the difference between let, const, and var?** <font color="#00b050">done</font>

|Feature|var|let|const|
|---|---|---|---|
|Scope|Function|Block|Block|
|Re-declaration|Allowed|Not Allowed|Not Allowed|
|Re-assignment|Allowed|Allowed|Not Allowed|
|Hoisting|Yes (initialized as undefined)|Yes (TDZ)|Yes (TDZ)|

**Interview Tip:**  
Explain why `let` and `const` are preferred in modern JS.

**Keywords Explained:**

- **Block Scope**: Accessible only within `{}`.
    

---

### 7. **What is the purpose of the async and await keywords in JavaScript?** <font color="#00b050">done</font>

**Answer:**  
`async` and `await` make asynchronous code look synchronous, improving readability.

```js
async function getData() {
  const response = await fetch('https://api.example.com');
  const data = await response.json();
  console.log(data);
}
```

- `async` functions always return a Promise.
    
- `await` pauses execution until the Promise is resolved.
    

**Interview Tip:**  
Explain how `await` only works inside `async` functions and how it simplifies promise chaining.

**Keywords Explained:**

- **Asynchronous**: Tasks that run in the background.
    
- **Promise**: An object representing the eventual completion of an async operation.
    

---

### 8. **What are higher-order functions in JavaScript? Provide an example.** <font color="#00b050">done</font>

**Answer:**  
A **higher-order function** either:

- Takes a function as an argument, or
    
- Returns a function.
    

```js
function greet(message) {
  return function(name) {
    return `${message}, ${name}`;
  };
}
const helloGreet = greet("Hello");
console.log(helloGreet("Alice"));
```

Common examples: `map`, `filter`, `reduce`.

**Interview Tip:**  
Show use cases in functional programming and callbacks.

**Keywords Explained:**

- **First-class function**: Functions can be passed as arguments or returned.
    

---

### 9. **What are promises in JavaScript?** <font color="#00b050">done</font>

**Answer:**  
A **Promise** is an object representing the eventual success or failure of an asynchronous operation.

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done!"), 1000);
});

promise.then(result => console.log(result));
```

States of a Promise:

- **Pending**: Initial state.
    
- **Fulfilled**: Operation successful.
    
- **Rejected**: Operation failed.
    

**Interview Tip:**  
Mention chaining using `.then()`, `.catch()`, and `.finally()`.

**Keywords Explained:**

- **Chaining**: Handling promise results in a sequence.
    

---

### 10. **Explain the difference between == and === in JavaScript.** <font color="#00b050">done</font>

| Operator | Type            | Behavior                                         |
| -------- | --------------- | ------------------------------------------------ |
| `==`     | Loose Equality  | Converts operands to same type before comparison |
| `===`    | Strict Equality | No type conversion; compares both type and value |

```js
'5' == 5     // true
'5' === 5    // false
```

**Interview Tip:**  
Always recommend using `===` for predictability.

**Keywords Explained:**

- **Type coercion**: Automatic or implicit conversion of values from one type to another.
    

---

### 11. **How do you handle asynchronous operations in JavaScript? Discuss callbacks, Promises, and async/await.** <font color="#00b050">done</font>

**Answer:**  
JavaScript handles asynchronous operations using:

**1. Callbacks**

- Functions passed as arguments to other functions.
    

```js
setTimeout(() => console.log("Callback!"), 1000);
```

- Downsides: Callback Hell, error handling is hard.
    

**2. Promises**

- Provides a cleaner API.
    

```js
fetch("/api").then(res => res.json()).then(data => console.log(data));
```

- Has `.then()`, `.catch()`, `.finally()`.
    

**3. async/await**

- Syntactic sugar over Promises.
    

```js
async function getData() {
  try {
    const res = await fetch("/api");
    const data = await res.json();
    console.log(data);
  } catch (e) {
    console.error(e);
  }
}
```

**Interview Tip:**  
Mention how each evolved to improve readability and maintainability.

**Keywords:**

- **Callback Hell**: Nesting of callbacks leading to unreadable code.
    

---

### 12. **What are the different data types in JavaScript?** <font color="#00b050">done</font>
**Answer:**  
JavaScript has 8 data types:

**Primitive Types:**

- `String`
    
- `Number`
    
- `BigInt`
    
- `Boolean`
    
- `Symbol`
    
- `undefined`
    
- `null`
    

**Non-Primitive (Reference) Type:**

- `Object` (includes Arrays, Functions, Dates, etc.)
    

**Interview Tip:**  
Mention `typeof null === 'object'` is a well-known bug.

**Keywords:**

- **Primitive**: Immutable and stored by value.
    
- **Reference**: Stored by reference.
    

---

### 13. **What is the difference between null and undefined in JavaScript?** <font color="#00b050">done</font>

| Feature     | null                | undefined              |
| ----------- | ------------------- | ---------------------- |
| Type        | object              | undefined              |
| Assigned by | Developer           | JS Engine              |
| Use Case    | Intentional absence | Uninitialized variable |

```js
let x;
console.log(x); // undefined
let y = null;
console.log(y); // null
```

**Interview Tip:**  
Highlight intent behind assigning `null`.

**Keywords:**

- **Falsy**: Both are falsy in Boolean context.
    

---

### 14. **What is the difference between synchronous and asynchronous programming in JavaScript?** <font color="#00b050">done</font>

**Synchronous:**

- Executes sequentially.
    
- Blocks the thread.
    

**Asynchronous:**

- Non-blocking.
    
- Delegates tasks and moves on.
    

```js
console.log("1");
setTimeout(() => console.log("2"), 1000);
console.log("3");
// Output: 1, 3, 2
```

**Interview Tip:**  
Mention how JS handles async via the event loop.

**Keywords:**

- **Blocking**: Pauses execution until task is complete.
    

---

### 15. **What is the purpose of the map(), filter(), and reduce() methods in JavaScript arrays <font color="#00b050">done</font>

```js
const arr = [1, 2, 3, 4];
arr.map(x => x * 2); // [2, 4, 6, 8]
arr.filter(x => x % 2 === 0); // [2, 4]
arr.reduce((acc, val) => acc + val, 0); // 10
```

- **map()**: Transforms each element.
    
- **filter()**: Filters based on condition.
    
- **reduce()**: Aggregates to a single value.
    

**Interview Tip:**  
Mention immutability — original array is not changed.

**Keywords:**

- **Accumulator**: The result being built in `reduce()`.
    

---

### 16. **What are arrow functions in JavaScript, and how do they differ from regular functions?** <font color="#00b050">done</font>

**Differences:**

- No own `this`.
    
- Shorter syntax.
    
- Cannot be used as constructors.
    
- No `arguments` object.
    

```js
const add = (a, b) => a + b;
```

**Interview Tip:**  
Mention arrow functions in callbacks and class methods.

**Keywords:**

- **Lexical this**: Inherits `this` from surrounding scope.
    

---

### 17. **What are JavaScript modules, and how do you export and import them?** <font color="#00b050">done</font>

**Modules:**

- Files that export values for use elsewhere.

```js
// math.js
export function add(x, y) { return x + y; }

// main.js
import { add } from './math.js';
```

**Types:**

- Named exports: multiple per file.
- Default export: only one per file.

**Interview Tip:**  
Mention ES6 modules vs CommonJS (`require`, `module.exports`).

**Keywords:**

- **Tree-shaking**: Removing unused code during bundling.

---

### 18. **How can you create a deep copy of an object in JavaScript?** <font color="#00b050">done</font>
**Methods:**

1. `JSON.parse(JSON.stringify(obj))` – Fast, but fails for functions, dates, etc.
    
2. Recursion or structured cloning:
    

```js
structuredClone(obj);
```

3. Libraries like lodash (`_.cloneDeep(obj)`)
    

**Interview Tip:**  
Explain difference between shallow and deep copies.

**Keywords:**

- **Deep copy**: Duplicates all nested objects.
    

---

### 19. **What is the difference between for...of and for...in loops in JavaScript?** <font color="#00b050">done</font>

|Loop|Iterates over|
|---|---|
|`for...in`|Keys (enumerable properties)|
|`for...of`|Values (iterables like arrays)|

```js
const arr = ['a', 'b'];
for (let i in arr) console.log(i); // 0, 1
for (let v of arr) console.log(v); // 'a', 'b'
```

**Interview Tip:**  
Warn against using `for...in` with arrays.

**Keywords:**

- **Enumerable**: Property that shows up during iteration.
    

---

### 20. **What is the purpose of the setTimeout and setInterval functions in JavaScript?** <font color="#00b050">done</font>

```js
setTimeout(() => console.log("Hello after 1s"), 1000);
let id = setInterval(() => console.log("Repeats"), 1000);
clearInterval(id);
```

- `setTimeout`: Executes a function once after delay.
    
- `setInterval`: Repeats a function every interval.
    

**Interview Tip:**  
Mention how they're scheduled via the Web API and event loop.

**Keywords:**

- **Timer ID**: Identifier returned for cancellation.
    

---

### 21. **Can you explain the concept of "debouncing" and "throttling" in JavaScript?**

**Debouncing:** Delays execution until after a specified time has passed since the last time the function was invoked.

```js
function debounce(fn, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}
```

**Throttling:** Ensures a function is only called once per specified time interval.

```js
function throttle(fn, limit) {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      fn.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}
```

**Interview Tip:**  
Mention use cases: input fields (debounce), scroll or resize events (throttle).

---

### 22. **Explain the concept of event delegation.**

**Event delegation** uses event bubbling to attach a single event listener to a parent element to handle events from its children.

```js
document.getElementById("parent").addEventListener("click", function(e) {
  if (e.target && e.target.matches(".child")) {
    console.log("Child clicked", e.target);
  }
});
```

**Interview Tip:**  
Useful for dynamically added elements or reducing event listeners.

---

### 23. **What is the difference between call(), apply(), and bind() methods in JavaScript?**

- `call()`: Invokes a function with a given `this` and arguments.
    
- `apply()`: Same as `call()` but accepts arguments as an array.
    
- `bind()`: Returns a new function with a bound `this` and optional arguments.
    

```js
function greet(msg) { console.log(msg + this.name); }
const user = { name: "John" };
greet.call(user, "Hi ");
greet.apply(user, ["Hello "]);
const bound = greet.bind(user, "Hey ");
bound();
```

**Interview Tip:**  
Explain bind returns a new function; call/apply invoke immediately.

---

### 24. **How do you handle errors in JavaScript using try...catch? Provide an example.**

**Answer:**  
`try...catch` handles runtime errors.

```js
try {
  let result = riskyFunction();
} catch (error) {
  console.error("An error occurred:", error);
} finally {
  console.log("Always runs");
}
```

**Interview Tip:**  
Mention `finally` always executes.

---

### 25. **How can you check if a variable is an array in JavaScript?**

Use:

```js
Array.isArray(value);
```

Other methods:

```js
Object.prototype.toString.call(value) === '[object Array]';
value instanceof Array;
```

**Interview Tip:**  
`Array.isArray()` is the preferred way.

---

### 26. **Can you explain the concept of closures in JavaScript with an example?**

Closures give functions access to variables from an outer function even after that outer function has finished executing.

```js
function outer() {
  let counter = 0;
  return function inner() {
    counter++;
    return counter;
  };
}
const increment = outer();
console.log(increment()); // 1
```

---

### 27. **Explain the concept of "currying" in JavaScript.**

Currying transforms a function with multiple arguments into a series of functions each taking one argument.

```js
function add(a) {
  return function(b) {
    return a + b;
  };
}
add(2)(3); // 5
```

Useful for functional programming and partial application.

---

### 28. **What are JavaScript generators, and how do they differ from regular functions?**

Generators are special functions that can pause execution using `yield` and resume with `next()`.

```js
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}
const it = gen();
console.log(it.next()); // { value: 1, done: false }
```

**Interview Tip:**  
Explain state preservation and lazy evaluation.

---

### 29. **How does the this keyword behave in arrow functions compared to regular functions?**

Arrow functions do not bind their own `this`; they inherit from the enclosing context.

```js
const obj = {
  name: "Test",
  arrow: () => console.log(this.name),
  regular() { console.log(this.name); }
};
obj.arrow(); // undefined
obj.regular(); // "Test"
```

---

### 30. **What are JavaScript Symbols, and how are they used?**

Symbols are primitive data types used to create unique identifiers.

```js
const sym1 = Symbol("id");
const sym2 = Symbol("id");
sym1 === sym2; // false
```

Often used to define hidden properties or keys in objects to avoid collisions.

---

### 31. **How can you implement inheritance in JavaScript using ES6 classes?**

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const d = new Dog("Rex");
d.speak();
```

---

### 32. **How do you handle memory leaks in JavaScript applications?**

Common sources:

- Global variables
    
- Forgotten timers or intervals
    
- Detached DOM nodes
    
- Closures holding large data
    

Solutions:

- Use `let/const`, not global variables
    
- Clear timers: `clearInterval` / `clearTimeout`
    
- Remove event listeners
    
- Use browser dev tools: Performance tab, Heap snapshots
    

---

### 33. **What are JavaScript proxies, and how can they be used?**

A proxy wraps an object and intercepts operations (get, set, etc).

```js
const target = { name: "John" };
const proxy = new Proxy(target, {
  get(obj, prop) {
    return prop in obj ? obj[prop] : "Not Found";
  }
});
console.log(proxy.name); // "John"
console.log(proxy.age); // "Not Found"
```

---

### 34. **How do you handle exceptions in JavaScript?**

Use `try...catch`, or attach `.catch()` to Promises.

```js
try {
  riskyCode();
} catch (error) {
  console.error(error);
}
```

Async:

```js
fetch('/api')
  .then(res => res.json())
  .catch(err => console.error(err));
```

---

### 35. **What is the purpose of the Object.freeze() method in JavaScript?**

`Object.freeze(obj)` makes an object immutable: no new properties, deletion, or modification.

```js
const user = Object.freeze({ name: "Alice" });
user.name = "Bob"; // Fails silently or throws in strict mode
```

---

### 36. **Explain the concept of "memoization" in JavaScript.**

Memoization caches results of expensive function calls.

```js
function memoize(fn) {
  const cache = {};
  return function(x) {
    if (cache[x]) return cache[x];
    cache[x] = fn(x);
    return cache[x];
  };
}
```

Useful for performance optimization.

---

### 37. **What is the purpose of the Reflect API in JavaScript?**

`Reflect` is a built-in object with methods for interceptable operations, like `get`, `set`, `apply`, etc.

```js
const obj = { x: 1 };
Reflect.set(obj, "x", 2);
console.log(Reflect.get(obj, "x")); // 2
```

---

### 38. **How can you optimize the performance of a JavaScript application?**

- Use debouncing/throttling
    
- Avoid unnecessary DOM manipulation
    
- Use virtual DOM (React)
    
- Lazy loading
    
- Code splitting
    
- Use `requestAnimationFrame`
    
- Optimize loops and recursion
    

---

### 39. **What are JavaScript WeakMaps and WeakSets? How do they differ from Maps and Sets?**

- `WeakMap` and `WeakSet` allow only objects as keys/elements.
    
- They do not prevent garbage collection.
    
- No size property or iteration.
    

Use cases: Private data storage, memory-sensitive mappings.

---

### 40. **How does the import and export syntax work in ES6 modules?**

```js
// export
export const a = 1;
export default function() {}

// import
import { a } from './file.js';
import myFunc from './file.js';
```

Use named exports for multiple exports; default for one main export.

---

### 41. **What is the purpose of the Promise.all() method in JavaScript?**

`Promise.all()` is used to run multiple promises in parallel and wait until all of them are resolved (or one rejects).

```js
Promise.all([
  fetch('/api/1'),
  fetch('/api/2'),
  fetch('/api/3')
])
.then(responses => Promise.all(responses.map(res => res.json())))
.then(data => console.log(data))
.catch(err => console.error(err));
```

- If any promise fails, the whole `Promise.all` fails.
    

**Use case:** When multiple dependent async tasks can run in parallel.

---

### 42. **Can you explain the concept of "tail call optimization" in JavaScript?**

Tail Call Optimization (TCO) is a technique where the last function call in a recursive function is optimized by the engine to avoid adding a new stack frame.

```js
function factorial(n, acc = 1) {
  if (n === 0) return acc;
  return factorial(n - 1, n * acc); // tail-recursive
}
```

- Supported only in strict mode in some JS engines (not widely implemented yet).
    

---

### 43. **What are JavaScript decorators, and how are they used?**

Decorators are special functions that modify classes or methods. They are proposed in future ECMAScript versions.

```js
function readonly(target, name, descriptor) {
  descriptor.writable = false;
  return descriptor;
}

class Person {
  @readonly
  name() { return 'John'; }
}
```

- Requires Babel or TypeScript to use currently.
    

---

### 44. **How do you handle asynchronous iterations in JavaScript?**

Using `for await...of` on async iterables:

```js
async function fetchData(urls) {
  for await (let url of urls) {
    const res = await fetch(url);
    const data = await res.json();
    console.log(data);
  }
}
```

- The iterable must return Promises.
    

---

### 45. **What is the purpose of the Symbol.iterator in JavaScript?**

`Symbol.iterator` is a method that returns the default iterator for an object.

```js
const myObj = {
  items: [1, 2, 3],
  [Symbol.iterator]() {
    let i = 0;
    return {
      next: () => ({
        done: i >= this.items.length,
        value: this.items[i++]
      })
    };
  }
};

for (let item of myObj) console.log(item);
```

---

### 46. **How can you create a singleton pattern in JavaScript?**

A singleton ensures only one instance of a class exists.

```js
class Singleton {
  constructor() {
    if (Singleton.instance) return Singleton.instance;
    Singleton.instance = this;
    this.data = "singleton data";
  }
}

const a = new Singleton();
const b = new Singleton();
console.log(a === b); // true
```

---

### 47. **What are JavaScript mixins, and how are they implemented?**

Mixins allow sharing functionality across classes.

```js
const CanEat = Base => class extends Base {
  eat() { console.log("Eating"); }
};

const CanWalk = Base => class extends Base {
  walk() { console.log("Walking"); }
};

class Person {}
class SuperPerson extends CanEat(CanWalk(Person)) {}

const hero = new SuperPerson();
hero.eat(); hero.walk();
```

---

### 48. **How does the async attribute in script tags affect the loading of JavaScript files?**

```html
<script src="script.js" async></script>
```

- Downloads and executes the script asynchronously.
    
- Doesn't wait for HTML parsing.
    
- Order of execution is **not guaranteed**.
    

Use for third-party scripts (e.g., ads, analytics).

---

### 49. **What is the purpose of the Function.prototype.call() method in JavaScript?**

`call()` sets the `this` value and executes the function immediately.

```js
function greet() { console.log(this.name); }
const person = { name: "Alice" };
greet.call(person); // "Alice"
```

---

### 50. **How can you implement a stack data structure in JavaScript?**

```js
class Stack {
  constructor() {
    this.items = [];
  }
  push(item) {
    this.items.push(item);
  }
  pop() {
    return this.items.pop();
  }
  peek() {
    return this.items[this.items.length - 1];
  }
  isEmpty() {
    return this.items.length === 0;
  }
}
```

---

### 51. **What is the difference between Object.seal() and Object.freeze() methods in JavaScript?**

|Method|Prevent new properties|Prevent deletion|Prevent modification|
|---|---|---|---|
|`seal`|✅|✅|❌|
|`freeze`|✅|✅|✅|

```js
const obj = Object.seal({ name: "A" });
obj.name = "B"; // Allowed
obj.age = 25; // Ignored
```

---

### 52. **How do you handle circular references in JSON.stringify()?**

Use a replacer function or library:

```js
const seen = new WeakSet();
JSON.stringify(obj, (key, value) => {
  if (typeof value === "object" && value !== null) {
    if (seen.has(value)) return;
    seen.add(value);
  }
  return value;
});
```

Or use libraries like `flatted`.

---

✅ All 52 JavaScript Interview Questions answered in depth!