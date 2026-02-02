# 1️⃣ Variables & Data Types

### Write a function that accepts different data types and prints their type using typeof.

```javascript
function printDataType(value) {
  console.log("DataType Of", value, "=", typeof value);
}
printDataType(10);
printDataType("Atharv");
printDataType(true);
printDataType(undefined);
printDataType(null);
printDataType({ a: 1 });
printDataType([1, 2, 3]);
printDataType(function(){});
```

### Explain the difference between null and undefined with code.
    Undefined :- Variable is created but value is not given.
	  Null :- Variable is created and value set to null (empty).


```javascript
// undefined example
let x;
console.log(x);       
console.log(typeof x);

// null example
let y = null;
console.log(y);       
console.log(typeof y);
```

---

# 2️⃣ Functions

### Normal Function

```javascript
function add(a, b) {
  return a + b;
}
console.log(add(5, 3));
```

### Arrow Function

```javascript
const addNum = (a, b) => {
  return a + b;
};
console.log(addNum(5, 3));
```

---

# 3️⃣ Strings

### ✔ == vs ===

```javascript
console.log(5 == "5");          // true
console.log(null == undefined); // true

console.log(5 === "5");         // false
console.log(null === undefined);// false
```

### ✔ Convert "hello world" to Title Case

```javascript
let text = "hello world";
let title = text
  .split(" ")
  .map(word => word[0].toUpperCase() + word.slice(1))
  .join(" ");

console.log(title); // Hello World
```

---

# 4️⃣ Objects

### ✔ Create user object

```javascript
let user = {
  name: "Atharv",
  age: 21,
  city: "Pune"
};
console.log(user);
```

### ✔ Print keys + values

```javascript
const keys = Object.keys(user);
console.log("Keys:", keys);

const values = Object.values(user);
console.log("Values:", values);

Object.keys(user).forEach(key => {
  console.log(key + ":", user[key]);
});
```

### ✔ Add / Delete properties

```javascript
user.mobileNumber = "8459772255";
delete user.city;

console.log(user);
```

### ✔ Group objects by role

```javascript
const users = [
  { name: "Pratik", role: "admin" },
  { name: "Amit", role: "user" },
  { name: "Neha", role: "admin" },
  { name: "Ravi", role: "user" },
];

function groupByRole(users) {
  return users.reduce((group, user) => {
    const role = user.role;

    if (!group[role]) group[role] = [];

    group[role].push(user);
    return group;
  }, {});
}

console.log(groupByRole(users));
```

---

# 5️⃣ Array Methods – map, filter, reduce, reverse

```javascript
const arr = [20, 4, 23, 56, 1, 23, 65, 78, 45, 3, 9, 6, 23, 1, 50];

// map
const multiplied = arr.map(num => num * 2);
console.log(multiplied);

// filter
const greaterThan10 = arr.filter(num => num > 10);
console.log(greaterThan10);

// reduce
const sum = arr.reduce((acc, num) => acc + num, 0);
console.log(sum);

// reverse
const reversed = arr.slice().reverse();
console.log(reversed);
```

---

# 6️⃣ ES6 Features – Destructuring / Spread / Rest

### ✔ Object Destructuring

```javascript
const userObj = {
  name: "Akshay",
  age: 25,
  city: "Pune"
};

const { name, age } = userObj;

console.log(name);
console.log(age);
```

### ✔ Spread Operator

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const mergedArray = [...arr1, ...arr2];
console.log(mergedArray);
```

### ✔ Rest Parameter

```javascript
function sumNumbers(...numbers) {
  const total = numbers.reduce((acc, num) => acc + num, 0);
  console.log("Sum:", total);
}

sumNumbers(10, 20, 30, 40, 50);
```

---

# 7️⃣ Closures

### ✔ Counter using closure

```javascript
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
console.log(counter());
```

### ✔ Explanation

Inner functions access outer variables because of **lexical scope** and **closures**.

---

# 8️⃣ Callbacks

### ✔ Execute callback after 10 seconds

```javascript
function run10S(callback) {
  setTimeout(() => {
    callback();
  }, 10000);
}

run10S(() => {
  console.log("Executed after 10 seconds!");
});
```

---

# 9️⃣ Promises

### ✔ Promise Function

```javascript
function getUserData(userId) {
  return new Promise((resolve, reject) => {
    if (userId === 1) {
      resolve({
        name: "Akshay",
        age: 25,
        city: "Pune"
      });
    } else {
      reject("Invalid User ID");
    }
  });
}
```

### ✔ Using then / catch

```javascript
getUserData(1)
  .then(user => console.log("User Data:", user))
  .catch(error => console.log("Error:", error));
```

### ✔ Execution Order Output

```
1: Start
4: End
3: Promise
2: setTimeout
```

---

# 🔟 Async / Await

```javascript
async function fetchUser() {
  try {
    const user = await getUserData(1);
    console.log("User Data:", user);
  } catch (error) {
    console.log("Error:", error);
  }
}
fetchUser();
```

---

# 1️⃣1️⃣ DOM Manipulation

### ✔ Change text on click

```javascript
const message = document.getElementById("message");
const btn = document.getElementById("changeBtn");

btn.addEventListener("click", () => {
  message.textContent = "Text Changed!";
});
```

### ✔ Add list item

```javascript
const list = document.getElementById("list");
const addBtn = document.getElementById("addItem");

addBtn.addEventListener("click", () => {
  const newItem = document.createElement("li");
  newItem.textContent = "New Item";
  list.appendChild(newItem);
});
```

### ✔ Remove element

```javascript
const removeText = document.getElementById("removeMe");
const removeBtn = document.getElementById("removeBtn");

removeBtn.addEventListener("click", () => {
  removeText.remove();
});
```

### ✔ Show input live

```javascript
const inputBox = document.getElementById("inputBox");
const output = document.getElementById("output");

inputBox.addEventListener("input", () => {
  output.textContent = inputBox.value;
});
```

---

# 1️⃣2️⃣ Timers – Countdown

### Browser countdown timer

```html
<p id="display"></p>
<button id="start">Start Timer</button>

<script>
let count = 10;

document.getElementById("start").addEventListener("click", () => {
  const timer = setInterval(() => {
    document.getElementById("display").textContent = count;
    count--;

    if (count < 0) {
      document.getElementById("display").textContent = "Time's up!";
      clearInterval(timer);
    }
  }, 1000);
});
</script>
```

---


