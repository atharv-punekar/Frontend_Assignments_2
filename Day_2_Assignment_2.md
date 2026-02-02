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

### Write a normal function to add two numbers.

```javascript
function add(a, b) {
  return a + b;
}
console.log(add(5, 3));
```

### Convert a above function into an arrow function.

```javascript
const addNum = (a, b) => {
  return a + b;
};
console.log(addNum(5, 3));
```

---

# 3️⃣ Strings

### Write difference between == and === in java script with examples.
    “==” (Loose Equality) Compares only values & performs type implicit conversion.
	“===” (Strict Equality) Compares both value & data type

```javascript
console.log(5 == "5");          // true
console.log(null == undefined); // true

console.log(5 === "5");         // false
console.log(null === undefined);// false
```

### "hello world" convert to title case. 

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

### Create a user object with properties name, age, and city.

```javascript
let user = {
  name: "Atharv",
  age: 21,
  city: "Pune"
};
console.log(user);
```

### Print all keys and values using methods Object.keys, Object.values and forEach loop

```javascript
const keys = Object.keys(user);
console.log("Keys:", keys);

const values = Object.values(user);
console.log("Values:", values);

Object.keys(user).forEach(key => {
  console.log(key + ":", user[key]);
});
```

### Add new property mobileNumber and delete city properties dynamically.

```javascript
user.mobileNumber = "8459772255";
delete user.city;

console.log(user);
```

### Convert below array of object group by role

```javascript
const users = [
	{ name: "Pratik", role: "admin" },
	{ name: "Amit", role: "user" },
	{ name: "Neha", role: "admin" },
	{ name: "Ravi", role: "user" },
];

Output: 
{
  admin: [
    { name: "Pratik", role: "admin" },
    { name: "Neha", role: "admin" }
  ],
  user: [
    { name: "Amit", role: "user" },
    { name: "Ravi", role: "user" }
  ]
}
```

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

# 5️⃣ Array Methods :- 
    1. Use map to multiply each array element by 2.
    2. Use filter to find numbers greater than 10.
    3. Use reduce to find the sum of array elements.
    4. Reverse an array.

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

# 6️⃣ ES6 Features

###     1. Destructure an object and console name and age from it.
````javascript
const user = {
  		name: "Akshay",
  		age: 25,
  		city: "Pune"
	};
output : 
console.log(name); // Akshay
console.log(age); // 25
````

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

###     2. Merge two arrays using spread operator.
````javascript
Const arr1 = [1, 2, 3];
	const arr2 = [4, 5, 6];
 
Output: 
console.log(mergedArray);
// [1, 2, 3, 4, 5, 6]
````

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const mergedArray = [...arr1, ...arr2];
console.log(mergedArray);
```

###  Create a function accepting 5 numbers using rest parameters and display sum of all numbers from function.

```javascript
function sumNumbers(...numbers) {
  const total = numbers.reduce((acc, num) => acc + num, 0);
  console.log("Sum:", total);
}

sumNumbers(10, 20, 30, 40, 50);
```

---

# 7️⃣ Closures

### Create a counter function using closure.

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

### Explain how inner functions access outer variables.
	JavaScript uses Lexical Scope:
    Function can access variables from the place where it was created, not where it called
	So, inner functions can read and modify outer variables because:
		They are created inside that outer function
		They carry the surrounding scope with them
		JS engine keeps outer variables alive if inner function is still using them
	

---

# 8️⃣ Callbacks

### Create a function that accepts a callback and executes it after 10 seconds.

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

### Create a function called getUserData that:
    - Returns a Promise
    - Resolves with user details object contains name, age, city if userId is 1
    - Rejects with an error message if userId is  0
    - Handles the response using .then() and .catch()

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

### Guess the execution sequence of below code
````javascript
console.log("1: Start");
	setTimeout(() => {
		console.log("2: setTimeout");
}, 0);

Promise.resolve().then(() => {
	console.log("3: Promise");
});
console.log("4: End");
````


```
1: Start
4: End
3: Promise
2: setTimeout
```

---

# 🔟 Async / Await

### Convert the question 1 from assignment 9, to async/await with try , catch block.

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

###     1. Take one div with some text and change text of an element on button click.
````html
<div id="message">Hello World</div>
<button id="changeBtn">Change Text</button>
````

```javascript
const message = document.getElementById("message");
const btn = document.getElementById("changeBtn");

btn.addEventListener("click", () => {
  message.textContent = "Text Changed!";
});
```

### Add a new list item dynamically.
````html
<ul id="list"><li>Item 1</li></ul>
<button id="addItem">Add Item</button>
````

```javascript
const list = document.getElementById("list");
const addBtn = document.getElementById("addItem");

addBtn.addEventListener("click", () => {
  const newItem = document.createElement("li");
  newItem.textContent = "New Item";
  list.appendChild(newItem);
});
```

### Remove an element from the DOM.
````html
<p id="removeMe">Remove this text</p>
<button id="removeBtn">Remove</button>
````

```javascript
const removeText = document.getElementById("removeMe");
const removeBtn = document.getElementById("removeBtn");

removeBtn.addEventListener("click", () => {
  removeText.remove();
});
```

### Display input value on screen while typing.
````html
<input type="text" id="inputBox" />
<p id="output"></p>
````

```javascript
const inputBox = document.getElementById("inputBox");
const output = document.getElementById("output");

inputBox.addEventListener("input", () => {
  output.textContent = inputBox.value;
});
```

---

# 1️⃣2️⃣ Timers

### Create a countdown timer using setInterval.

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


