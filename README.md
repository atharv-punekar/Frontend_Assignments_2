# Frontend Day 2 Assignment 1

## Find and Fix the Bugs (JavaScript)

---

## 1. Variable Scope Issue

### CODE :-
```js
function printName() {

  if (true) {

    var name = "Akshay";

  }

  console.log(name);

}

printName();
````

**Bug :-** Variable scope issue

### Fixed CODE :-

```js
function printName() {
  if (true) {
    let name = "Akshay";
    console.log(name);
  }
}

printName();
```

**Reason :-**
`var` is function-scoped, whereas `let` is block-scoped. Therefore, the variable is accessible only inside the `if` block.

---

## 2. Strict Comparison Type Issue

### CODE :-

```js
let age = "18";

if (age === 18) {

  console.log("Adult");

} else {

  console.log("Minor");

}
```

**Bug :-** Strict comparison type issue

### Fixed CODE :-

```js
let age = 18;

if (age === 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

**Reason :-**
Strict equality (`===`) compares both value and type. `"18"` (string) is not equal to `18` (number).

---

## 3. Array Index Out of Range

### CODE :-

```js
const arr = [10, 20, 30];

for (let i = 0; i <= arr.length; i++) {
  console.log(arr[i]);
}
```

**Bug :-** Array index out of range

### Fixed CODE :-

```js
const arr = [10, 20, 30];

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

**Reason :-**
Array indices range from `0` to `length - 1`. Using `<=` accesses an undefined index.

---

## 4. Asynchronous Execution Issue

### CODE :-

```js
let data;

setTimeout(() => {
  data = "Loaded";
}, 1000);

console.log(data);
```

**Bug :-** Asynchronous execution issue

### Fixed CODE :-

```js
let data;

setTimeout(() => {
  data = "Loaded";
  console.log(data);
}, 1000);
```

**Reason :-**
`setTimeout` is asynchronous, so the log must be inside the callback to access the updated value.

---

## 5. Missing Return Statement

### CODE :-

```js
function add(a, b) {
  a + b;
}

const result = add(2, 3);
console.log(result);
```

**Bug :-** Missing return statement

### Fixed CODE :-

```js
function add(a, b) {
  return a + b;
}

const result = add(2, 3);
console.log(result);
```

**Reason :-**
Without a `return` statement, the function returns `undefined`.

---

## 6. Object Reference Behavior

### CODE :-

```js
const user = {
  name: "John",
  age: 25,
};

function updateAge(u) {
  u.age = 30;
}

updateAge(user);
console.log(user.age);
```

**Bug :-** No bug (object reference behavior)

### Fixed CODE :-

```js
// No change required
```

**Reason :-**
Objects are passed by reference, so changes made inside the function affect the original object.

---

## 7. Event Listener Function Execution Issue

### CODE :-

```html
<button id="btn">Click</button>

<script>
  const btn = document.getElementById("btn");
  btn.addEventListener("click", handleClick());

  function handleClick() {
    alert("Clicked");
  }
</script>
```

**Bug :-** Event listener function execution issue

### Fixed CODE :-

```html
<button id="btn">Click</button>

<script>
  const btn = document.getElementById("btn");
  btn.addEventListener("click", handleClick);

  function handleClick() {
    alert("Clicked");
  }
</script>
```

**Reason :-**
Passing `handleClick()` executes the function immediately. Instead, the function reference should be passed.

---

## 8. Promise Chain Break

### CODE :-

```js
fetch("https://api.example.com/data")
  .then((res) => {
    res.json();
  })
  .then((data) => {
    console.log(data);
  });
```

**Bug :-** Promise chain break

### Fixed CODE :-

```js
fetch("https://api.example.com/data")
  .then((res) => {
    return res.json();
  })
  .then((data) => {
    console.log(data);
  });
```

**Reason :-**
`res.json()` must be returned so that the next `.then()` receives the parsed data.

---

## 9. map Variable Issue

### CODE :-

```js
const nums = [1, 2, 3, 4];

const result = nums.map(No => {
  if (n % 2 === 0) {
    return n * 2;
  }
});

console.log(result);
```

**Bug :-** Variable name mismatch and missing return

### Fixed CODE :-

```js
const nums = [1, 2, 3, 4];

const result = nums.map(n => {
  if (n % 2 === 0) {
    return n * 2;
  }
  return n;
});

console.log(result);
```

**Reason :-**
An incorrect variable name caused an error, and the missing return statement resulted in `undefined` values.

---

## 10. Incorrect `this` Binding

### CODE :-

```js
const person = {
  name: "Amar",
  greet: () => {
    console.log("Hello " + this.name);
  },
};

person.greet();
```

**Bug :-** Incorrect `this` binding

### Fixed CODE :-

```js
const person = {
  name: "Amar",
  greet: function () {
    console.log("Hello " + this.name);
  },
};

person.greet();
```

**Reason :-**
Arrow functions do not have their own `this`. Regular functions correctly bind `this` to the object.

---

```
```
